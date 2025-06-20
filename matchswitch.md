## Pattern Matching: `match` and `switch` Statements

Vulpes supports both `match` (for exhaustive, pattern-based branching) and `switch` (for classic constant branching).  
Use `match` for sum types, enums, and deep destructuring; use `switch` for simple constant values.

---

### 1. `match` Statement

- **Purpose:** Powerful, exhaustive pattern matching on enums, tuples, kits, options, results, etc.
- **Syntax:**
  ```vlp
  match expr {
      Pattern1 => {
          // statements
      },
      Pattern2 => {
          // statements
      },
      _ => {
          // default case (optional but recommended)
      }
  }
  ```

- **Examples:**
  ```vlp
  // Enum
  enum Color { Red, Green, Blue }
  var c = Color::Green;

  match c {
      Color::Red => print("Stop!"),
      Color::Green => print("Go!"),
      Color::Blue => print("Chill!"),
      _ => print("Unknown color")
  }

  // Option type
  var maybe = Some(42);
  match maybe {
      Some(n) => print("Number: " + n),
      None => print("No value!")
  }

  // Kit destructuring
  kit Point { x: int, y: int }
  var p = Point { x: 2, y: 3 };
  match p {
      Point { x: 0, y } => print("On y-axis at " + y),
      Point { x, y } => print("Point at (" + x + ", " + y + ")")
  }
  ```

- **Features:**
    - Patterns can destructure data.
    - Catch-all case: `_ => ...`
    - The compiler can warn if patterns are non-exhaustive (recommended).
    - Can be used as a statement (or as an expression, planned).

---

### 2. `switch` Statement

- **Purpose:** Classic, C/Java/C++/JavaScript-style branching on constant values.
- **Syntax:**
  ```vlp
  switch (expr) {
      case Value1: {
          // statements
      }
      case Value2: {
          // statements
      }
      default: {
          // statements
      }
  }
  ```

- **Examples:**
  ```vlp
  var n = 2;
  switch (n) {
      case 1: {
          print("One");
      }
      case 2: {
          print("Two");
      }
      default: {
          print("Other");
      }
  }
  ```

- **Features:**
    - Branch on constant values only (int, char, string, enum variants).
    - Fallthrough is **NOT** allowed by default—each case is independent (no accidental bugs!).
    - `default:` is optional but recommended.

---

### 3. Differences & Guidance

| Feature      | `match`                                 | `switch`                             |
|--------------|-----------------------------------------|--------------------------------------|
| Patterns     | Full patterns, destructuring, types     | Constant values only                 |
| Exhaustiveness | Compiler checks all patterns           | No requirement, but `default` is common |
| Data types   | Works with enums, kits, tuples, option  | Only on values like int/char/enum    |
| Fallthrough  | No                                     | No (by design)                       |
| Use for      | Sum types, results, pattern matching    | Simple value branching               |

---

### 4. Best Practices & Gotchas

- Use `match` for sum types, deep data, or when you want the compiler to help you handle all cases.
- Use `switch` for classic "value is X, do Y" logic.
- Always provide a catch-all (`_` or `default`) unless you want to catch missing cases as errors/warnings.
- Braces are **required** for each block (no implicit fallthrough bugs).
- Pattern order matters in `match`—first match wins.

---

### 5. Advanced (Planned)

- **Match guards:** Add `if` to patterns for extra filtering.
    ```vlp
    match n {
        x if x > 10 => print("Large"),
        _ => print("Small or equal")
    }
    ```
- **Match as expression:** Assign result from match.

---

### 6. Common Errors

- **Missing braces:**  
  ```vlp
  case 1: print("hi") // ❌ Must use { }
  ```
- **Non-constant in `switch` case:**  
  ```vlp
  case x + 1: ... // ❌ Only constant expressions allowed
  ```
- **Non-exhaustive `match`:**  
  ```vlp
  // Compiler warning or error if not all variants are matched
  ```

---

> **Summary:**  
> Use `match` for full-featured, type-safe pattern matching and `switch` for classic constant branching.  
> Both are safe, readable, and error-resistant in Vulpes.
