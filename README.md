# Hello example for V2M-MPS3-SSE-300-FVP

This is a simple "Hello World" example for the Arm V2M-MPS3 board with a Corstone SSE-300 subsystem. The example also executes on Arm Virtual Hardware (AVH) modeling the hardware. This example prints "Hello World" and a counter value via the standard output.

[![Keil Studio Cloud - Import Project](https://img.shields.io/badge/Keil_Studio_Cloud-Import_Project-0091bd?logo=arm&logoColor=0091bd)](https://studio.keil.arm.com/?import=https://github.com/Arm-Examples/Hello_V2M-MPS3-SSE-300-FVP.git)
[![example workflow](https://img.shields.io/github/actions/workflow/status/Arm-Examples/Hello_V2M-MPS3-SSE-300-FVP/ci.yml?logo=arm&logoColor=0091bd&label=Example%20Publishable)](https://www.keil.arm.com/)

## Arm Tools Artifactory

To facilitate tool integration, Arm provides critical foundation tools in an artifactory. The following tools are installed via the `vcpkg-configuration.json` file. In addition utilities such as CMake and Ninja are installed.

URL/Tool       | Description
:--------------|:-------------------
[https://www.keil.arm.com/artifacts/#models/arm/avh-fvp](https://www.keil.arm.com/artifacts/#models/arm/avh-fvp)                      | [Arm Virtual Hardware FVP Models](https://arm-software.github.io/AVH/main/simulation/html/Using.html)
[https://www.keil.arm.com/artifacts/#tools/open-cmsis-pack/cmsis-toolbox](https://www.keil.arm.com/artifacts/#tools/open-cmsis-pack/cmsis-toolbox)  | [CLI Build System for CMSIS-Pack based projects](https://github.com/Open-CMSIS-Pack/cmsis-toolbox/blob/main/docs/README.md#cmsis-toolbox)
[https://www.keil.arm.com/artifacts/#compilers/arm/armclang](https://www.keil.arm.com/artifacts/#compilers/arm/armclang)      | [Arm Compiler for Embedded](https://developer.arm.com/Tools%20and%20Software/Arm%20Compiler%20for%20Embedded) (commercial)
[https://www.keil.arm.com/artifacts/#compilers/arm/arm-none-eabi-gcc](https://www.keil.arm.com/artifacts/#compilers/arm/arm-none-eabi-gcc) | [Arm GNU Toolchain](https://developer.arm.com/Tools%20and%20Software/GNU%20Toolchain) (community supported); not recommended for Cortex-M with Helium
[https://www.keil.arm.com/artifacts/#debuggers/arm/armdbg](https://www.keil.arm.com/artifacts/#debuggers/arm/armdbg) | Arm Debugger


## Build Solution/Project

### Using Visual Studio Code with extensions

Required tools described in file `vcpkg-configuration.json` are automatically installed by the VS code extensions. You can see the status of the process in the status bar.

Required CMSIS-Packs also need to be installed. In case a required pack is missing, a notification window will pop-up to install the missing pack.

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

## Run and debug the application using Arm Virtual Hardware (AVH)

*Note:* AVH is only available on Windows PCs and Linux machines.

### Run the application using Command Line Interface (CLI)

Run the project by executing the following command:
```sh
FVP_Corstone_SSE-300 -f vht_config.txt -a out/hello/V2M-MPS3-SSE-300-FVP/Debug/hello.axf --simlimit 20
```

### Debug the application

Make sure that you have selected the virtual device in the Device Manager ("Corstone SSE 300"). In the CMSIS view, click on the debug button at the top to start the debug session.
