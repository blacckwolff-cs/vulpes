# 11. Error Handling

Vulpes provides expressive, predictable error handling mechanisms—  
designed to prevent hidden bugs, clarify intent, and make failures safe to manage.

---

## 11.1 Philosophy

- **No silent failures:** All errors are explicit—no hidden “null” dereferences or unchecked exceptions.
- **Choice, not dogma:** Use Option/Result types for recoverable errors, and panic/exception for truly unrecoverable states.
- **Pattern matching first:** Use `match` to elegantly handle all cases.

---

## 11.2 Option & Result Types

- **Option:** Value is present (`Some(val)`) or absent (`None`).
    ```vlp
    fx get_env(name: string) => option(string) {
        if (os::has_env(name)) {
            return Some(os::get_env(name));
        }
        return None;
    }
    ```
- **Result:** Value is `Ok(val)` on success, or `Err(msg)` on error.
    ```vlp
    fx parse_int(s: string) => result(int) {
        // returns Ok(42) or Err("not a number")
    }
    ```

---

## 11.3 Pattern Matching for Errors

- Handle Option and Result with `match` or `if`/`else` chains:

```vlp
match parse_int(input) {
    Ok(n) => print("Parsed: " + n),
    Err(e) => print("Failed: " + e),
}
```

- You can also use early return for error cases:

```vlp
fx div(a: int, b: int) => result(int) {
    if (b == 0) {
        return Err("divide by zero");
    }
    return Ok(a / b);
}
```

---

## 11.4 Propagation and Early Exit

- Use early return to propagate errors:

```vlp
fx process(filename: string) => result(unit) {
    var file = fs::open(filename)?;
    // process file
    return Ok(());
}
```

- The `?` operator (planned) propagates error upward if present, otherwise extracts value.

---

## 11.5 Panics & Unrecoverable Errors

- Use `panic` or `assert` for unrecoverable conditions—these immediately terminate the program.

```vlp
if (!condition) {
    panic("Invariant violated!");
}
```

- **Panic** should only be used when recovery is impossible or makes no sense (e.g., memory corruption, critical bug).

---

## 11.6 Try/Catch Exceptions *(planned/optional)*

> **TODO:**  
> Decide if Vulpes will support classic exceptions or strictly Option/Result.
> If exceptions are added:
> ```vlp
> try {
>     might_fail();
> } catch (e) {
>     print("Caught error: " + e);
> }
> ```

---

## 11.7 Best Practices

- Use `option` and `result` for all recoverable errors and absence-of-value cases.
- Reserve `panic`/`assert` for truly unrecoverable logic errors.
- Prefer exhaustive `match` or `if`/`else` branches—handle all possible cases.
- Document error behaviors in public APIs (what errors, what causes them).

---

## 11.8 Examples

```vlp
fx read_number() => result(int) {
    var line = input("Enter a number: ");
    return parse_int(line);
}

var res = read_number();
match res {
    Ok(n) => print("Your number: " + n),
    Err(e) => print("Error: " + e),
}
```

---

<!--
TODO:
- Decide on language-wide exception model (try/catch/finally)
- Document ? error-propagation operator rules
- Provide recipes for common error handling patterns
- List standard error types and codes (IO, parse, custom)
-->

---

> **Summary:**  
> Error handling in Vulpes is safe, explicit, and powerful—giving you the right tool for every error, from a missing file to a fatal bug.
