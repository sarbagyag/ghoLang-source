# ghoLang

ghoLang is a small scripting language with a bytecode virtual machine written in C99. It is based on Lox from [*Crafting Interpreters*](https://craftinginterpreters.com/) by Robert Nystrom (Part III, "A Bytecode Virtual Machine").

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
make          # builds ./gho
make clean    # removes the binary
```

## Usage

```sh
./gho              # start the REPL
./gho path/to/script.gho   # run a file
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

## VS Code extension

Syntax highlighting, comment toggling and snippets for `.gho` files live in `vscode-gho/`. From the repo root:

```sh
ln -s "$(pwd)/vscode-gho" ~/.vscode/extensions/gholang
```

Then reload VS Code (Developer: Reload Window). To build a `.vsix` instead, run `npx @vscode/vsce package` inside `vscode-gho/` and install it with `code --install-extension gholang-0.1.0.vsix`.

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
vscode-gho/      VS Code extension for .gho files
```

## Credits

ghoLang is derived from Lox, the language in the book *Crafting Interpreters* by Robert Nystrom, which is free to read online at [craftinginterpreters.com](https://craftinginterpreters.com/).
