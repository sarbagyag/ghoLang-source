# ghoLang

ghoLang is a small scripting language with a bytecode virtual machine written in C99. It is based on Lox from [*Crafting Interpreters*](https://craftinginterpreters.com/) by Robert Nystrom (Part III, "A Bytecode Virtual Machine"). The interpreter binary is still named `clox`.

Source goes through a single-pass compiler into bytecode, which a stack-based VM then executes.

## Status

Done through the **Garbage Collection** chapter (26).

| Feature | Status |
|---|---|
| Scanner | done |
| Pratt-parser compiler (single pass, no AST) | done |
| Expressions: arithmetic, comparison, equality, logic (`and`/`or`) | done |
| Strings (with interning) | done |
| Global and local variables, block scoping | done |
| Control flow: `if`, `while`, `for` | done |
| Functions, calls, `return`, native functions | done |
| Closures and upvalues | done |
| Garbage collection (mark-sweep) | done |

## Build

You need a C compiler (the Makefile uses `clang`) and `make`.

```sh
make          # builds ./clox
make clean    # removes the binary
```

## Usage

```sh
./clox              # start the REPL
./clox path/to/script   # run a file
```

Exit codes: `64` bad usage, `65` compile error, `70` runtime error, `74` I/O error.

### Example

```
fun makeCounter() {
  var i = 0;
  fun count() {
    i = i + 1;
    print i;
  }
  return count;
}

var counter = makeCounter();
counter(); // 1
counter(); // 2

print clock(); // built-in native function
```

## Debugging

`src/common.h` enables two debug flags by default:

```c
#define DEBUG_PRINT_CODE        // disassemble each function after compiling
#define DEBUG_TRACE_EXECUTION   // print the stack and each instruction as it runs
```

They make output very noisy. Comment them out in `src/common.h` for normal runs.

Two more flags, off by default, are for the garbage collector:

```c
// #define DEBUG_STRESS_GC   // collect on every allocation (finds missing GC roots)
// #define DEBUG_LOG_GC      // log allocation, marking, blackening and freeing
```

## Project layout

```
src/
├── main.c       entry point, REPL, file runner
├── scanner.*    lexer: source text to tokens
├── compiler.*   Pratt parser + bytecode emitter
├── chunk.*      bytecode container and opcodes
├── vm.*         stack-based interpreter loop, call frames, upvalues
├── value.*      ghoLang value representation and dynamic arrays
├── object.*     heap objects: strings, functions, closures, upvalues, natives
├── table.*      hash table (globals, string interning; weak string table)
├── memory.*     allocation helpers and the mark-sweep garbage collector
└── debug.*      disassembler
```

## Credits

ghoLang is derived from Lox, the language in the book *Crafting Interpreters* by Robert Nystrom, which is free to read online at [craftinginterpreters.com](https://craftinginterpreters.com/).
