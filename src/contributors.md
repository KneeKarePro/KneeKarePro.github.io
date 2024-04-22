# Contributors
Our team consists of the following members:
- Cole Rottenberg
- Sebastion Lopez
- Nicole Meers
- Daniyal Ansari

We are split into two subteams: hardware and software. The hardware team is responsible for the design and implementation of the KneeKarePro Brace, while the software team is responsible for the design and implementation of the KneeKarePro Web Application. The hardware team consists of Cole Rottenberg and Sebastion Lopez, while the software team consists of Nicole Meers and Daniyal Ansari.

## Hardware Team

**Cole Rottenberg** is responsible for the design and implementation of the KneeKarePro Brace. He has experience with embedded systems and microcontrollers, and is excited to apply his knowledge to this project. Cole has been working on the communication between the microcontroller and the web application. The team achieved this via establishing a soft access point(AP) from the **ESP32** and having a mobile device, like a laptop, connect to the network and establish a websocket from the AP and poll data.

**Sebastion Lopez** is responsible for the design and implementation of the KneeKarePro Brace. He has experience with embedded systems and microcontrollers, and is excited to apply his knowledge to this project. Sebastion has been working on the design of the knee brace and the integration of the microcontroller and potentiometer. The team achieved this by designing a knee brace that can be worn by patients with knee injuries and integrating a microcontroller and potentiometer to monitor the knee movements. Initial, he worked with the **TrinKey Rotary Encoder**, but moved towards a more analog device for a higher resolution of our analog.

## Software Team

**Nicole Meers** is responsible for the design and implementation of the KneeKarePro Web Application. She has experience with web development and is excited to apply her knowledge to this project. Nicole has been working on the internal design and function of the web app. 

**Daniyal Ansari** is responsible for the design and implementation of the KneeKarePro Web Application. He has experience with web development and is excited to apply his knowledge to this project. Daniyal has been working on the external design and user interface of the web app. He has been working on the front-end of the web application, and has been using **React** to create the user interface. He has also been working on the back-end of the web application, and has been using **Node.js** to create the server. The back-end establishes a websocket connection with the **ESP32** and begins polling potentiometer data that has been transformed to reflect the angle of rotation.
