# CMake (language), Introduction to basics

### Using a build system and why it matters.

**Wikipedia** : "Build automation is the process of automating the creation of a software build and the associated processes including: compiling computer source code into binary code, packaging binary code, and running automated tests."

#### Project

Example details are grouped into subject related points and showcase investigation result on the subject of build system and `CMake`. Further details will be provided on more advance features that are covered in the making of our examples.

#### What this README.md is not

Be aware that some of the tooling used in the making of this `Demo` project won't be covered here. External documentations will be provided for your own benefit, which in most case, are also where most of the information mentioned here will be coming from.

## What's a build system

A build system describes how to build a project's executables and libraries from its source code using a build tool to automate the process. For example, a build system may be a Makefile for use with a command-line `make` tool or a project file for an Integrated Development Environment (IDE).

* [Make](https://en.wikipedia.org/wiki/Make_(software))
* [Ninja](https://en.wikipedia.org/wiki/Ninja_(build_system))
* [MSBuild](https://en.wikipedia.org/wiki/MSBuild)
* [...](https://en.wikipedia.org/wiki/List_of_build_automation_software)

## CMake

**Wikipedia** : "[CMake](https://en.wikipedia.org/wiki/CMake) is a cross-platform software for build automation, testing, packaging and installation of software by using a compiler-independent method. CMake is not a build system itself. It generates another system's build files and can invoke native build environments such as Make, Qt Creator, Ninja, Android Studio, Apple's Xcode, and Microsoft Visual Studio."

#### Build process

The build of a program or library with CMake is a two-stage process. First, build files (usually scripts) are created (generated) from configuration files (CMakeLists.txt scripts) written in the CMake language. Then the platform's native build tools that can read these build files (native toolchain) are invoked either manually externally or via `cmake --build` for actual building of programs (build targets). The generator specified by the user on the command-line determines which build tool chain to use.

#### Generators

The build files are configured depending on the generator used (e.g. Unix Makefiles for make) and associated toolchain files. Advanced users can also create and incorporate additional makefile generators to support their specific compiler and OS needs. The generation process and the output can be fine-tuned via target properties.

* [Makefile Generators](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html#makefile-generators)
* [Ninja Generators](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html#ninja-generators)
* [Visual Studio Generators](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html#visual-studio-generators)
* [...](https://cmake.org/cmake/help/latest/manual/cmake-generators.7.html)

## An image worth a thousand word

![build_process](https://github.com/guyllaumedemers/CMake-Introduction-to-basics/blob/master/res/Build_process.png)

# Building a project

To generate a build system with CMake, the following must be selected:

* [Source Tree]() : The top-level directory containing source files provided by the project.
* [Build Tree]() : The top-level directory in which build system files and build output artifacts (e.g. executables and libraries) are to be stored.
* [Generator]() : The kind of build system to generate.

### How to build a Binary target

Executables and libraries are defined using the `add_executable()` and `add_library()` commands. The resulting binary files have appropriate PREFIX, SUFFIX and extensions for the platform targeted.

#### Building an executable

```
C:> cmake -B out/build -S .
```
**Hint** : `Visual Studio Generator` is invoked implicitly by the Integrated development environment (IDE) command-line interface (CLI) when performing CMake commands. To confirm the default generator target, call `C:> cmake -g -h` or explicitly invoke the target using `C:> cmake -B out/build /S . -g "SomeGenerator"`.

```
// CMakeLists.txt

cmake_minimum_required(VERSION "3.5")

project("HelloWorld")

add_executable("${PROJECT_NAME}" "Main.cc")
```

#### Building Library types

##### Static library

**Reminder** : "A static library or statically-linked library is a set of routines, external functions and variables which are resolved in a caller at compile-time and copied into a target application by a compiler, linker, or binder, producing an object file and a stand-alone executable."

```
// CMakeLists.txt

cmake_minimum_required(VERSION "3.5")

project("GetGreetings")

add_library("static_get_greeting_lib" STATIC "GetGreetings.cc

add_executable("${PROJECT_NAME}" "Main.cc")

target_link_libraries("${PROJECT_NAME}" PRIVATE "static_get_greeting_lib")
```

##### Shared library

**Reminder** : "A shared library or shared object is a file that is intended to be shared by executable files and further shared object files. Modules used by a program are loaded from individual shared objects into memory at load time or runtime, rather than being copied by a linker when it creates a single monolithic executable file for the program."

```
// CMakeLists.txt

cmake_minimum_required(VERSION "3.5")

project("shared-GetGreetings")

add_library("shared_get_greeting_lib" SHARED "GetGreetings.cc")

add_executable("${PROJECT_NAME}" "Main.cc")

target_link_libraries("${PROJECT_NAME}" PRIVATE "shared_get_greeting_lib")
```

Tips : Further details are provided on library types at the following link - [MSVC, Building a library](https://github.com/guyllaumedemers/MSVC-Building-a-library/tree/master).

# Installing a project

aaaa