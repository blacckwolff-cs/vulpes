## Break & Continue Statements

Vulpes provides `break` and `continue` statements to control loop execution flow.

---

### 1. **`break` Statement**

- **Purpose:** Immediately exits the nearest enclosing loop (for, while).
- **Syntax:**
  ```vlp
  break;
  ```
- **Example:**
  ```vlp
  for i in 1..10 {
      if (i > 5) {
          break;  // Stop loop when i > 5
      }
      print(i);
  }
  // Only prints 1 through 5
  ```

---

### 2. **`continue` Statement**

- **Purpose:** Skips the rest of the current iteration and moves to the next loop iteration.
- **Syntax:**
  ```vlp
  continue;
  ```
- **Example:**
  ```vlp
  var n = 0;
  while (n < 10) {
      n = n + 1;
      if (n % 2 == 0) {
          continue;  // Skip even numbers
      }
      print(n);
  }
  // Prints 1, 3, 5, 7, 9
  ```

---

### 3. **Nested Loops & Loop Labels (Planned/Optional)**

- By default, `break` and `continue` only affect the **innermost loop**.
- In the future, Vulpes may support **labeled loops** for breaking out of outer loops:

    ```vlp
    outer: for i in 0..5 {
        for j in 0..5 {
            if (i == j) {
                break outer; // exits both loops
            }
        }
    }
    ```

---

### 4. **Best Practices & Gotchas**

- Avoid excessive use of `break`/`continue`—use them for clarity, not cleverness.
- If a loop is only used to search for a value or condition, consider returning early or refactoring to a function.
- Make sure `continue` doesn't skip necessary logic (like variable updates).

---

### 5. **Common Errors**

- **Using outside a loop:**
  ```vlp
  fx foo() => unit {
      break; // ❌ Error: not inside a loop
  }
  ```
- **Confusing break/continue:**
  - `break` exits the whole loop.
  - `continue` just moves to the next iteration.

---

> **Summary:**  
> Use `break` to exit loops early, and `continue` to skip to the next iteration.  
> For nested loops, labeled break/continue may be added in future Vulpes versions.
