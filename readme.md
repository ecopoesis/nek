nek
========

nek (any-kay) is my toy programming language. I want to make a language that doesn't use nulls, so there is no chance of having something like a NullPointerException. Let's see if that's possible!

based on: http://llvm.org/releases/3.6.2/docs/tutorial/index.html

###### Build the compiler (requires LLVM 3.6.2):

1) Update `CMakeLists.txt` with path to your install of LLVM
2) Use cmake and make:


    cd build
    cmake ..
    make

This creates two things you need:
* `build/out/nek-cpp` which generated LLVM IR assemble from `nek` files
* `build/out/libnek-standard.a` which is the nek standard library (passthroughs to C functions)

###### Use the compiler

1) `nek-cpp` outputs IR to stdout, so pipe it into a file:


    ./build/out/nek-cpp fib.nek > fib.ll


2) Use clang to compile the IR and link it with the standard library:


    clang fib.ll build/out/libnek-standard.a -o fib


3) Run your program:


    ./fib
