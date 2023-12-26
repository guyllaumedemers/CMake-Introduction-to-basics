## Copyright(c) 2023 gdemers
## 
## Permission is hereby granted, free of charge, to any person obtaining a copy
## of this software and associated documentation files(the "Software"), to deal
## in the Software without restriction, including without limitation the rights
## to use, copy, modify, merge, publish, distribute, sublicense, and /or sell
## copies of the Software, and to permit persons to whom the Software is
## furnished to do so, subject to the following conditions :
## 
## The above copyright notice and this permission notice shall be included in all
## copies or substantial portions of the Software.
## 
## THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
## IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
## FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.IN NO EVENT SHALL THE
## AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
## LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
## OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
## SOFTWARE.

## Sets the minimum required version of cmake for a project. Also updates the policy settings as explained below.
cmake_minimum_required(VERSION "3.5")

## Sets the name of the project, and stores it in the variable PROJECT_NAME.
project("shared-GetGreetings")

## Adds a library target called <name> to be built from the source files listed in the command invocation.
add_library("shared_get_greeting_lib" SHARED "GetGreetings.cc")

## A CMake-based build system is organized as a set of high-level logical targets. Each target corresponds to an executable or library,
## or is a custom target containing custom commands. Dependencies between the targets are expressed in the build system to determine the build order
## and the rules for regeneration in response to change.
add_executable("${PROJECT_NAME}" "Main.cc")

## Dependencies between binary targets are expressed using the target_link_libraries()
target_link_libraries("${PROJECT_NAME}" PRIVATE "shared_get_greeting_lib")