# cmake-util
cmake project util. used to conventiently add cmake binary and library

## usage
first add submodule
```bash
git submodule add git@github.com:ly3too/cmake-util.git cmakefiles
```

then include it in CMakeLists
```cmake
set(CMAKE_MODULE_PATH ${CMAKE_CURRENT_LIST_DIR}/cmakefiles ${CMAKE_MODULE_PATH})
include(util)
```

then you can use util macros:
```cmake
# add subdirs to add_subdirectory if it containes a CMakeLists.txt
auto_add_subdirs()

# auto add a dir as library. directories should be in following structure：
# + subproject_root
#   - include/
#   - src/
#       - *.cpp/*.c
# usage: auto_add_library(target TYPE static DEPENDS libxxx)
auto_add_library(tree TYPE INTERFACE DEPENDS stack)

# automatically add an test
auto_add_test(test_hash SRCS test/test_hash.cpp DEPENDS hash ${GTEST})
```
