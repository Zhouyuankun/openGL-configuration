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

![](https://raw.githubusercontent.com/Zhouyuankun/openGL-configuration/main/res/pic1.jpg)

![](C:\Users\Celeglow%20Zhou\Desktop\OpenGL%20Build%20Workspace\pic2.jpg)

STEP 2 Compile 

When you press "generate" and "open project", you will be directed to the visual studio,then

![](C:\Users\Celeglow%20Zhou\Desktop\OpenGL%20Build%20Workspace\pic3.jpg)

STEP 3 Configuration

Open your module binary folder(the one you designate when you use CMake), locate /code/Debug, you will found the lib and dll you need.

For GLFW, you only need **glfw3.lib**

For ASSIMP, you need both **assimp-vc142-mtd.lib** and **assimp-vc142-mtd.dll** 

![](C:\Users\Celeglow%20Zhou\Desktop\OpenGL%20Build%20Workspace\pic4.jpg)

Open your openGL project and configure the include and lib

![](C:\Users\Celeglow%20Zhou\Desktop\OpenGL%20Build%20Workspace\pic5.jpg)

![](C:\Users\Celeglow%20Zhou\Desktop\OpenGL%20Build%20Workspace\pic6.jpg)

![](C:\Users\Celeglow%20Zhou\Desktop\OpenGL%20Build%20Workspace\pic7.jpg)

The "include" folder is in the module folder-> include(maybe the module binary folder you CMaked has an include folder as well, you at better combine these two include folders)

![](C:\Users\Celeglow%20Zhou\Desktop\OpenGL%20Build%20Workspace\pic8.jpg)

After configured include, next configure lib

![](C:\Users\Celeglow%20Zhou\Desktop\OpenGL%20Build%20Workspace\pic9.jpg)

![](C:\Users\Celeglow%20Zhou\Desktop\OpenGL%20Build%20Workspace\pic10.jpg)

For .dll file you need, you have to put it in your project .exe same directory

![](C:\Users\Celeglow%20Zhou\Desktop\OpenGL%20Build%20Workspace\pic11.jpg)

OK ! That's all for the first type !

**Direct use**

you just need to download the files and configure the include path in your project as have mentioned.

For <u>GLAD</u>, after your finished your online service configuration(you would better search the Internet to find how to configure), you will get a folder.  

Add glad.c (/glad/src/glad.c) file to your project(it means put glad.c in the same dir as your project main.cpp, and make it visiable on your visual studio). 

![](C:\Users\Celeglow%20Zhou\Desktop\OpenGL%20Build%20Workspace\pic12.jpg)

Configure "include" folder(/glad/include) to your project Include path as have mentioned.

For <u>STB_IMAGE</u>, simply add stb_image.h to your project(as glad.c)

For <u>GLM,</u> simply configure "include" folder to your project Include path as have mentioned

OK! That's all for the second type !

Check whether you forget to configure something

![](C:\Users\Celeglow%20Zhou\Desktop\OpenGL%20Build%20Workspace\pic13.jpg)

![](C:\Users\Celeglow%20Zhou\Desktop\OpenGL%20Build%20Workspace\pic14.jpg)

![](C:\Users\Celeglow%20Zhou\Desktop\OpenGL%20Build%20Workspace\pic15.jpg)

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

![](/Users/celeglow/Desktop/OpenGL%20Build%20Workspace/pic16.jpg)

STEP 2 Compile

Simply press "generate", the 

STEP 3 Configuration

All include files can be found in /usr/local/include

All lib files can be found in /usr/local/lib

For GLFW, you only need **libglfw3.a**

For ASSIMP, you only need  **libassimp.5.0.0.dylib**

Configure the head file path and lib file path

![](/Users/celeglow/Desktop/OpenGL%20Build%20Workspace/pic17.jpg)

In Build Phases-> Link Binary With Libraries :

Add these

- Cocoa

- OpenGL

- IOKit

- CoreVideo

- libglfw3.a

- libassimp.5.0.0.dylib

![](/Users/celeglow/Desktop/OpenGL%20Build%20Workspace/pic18.jpg)

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
