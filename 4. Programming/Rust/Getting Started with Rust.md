# Rust Intro

## Rust Lang Book

Full playlist of the Rust book:
https://www.youtube.com/playlist?list=PLai5B987bZ9CoVR-QEIN9foz4QCJ0H2Y8

## The Basics

-   Used for web servers and web browsers, etc.
    -   present in compilers and software databases, especially cryptography.
-   Best alternative to C++ (what I was originally learning) since Rust guarantees memory safety.
    -   Strikes a unique balance among performance, safety, and implementation expressions.

### What is Rust

-   **Type safe:** The compiler assures that no operation will be applied to a variable of a wrong type.
-   **Memory safe:** Rust pointers (known as _references_) always refer to valid memory.
-   **Data race-free:** Rust's borrow checker guarantees thread-safety by ensuring that multiple parts of a program can't mutate the same value at the same time.
-   **Zero cost abstractions:** Rust allows the use of high-level concepts, like iteration, interfaces, and functional programming, with minimal to no performance costs. The abstractions perform as well, as if you wrote the underlying code by hand.
-   **Minimal runtime:** Rust has a very minimal and optional runtime. The language also has no garbage collector to manage memory efficiently. In this way Rust is most similar to languages like C and C++.
-   **Targets bare-metal:** Rust can target embedded and "bare metal" programming, making it suitable to write an operating system kernel or device drivers.

### Install Visual Studio Code

A Rust source file is a text file with a _.rs_ file extension

-   After saving code to your text file, use Rust compiler `(rustc)` or Cargo to compile your code into a program.
    
-   You typically write Rust syntax in a text file and save it to your local hard drive. You can write code by using a simple text file editor, like Notepad in Windows. Notepad edits ASCII text, a standard text file format.
    
-   Install Visual Studio Code on Windows
    
    -   Download the installer (Create inline code by wrapping text with ``` (or with the shortcut `cmd/ctrl + e`).
    
    [Download Visual Studio Code - Mac, Linux, Windows](https://code.visualstudio.com/download)
    
    -   ## Go through [starter videos](https://code.visualstudio.com/docs/introvideos/basics) and how to apply the code
        

### Install Rust

-   Use `rustup` to install Rust
    
    -   This website includes instructions, etc.
    
    [rustup.rs - The Rust toolchain installer](https://rustup.rs/)
    
    -   You can add anything to toggles, including images and embeds. 

