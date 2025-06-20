# 6. Control Flow

Vulpes provides a rich set of control flow tools to direct how code is executed.  
The goal is clear, concise logic without hidden traps or surprises.

---

## 6.1 Conditionals

### 6.1.1 If / Else

- Use `if` and `else` for standard branching logic.
- Parentheses are required around the condition.
- Braces `{}` define the block to execute.

```vlp
if (score > 90) {
    print("Excellent!");
} else if (score > 75) {
    print("Good job!");
} else {
    print("Keep practicing.");
}
```

### 6.1.2 Elif

- Use `elif` for “else if” branches (optional, may use nested `if` instead).

```vlp
if (temp < 0) {
    print("Freezing!");
} elif (temp < 20) {
    print("Cold");
} else {
    print("Warm");
}
```

---

## 6.2 Pattern Matching

- Vulpes supports `match` for pattern matching (like `switch` in other languages, but more powerful).
- Patterns can include literals, enum variants, option/result types, or destructured kits.

```vlp
match color {
    Color::Red => print("Stop!"),
    Color::Green => print("Go!"),
    Color::Blue => print("Cool color!"),
    _ => print("Unknown color"),
}
```

- The `_` pattern is a catch-all (default case).
- Pattern matching supports destructuring for kits and tuples:

```vlp
kit Point { x: int, y: int }
var p = Point { x: 5, y: 8 };
match p {
    Point { x: 0, y } => print("On y-axis at " + y),
    Point { x, y } => print("At (" + x + ", " + y + ")"),
}
```

---

## 6.3 Loops

### 6.3.1 While Loops

- Repeat a block while a condition is true.

```vlp
var n = 5;
while (n > 0) {
    print(n);
    n = n - 1;
}
```

### 6.3.2 For Loops

- Loop over ranges or iterable collections.

```vlp
for i in 0..5 {
    print(i);
}
for item in items {
    print(item);
}
```

- Range syntax `start..end` is inclusive of `start`, exclusive of `end`.

---

## 6.4 Loop Control: Break & Continue

- `break` exits the nearest enclosing loop.
- `continue` skips to the next iteration.

```vlp
for i in 1..10 {
    if (i % 2 == 0) {
        continue; // Skip even numbers
    }
    if (i > 7) {
        break; // Exit loop early
    }
    print(i);
}
```

---

## 6.5 Early Return

- Use `return` to immediately exit a function and return a value.

```vlp
fx divide(a: int, b: int) => option(int) {
    if (b == 0) {
        return None;
    }
    return a / b;
}
```

---

## 6.6 Exception / Panic / Bailout System *(planned)*

> **TODO:**  
> Decide on approach for errors and exceptions:
> - Should Vulpes use exceptions, explicit result/option types, or both?
> - What is the syntax for throwing/catching exceptions? (`try`, `catch`, `throw`, `panic`)
> - Can you bail out of multiple levels of control flow at once?

Example (proposed):

```vlp
try {
    risky_op();
} catch (e) {
    print("Error: " + e);
}
```

---

## 6.7 Best Practices

- Prefer pattern matching for complex branching.
- Use loops and range expressions for clarity.
- Minimize deeply nested conditionals—use early return or match when possible.
- Handle all possible cases explicitly in `match` to avoid surprises.

---

## 6.8 Examples

```vlp
// Classic conditional
if (ready) {
    start();
} else {
    wait();
}

// Pattern matching
match result {
    Ok(val) => print("Got: " + val),
    Err(e) => print("Failed: " + e),
}

// Loop with continue/break
for i in 0..10 {
    if (i == 5) {
        break;
    }
    print(i);
}
```

---

<!--
TODO:
- Finalize error/exception system
- Document match guards and advanced patterns (if supported)
- Add examples for loop labels or advanced loop control (if planned)
-->

---

> **Summary:**  
> Vulpes provides modern, powerful control flow tools—combining the best of classic and expressive styles for robust, readable logic.
