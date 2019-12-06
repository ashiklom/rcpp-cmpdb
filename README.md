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
2. Add a line like `PKG_CPPFLAGS += -MJ <tempdir>/$@.json` to have `clang` create individual compilation databases for each target as part of the R package build.
3. Build the R package in a temporary folder. While compiling, it will generate compilation databases for every C++ file.
4. Combine all the individual compilation database files into a single file: `<path>/src/compilation_commands.json`
5. Remove all temporary directories, and restore the original `Makevars` file.

## Helpful links

- https://github.com/cquery-project/cquery/wiki/Compilation-database
- https://sarcasm.github.io/notes/dev/compilation-database.html
- https://clang.llvm.org/docs/JSONCompilationDatabase.html
- https://clang.llvm.org/extra/clangd/Installation.html#compile-flags-txt
