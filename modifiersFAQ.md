## Modifiers Compatibility & FAQ

Not all modifiers can be mixed together—some combinations are meaningless or disallowed for safety or clarity.  
Here’s what you can and can’t do.

---

### 1. **Can I combine `SOLID` and `FX`?**
- **No.**  
  `SOLID` makes a variable constant (immutable); `FX` creates a lambda/function value, which is always reassignable unless explicitly constant.
  - **Error:** “Cannot declare a lambda as both `SOLID` and `FX`.”

---

### 2. **Can I use `ARRAY` with `PTR`?**
- **Yes, but with care.**  
  - `var[ARRAY(4)]::int x = ...;` — A fixed-size array of ints.
  - `var[PTR, ARRAY(4)]::int x = ...;` — A pointer to a fixed-size array of ints.
  - `var[ARRAY(4), PTR]::int x = ...;` — An array of pointers (each to an int).
- **Tip:** The order of modifiers matters for what is being pointed to.

---

### 3. **Can I combine multiple pointer flavors? (`PTR(UNIQUE, SHARED)`)**
- **No.**  
  Each pointer can have only one flavor (`UNIQUE`, `SHARED`, `WEAK`, or `STRONG`).
  - **Error:** “Multiple pointer flavors are not allowed.”

---

### 4. **Can I use `OPTION` or `RESULT` with arrays or pointers?**
- **Yes.**  
  Optional/Result values can wrap any type:
    - `var[OPTION]::int x = None;`
    - `var[OPTION, ARRAY(4)]::int xs = None;` (optional array)
    - `var[RESULT, PTR(UNIQUE)]::Point p = ...;` (result of a unique pointer)

---

### 5. **Can I use `SOLID` and `PTR` together?**
- **Yes, but:**  
  This makes an immutable pointer—you can’t change which value it points to, but the value it points at may still be mutable (unless *that* value is also `SOLID`).

---

### 6. **Can I combine `FX` and `PTR`?**
- **Usually not.**  
  Function values are already “first class”; pointers to functions are not generally needed, but may be allowed for FFI or callbacks.
  - **Allowed only with explicit intent:**  
    - `var[PTR]::fn(int)=>int fptr = ...;`

---

### 7. **Can I have multiple `ARRAY` or `PTR` modifiers?**
- **Yes, but only for nesting:**  
  - `var[ARRAY(3), ARRAY(2)]::int mtx = ...;` // 2D array (array of arrays)
  - `var[PTR, PTR]::int pp = ...;` // Pointer to a pointer
- **But:** Don’t mix multiple pointer flavors or array sizes at the same level.

---

### 8. **Are there any truly illegal combos?**
- **Illegal or discouraged:**
  - `[SOLID, FX]` — see above
  - `[PTR(UNIQUE), PTR(SHARED)]` — only one pointer flavor per pointer
  - `[OPTION, RESULT]` — nesting both rarely makes sense (use one or nest intentionally)
  - `[ARRAY(N), ARRAY(M)]` — must be clearly nested (not two array sizes at the same level)

---

### 9. **How does modifier order work?**
- **Order matters for complex types.**
  - `[PTR, ARRAY(4)]` is a pointer to an array
  - `[ARRAY(4), PTR]` is an array of pointers

---

### 10. **What if I use an unknown or reserved modifier?**
- The compiler will error: “Unknown modifier `FOO`.”
- Custom modifiers may be allowed in the future (with explicit registration).

---

### **Quick Compatibility Matrix**

|                | `SOLID` | `FX` | `PTR` (any) | `ARRAY` | `OPTION` | `RESULT` |
|----------------|---------|------|-------------|---------|----------|----------|
| **SOLID**      |    —    |  ❌  |     ✔️      |   ✔️    |    ✔️    |    ✔️    |
| **FX**         |   ❌    |  —   |     ?*      |   ✔️    |    ✔️    |    ✔️    |
| **PTR**        |   ✔️    |  ?*  |     —       |   ✔️    |    ✔️    |    ✔️    |
| **ARRAY**      |   ✔️    |  ✔️  |     ✔️      |   —     |    ✔️    |    ✔️    |
| **OPTION**     |   ✔️    |  ✔️  |     ✔️      |   ✔️    |    —     |    ✔️    |
| **RESULT**     |   ✔️    |  ✔️  |     ✔️      |   ✔️    |    ✔️    |    —     |

- `✔️` = valid/meaningful combo
- `❌` = forbidden
- `?*` = rare/advanced/only for special cases (e.g., pointers to functions)

---

### **Summary**

- Most combos are legal and meaningful if you understand their order and effect.
- Some combos are blocked for safety or because they are redundant or contradictory.
- **When in doubt, try to state your intent clearly with only the modifiers you need.**

---

> **If you ever get a confusing error, check this chart or the error message for details!
> The Vulpes compiler will always tell you *why* a combo is invalid.**
