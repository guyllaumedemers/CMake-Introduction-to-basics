# CMake (language), Introduction to basics

### Using a build system and why it matters.

A build system is a broad term that groups together a set of tools used to generally compile and link source code, but it can also include auxiliary tools used during a build process.

#### Project

Example details are grouped into subject related points and showcase investigation result on the subject of build system and `CMake`. Further details will be provided on more advance features that are covered in the making of our examples.

#### What this README.md is not

Be aware that some of the tooling used in the making of this `Demo` project won't be covered here. External documentations will be provided for your own benefit, which in most case, are also where most of the information mentioned here will be coming from.

## What's a build system

**Wikipedia** : "Build automation is the process of automating the creation of a software build and the associated processes including: compiling computer source code into binary code, packaging binary code, and running automated tests."

* [Make](https://en.wikipedia.org/wiki/Make_(software))
* [Ninja](https://en.wikipedia.org/wiki/Ninja_(build_system))
* [...](https://en.wikipedia.org/wiki/List_of_build_automation_software)

## CMake

**Wikipedia** : "[CMake](https://en.wikipedia.org/wiki/CMake) is a cross-platform software for build automation, testing, packaging and installation of software by using a compiler-independent method. CMake is not a build system itself. It generates another system's build files and can invoke native build environments such as Make, Qt Creator, Ninja, Android Studio, Apple's Xcode, and Microsoft Visual Studio."

#### Generators

The build files are configured depending on the generator used (e.g. Unix Makefiles for make) and associated toolchain files. Advanced users can also create and incorporate additional makefile generators to support their specific compiler and OS needs. The generation process and the output can be fine-tuned via target properties.

* [Makefile Generators]()
* [Ninja Generators]()
* [Visual Studio Generators]()
* [...](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html)

#### Build process

The build of a program or library with CMake is a two-stage process. First, build files (usually scripts) are created (generated) from configuration files (CMakeLists.txt scripts) written in CMake language. Then the platform's native build tools that can read these build files (native toolchain) are invoked either manually externally or via cmake --build for actual building of programs (build targets). The generator specified by the user on the commandline determines which build tool chain to use.

## An image worth a thousand word

![build_process](https://github.com/guyllaumedemers/CMake-Introduction-to-basics/blob/master/res/Build_process.png)

> Tips : An alternative to CMake that offer a simpler approach to build file configuration [Premake](https://premake.github.io/).
