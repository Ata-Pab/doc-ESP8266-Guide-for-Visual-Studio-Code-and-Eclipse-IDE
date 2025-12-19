<h1 align="left">ESP8266 VSCode & Eclipse Setup</h1>


- Open **Eclipse C/C++ IDE**

- Follow;  **File**  **>>**  **Import** **>>**  **C/C++** **>>** **Existing Code as Makefile Project**

<p align="center">
  <img src="https://user-images.githubusercontent.com/52567674/61786202-da358e80-ae15-11e9-89ff-edb318674e69.jpg">
</p>

- Choose an example project  from  `C:\msys32\home\User\esp\ESP8266_RTOS_SDK\examples`  file.

- Check Cross GCC option.

- Project File has been added to Project Explorer.

- Right Click to Project File and follow;  **Properties** **>>** **C/C++ Build** **>>** **Environment** **>>** **Add**

<p align="center">
  <img src="https://user-images.githubusercontent.com/52567674/61787152-e15d9c00-ae17-11e9-8a21-829b3a6dedb8.jpg">
</p>

**Name**: BATCH_BUILD, **Value**: 1
**Name**: IDF_PATH, **Value**:  "C:/msys32/home/User/esp/ESP8266_RTOS_SDK"
**Name**: PATH, **Value**:  "C:\msys32\usr\bin;C:\msys32\mingw32\bin;C:\msys32\opt\xtensa-lx106-elf\bin"

**Properties** **>>** **C/C++ General** **>>**  **CDT Cross GCC Built in Compiler Settings** : 
`${COMMAND} ${FLAGS} -E -P -v -dD “${INPUTS}”`
**Properties** **>>** **C/C++ General** **>>** **CDT GCC Build Output Parser**:  
`(g?cc)|([gc]\+\+)|(clang)`
additions were made.

**C/C++ Build: Behavior**  **>>**  Check  **Enable parallel build**

<p align="center">
  <img src="https://user-images.githubusercontent.com/52567674/61787337-41ecd900-ae18-11e9-9b5f-f50e95621f54.jpg">
</p>

- Right click to Project File **>>**  **Add Folder**  **>>**  Add a file which name is **libraries**

- Right click to  **libraries**  **>>**  Import: **General**:  **File System** **>>** Browse:  `C:\msys32\home\User\esp\ESP8266_RTOS_SDK\components`   

This step provides adding ESP8266 Libraries to Eclipse IDE. 

<p align="center">
  <img src="https://user-images.githubusercontent.com/52567674/61787313-36011700-ae18-11e9-95d7-9b6965614b94.jpg">
</p>

**_Flash Configuration_**:  Project File (Right click) **>>** **Build Targets** **>>** **create** **>>** **flash** 

<p align="center">
  <img src="https://user-images.githubusercontent.com/52567674/61787428-6ea0f080-ae18-11e9-9150-d88d7dc3eda2.jpg">
</p>

Other Files which ones are needed for compiling are on the follows;

- Firstly we should go to  `.settings`,  `.cproject` and  `.project` files location. These files exist in below location;

 `C:\msys32\home\User\esp\ESP8266_RTOS_SDK\examples\get-started\project_template`

- These files should be copy to project file. 
- The `.settings` file will remain intact and no changes will be made. 
- The sections in the html format (**project_template**) in the `.cproject` and `.project` files which ones are given on the follow should be replaced with the name of the opened project.

**_.cproject_**

<p align="center">
  <img src="https://user-images.githubusercontent.com/52567674/61787228-0e11b380-ae18-11e9-884b-8395c9624842.jpg">
</p>

**_.project_**

<p align="center">
  <img src="https://user-images.githubusercontent.com/52567674/61787278-25e93780-ae18-11e9-9779-c50730d28590.jpg">
</p>

After the additions given above, the contents of the file should be as follows;

<p align="center">
  <img src="https://user-images.githubusercontent.com/52567674/61787388-5f21a780-ae18-11e9-9734-ff202c5d6506.jpg">
</p>

Finally, you can build and flash the project.

- Project File (Right click) **>>** **Build Project** . (“make –j4”  command is used)

- If there is no error has seen on the output screen, code can be flashed to the ESP8266 Card.  **Build Targets** **>>**  **Flash** 

### **_ESP8266 USAGE WITH VISUAL STUDIO CODE_** ###

- Project file has copied from **examples** folder to **esp** folder. 

<p align="center">
  <img src="https://user-images.githubusercontent.com/52567674/61787367-53ce7c00-ae18-11e9-98e8-8f8508c525ea.jpg">
</p>

Some changes should be done in the project file. (For this example it is "pwm", you can select another project file). Steps followed;

- The file which name is `.vscode` has created. (Name should be same!)

_`c_cpp_properties.json`_
_`settings.json`_
_`tasks.json`_

“.JSON” files which are above have been added to `.vscode` folder. The contents of these files have been opened and changed with an application such as "Notepad++" or "CodeWriter".

**_c_cpp_properties.json_**

