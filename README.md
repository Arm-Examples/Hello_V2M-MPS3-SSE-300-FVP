# Hello example for V2M-MPS3-SSE-300-FVP

Simple Hello World example for Arm V2M-MPS3 Board with Corstone SSE-300 Subsystem. The example can execute also on Arm Virtual Hardware (AVH) modeling the hardware. 
This example prints "Hello World" and a counter value via the standard output.

## Prerequisites

### Tools:
 - [CMSIS-Toolbox v2.0.0](https://github.com/Open-CMSIS-Pack/cmsis-toolbox/releases) or newer
 - [Microsoft Visual Studio Code](https://code.visualstudio.com/download) with Keil Studio Pack extension (optional, alternatively CLI can be used)
 - [Arm Compiler 6](https://developer.arm.com/Tools%20and%20Software/Arm%20Compiler%20for%20Embedded) (automatically installed when using Visual Studio Code with vcpkg)
 - Arm Virtual Hardware for Corstone-300 (when executing on a model)

## Build Solution/Project

### Using Visual Studio Code with extensions

Required tools described in file 'vcpkg-configuration.json' should be automatically installed by vcpkg. You can see the status of vcpkg in the status bar.

Required CMSIS packs need to be also installed. In case a required pack is missing, a notification window will pop-up to install the missing pack.

Open the 'CMSIS' view from the side bar, select desired 'Build Type' and press the 'Build' button.

### Using Command Line Interface (CLI)

Download required packs (not required when the packs are already available) by executing the following commands:
   ```sh
   csolution list packs -s hello.csolution.yml -m >packs.txt
   cpackget update-index
   cpackget add -f packs.txt
   ```
Build the project by execute the following command:
```sh
cbuild hello.csolution.yml
```

## Run the application using Arm Virtual Hardware (AVH)

### Using Command Line Interface (CLI)

Run the project by executing the following command:
```sh
VHT_MPS3_Corstone_SSE-300 -f vht_config.txt -a out/hello/V2M-MPS3-SSE-300-FVP/Debug/hello.axf --simlimit 20
```
