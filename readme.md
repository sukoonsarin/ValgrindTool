# Valgrind Tool
[![Build Status](https://travis-ci.org/sukoonsarin/ValgrindTool.svg?branch=master)](https://travis-ci.org/github/sukoonsarin/ValgrindTool)
[![Coverage Status](https://coveralls.io/repos/github/sukoonsarin/ValgrindTool/badge.svg?branch=master)](https://coveralls.io/github/sukoonsarin/ValgrindTool?branch=master)
---

## Overview

A C++ exercise involving usage of Valgrind to identify and fix bugs. Valgrind is a multi-tool useful for identifying undefined behaviour, function and memory profiling, data-race detection and leak checking. Additional tools to valgrind are callgrind and massif that are used here. Callgrind generates an output file that shows the flow of the code and massif shows the memory allocation. KCachegrind is a visualization tool for viewing callgrind files.


## Standard install via command-line
```
git clone --recursive https://github.com/sukoonsarin/ValgrindTool
cd <path to repository>
mkdir build
cd build
cmake ..
make
Run tests: ./test/cpp-test
Run program: ./app/shell-app
```

## Building for code coverage
```
sudo apt-get install lcov
cmake -D COVERAGE=ON -D CMAKE_BUILD_TYPE=Debug ../
make
make code_coverage
```
This generates a index.html page in the build/coverage sub-directory that can be viewed locally in a web browser.


## Using Valgrind 

To install valgrind:

```
sudo apt-get install valgrind
```

To install KCachegrind:

```
sudo apt-get install kcachegrind
```

To check for errors:

```
cd <path to repo>
cd build
valgrind ./app/shell-app
```

For detailed results on memory leaks, use flags: 

```
valgrind --leak-check=full ./app/shell-app
```

To use function and memory profiler:

```
valgrind --tool=callgrind ./app/shell-app
valgrind --tool=massif ./app/shell-app
```

These generate callgrind and massif .out files in the build directory.

Visualize the callgrind.out file in KCachegrind:
```
kcachegrind
```

Open the callgrind.out file in the tool

To visualize the massif.out file:
```
ms_print <massif.out filename>
```


