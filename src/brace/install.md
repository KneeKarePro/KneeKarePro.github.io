# Installation
The current software development environment for the KneeKarePro Brace is the **Arduino CLI**. The **Arduino CLI** is a command line interface that allows for the compilation and uploading of code to an **Arduino** board. The **Arduino CLI** is a lightweight alternative to the **Arduino IDE** and is more suitable for automation and integration into other development environments. The **Arduino CLI** is used in conjunction with a `justfile`, which is a modern implementation of a `makefile`. 

## Prerequisites
### **Arduino CLI**
For more information regarding the installation of the **Arduino CLI**, please refer to the [official documentation](https://arduino.github.io/arduino-cli/0.35/installation/) for the **Arduino CLI**.
The **Arduino CLI** can be installed on a range of operating systems, including Windows, MacOS, and Linux. After the installation of the **Arduino CLI**, the `arduino-cli` command should be available in the terminal.
After installing the **Arduino CLI**, the next step is to install the necessary **Arduino** board support packages. The **Arduino** board support packages are required to compile and upload code to an **Arduino** board. The **Arduino** board support packages can be installed using the `arduino-cli` command. 
To install the **ESP32** board support package, use the following command:
```bash
arduino-cli config init
```
This command initializes the **Arduino CLI** configuration. After initializing the configuration, the next step is to add the **ESP32** board support package. The **ESP32** board support need to be added to the following section of the configuration:
```yaml

board_manager:
    additional_urls:
        - https://dl.espressif.com/dl/package_esp32_index.json
```
After adding the **ESP32** board support package, the next step is to install the **ESP32** board support package. The **ESP32** board support package can be installed using the following command:
```bash
arduino-cli core update-index
arduino-cli core install esp32:esp32
```

### **Justfile**
The `just` program is a command runner that can be used to run commands from a `justfile`. The `justfile` is a modern implementation of a `makefile` and is used to automate the compilation and uploading of code to an **Arduino** board. The `just` program can be installed by following the specific instructions on the [official documentation](https://just.systems/man/en/chapter_1.html). Running commands with `just` is not necessary, but it is nice to have.
