# 3. Types & Values

Vulpes features a strong, expressive type system designed to be both intuitive and powerful.  
Types define what kind of values can be stored and manipulated, enabling both safety and performance.

---

## 3.1 Primitive Types

Vulpes provides a set of built-in types for common values:

| Type    | Description                    | Examples          |
|---------|--------------------------------|-------------------|
| `int`   | Integer (default size, e.g. 32)| `42`, `-7`        |
| `int(8)`/`int(64)` | Fixed-width integer  | `int(8) x = 100;` |
| `float` | Floating-point number (default)| `3.14`, `-0.001`  |
| `float(64)` | 64-bit float                |                   |
| `bool`  | Boolean                        | `true`, `false`   |
| `char`  | Single Unicode character       | `'a'`, `'\n'`     |
| `string`| Text string                    | `"hello"`         |
| `unit`  | No value (like `void`)         | Used as a return type for no result |

> 🦊 **Tip:**  
> Use `::type(bits)` for explicit size, e.g., `var::int(16) x = 10;`

---

## 3.2 Type Modifiers

Vulpes uses **modifiers** to extend or specialize types:

| Modifier      | Meaning                                  | Example                         |
|---------------|------------------------------------------|---------------------------------|
| `SOLID`       | Makes a variable immutable/constant      | `var[SOLID]::int x = 10;`       |
| `PTR`         | Pointer to a value                       | `var[PTR]::int p = &x;`         |
| `ARRAY(n)`    | Fixed-length array of type               | `var[ARRAY(4)]::float xs = ...` |
| `OPTION`      | Optional value (present or None)         | `var[OPTION]::int y = None;`    |
| `FX`          | Function type modifier (lambda/closure)  | `var[FX] f = (a) => a + 1;`     |

Modifiers are written in brackets after `var` and before `::type`.

---

## 3.3 Type Inference & Explicit Types

- Vulpes will **infer** types where possible:
    ```vlp
    var x = 42;      // Inferred as int
    var name = "Sam"; // Inferred as string
    ```
- You can always **specify** a type explicitly:
    ```vlp
    var::int(64) large = 10000000000;
    var[SOLID]::float pi = 3.14159;
    ```

> **Explicit types are required** for function parameters and public APIs.

---

## 3.4 Option, Result, and “No Value”

- **Option:** Represents a value that may or may not be present.
    ```vlp
    var[OPTION]::int maybeAge = None;
    ```
- **Result:** For error handling—stores either a value or an error.
    ```vlp
    var[RESULT]::int result = Ok(42);
    ```
- **None:** The absence of a value, used with `OPTION`.

---

## 3.5 Type Parameters & Generics

- Many types in Vulpes can be parameterized:
    ```vlp
    var::array(int, 10) numbers = [0,1,2,3,4,5,6,7,8,9];
    var::option(string) maybeName = None;
    ```
- Syntax: `::type(param1, param2, ...)`

---

## 3.6 User-defined Types

- **Kits:** Custom structures for organizing data.
    ```vlp
    kit Point {
        x: float,
        y: float
    }
    ```
- **Enums:** Tagged unions for sum types.
    ```vlp
    enum Color {
        Red,
        Green,
        Blue
    }
    ```

---

## 3.7 Type Aliases

- Use `type` to create type synonyms for complex or common types.
    ```vlp
    type Score = int(16);
    ```

---

## 3.8 Type Conversions

- Explicit casts/conversions can be performed using cast syntax (to be defined).
    ```vlp
    var x = 42;
    var y = x as float;
    ```

---

<!--
TODO:
- Decide on syntax for generic kits/enums (if any)
- Finalize full list of built-in types and modifiers
- Document default sizes/platform dependencies for primitive types
- Specify rules for implicit vs explicit conversion
-->

---

> **Summary:**  
> The Vulpes type system balances expressiveness and safety.  
> Whether you prefer concise inference or strict explicitness, you control how types work in your code!
