# clox

A bytecode virtual machine for the Lox language, written in C99 by following [*Crafting Interpreters*](https://craftinginterpreters.com/) by Robert Nystrom (Part III, "A Bytecode Virtual Machine").

Source goes through a single-pass compiler into bytecode, which a stack-based VM then executes.

## Status

Done through the **Closures** chapter (25).

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
| Garbage collection | not yet |
| Classes, methods, inheritance | not yet |

## Build

You need a C compiler (the Makefile uses `clang`) and `make`.

```sh
make          # builds ./clox
make clean    # removes the binary
```

## Usage

```sh
./clox              # start the REPL
./clox script.lox   # run a file
```

Exit codes: `64` bad usage, `65` compile error, `70` runtime error, `74` I/O error.

### Example

```lox
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

## Project layout

```
src/
├── main.c       entry point, REPL, file runner
├── scanner.*    lexer: source text to tokens
├── compiler.*   Pratt parser + bytecode emitter
├── chunk.*      bytecode container and opcodes
├── vm.*         stack-based interpreter loop, call frames, upvalues
├── value.*      Lox value representation and dynamic arrays
├── object.*     heap objects: strings, functions, closures, upvalues, natives
├── table.*      hash table (globals, string interning)
├── memory.*     allocation helpers
└── debug.*      disassembler
```

## Credits

Based on the book *Crafting Interpreters* by Robert Nystrom, which is free to read online at [craftinginterpreters.com](https://craftinginterpreters.com/).
