# Generate compilation databases for Rcpp packages

A simple shell script for generating `compile_commands.json` files for `clangd` and other C++ LSP servers for R packages using C code.

**NOTE**: This currently only works with the `clang` compiler (>5.1).
You will need a different solution for `gcc` and other compilers.

## Installation

Download the `rcpp-compdb` script into a location on your `$PATH`.

## Usage

```
rcpp-cmpdb <path>
```

`<path>` defaults to the current R package directory.

## How it works

1. Copy `Makevars` to a temporary file.
2. Add the `-MJ`

## Helpful links

- https://github.com/cquery-project/cquery/wiki/Compilation-database
- https://sarcasm.github.io/notes/dev/compilation-database.html
- https://clang.llvm.org/docs/JSONCompilationDatabase.html
- https://clang.llvm.org/extra/clangd/Installation.html#compile-flags-txt
