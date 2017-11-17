# cmake_test_lib
CMake sample library to show how to properly export a library for later importing by an outside CMake project.

This pairs up with [cmake_test_find_package](https://github.com/samaursa/cmake_test_find_package) project which shows how to import this library easily.

# Building

Simply run 
```
mkdir build
cd build
cmake ../
```
or 
```
mkdir build
cd build
cmake ../ -DCMAKE_INSTALL_PREFIX=../install
``` 
which sets the installation directory to the root of the project.

# Installing

Run `make install`. This will also `export` the library to the `CMake` global package registry.

On `Windows`, this is (unfortunately) stored in the registry, while on `Unix` platforms it is in the home directory. See [this link](https://cmake.org/Wiki/CMake/Tutorials/Package_Registry) for more information.
