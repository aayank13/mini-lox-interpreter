
# mini-lox-interpreter

A small, educational Lox interpreter implemented in Rust. This repository contains a simple lexer and parser (and a tiny runtime) intended for learning and experimentation. The code exposes a small CLI with three subcommands: `Tokenize`, `Parse`, and `Run`.

This project is implemented as both a binary CLI and a library crate (`mini_lox_interpreter`) so parts (lexer, parser) can be reused from other Rust programs.

## Contents

- `src/lex.rs` — lexer/tokenizer implementation
- `src/parse.rs` — parser for Lox expressions/statements
- `src/lib.rs` — library exports and core types
- `src/main.rs` — small CLI that provides `Tokenize`, `Parse`, and `Run` subcommands

## Requirements

- Rust 1.80 or newer (the crate sets `rust-version = "1.80"` in `Cargo.toml`)
- A working Rust toolchain (rustup + cargo)

## Build

Use the standard Cargo workflow:

```bash
cargo build --release
```

Or for a quick development build:

```bash
cargo build
```

## CLI Usage

The binary exposes three subcommands via `clap`:

- `tokenize <filename>` — Runs the lexer over the given file and prints tokens (or lexer errors).
- `parse <filename>` — Parses a single expression from the file and prints the parsed representation (or parse errors).
- `run <filename>` — Parses the entire input and prints the resulting value (or AST representation), intended as a minimal program runner.

Examples:

```bash
# Print tokens from a Lox source file
cargo run -- tokenize examples/sample.lox

# Parse one expression from the file and print the parsed output
cargo run -- parse examples/sample.lox

# Parse and run a script (prints the top-level parsed output/result)
cargo run -- run examples/sample.lox
```

Note: When using `cargo run -- <subcommand>` the `--` is required to forward arguments to the compiled binary.

## Example Lox source

Create a small file `examples/sample.lox` to experiment with the interpreter:

```lox
var a = 1 + 2 * (3 - 4);
print a;
```

Feed that file to any of the three subcommands to see tokens, parsed output, or the runner's result.