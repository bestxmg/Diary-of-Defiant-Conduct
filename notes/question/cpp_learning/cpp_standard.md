## C++ standard🐶

### what's C++ standard  
The C++ standard is a formal specification that defines the C++ programming language, including its syntax, semantics, standard libraries, and other requirements that implementations (like compilers) must adhere to.

---
### how different versions of C++ standard affect the execution of our program
Generally, a compiler will pick a standard to default to. Typically the default is not the most recent language standard -- many default to C++14, which is missing many of the latest and greatest features.

We can query the C++ standard that our compile are using by using a method similar to the following example:

[compiling options in g++](../../practical/compile_option.md#1)

### the features that newly introduced between C++ 11 and latest C++ standard(WIP)

---

### Which language standard should you choose?
it’s common to choose a language standard that is one or two versions back from the latest finalized standard for the following reasons:
- compiler makers had a chance to solve defeats
- some platform may not fully prepared for new standard

### Setting a language standard in Visual Studio

[reference](../../practical/tool_vscode#2-setting-a-language-standard-in-visual-studiowip)