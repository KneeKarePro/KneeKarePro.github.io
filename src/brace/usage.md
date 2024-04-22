# Usage
The usage of the development environment for the KneeKarePro Brace is the **Arduino CLI**. The **Arduino CLI** is a command line interface that allows for the compilation and uploading of code to an **Arduino** board. The **Arduino CLI** is a lightweight alternative to the **Arduino IDE** and is more suitable for automation and integration into other development environments. The **Arduino CLI** is used in conjunction with a `justfile`, which is a modern implementation of a `makefile`.
There are four main processes that are involved in the usage of the **Arduino CLI**: **building**, **flashing**, **monitoring**, and **serving**. The **building** process involves compiling the code and generating the binary file. The **flashing** process involves uploading the binary file to the **Arduino** board. The **monitoring** process involves viewing the serial output from the **Arduino** board. The **serving** process involves establishing a soft access point(AP) from the **ESP32** and allowing for incoming connections from the web app.

## Building
The **building** process involves compiling the code and generating the binary file. The following command can be used to build the code:
```bash
just build
```
or
```bash
just b
```
The manual command to build the code is:
```bash
arduino-cli compile --fqbn esp32:esp32:esp32doit-devkit-v1 .
```

## Flashing
The **flashing** process involves uploading the binary file to the **Arduino** board. There are two main types of flashing: flashing and hard flashing. The later wipes and verifies the binary before and after flashing respectively. The following command can be used to flash the code normally:
```bash
just flash
```
or
```bash
just f
```
The manual command to flash the code is:
**For Linux**
```bash
arduino-cli upload -p /dev/ttyUSB0 --fqbn esp32:esp32:esp32doit-devkit-v1
```
**For MacOS**
```bash
arduino-cli upload -p /dev/cu.usbserial-0001 --fqbn esp32:esp32:esp32doit-devkit-v1
```
To hardflash the code, the following command can be used:
```bash
just hardflash
```
or
```bash
just hf
```
The manual command to hardflash the code is:
```bash
arduino-cli upload -p /dev/cu.usbserial-0001 --fqbn esp32:esp32:esp32doit-devkit-v1 -t
```

## Monitoring
The **monitoring** process involves viewing the serial output from the **Arduino** board. The following command can be used to monitor the serial output:
```bash
just monitor
```
or
```bash
just m
```
The manual command to monitor the serial output is:
```bash
arduino-cli serial monitor -p /dev/cu.usbserial-0001
```
or 
```bash
arduino-cli serial monitor -p /dev/ttyUSB0
```

## Serving
The **serving** process involves starting up a demo `node.js` server that can be used to interact with the **Arduino** board. The following command can be used to start the server:
```bash
just serve
```
or
```bash
just s
```
The manual command to start the server is:
```bash
node server.js
```
