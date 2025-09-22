# Monkey Programming Language Interpreter

A Go implementation of the Monkey programming language interpreter, built following the excellent guide from "Writing an Interpreter in Go" by Thorsten Ball.

## 🐒 What is Monkey?

Monkey is a toy programming language designed to demonstrate the fundamentals of programming language implementation. This interpreter showcases the core components needed to build a programming language from scratch.

## 🚀 Features

### Language Features
- **Variables**: Bind values to names using `let`
- **Integers**: Support for integer arithmetic
- **Booleans**: `true` and `false` values
- **Functions**: First-class functions with closures
- **Conditionals**: `if-else` expressions
- **Return statements**: Early returns from functions
- **Operators**: Arithmetic (`+`, `-`, `*`, `/`) and comparison (`==`, `!=`, `<`, `>`)
- **Prefix operators**: Unary `!` (not) and `-` (negation)

### Interpreter Components
- **Lexer**: Tokenizes source code into tokens
- **Parser**: Builds Abstract Syntax Tree (AST) from tokens
- **Evaluator**: Executes the AST and produces results
- **REPL**: Interactive Read-Eval-Print Loop

## 📁 Project Structure

```
src/
├── main.go              # Entry point
├── lexer/               # Tokenization
│   ├── lexer.go
│   └── lexer_test.go
├── parser/              # AST construction
│   ├── parser.go
│   ├── parser_test.go
│   └── parser_tracing.go
├── ast/                 # Abstract Syntax Tree
│   ├── ast.go
│   └── ast_test.go
├── evaluator/           # Expression evaluation
│   ├── evaluator.go
│   └── evaluator_test.go
├── object/              # Runtime objects
│   ├── object.go
│   └── object_test.go
├── token/               # Token definitions
│   └── token.go
└── repl/                # Interactive shell
    └── repl.go
```

## 🛠️ Installation & Usage

### Prerequisites
- Go 1.22.2 or later

### Building and Running

1. **Clone and navigate to the project:**
   ```bash
   cd ./interpreter-monkey/src
   ```

2. **Run the REPL:**
   ```bash
   go run main.go
   ```

3. **Build executable:**
   ```bash
   go build -o monkey main.go
   ./monkey
   ```

## 📝 Language Syntax Examples

### Variables and Arithmetic
```monkey
let five = 5;
let ten = 10;
let result = five + ten * 2;  // 25
```

### Functions
```monkey
let add = fn(x, y) {
    x + y;
};

let multiply = fn(x, y) {
    x * y;
};

let result = add(multiply(2, 3), 4);  // 10
```

### Conditionals
```monkey
let max = fn(a, b) {
    if (a > b) {
        return a;
    } else {
        return b;
    }
};
```

### Boolean Logic
```monkey
let isEven = fn(n) {
    if (n % 2 == 0) {
        return true;
    } else {
        return false;
    }
};

let result = !isEven(5);  // true (5 is odd, so !isEven(5) is true)
```

### Complex Example
```monkey
let fibonacci = fn(n) {
    if (n < 2) {
        return n;
    } else {
        return fibonacci(n - 1) + fibonacci(n - 2);
    }
};

let result = fibonacci(10);  // 55
```

## 🧪 Testing

Run the test suite to verify all components work correctly:

```bash
go test ./...
```

Individual package tests:
```bash
go test ./lexer
go test ./parser
go test ./evaluator
go test ./object
```

## 🏗️ Architecture Overview

### Lexer (Tokenization)
Converts source code into a stream of tokens:
- Identifiers: `let`, `fn`, variable names
- Literals: integers, booleans
- Operators: `+`, `-`, `*`, `/`, `==`, `!=`, etc.
- Delimiters: `(`, `)`, `{`, `}`, `;`, `,`

### Parser (AST Construction)
Builds an Abstract Syntax Tree from tokens using recursive descent parsing:
- Handles operator precedence
- Manages nested expressions
- Constructs statement and expression nodes

### Evaluator (Execution)
Executes the AST using a tree-walking interpreter:
- Implements variable binding and lookup
- Evaluates expressions and statements
- Manages function calls and returns
- Handles control flow (conditionals, returns)

### Object System
Runtime representation of Monkey values:
- `Integer`: 64-bit integers
- `Boolean`: true/false values
- `Null`: null value
- `ReturnValue`: Wrapper for return statements

## 🎯 Learning Objectives

This project demonstrates:
- **Compiler Design**: Lexical analysis, parsing, and evaluation
- **Go Programming**: Interfaces, structs, methods, and testing
- **Language Theory**: ASTs, recursive descent parsing, tree-walking evaluation
- **Software Architecture**: Modular design with clear separation of concerns

## 📚 Resources

- [Writing an Interpreter in Go](https://interpreterbook.com/) by Thorsten Ball
- [Monkey Language Specification](https://monkeylang.org/)

## 🤝 Contributing

This is a learning project following the book's implementation. Feel free to experiment with additional language features or optimizations!

## 📄 License

This project is for educational purposes. Please refer to the original book for licensing information.

---

*Happy coding with Monkey! 🐒*
