# Usage
The Web Application is split into a frontend and a backend. The frontend is built using React and Material-UI, while the backend is built using Node.js. The frontend is responsible for rendering the user interface and handling user interactions, while the backend is responsible for handling data storage and authentication. Luckily, usage of both services revolves around the same command.

## Network Configuration
In order to access the data from the KneeKarePro Brace, the device must be connected to the network hosted by the ESP32. The ESP32 will host a network with the SSID `ESP32-AP` and contain a password of... `password`. Groundbreaking security! After connecting, the backend polling machine can communicate with the ESP32's TCP server.

## Running the Web Application
To run the Web Application, navigate to the `WebApp` directory. If you have not already installed the repository and dependencies, please refer to the [Installation Guide](./install.md) before proceeding. Once you have installed the repository and dependencies, you can run the Web Application by running the following command in your terminal:

```bash
cd WebApp/knee-kare-pro/frontend && npm start
```
This will kickoff the frontend of the Web Application. To start the backend, open a new terminal window and run the following command:

```bash
cd WebApp/knee-kare-pro/backend && npm start
```
Now if you navigate to `http://localhost:3000` in your web browser, you should see the Web Application running. If you are not automatically redirected, you can manually navigate to the URL. If you see the login screen, you have successfully started the Web Application.
