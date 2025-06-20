# 15. Style Guide & Best Practices

Vulpes encourages clarity, expressiveness, and consistency.  
Follow these guidelines for readable, maintainable, idiomatic code—whether you’re hacking a demo or building a production system.

---

## 15.1 Naming Conventions

| Element        | Convention      | Example            |
|----------------|----------------|--------------------|
| Variables      | `camelCase`    | `countDown`        |
| Functions      | `camelCase`    | `computeTotal`     |
| Kits (Structs) | `PascalCase`   | `FileReader`       |
| Enums          | `PascalCase`   | `FileType`         |
| Constants      | `ALL_CAPS`     | `MAX_SIZE`         |
| Modules        | `snake_case`   | `math_utils`       |

---

## 15.2 Indentation & Formatting

- Use 4 spaces per indentation level (no tabs).
- Keep lines ≤ 100 characters.
- Add blank lines between logical code blocks (functions, sections).
- Consistent brace style:

    ```vlp
    fx main() => unit {
        // ...
    }
    ```

- Prefer one statement per line.

---

## 15.3 Comments & Documentation

- Use comments to clarify *why*, not just *what*.
- Favor doc comments (`///` or `/** ... */`) for public APIs and modules.
- Keep comments up-to-date—remove obsolete notes.

---

## 15.4 Function & Kit Design

- Favor short, focused functions—ideally 5–20 lines.
- Prefer explicit parameter and return types, especially in public APIs.
- Use kits for related data—avoid “God structs” with too many responsibilities.
- Document public fields and methods.

---

## 15.5 Control Flow

- Use `match` or early return to avoid deeply nested if/else ladders.
- Prefer clear, explicit logic over clever one-liners.
- Handle all cases explicitly in `match` statements.

---

## 15.6 Error Handling

- Use `option` and `result` for recoverable errors.
- Reserve `panic`/`assert` for unrecoverable conditions.
- Always handle or propagate errors—don’t ignore them.

---

## 15.7 Modules & Imports

- Group related functions/kits into logical modules.
- Use explicit `import`—avoid wildcard imports unless truly necessary.
- Export only what you intend as the public API.

---

## 15.8 Concurrency

- Prefer message passing and immutability for safe concurrent code.
- Document which APIs are thread-safe.
- Avoid unnecessary shared mutable state.

---

## 15.9 Metaprogramming

- Use macros and trinkets to eliminate repetition, not to make clever magic.
- Always document the purpose and usage of macros.

---

## 15.10 File Organization

- One module per file.
- Keep related files together in folders by namespace.
- Name files, folders, and modules consistently.

---

## 15.11 Example: Idiomatic Vulpes

```vlp
/// Computes the nth Fibonacci number.
fx fibonacci(n: int) => int {
    if (n <= 1) {
        return n;
    }
    return fibonacci(n - 1) + fibonacci(n - 2);
}
```

---

<!--
TODO:
- Write a “Vulpes Style Linter” for automated checks
- Document idioms for common patterns (builder, visitor, etc.)
- Add community style guides for web, games, CLI, etc.
-->

---

> **Summary:**  
> Idiomatic Vulpes code is readable, explicit, and welcoming to future you and your teammates—write for clarity, and your code will live long and prosper!
