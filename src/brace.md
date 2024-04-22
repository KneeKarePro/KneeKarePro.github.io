# KneeKarePro Brace
The brace is designed to be worn by patients with knee injuries. It is equipped with a microcontroller and potentiometer to monitor the knee movements. The microcontroller and potentiometer are integrated into the brace via some a breadboard and a potentiometer with a breakout board. 
The embedded system is responsible for monitoring the knee movements and sending the data to the web application. The data is sent via a websocket connection that is established between the microcontroller and the web application. The data is sent in the form of the angle of rotation of the knee. The web application then processes the data and displays it to the user. The user can then view the data and track their progress over time. The data is also stored in a database so that the user can view their progress over time. The user can also set goals for themselves and track their progress towards those goals. The user can also view their progress in the form of graphs and charts. The user can also view their progress in the form of a timeline. The user can also view their progress in the form of a calendar

## Design 
The brace is designed to be worn by patients with knee injuries. It is equipped with a microcontroller and potentiometer to monitor the knee movements. The microcontroller and potentiometer are integrated into the brace via some a breadboard and a potentiometer with a breakout board. The microcontroller embedded software was developed within the **arduino** using the **arduino-cli** for compilation and flashing. 
The microcontroller begins its setup process by establishing a soft access point(AP) from the **ESP32** and allowing for incoming connections from the web app. After the AP is established, we then define a client which is essentially our **TCP** server. The `loop()` phase of our design then passes through some conditional logic determining whether there is an established connection from another source. The code then goes into more logic which requests the analog value from the ADC and through linear interpolation, we convert our `u16` value into a angle range in degrees.

## Implementation

### Establishing a Soft Access Point(AP)
The following code snippet demonstrates the process of establishing a soft access point(AP) from the **ESP32** and allowing for incoming connections from the web app. 
```cpp
const char* SSID = "ESP32-AP";
const char* PASSWORD = "password";
WiFiServer server(80);

String header;

void setup() {
  // Set up the access point
  WiFi.mode(WIFI_AP);
  Serial.println("Setting up WiFi AP");
  WiFi.softAP(SSID, PASSWORD);
  Serial.println("WiFi AP started");
  IPAddress IP = WiFi.softAPIP();
  Serial.print("IP Address: ");
  Serial.println(IP);
}

void loop() {
  // Output to HTTP server
  WiFiClient client = server.available();
  if(client){
    Serial.println("New client");
    while(client.connected()){
      if(client.available()){
        char c = client.read();
        if(c == '\n'){
          int potValue = readPot();
          Serial.print("Potentiometer value: ");
          Serial.println(potValue);
          client.println("HTTP/1.1 200 OK");
          client.println("Content-type:text/html");
          client.println("Connection: close");
          client.println();
          client.println(potValue);
          break;
        }
        else if (c == '\r'){
          // Do nothing
        }
        else{
          header += c;
        }
    }
  }
  client.stop();
  Serial.println("Client disconnected");
  }
  else {
    Serial.println("No client connected");
    delay(1000);
  }
}
```

### Requesting the Analog Value from the ADC and Linear Interpolation
The following code explore the few functions we use in order to: 1) request the analog value from the ADC and 2) through linear interpolation, convert our `u16` value into a angle range in degrees. This is be no means a final state to our code, but for now this is a functional implementation.
```cpp
float readPot() {
  int analog = analogRead(potPin);
  // Base range of 0 - 104 and we need a multiplier to get the range of 0 - 280 
  // float multiplier = 1.0; 
  return floatMap(analog, 0, 65520, 0, 2800);
}

float floatMap(float x, float in_min, float in_max, float out_min, float out_max) {
  return (x - in_min) * (out_max - out_min) / (in_max - in_min) + out_min;
}
```

## Future Work
The future work for the KneeKarePro Brace includes migrating from a soft access point and connections through TCP polling to a bluetooth LE connection with a mobile device. The mobile device will then stream the real-time data to something like a `Google Firebase` for IoT data storage.
Another future work item is to implement a more robust RTOS for the ESP32, as the current implementation using `arduino` is not the most efficient for real-time data streaming. Something like `ESP-IDF` or `PlatformIO` could be possible solutions to this. Another solution to boosting resource efficiency is through and implementation base on Rust, however we would encounter some roadblocks such as the lack of support for the `Xtensa ISA` by `LLVM`.
