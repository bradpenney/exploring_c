# Hello World

Here's a simple "Hello, World!" program written in C. This program demonstrates the basic structure
of a C program, including the inclusion of standard libraries and the main function where execution
begins.

``` c title="hello.c"
#include <stdio.h> // (1)!

int main(void){ // (2)!
    printf("hello, world\n"); // (3)!
    return 0; // (4)!
} // (5)!
```

1.  Include the Standard Input Output library, which is necessary for using the `printf` function to print text to the console.
2.  The `main` function is the entry point of any C program. The `void` indicates that this function does not take any arguments.
3.  The `printf` function is used to print the string "hello, world" followed by a newline character (`\n`) to the console.
4.  Indicates that the program has executed successfully.
5.  Marks the end of the `main` function.

??? warning "Prerequisites Needed!"

    To compile and run C programs, you need to have a C compiler installed on your system. Common
    compilers include `gcc` (GNU Compiler Collection) and `clang`. Make sure you have one of these
    installed before proceeding.


To compile and run this program, these are the typical commands used in a terminal:

```bash title="Compile and Run"
gcc -std=c23 -Wall -Wextra -pedantic -o ../programs/hello hello.c # (1)!
./../programs/hello # (2)!
```

1.  Compiles the `hello.c` file with the C23 standard.
    - `-std=c23` Enforces the 2023 C standard (current stable version).
    - `-Wall` Enables common warnings.
    - `-Wextra` Enables additional, useful warnings that `-Wall` doesn’t cover.
    - `-pedantic` Ensures strict ISO C compliance. Helps you avoid compiler extensions sneaking in.
    - `-o ../programs/hello` → Names the output file hello instead of the default a.out.
    - `hello.c` → Your source file.
2.  Runs the compiled program.

When you run the program, you should see the following output in your terminal:

``` bash title="Output"
hello, world
```
