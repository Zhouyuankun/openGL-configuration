# OpenGL Build Workspace Environment

---------

> The basic module needed are [GLFW](http://www.glfw.org/download.html), [GLAD](http://glad.dav1d.de/), [STB_IMAGE](https://github.com/nothings/stb/blob/master/stb_image.h), [GLM](https://glm.g-truc.net/0.9.8/index.html) and [ASSIMP](http://assimp.org/main_downloads.html)
> 
> The modules can be divided into two types concerned with their configuration
> 
> **Need CMake** GLFW ASSIMP
> 
> **Direct Use** GLAD STB_IMAGE GLM
> 
> The following tutorial will focus on these two type 

## For Windows User:

*Visual Studio as an example*

**Need CMake**

GLFW needs CMake and configure include and lib(static)

ASSIMP needs CMake and configure include and lib(static & dynamic)

STEP 1 CMake

Download the module and unzip it, then

![](https://github.com/Zhouyuankun/openGL-configuration/blob/main/res/pic1.jpg?raw=true)

![](https://github.com/Zhouyuankun/openGL-configuration/blob/main/res/pic2.jpg?raw=true)

STEP 2 Compile 

When you press "generate" and "open project", you will be directed to the visual studio,then

![](https://github.com/Zhouyuankun/openGL-configuration/blob/main/res/pic3.jpg?raw=true)

STEP 3 Configuration

Open your module binary folder(the one you designate when you use CMake), locate /code/Debug, you will found the lib and dll you need.

For GLFW, you only need **glfw3.lib**

For ASSIMP, you need both **assimp-vc142-mtd.lib** and **assimp-vc142-mtd.dll** 

![](https://github.com/Zhouyuankun/openGL-configuration/blob/main/res/pic4.jpg?raw=true)

Open your openGL project and configure the include and lib

![](https://github.com/Zhouyuankun/openGL-configuration/blob/main/res/pic5.jpg?raw=true)

![](https://github.com/Zhouyuankun/openGL-configuration/blob/main/res/pic6.jpg?raw=true)

![](https://github.com/Zhouyuankun/openGL-configuration/blob/main/res/pic7.jpg?raw=true)

The "include" folder is in the module folder-> include(maybe the module binary folder you CMaked has an include folder as well, you at better combine these two include folders)

![](https://github.com/Zhouyuankun/openGL-configuration/blob/main/res/pic8.jpg?raw=true)

After configured include, next configure lib

![](https://github.com/Zhouyuankun/openGL-configuration/blob/main/res/pic9.jpg?raw=true)

![](https://github.com/Zhouyuankun/openGL-configuration/blob/main/res/pic10.jpg?raw=true)

For .dll file you need, you have to put it in your project .exe same directory

![](https://github.com/Zhouyuankun/openGL-configuration/blob/main/res/pic11.jpg?raw=true)

OK ! That's all for the first type !

**Direct use**

you just need to download the files and configure the include path in your project as have mentioned.

For <u>GLAD</u>, after your finished your online service configuration(you would better search the Internet to find how to configure), you will get a folder.  

Add glad.c (/glad/src/glad.c) file to your project(it means put glad.c in the same dir as your project main.cpp, and make it visiable on your visual studio). 

![](https://github.com/Zhouyuankun/openGL-configuration/blob/main/res/pic12.jpg?raw=true)

Configure "include" folder(/glad/include) to your project Include path as have mentioned.

For <u>STB_IMAGE</u>, simply add stb_image.h to your project(as glad.c)

For <u>GLM,</u> simply configure "include" folder to your project Include path as have mentioned

OK! That's all for the second type !

Check whether you forget to configure something

![](https://github.com/Zhouyuankun/openGL-configuration/blob/main/res/pic13.jpg?raw=true)

![](https://github.com/Zhouyuankun/openGL-configuration/blob/main/res/pic14.jpg?raw=true)

![](https://github.com/Zhouyuankun/openGL-configuration/blob/main/res/pic15.jpg?raw=true)

Tips:

1. If you the function in stb_image.h can't use, it maybe

```
#define STB_IMAGE_IMPLEMENTATION //Needed before include
#include "stb_image"
```

2. The char * variable of Windows path should be written as ("C:\\\my\\\use"), '\' single is wrong.

3. Visual studio don't recognize .obj file(3D file), don't add it to your **project resources**, only add other resource files except for that. You can specify the full file path when you need load that .obj file.

## For MacOS User:

*Xcode as an example*

**Need CMake**

GLFW needs CMake and configure include and lib(static)

ASSIMP needs CMake and configure include and lib(static & dynamic)

STEP 1 CMake

(the step is identical to the Windows, so please see the steps above)

Use the defalut setting(Unix Makefiles) for generator

![](https://github.com/Zhouyuankun/openGL-configuration/blob/main/res/pic16.jpg?raw=true)

STEP 2 Compile

Simply press "generate", the 

STEP 3 Configuration

All include files can be found in /usr/local/include

All lib files can be found in /usr/local/lib

For GLFW, you only need **libglfw3.a**

For ASSIMP, you only need  **libassimp.5.0.0.dylib**

Configure the head file path and lib file path

![](https://github.com/Zhouyuankun/openGL-configuration/blob/main/res/pic17.jpg?raw=true)

In Build Phases-> Link Binary With Libraries :

Add these

- Cocoa

- OpenGL

- IOKit

- CoreVideo

- libglfw3.a

- libassimp.5.0.0.dylib

![](https://github.com/Zhouyuankun/openGL-configuration/blob/main/res/pic18.jpg?raw=true)

OK ! That's all for the first type !

**Direct use**

you just need to download the files and configure the include path in your project as have mentioned.

For <u>GLAD</u>, after your finished your online service configuration(you would better search the Internet to find how to configure), you will get a folder.

Add glad.c (/glad/src/glad.c) file to your project(it means put glad.c in the same dir as your project main.cpp, and make it visiable on your Xcode).

Put the "include" folder contents to (/usr/local/include), you need to add header search path to your project, as above have mentioned

For <u>STB_IMAGE</u>, simply add stb_image.h to your project(as glad.c)

For <u>GLM,</u> simply put the "include" folder contents to (/usr/local/include), if you already set the header file path for your project, there is no need to do it again.

OK! That's all for the second type !

Tips:

1. If you the function in stb_image.h can't use, it maybe

```
#define STB_IMAGE_IMPLEMENTATION //Needed before include
#include "stb_image"
```

2. The char * variable of MacOS path should be written as full path even if it is put in the same dir as main.cpp, or the file can not be found.
