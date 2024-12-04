# Lexical Analysis Implementation 

Lexical analysis is the first phase of a compiler. It takes the input program, divides it into tokens, and removes any white space or comments. This process also checks for lexical errors and reports them. 

### Lexical Analyzer Structure 

A lexical analyzer consists of two parts: the **lexer** and the **driver**. The lexer, also known as the scanner, generates tokens. The driver invokes the lexer and gets the tokens while passing them to the syntax analyzer.

### Lexer 

The lexer can be implemented using regular expressions and finite automata theory. Each token is identified by a regular expression. 

For example, let's consider a simple lexer for a language that has `int` keyword, `=` operator, and identifiers. 

```python
import re

def lexer(code):
    token_specification = [
        ('NUMBER',   r'\d+(\.\d*)?'), 
        ('ASSIGN',   r'='), 
        ('ID',       r'[A-Za-z]+'),  
        ('OP',       r'[+\-*/]'), 
        ('NEWLINE',  r'\n'),   
        ('SKIP',     r'[ \t]+'),   
        ('MISMATCH', r'.'),   
    ]

    tok_regex = '|'.join('(?P<%s>%s)' % pair for pair in token_specification)
    get_token = re.compile(tok_regex).match
    line_num = 1
    line_start = 0
    for mo in re.finditer(tok_regex, code):
        kind = mo.lastgroup
        value = mo.group()
        if kind == 'NUMBER':
            value = float(value) if '.' in value else int(value)
        elif kind == 'NEWLINE':
            line_start = mo.end()
            line_num += 1
            continue
        elif kind == 'SKIP':
            continue
        elif kind == 'MISMATCH':
            raise RuntimeError(f'{value!r} unexpected on line {line_num}')
        yield Token(kind, value, line_num, mo.start()-line_start)
```

### Driver

The driver function controls the lexer and gets the tokens. It then passes these tokens to the syntax analyzer (parser). 

```python
def driver():
    code = "int = 5"
    for token in lexer(code):
        print(token)
```

This is a rudimentary example. In a real-world scenario, the lexical analyzer should be capable of handling more complex languages, including semantic analysis. This often involves the use of parser generators or lexer generators like Lex and Yacc.