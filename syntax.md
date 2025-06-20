# 2.1 Reserved Keywords in Vulpes

| Keyword   | Purpose / Notes                  | Use Now | Reserve (Future) | Never |
|-----------|----------------------------------|:-------:|:----------------:|:-----:|
| var       | Variable declaration             |   ✔     |                  |       |
| fx        | Function definition              |   ✔     |                  |       |
| enum      | Enumeration                      |   ✔     |                  |       |
| kit       | User-defined struct (Kits)       |   ✔     |                  |       |
| solid     | Const/immutable modifier         |   ✔     |                  |       |
| ptr       | Pointer modifier                 |   ✔     |                  |       |
| array     | Array modifier/type              |   ✔     |                  |       |
| option    | Optional type                    |   ✔     |                  |       |
| result    | Result/error type                |   ✔     |                  |       |
| unit      | Unit/void type                   |   ✔     |                  |       |
| true      | Boolean literal                  |   ✔     |                  |       |
| false     | Boolean literal                  |   ✔     |                  |       |
| None      | Empty/absent value (Option)      |   ✔     |                  |       |
| self      | Receiver in methods (if used)    |   ✔     |                  |       |
| super     | Parent kit/namespace (if needed) |         |        ✔         |       |
| if        | If statement                     |   ✔     |                  |       |
| else      | Else branch                      |   ✔     |                  |       |
| elif      | Else if (optional, for clarity)  |   ✔     |                  |       |
| match     | Pattern matching/switch          |   ✔     |                  |       |
| while     | While loop                       |   ✔     |                  |       |
| for       | For loop                         |   ✔     |                  |       |
| break     | Loop/control break               |   ✔     |                  |       |
| continue  | Continue next loop iteration     |   ✔     |                  |       |
| return    | Return from function             |   ✔     |                  |       |
| import    | Import modules/files             |   ✔     |                  |       |
| export    | Export modules/files             |   ✔     |                  |       |
| as        | Import aliasing                  |   ✔     |                  |       |
| pub       | Public visibility                |   ✔     |                  |       |
| priv      | Private visibility               |   ✔     |                  |       |
| internal  | Internal visibility (if needed)  |         |        ✔         |       |
| try       | Error handling (try block)       |   ✔     |                  |       |
| catch     | Error handling (catch block)     |   ✔     |                  |       |
| throw     | Error throwing                   |   ✔     |                  |       |
| panic     | Abort, unrecoverable error       |   ✔     |                  |       |
| async     | Async/await (concurrency)        |         |        ✔         |       |
| await     | Awaitable (concurrency)          |         |        ✔         |       |
| spawn     | Thread/task spawning             |         |        ✔         |       |
| inline    | Inline attribute/trinket         |   ✔     |                  |       |
| static    | Static/global modifier           |         |        ✔         |       |
| defer     | Cleanup/finalization             |         |        ✔         |       |
| yield     | Coroutines/generators            |         |        ✔         |       |
| macro     | Macro definition                 |         |        ✔         |       |
| trait     | Traits/Interfaces                |         |        ✔         |       |
| interface | Interface/contract               |         |        ✔         |       |
| override  | OOP/Inheritance                  |         |        ✔         |       |
| virtual   | OOP/Inheritance                  |         |        ✔         |       |
| type      | Type alias/definition            |         |        ✔         |       |
| operator  | Operator overloading             |         |        ✔         |       |
| dyn       | Dynamic typing                   |         |        ✔         |       |

## 2.2 Identifiers

Identifiers are names for variables, kits, enums, functions, modules, and other user-defined entities in Vulpes.

### Rules for Identifiers

