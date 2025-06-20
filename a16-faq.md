# 16. FAQ & Troubleshooting

Got a question or stuck on something in Vulpes?  
This FAQ covers common pitfalls, surprising behaviors, and the most helpful places to get help.

---

## 16.1 Common Errors

### “Undefined variable: ‘x’”

- **Meaning:**  
  You’re using a variable that hasn’t been declared or is out of scope.
- **Fix:**  
  Check spelling, scope, and that `var` is used before the variable name.

---

### “Type mismatch: expected int, found string”

- **Meaning:**  
  You assigned a value of one type to a variable of a different (incompatible) type.
- **Fix:**  
  Ensure types match, or use explicit type casting if supported.

---

### “Expected ; (semicolon)”

- **Meaning:**  
  You forgot a semicolon at the end of a statement.
- **Fix:**  
  Add a semicolon.

---

### “Cannot assign to immutable variable”

- **Meaning:**  
  You tried to change a `[SOLID]` (immutable) variable.
- **Fix:**  
  Either remove `[SOLID]` or only assign once.

---

## 16.2 Why doesn’t my import work?

- Check your file and directory structure. Module names must match file names.
- Did you use the correct path (e.g., `import math::trig;`)?
- Only exported items can be used from another module.

---

## 16.3 “Why isn’t my function visible?”

- Only functions, kits, enums, and variables marked with `export` (or `pub`) are accessible from other modules.

---

## 16.4 “How do I debug my code?”

- Use `print`, `debug`, or run with `foxhole run --debug` for extra info.
- Check error messages for file, line, and helpful suggestions.
- Use IDE features: breakpoints, variable watch, and call stacks (if available).

---

## 16.5 “How do I fix circular imports?”

- Refactor code to break cycles: move shared code to a third module, or restructure imports.

---

## 16.6 “How do I handle Option/Result values?”

- Always handle both `Some/None` or `Ok/Err` cases with `match` or early return.

    ```vlp
    match get_env("HOME") {
        Some(path) => print("Your home is: " + path),
        None => print("No HOME set."),
    }
    ```

---

## 16.7 My program “panics”—what does that mean?

- A `panic` means Vulpes found an unrecoverable error and stopped.
- Read the error message and stack trace for clues.
- Panics should be rare; use `option`/`result` for recoverable errors.

---

## 16.8 “Why doesn’t my code compile/run?”

- Double-check:
    - All statements end with semicolons.
    - Types match.
    - Modules and file names are correct.
    - Imports/export visibility.
    - The entry point is `fx main()`.

---

## 16.9 Where can I get more help?

- **Official docs:** [vulpes-lang.org/docs](https://vulpes-lang.org/docs) (planned)
- **Community forum:** [forum.vulpes-lang.org](https://forum.vulpes-lang.org) (planned)
- **Discord/Matrix:** Live chat and support (planned)
- **GitHub Issues:** File bugs or feature requests

---

## 16.10 “Can I use Vulpes for X?”

- Games, CLI tools, servers, scientific computing, embedded, scripting—all are supported or planned.
- If you hit a limitation, check the roadmap or suggest a feature!

---

<!--
TODO:
- Expand with more “gotchas” as the language grows
- Link to common recipes, quickstart, and migration guides
- Add “ask for help” command to Foxhole CLI
-->

---

> **Summary:**  
> Every language has learning curves and surprises—use this FAQ, the docs, and the community to smooth the path.  
> If you’re stuck, **ask for help**—everyone started somewhere!
