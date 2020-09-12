# Matrix library in c++

## Usage

Directory structure

```sh
| => tree
.
|-- CMakeLists.txt
|-- README.md
|-- build
|-- include
|   `-- matrix.hpp
|-- src
|   |-- CMakeLists.txt
|   `-- matrix.cpp
`-- test
    |-- CMakeLists.txt
    `-- test.cpp
```

# How to build and test

## c++ setup

```sh
| => gcc --version
gcc (Homebrew GCC 10.2.0) 10.2.0
Copyright (C) 2020 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

| => g++ --version
g++ (Homebrew GCC 10.2.0) 10.2.0
Copyright (C) 2020 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

| => cmake --version
cmake version 3.18.2

CMake suite maintained and supported by Kitware (kitware.com/cmake).
```

Pasting the simbolic link of gcc and g++ in the `/usr/local/bin` directory.

```sh
| => which g++
/usr/local/bin/g++
| => which gcc
/usr/local/bin/gcc
```
Add the folllowing in `~/.bash_profile`.

```sh
export C_INCLUDE_PATH="/usr/local/include" 
export CPLUS_INCLUDE_PATH="/usr/local/include"
export LIBRARY_PATH="/usr/local/lib/"
alias cmake='cmake -DCMAKE_C_COMPILER=/usr/local/bin/gcc -DCMAKE_CXX_COMPILER=/usr/local/bin/g++'
```
Update the profile by `source ~/.bash_profile`.

Check the include path of gcc and see if `/usr/local/include` is in your include path. Goolge test will be installed here.

```sh
| => echo | gcc -E -Wp,-v -
...
#include <...> search starts here:
 /usr/local/include
```

## install google test locally

Build google test using cmake.

```sh
git clone https://github.com/google/googletest.git
cd googletest
mkdir build
cd build
cmake ..
make
```

Install header and libraries to `/usr/local/include` and `/usr/local/lib` resp.

```sh
sudo cp -r ./googletest/googlemock/include/gmock /usr/local/include/gmock
sudo cp -r ./googletest/googletest/include/gtest /usr/local/include/gtest
sudo cp ./googletest/build/lib/*.a /usr/local/lib/
```

Check if you can use google test.
Create `test.cpp` file with the following contents.

```sh
#include <gtest/gtest.h>

TEST(TestCaseName, TestName){
    EXPECT_EQ(1, 1);
}
```

See if you can compile this code.

```sh
g++ test.cpp -pthread -lgtest_main -lgtest
```

Then `./a.out` will execute the test.

```sh
| => ./a.out
Running tests...
Test project XXX
    Start 1: test01
1/1 Test #1: test01 ...........................   Passed    0.47 sec

100% tests passed, 0 tests failed out of 1

Total Test time (real) =   0.48 sec
```

## test matrix_lib

Now you can test this library using google test.

```sh
git clone https://github.com/wattlebirdaz/matrix_lib.git
cd matrix_lib
mkdir build
cd build
cmake ..
make
make test
```
