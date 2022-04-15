# CPL Compiler
Language Processors assignment

This is a compiler for the Compiler Programming Language (CPL). This is a very simple language which is designed to make it relatively simple to write a compiler. 

My compiler handles:
* Parsing
* Syntax Error Detection
* Error Recovery
* Semantic Error Detection
* Assembly Code Generation

Given:

1. A formal EBNF grammar for a computer language (the "Compiler Project Language", CPL), in the file "grammar.pdf" in Resources / lecture-slides.
     
2. Routines for:
    Character handling
    String table manipulation
    Scanning
    Symbol table manipulation
    (All available via the module's "compiler kit" in the file "distrib-unix.tgz / distrib-unix.zip", see below.).
         
3. An interpreter for the target machine assembly language ("sim" - command line, or "simgui" - graphical).


Write the following:

**parser1.c:**

This is a pure parser for the CPL. This program should accept all syntactically valid CPL programs and reject all invalid ones. On acceptance the program should print "valid", on rejection it should stop parsing at the first syntax error in the CPL source being analysed and print "syntax error". Marks: 5 (5% of total module marks).
    
**parser2.c:**

This is a pure parser which includes full syntax error detection and recovery. This should report syntax errors by type, recover from them and continue parsing the CPL source being analysed. Marks: 10 (10% of total module marks).
    
**comp1.c:**

This is a compiler performing syntax and semantic error detection and code generation for the CPL language, excluding procedure definitions. (Please note, comp1 must handle READ and WRITE statements fully. These look like procedure calls syntactically, but they should compile to Read and Write instructions). Marks: 15 (15% of total module marks).

**comp2.c:**

This is a full compiler performing syntax and semantic error detection and code generation for all parts of the CPL language, including procedure definitions with parameters. Marks: 10 (10% of total module marks).



The idea is that you build up the project in small incremental parts. First you write and test parser1.c, when this is working, and has passed all the tests you think appropriate, copy it to parser2.c, and save parser1.c in a safe place. Take the source in file parser2.c, extend this to implement the required parser2 functionality and test it. When you are happy that parser2.c is working properly, copy it to comp1.c, and save parser2.c in a safe place. Extend comp1.c and test, etc.


Command-line calling conventions for your project work:

I expect the four programs which you submit as your project work to obey the following command-line argument conventions:

 - The first argument ( argv[1]) must be the name of the source program to be parsed or compiled.
 - The second argument ( argv[2]) must be the name of the listing file to be generated by your parser (or compiler).
 - The third argument ( argv[3]) is only required for the two compiler programs, in which case it represents the name of the file into which the assembly language code is to be written.

Hence, I will expect to be able to call the programs like so:

    $ parser1 <source program>  <listing file >         (ex:   $ parser1 t est1.prog test1.lis )
    $ parser2  <source program>   <listing file>
    $ comp1 <source program>   <listing file>  <assembly code file>
    $ comp2 <source program>   <listing file>  <assembly code file>


It is important that your programs obey these command-line argument conventions because the testing software will expect to be able to call them in this fashion.

The tests are normally carried out on a unix or Linux box, so please ensure that your programs are written in ANSI standard C. It is particularly important to check that this is the case if you choose to use an IDE to write your software.


Project Software

The software kit for the module consists of a set of sources which compile into a character-handler, scanner, string table and symbol table for the project compiler. It is designed to work on any Unix system that supports the gcc compiler, Gnu make and Gnu ar. This, of course, includes all popular desktop Linux distributions. It will also work with Cygwin on Windows. The kit has been tested with gcc 9.x on Mac OS/X. Ubuntu, Debian, Arch Linux, and Cygwin.  Clang also works well.


N.B., The software environment assumed for the module is Unix/Linux.  In particular, I will expect your code to compile cleanly using the gcc or clang compilers in a Unix/Linux environment.  Do not use a Windows C compiler. 

If you don't have Linux on your laptop, you can use a virtual machine with Ubuntu (VirtualBox is good), or the Cygwin environment, or, (for Windows 10), the Windows Subsystem for Linux (WSL) with Ubuntu.  I've used all of these alternatives, and they all work fine.
