## compiling options in g++🐶
### 1
```bash
# query the default c++ standard that g++ is using
# windows version
g++ -dM -E -x c++ nul | findstr __cplusplus
# output:
#define __cplusplus 201402L
```
- -dM : lists all macros defined by the preprocessor.
- -E : stops after the preprocessing stage.
- -x c++ : tells GCC to treat the input as C++ code.
---
### 2
```bash
# compile the cpp files in current directory
g++ -std=c++11 ./*.cpp -Wall
```
- -Wall : warning all
- -std=c++11 : compile the program with c++11 standard