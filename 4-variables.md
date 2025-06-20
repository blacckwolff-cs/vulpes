# 4. Variables & Bindings

Variables are the heart of all computation in Vulpes.  
Vulpes unifies variable declarations, modifiers, and types into a single, flexible system.

---

## 4.1 Declaration Syntax

Every variable is declared using the `var` keyword, with optional **modifiers** and **type annotations**:

```vlp
var x = 5;                            // Mutable, type inferred
var::int n = 42;                      // Mutable, explicit type
var[SOLID] y = "immutable";           // Immutable, type inferred
var[SOLID]::float pi = 3.14159;       // Immutable, explicit type
var[ARRAY(3)]::int arr = [1,2,3];     // Array of ints, length 3
var[FX]::fn(int)=>int add = (a) => a + 1; // Lambda function
```

**Formula:**  
```
#[trinket] var[Modifier1, Modifier2, ...]::type(type_param) name = initial_value;
```

---

## 4.2 Modifiers

- **SOLID:** Immutable (constant) variable
- **FX:**  
    - **Named local function**:  
      ```vlp
      var[FX] add(a: int, b: int) => int {
          return a + b;
      }
      ```
    - **Anonymous function (lambda)**:  
      ```vlp
      var[FX] inc = (x: int) => x + 1;
      ```
    - **Closures**: `[FX]` functions can capture local variables.
    - Named `[FX]` functions behave like locally-scoped, assignable functions—perfect for higher-order programming, callbacks, or passing as values.
- **ARRAY(n):** Array of `n` elements
- **PTR:** Pointer/reference
- **OPTION:** Optional value
- (Future: custom modifiers, e.g. RESULT, STRUCT, etc.)

Modifiers appear in brackets directly after `var` and can be combined.

---

## 4.3 Type Annotations

- Use `::type` for explicit type.
- Use `::type(params)` for parameterized types (e.g., `int(32)`, `array(int, 10)`).
- Type annotation is **optional** for local vars, **required** for function params and public API.

```vlp
var::float(32) value = 1.5;
var[ARRAY(4)]::string names = ["a", "b", "c", "d"];
```

---

## 4.4 Mutability & Immutability

- **Mutable by default**—all variables can be reassigned unless declared `[SOLID]`.
- `[SOLID]` makes a variable immutable (cannot be changed after initialization).

```vlp
var count = 10;        // mutable
var[SOLID] max = 100;  // immutable
```

---

## 4.5 Initialization & Assignment

- Variables can be declared and initialized in one line.
- Declaring without initialization is allowed, but use before assignment is an error.

```vlp
var age;
age = 30; // OK

var[SOLID] answer; // ❌ Error: SOLID vars must be initialized
```

---

## 4.6 Scoping, Lifetime, and Shadowing

- **Block-scoped:** A variable exists only within the block it is declared.
- **Shadowing:** Declaring a variable with the same name in an inner block temporarily hides the outer variable.

```vlp
var x = 1;
if (foo) {
    var x = 2; // Shadows outer x
    print(x);  // Prints 2
}
print(x);      // Prints 1
```

---

## 4.7 Attribute Trinkets

- Optional `#[trinket]` syntax allows adding metadata or behavior to variables.
- Used for things like deprecation, inlining, documentation, etc.

```vlp
#[deprecated("use newName instead")]
var[SOLID]::int oldName = 0;
```

---

## 4.8 First-Class Functions with [FX]

Vulpes treats functions as values. Using `[FX]` enables both named and anonymous functions within any scope.

**Named local function:**
```vlp
var[FX] add(a: int, b: int) => int {
    return a + b;
}
```

**Anonymous function (lambda):**
```vlp
var[FX] inc = (x: int) => x + 1;
```

**Passing functions as values:**
```vlp
var[FX] multiply(a: int, b: int) => int {
    return a * b;
}

fx apply_twice(f: fn(int, int)=>int, x: int, y: int) => int {
    return f(f(x, y), f(x, y));
}

apply_twice(add, 2, 3); // Returns 10
```

---

## 4.9 Examples

```vlp
// Mutable, inferred type
var msg = "Welcome to Vulpes!";

// Immutable, explicit type
var[SOLID]::float e = 2.71828;

// Array of 5 floats, mutable
var[ARRAY(5)]::float samples = [1.0, 2.0, 3.0, 4.0, 5.0];

// Pointer to int
var[PTR]::int ptr = &count;

// Named function in local scope
var[FX] square(x: int) => int {
    return x * x;
}

// Lambda (anonymous function)
var[FX] triple = (x: int) => x * 3;
```

---

<!--
TODO:
- Decide if uninitialized mutable vars default to None/undefined, or error on access
- Specify how uninitialized values interact with types (option vs. error)
- Document shadowing/visibility rules for nested blocks and modules
- Expand on trinket syntax and standard trinkets
-->

---

> **Summary:**  
> Vulpes variables are flexible, explicit, and composable—designed to let you express both low-level detail and high-level intent.  
> Named `[FX]` functions give you local, first-class functions without boilerplate—bridging the gap between functional and procedural styles!
