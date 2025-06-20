## Function Call Statements

Function calls in Vulpes are expressions that invoke code—either standalone functions or methods attached to kits (structs).

---

### 1. **Standalone Function Call**

- **Syntax:**  
  ```
  functionName(arg1, arg2, ...);
  ```
- **Examples:**
  ```vlp
  print("hello, world!");
  add(3, 4);
  fx main() => unit {
      do_something();
  }
  ```

---

### 2. **Kit Method (Member Function) Call**

- **Syntax:**  
  ```
  object.methodName(arg1, arg2, ...);
  ```
- **Examples:**
  ```vlp
  var s = "hello";
  s.len();            // calls 'len' method on string

  var point = Point { x: 2, y: 3 };
  point.move(5, 7);   // calls 'move' on a Point kit

  // Chaining
  point.translate(1, 2).normalize();
  ```

---

### 3. **Static/Associated Functions**

- **Syntax:**  
  ```
  TypeName.functionName(args...);
  ```
- **Examples:**
  ```vlp
  Point.origin();     // calls static 'origin' constructor on Point kit
  Math.sqrt(2.0);     // from a Math module/kit
  ```

---

### 4. **Passing/Returning Functions**

- **Passing a function:**
  ```vlp
  apply_twice(add, 2, 3);
  ```
- **Returning a function from another function (higher-order):**
  ```vlp
  fx make_adder(n: int) => fn(int) => int {
      return (x: int) => x + n;
  }
  var add5 = make_adder(5);
  add5(10); // returns 15
  ```

---

### 5. **Best Practices & Gotchas**

- Use parentheses for *every* call, even if no arguments (`foo();`).
- For member calls, always use the dot: `object.method()`.
- Function/method calls are expressions and can be nested:
  ```vlp
  print(get_message().to_upper());
  ```
- Avoid excessive chaining for readability.
- If a function returns a value you don’t use, it’s okay to ignore the result, but prefer explicit assignment or discard (`_ = foo();`) for clarity.

---

### 6. **Advanced (Planned)**

- **Named arguments:**  
  ```vlp
  foo(x: 5, y: 3);
  ```
- **Default parameters:**  
  ```vlp
  fx greet(name: string = "world") => unit { ... }
  greet(); // uses default
  ```

---

> **Summary:**  
> In Vulpes, call standalone functions as `function(args...)`, call methods with `object.function(args...)`, and use dot syntax for both chaining and clarity.