- **Start:** Must begin with a letter (`a-z`, `A-Z`) or underscore (`_`)
- **Continue:** May contain letters, digits (`0-9`), or underscores
- **Case-sensitive:** `myVar`, `MyVar`, and `myvar` are all distinct
- **No reserved keywords:** Identifiers cannot use any [reserved keywords](#21-reserved-keywords-in-vulpes)
- **No special symbols:** `$`, `@`, `-`, etc. are *not* allowed

### Naming Conventions

| Use               | Convention    | Example          |
|-------------------|--------------|------------------|
| Variables         | `camelCase`  | `countDown`      |
| Functions         | `camelCase`  | `computeSum`     |
| Kits (Structs)    | `PascalCase` | `NetworkPacket`  |
| Enums             | `PascalCase` | `FileType`       |
| Constants         | `ALL_CAPS`   | `MAX_SIZE`       |

> **Tip:**  
> Following these conventions isn’t required by the compiler, but is highly recommended for clarity and “idiomatic” Vulpes code.

### Examples

Valid:
```vlp
counter
answer42
_fooBar
FileReader
parseFile
MAX_LENGTH

Invalid:
9lives        // starts with digit
var           // reserved keyword
my-value      // contains hyphen
$budget       // contains $
```

## 2.3 Literals

Literals are fixed values written directly in Vulpes source code. They’re the building blocks for variables, expressions, and function calls.

### Supported Literal Types

| Type      | Example(s)               | Notes                                           |
|-----------|--------------------------|-------------------------------------------------|
| Integer   | `0`, `42`, `-17`         | Underscores allowed for readability: `1_000_000`|
| Float     | `3.14`, `0.0`, `-1.2e6`  | Must include a decimal or exponent              |
| Boolean   | `true`, `false`          | Case-sensitive                                  |
| String    | `"hello"`, `"fox\nkit"`  | Double quotes, supports escapes                 |
| Char      | `'a'`, `'\n'`            | Single quotes, one character or escape          |
| Array     | `[1, 2, 3]`              | Comma-separated elements in square brackets     |
| None      | `None`                   | Special literal for “no value” (option types)   |

---

### Integer Literals

- Decimal: `42`, `-17`
- Hexadecimal: `0x2A`, `0xFF`
- Binary: `0b1010`
- Octal: `0o77`
- Underscores for readability: `1_000_000`

### Float Literals

- Standard: `3.14`, `0.0`, `-12.0`
- Exponent: `6.022e23`, `-1.2E-6`
- Must have a decimal point or exponent

### Boolean Literals

- `true` and `false` only

### String Literals

- Double quotes: `"Hello, world!"`
- Escape sequences: `\n` (newline), `\t` (tab), `\\`, `\"`, `\x41` (hex), etc.

```vlp
var message = "Welcome to Vulpes!\nEnjoy your stay.";
var nums = [10, 20, 30];
var letters = ['a', 'b', 'c'];
var maybeName = None;
```

## 2.4 Comments

Comments are used to annotate, document, or temporarily disable parts of Vulpes code.  
They are completely ignored by the compiler and have no effect on program behavior.

---

```vlp
// This is a single-line comment

var x = 5; // Comments can appear after code, too

/*
  This is a multi-line (block) comment.
  It can span multiple lines and is useful for:
    - Temporarily disabling code
    - Explaining algorithms or design decisions
    - Providing high-level documentation for sections of code
*/

/* 
   This is okay.
   /* This is NOT a nested comment. The first */ closes the comment block. */
   var x = 10; // This code is now outside the comment!
*/

/// Computes the factorial of a number
fx factorial(n: int) => int { ... }

/**
 * Represents a network packet
 */
kit NetworkPacket { ... }
// Binary search assumes the array is sorted
// TODO: Optimize this algorithm
/*
var oldLogic = ...
// This code is obsolete but kept for reference
*/
```

## 2.5 Whitespace & Formatting

Whitespace in Vulpes helps make code readable but (with rare exceptions) does not affect meaning or execution.

---

### 2.5.1 Significance of Whitespace

- **Spaces, tabs, and newlines** are generally ignored except as token separators.
- **Indentation** is recommended for clarity but not required for program correctness (unlike Python).
- Multiple spaces or blank lines are allowed between statements or within blocks.

```vlp
fx main() => unit {
    var x = 5;
    var y = 10;
    
    if (x < y) {
        print("x is less than y");
    }
}
```

---

### 2.5.2 Statement Terminators

- **Semicolons (`;`)** are used to end statements.
- Multiple statements can be written on one line, separated by semicolons (not recommended for readability).

```vlp
var a = 1; var b = 2;
```

- You may place a statement across multiple lines as long as it is not ambiguous:

```vlp
var total = a +
            b +
            c;
```

---

### 2.5.3 Indentation and Style

- Use consistent indentation (spaces or tabs—pick one per project).
- **Recommended:** 4 spaces per indent level.
- Align related code visually for clarity.

```vlp
fx factorial(n: int) => int {
    if (n <= 1) {
        return 1;
    } else {
        return n * factorial(n - 1);
    }
}
```

> 🦊 **Tip:**  
> Idiomatic Vulpes code favors clarity—prefer readable formatting over clever one-liners.

---

### 2.5.4 Blank Lines

- Use blank lines to separate logical sections of code (e.g., between functions, before/after large blocks).

---

### 2.5.5 Edge Cases

- Extra whitespace inside expressions/statements is ignored:

```vlp
var x      =   5    +   7 ;
```

- Do **not** add whitespace within identifiers or between function name and parameter list:

```vlp
fx  main ( )   // ❌ Not valid—extra spaces in function signature
fx main()      // ✔️ Correct
```

---

<!--
TODO:
- Decide if a linter/formatter should enforce a specific style
- Specify if trailing whitespace is always ignored (recommended)
-->

---

> **Summary:**  
> Whitespace in Vulpes is for humans, not the compiler—write code that you (and others) want to read!