```
{
    "configurations": [
        {
            "name": "ESP32-Win",
            "includePath": [
                "${workspaceRoot}",
                "${workspaceRoot}/build/include",
                "${workspaceRoot}/build/",
                "C:/msys32/home/User/esp/ESP8266_RTOS_SDK/components/**",

                
                "C:/msys32/opt/xtensa-lx106-elf/include",
                "C:/msys32/opt/xtensa-lx106-elf/xtensa-lx106-elf/include",
                "C:/msys32/opt/xtensa-lx106-elf/xtensa-lx106-elf/include/c++/5.2.0",
                "C:/msys32/opt/xtensa-lx106-elf/lib/gcc/xtensa-lx106-elf/5.2.0/include",
                "C:/msys32/opt/xtensa-lx106-elf/lib/gcc/xtensa-lx106-elf/5.2.0/include-fixed"
            ],  
            "intelliSenseMode": "clang-x64",
            "browse": {
                "path": [
                    "${workspaceRoot}",
                    "${workspaceRoot}/build/include",
                    "${workspaceRoot}/build/",
                    "C:/msys32/home/User/esp/ESP8266_RTOS_SDK/components/**",
    
                   
                    "C:/msys32/opt/xtensa-lx106-elf/include",
                    "C:/msys32/opt/xtensa-lx106-elf/xtensa-lx106-elf/include",
                    "C:/msys32/opt/xtensa-lx106-elf/xtensa-lx106-elf/include/c++/5.2.0",
                    "C:/msys32/opt/xtensa-lx106-elf/lib/gcc/xtensa-lx106-elf/5.2.0/include",
                    "C:/msys32/opt/xtensa-lx106-elf/lib/gcc/xtensa-lx106-elf/5.2.0/include-fixed"
                    ],
                "limitSymbolsToIncludedHeaders": true,
                "databaseFilename": "${workspaceRoot}/.vscode/browse.vc.db"
            },
            "cStandard": "c11",
            "cppStandard": "c++17"
        }
    ],
    "version": 4
}
```

**_settings.json_**

```
{
    "terminal.integrated.shell.windows": "C:/msys32/mingw32.exe", //C:/msys32/usr/bin/bash.exe",
    
	"terminal.integrated.shellArgs.windows": [
	"--login",
	],
	"terminal.integrated.env.windows": {
		"CHERE_INVOKING": "1",
		"MSYSTEM": "MINGW32",
	},
	"files.associations": {
		"task.h": "c",
		"freertos.h": "c"
	},
}

```

**_tasks.json_**


```
{
    // See https://go.microsoft.com/fwlink/?LinkId=733558
    // for the documentation about the tasks.json format
    "version": "2.0.0",
    "tasks": [
        {
            "label": "F4",
            "group": "build",
            "command": "make",
            "type": "shell",
            "args": [
                "-j8",
                "app"
            ],
            "presentation": {
                "reveal": "always",
            },
        },
        {
            "label": "F5",
            "command": "make",
            "type": "shell",
            "args": [
                "-j8",
                "flash"
            ],
            "presentation": {
                "reveal": "always",
            },
        },
        {
            "label": "F8",
            "command": "make",
            "type": "shell",
            "args": [
                "-j8",
                "flash",
                "monitor"
            ],
            "presentation": {
                "reveal": "always",
            },
        },
        {
            "label": "F9",
            "command": "make",
            "type": "shell",
            "args": [
                "clean"
            ],
            "presentation": {
                "reveal": "always",
            },
        },
        {
            "label": "F12",
            "type":"shell",
            "windows": {
                "command": "C:/msys32/mingw32.exe",
                "args": [
                    "make",
                    "menuconfig"
                ]
            },
            "presentation": {
                "reveal": "always",
            },
            "problemMatcher": []
        }
    ]
}

```


The purpose of the above file changes;

- Showing the path to the required ESP8266 Libraries (Components)
- Runnig the **MINGW32 - bash** as terminal
- Showing location of the **_xtensa-lx106f-elf-gcc_** compiler

<p align="center">
  <img src="https://user-images.githubusercontent.com/52567674/61787516-9c863500-ae18-11e9-87dc-229439bafb96.jpg">
</p>

When you open a project file with Visual Studio Code, it should look like the following;

<p align="center">
  <img src="https://user-images.githubusercontent.com/52567674/61787544-ab6ce780-ae18-11e9-8e05-283ae56858b4.jpg">
</p>

- CmakeList and MakeFile files should absolutely exist.

- **Terminal** **>>**  **New Terminal**  **>>**  MINGW32 bash will be opened

- Serial Port configuration can be set with `make menuconfig` command.

- Project can be build with `make build` command.

<p align="center">
  <img src="https://user-images.githubusercontent.com/52567674/61787469-7bbddf80-ae18-11e9-8287-9cf0805d9969.jpg">
</p>

- Compiled project (code) can be flashed to the ESP8266 Card

<p align="center">
  <img src="https://user-images.githubusercontent.com/52567674/61787493-8e381900-ae18-11e9-996d-fb0b400774a6.jpg">
</p>

<p align="center"><strong>Author:</strong> Atalay PABUŞÇU</p>
