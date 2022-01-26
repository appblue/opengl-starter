# OpenGL for Linux

Simple OpenGL project that should run on Ubuntu/PopOS.

## setup libraries and tools

```console
$ sudo apt-get install cmake pkg-config
$ sudo apt-get install mesa-utils libglu1-mesa-dev freeglut3-dev mesa-common-dev
$ sudo apt-get install libglew-dev libglfw3-dev libglm-dev
$ sudo apt-get install libao-dev libmpg123-dev
$ cd /usr/local/lib/
$ sudo git clone https://github.com/glfw/glfw.git
$ cd glfw/
$ sudo cmake .
$ sudo make
$ sudo make install
```

## setup GLAD loader

Download multi-lanuguage loader-generator (GALD) from <https://glad.dav1d.de/> and follow the steps:

* Set the language to C++ and choose the specification as OpenGL.
* In the API section, select gl version of at least 3.3, make sure the profile is set to Core, and that the Generate a loader option is ticked.
* Ignore the extensions and click Generate to produce the resulting library files.
* GLAD, by now, should have provided you a zip file: `glad.zip` containing two folders (include and src).
* Copy the folders inside include (glad and KHR) into your include(s) directory: `cp -R include/* /usr/include/`
* Now copy the file `glad.c` inside the src folder to your current working directory.

```console
$ unzip -l glad.zip 
$ cd /usr
$ ls
$ cd -
$ unzip glad.zip 
$ mv src/glad.c ~/_work_/opengl
$ sudo cp -R include/* /usr/include/
```

## build and run

Use `make` to build the binary, or run the command show below:

```console
$ g++ triangle.cpp glad.c -ldl -lglfw
$ ./triangle
```

Note: the code in the triangle.cpp is taken from excellent website on OpenGL programming: <https://learnopengl.com/>
