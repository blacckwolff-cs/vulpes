# 13. Metaprogramming, Macros & Reflection

Vulpes empowers advanced users to write code that writes code—enabling flexible, efficient, and DRY (Don’t Repeat Yourself) solutions.  
Macros and reflection provide both compile-time and runtime introspection and code generation.

---

## 13.1 Philosophy

- **Power with restraint:** Macros and metaprogramming should boost productivity, not destroy readability.
- **Clear boundaries:** Macros are opt-in and explicit—no “magic” or invisible behavior.
- **Reflection is safe:** Only exposes metadata, not unchecked dynamic behavior.

---

## 13.2 Macros

- Macros are reusable templates that expand into code at compile time.
- Declared with the `macro` keyword (planned):

```vlp
macro repeat(times: int, code: block) {
    for i in 0..times {
        code
    }
}

repeat(3, {
    print("Hello from macro!");
});
```

- Macros can generate functions, types, or repetitive code patterns.
- Macro expansion happens before compilation—errors inside macros are surfaced in expanded code.

---

## 13.3 Attribute Trinkets

- Trinkets (attributes) provide metadata or change compilation behavior.

```vlp
#[inline]
fx fast_add(a: int, b: int) => int {
    return a + b;
}

#[deprecated("use fast_add instead")]
fx old_add(a: int, b: int) => int { ... }
```

- Standard trinkets:
    - `#[inline]`: Request inlining.
    - `#[deprecated(msg)]`: Mark as deprecated.
    - `#[gc]`: Enable garbage collection.
    - `#[test]`: Mark a function as a test.

---

## 13.4 Reflection & Introspection

- The `reflect` module (planned) allows runtime inspection of types, fields, and methods.

```vlp
import reflect;

var t = type(my_obj);
var fields = reflect::fields(my_obj); // List of field names/types
var methods = reflect::methods(my_obj); // List of method names
```

- Reflection is read-only—no runtime code injection.

---

## 13.5 Compile-Time Evaluation (Planned)

- Support for compile-time computation, constants, and code analysis is planned:

```vlp
const PI = math::pi(); // Evaluated at compile time
```

- Potential for `const fn` (compile-time functions) for more advanced patterns.

---

## 13.6 Code Generation & Templates (Planned)

- Macros can be used to generate code for repetitive patterns, data structures, and boilerplate.

```vlp
macro newtype(name: string, base: type) {
    kit $name {
        value: $base
    }
}
newtype("Meters", float); // Expands to a kit called Meters
```

---

## 13.7 Best Practices

- Use macros to eliminate true repetition, not to make clever one-liners.
- Always document what a macro or trinket does.
- Use reflection for diagnostics, debugging, or serialization—not for regular logic.

---

## 13.8 Examples

```vlp
// Attribute trinket for test
#[test]
fx test_add() => unit {
    assert(add(1, 2) == 3);
}

// Macro for generating getters (planned)
macro getter(field: string) {
    fx get_$field(self) => auto {
        return self.$field;
    }
}
```

---

<!--
TODO:
- Finalize macro syntax, hygiene, and scope
- Document full list of standard trinkets/attributes
- Specify reflection module API
- Plan for compile-time evaluated functions and constants
-->

---

> **Summary:**  
> Vulpes metaprogramming keeps code DRY, powerful, and explicit—macros and reflection that serve you, not the other way around.
