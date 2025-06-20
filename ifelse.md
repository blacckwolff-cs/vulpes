## If / Else Statements

Conditional execution in Vulpes is handled with `if`, `elif`, and `else`.  
These allow code to branch based on boolean conditions.

---

### 1. **Basic If Statement**

- **Syntax:**
  ```vlp
  if (condition) {
      // statements if condition is true
  }
  ```

- **Example:**
  ```vlp
  if (score > 90) {
      print("Excellent!");
  }
  ```

---

### 2. **If / Else**

- **Syntax:**
  ```vlp
  if (condition) {
      // if-true
  } else {
      // if-false
  }
  ```

- **Example:**
  ```vlp
  if (ready) {
      start();
  } else {
      wait();
  }
  ```

---

### 3. **If / Elif / Else (Multiple Branches)**

- **Syntax:**
  ```vlp
  if (condition1) {
      // branch 1
  } elif (condition2) {
      // branch 2
  } else {
      // fallback
  }
  ```

- **Example:**
  ```vlp
  if (n < 0) {
      print("Negative");
  } elif (n == 0) {
      print("Zero");
  } else {
      print("Positive");
  }
  ```

---

### 4. **Nested Ifs**

```vlp
if (a > 0) {
    if (b > 0) {
        print("Both positive");
    }
}
```
> **Tip:** Use `elif` to flatten deeply nested chains for clarity.

---

### 5. **Expression Form (Planned)**

- In future, Vulpes may allow if-expressions (returning a value):

  ```vlp
  var sign = if (n < 0) {
      -1
  } elif (n > 0) {
      1
  } else {
      0
  };
  ```

---

### 6. **Best Practices & Gotchas**

- Always use parentheses around the condition: `if (cond) { ... }`
- Braces are **required** for the body, even for single-line blocks.
- Only booleans are valid in conditions (`if (x)` requires `x` to be `bool`).
- Prefer `elif` over nested `if`s for multi-way branches.
- For multiple mutually exclusive cases, consider `match` (pattern matching) for clarity and exhaustiveness.

---

### 7. **Common Errors**

- **Forgot parentheses:**  
  ```vlp
  if x > 3 { ... } // ❌ Invalid, must be if (x > 3)
  ```
- **Forgot braces:**  
  ```vlp
  if (x) print(x); // ❌ Invalid, must use { }
  ```
- **Non-boolean in condition:**  
  ```vlp
  if (5) { ... } // ❌ Error: must be a bool
  ```

---

> **Summary:**  
> Use `if`, `elif`, and `else` to branch your code based on conditions.  
> Always use parentheses and braces for clarity and safety.
