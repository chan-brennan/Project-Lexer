# CSE 340 Projects – Lexical Analysis to Code Generation

Author: Brennan Chan  
Initial Codebase: Rida Bazzi  
Course: CSE 340 – Principles of Programming Languages

---

## 📘 Overview

This repository contains three sequential projects completed for CSE 340. Together, they form a simplified compiler pipeline for a basic programming language, progressing through lexical analysis, grammar analysis, and intermediate code generation with interpretation.

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

## 📦 Project 3 – Code Generator & Interpreter

**Description:**  
Generates intermediate code from parsed input and simulates execution using a virtual machine. Supports arithmetic, assignment, loops, conditionals, and I/O.

**Key Features:**
- Instruction list generation (InstructionNode)
- Parsing with a lexer-driven grammar
- Execution of intermediate instructions via execute_program()

**Run Instructions:**
```bash
g++ compiler.cc demo.cc lexer.cc inputbuf.cc -o a.out
./a.out < tests/input.txt
```
Token Types:
Keywords: TYPE, VAR, REAL, INT, ...
Operators: +, -, /, *, =, <>, ...
Delimiters: ,, :, {, }, ...
Special: ERROR, END_OF_FILE

## 🗂 Project Directory Structure
```
Project/
├── inputbuf.cc/.h         # Character input buffering
├── lexer.cc/.h            # Lexical analyzer
├── project2.cc            # Grammar analyzer logic
├── compiler.cc/.h         # Intermediate code generator and VM
├── demo.cc                # Sample integration for Project 3
├── test_p3.sh             # Test script for Project 3
├── tests/                 # Sample input/output test cases
└── README.md              # This file
```
