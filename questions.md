## List of questions -- Rust related

* external linkage -- [Rust docs]( https://internals.rust-lang.org/t/precise-semantics-of-no-mangle/4098 )
* #[ no_mangle ] macro
    + A way to get a symbol exported from a staticlib?
    + A way to preserve a symbol that is not otherwise referenced from Rust code in a binary 
    + does this also imply EXTERNAL LINKAGE ?

* staticlib --> what is this? *static lib* ? How does it work? What is it used for?

* symbol naming versus linking

* crate mangling --> [ mangling ]( https://docs.rs/mangling/latest/mangling/ )
### Symbol Name Mangling 
#### Requirements for symbol mangling scheme:
* String must provide a clear STRING ENCODING for everything that can end up in a bineary's symbol table
    + The String encoding tells us everythgin that can be inclulded in binary's symbol table'
    + TODO: what is a symbol table for a binary?
* Mangled symbols should be DECODABLE, to some degree
    + I should be able to know which instance of a polymorphic function a symbold identifies, for example
    + This is true for nearly everything, e.g., external tools, backtraces, or a binary representation of some code available

* A mangling scheme should be platform independent
    + How is this achieved? 
        + By restricting a character set to A-Z, a-z, 0-9, _
        + All other characters might have special meaning in some context 
        + e.g., for MSVC -> def files, or are not supported, e.g., Unicode 

* Scheme should be efficient
    + Meaning what? 
        + Symbols)    

Unambiguous, meaning: 
    + No two distinct compiler generated entities ( i.e., object code for functions ) can be mapped to the same symbol name.

### Definitions: 

* Compiler: 
    + Software that translates a program written in high-level programming lang, e.g., C/C++, Rust into machine language
    + Usually generates assembly language first --> then translates assembly lang to machine language
    + A utility known as a "linker" combines all machine language modules into an executable program that can run in the computer
 

* Executable Code: 
    + Rust: after being compiled, rust code outputs a BINARY EXECUTABLE
    + Rust is an ahead-of-time compiled language --> Meaning: 
        + You can compile a program, then give the executable to someone else
        + And they can run the program without ever installing Rust
    + Software that can be run on a computer --> Generally refers to machine language
        + Machine language is a set of instructions the computer carries out in hardware
         

* Linker: 
    + A utility program, also known as a "link editor"  
    + This program connects a compiled or assembled program to a specific environment 
    + The purpose of the linker is to *UNITE* references between program modules and libraries of subroutines. 
    + Output: A load module -> which is executable code ready to run on computer 
