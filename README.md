# @caijs/lexer

[![Build Status](https://travis-ci.com/CAI-js/lexer.svg?branch=master)](https://travis-ci.com/CAI-js/lexer)
[![NPM version](https://img.shields.io/npm/v/@caijs/lexer.svg?style=flat)](https://www.npmjs.com/package/@caijs/lexer)
[![NPM downloads](https://img.shields.io/npm/dm/@caijs/lexer.svg?style=flat)](https://www.npmjs.com/package/@caijs/lexer)

@caijs/lexer Is a lexer to build language parsers.

## Installation

In your project folder run:

```bash
$ npm install @caijs/lexer
```

## Examples of use

You can evaluate an string

```javascript
const Lexer = require('@caijs/lexer');

const script = `
n = 0
while n < 10:
  n += 1
print("hola")
`;
const lexer = new Lexer();
lexer.init(script);
const tokens = [];
let token;
do {
  token = lexer.nextToken();
  tokens.push(token);
} while (token && token.type !== Lexer.TokenType.EndOfFile);
console.log(tokens);
```

This will show: 
```javascript
[
  Token { value: 'n', type: 1 },     // Identifier
  Token { value: '=', type: 7 },     // Assignment
  Token { value: '0', type: 2 },     // Number
  Token { value: '\n', type: 6 },    // End of Line
  Token { value: 'while', type: 1 }, // Identifier
  Token { value: 'n', type: 1 },     // Identifier
  Token { value: '<', type: 4 },     // Operator
  Token { value: '10', type: 2 },    // Number
  Token { value: ':', type: 5 },     // Separator
  Token { value: '\n', type: 6 },    // End of Line
  Token { value: 'n', type: 1 },     // Identifier
  Token { value: '+=', type: 7 },    // Assignment
  Token { value: '1', type: 2 },     // Number
  Token { value: '\n', type: 6 },    // End of Line
  Token { value: 'print', type: 1 }, // Identifier
  Token { value: '(', type: 5 },     // Separator
  Token { value: 'hola', type: 3 },  // String
  Token { value: ')', type: 5 },     // Separator
  Token { value: '', type: 8 }       // End of File
]
```
