# Project – Lexical Analysis and Code Interpretation

Author: Brennan Chan  
Initial Codebase: Rida Bazzi  
Course: CSE 340 – Principles of Programming Languages

---

## 📘 Overview

This repository contains three sequential projects completed for CSE 340, The Principles of Programming Languages.

Together, they form a simplified compiler pipeline for a basic programming language, progressing through lexical analysis, grammar analysis, and intermediate code generation with interpretation.

---

## 📦 Project 1 – Lexical Analyzer

**Description:**  
Implements a lexical analyzer (lexer) in C++ that reads source code and breaks it into tokens such as identifiers, keywords, operators, numbers, and delimiters.

**Key Features:**
- Supports keywords, identifiers, base-08/16 integers, real numbers
- Token lookahead with `UngetToken()`
- Skips whitespace and detects invalid tokens

**Run Instructions:**
```bash
g++ lexer.cc inputbuf.cc -o lexer
./lexer < input.txt
```
Token Types:
- Keywords: TYPE, VAR, REAL, INT, ...
- Operators: +, -, /, *, =, <>, ...
- Delimiters: ,, :, {, }, ...
- Special: ERROR, END_OF_FILE

## 📦 Project 2 – Grammar Analyzer

**Description:**  
Parses a context-free grammar from input and performs one of five tasks: listing grammar symbols, removing useless symbols, or computing FIRST and FOLLOW sets.

**Tasks Supported:**
- Print grammar symbols (terminals and non-terminals)
- Eliminate useless symbols
- Compute FIRST sets
- Compute FOLLOW sets
- Check if grammar supports predictive parsing

**Run Instructions:**
```bash
g++ project2.cc lexer.cc inputbuf.cc -o grammar_analyzer
./grammar_analyzer [TASK_NUMBER] < grammar_input.txt
```
Token Types:
- ID – Alphanumeric identifiers
- ARROW – ->
- STAR – *
- HASH – #
- END_OF_FILE, ERROR

## 📦 Project 3 – Intermediate Code Generator & Interpreter

**Description:**  
Implements a compiler for a simple C-like language that parses input code, builds a linked list-based intermediate representation (IR), and simulates execution using a provided interpreter.

**Key Features:**
- Parses constructs like `assign`, `if`, `while`, `switch`, `for`, `input`, and `output`
- Builds an IR graph using `InstructionNode` structures
- Supports jump logic with conditional and unconditional branches (`CJMP`, `JMP`)
- Uses a memory model and variable-location mapping (`mem[]` and location table)
- Execution is performed by traversing and interpreting the generated instruction graph

**Run Instructions:**
```bash
g++ compiler.cc demo.cc lexer.cc inputbuf.cc -o a.out
./a.out < tests/input.txt
```
Token Types:
- Keywords: TYPE, VAR, REAL, INT, ...
- Operators: +, -, /, *, =, <>, ...
- Delimiters: ,, :, {, }, ...
- Special: ERROR, END_OF_FILE

**Execution Model:**
- Variables declared in the var section are assigned memory locations using a location table
- Input values are consumed sequentially from the inputs section
- The compiler builds a linked list of instructions representing the input program
- The interpreter walks through this instruction list, simulating control flow and memory updates

**Supported Statements:**
- `assign` – assignment of variables or expressions  
- `input` / `output` – read input values or print variable contents  
- `if` – conditional execution using `CJMP` and `NOOP`  
- `while` – loops implemented with `CJMP`, `JMP`, and `NOOP`  
- `for` – translated into `assign`, `CJMP`, `JMP` sequences like C-style for-loops  
- `switch` – implemented via a sequence of `CJMP` and conditional blocks  

## 🗂 Project Directory Structure
```
Project/
├── inputbuf.cc/.h         # Character input buffering
├── lexer.cc/.h            # Lexical analyzer
├── project2.cc            # Grammar analyzer logic
├── compiler.cc/.h         # Intermediate instruction generator and VM
├── demo.cc                # Sample integration for Project 3
├── test_p3.sh             # Test script for Project 3
├── tests/                 # Sample input/output test cases
└── README.md              # This file
```
