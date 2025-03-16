# STEP Express Schema to OCCT Classes Generator

ExpToCasExe is an auxiliary tool that generates code for implementing new STEP entities into OpenCascade Technology (OCCT). It helps developers automate the process of creating STEP entity classes and their corresponding read/write handlers.

## Overview

The tool consists of two main packages:

| Package | Description |
| :------ | :---------- |
| ExpToCasExe | Core package that parses express schemas and generates class lists |
| TKExpress | Package that generates OCCT-compatible entity descriptions |

Each generated STEP entity includes multiple files for full OCCT integration:
- Header and source files for the entity class
- Header and source files for read/write operations
- Registration code for various OCCT modules

## Getting Started

To use the ExpToCas generator:

```bash
ExpToCasExe <schema.exp> [<new.lst> [<existed.lst> [start_index]]]
```

Where:
- **schema.exp**: STEP Express schema file
- **new.lst**: List of new STEP entities to generate ("-" for all)
- **existed.lst**: List of already implemented entities
- **start_index**: First index for entity registration

## Input File Format

Entity list files (.lst) use the following format:

```
item_name package_name [shortname [check_flag fillshared_flag [category]]]
# Comments start with #
```

## Building

Required tools:
- CMake
- FLEX (Lexical analyzer generator)
- GNU Bison (Parser generator)
- C++ compiler
- OpenCascade

Build process:
```bash
mkdir build
cd build
cmake ..
cmake --build .
```

The build process will:
1. Generate lexer/parser files using FLEX/Bison
2. Compile the generator components
3. Create the ExpToCasExe executable

## Generated Output

The tool generates several directories:

- **_{package_name}_**: Contains entity class files
- **RW_{package_name}_**: Contains read/write handler files
- **Registration**: Contains integration code for OCCT modules

## License

This tool is part of OpenCascade Technology and is released under the LGPL 2.1 license with the Open CASCADE exception.

## Notes

- Some STEP schemas may require manual editing if they don't match the parser's expectations
- For parser debugging, uncomment `//aScanner.set_debug(1)` in exptocas.yacc
- Always update occt_existed_step_entities.lst after generating new entities
