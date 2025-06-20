## Modifiers in Vulpes

Modifiers are annotations that change the behavior or type of a variable or function.  
They appear in square brackets `[Modifier, ...]` immediately after `var` or relevant keyword.

**Syntax:**

```vlp
var[Modifier1, Modifier2]::type name = value;
```

---

### Common Modifiers

| Modifier         | Parameters    | Applies To              | Purpose/Effect                            | Example                                 |
|------------------|--------------|-------------------------|-------------------------------------------|-----------------------------------------|
| `SOLID`          | (none)       | Variables               | Makes variable constant/immutable         | `var[SOLID]::int x = 10;`               |
| `FX`             | (none)       | Variables               | Declares an in-scope function (lambda)    | `var[FX] double = (x: int) => x * 2;`   |
| `PTR`            | flavor/type  | Variables, fields       | Pointer/reference to another value        | `var[PTR(UNIQUE)]::Point p = ...;`      |
| `ARRAY`          | size (int)   | Variables, fields       | Fixed-size array                          | `var[ARRAY(4)]::int nums = [1,2,3,4];`  |
| `OPTION`         | (none)       | Variables, fields       | Optional value, may be None               | `var[OPTION]::int maybe = None;`        |
| `RESULT`         | (none)       | Variables, fields       | Success or error value                    | `var[RESULT]::string res = ...;`        |
| `MUT` (reserved) | (none)       | (Usually not needed)    | Explicit mutability (default in Vulpes)   | *Unused; all vars mutable unless SOLID* |

---

### Pointer Flavors (as PTR parameters)

| Flavor    | Description                                | Example                             |
|-----------|--------------------------------------------|-------------------------------------|
| `UNIQUE`  | Single, move-only owner                    | `var[PTR(UNIQUE)]::T val = ...;`   |
| `SHARED`  | Reference-counted shared ownership         | `var[PTR(SHARED)]::T val = ...;`   |
| `WEAK`    | Weak reference, does not prevent GC        | `var[PTR(WEAK)]::T val = ...;`     |
| `STRONG`  | Strong reference, prevents GC              | `var[PTR(STRONG)]::T val = ...;`   |

---

### Array & Collection Modifiers

- **`ARRAY(N)`**: Fixed-length array, enforces size at compile-time.
    ```vlp
    var[ARRAY(8)]::byte buffer = ...;
    ```
- **Future:**
    - `VECTOR`: Dynamic array
    - `MAP`, `SET`: Collections (when supported)

---

### Function Modifiers

- **`FX`**: Makes variable a first-class function/lambda, usable in-scope.
    ```vlp
    var[FX] add = (a: int, b: int) => a + b;
    ```

---

### Modifier Placement & Stacking

- Multiple modifiers are separated by commas:
    ```vlp
    var[SOLID, PTR(UNIQUE)]::int ptr = ...;
    ```
- Modifiers always come **after** the `var` or keyword, and **before** type annotation.

---

### Example Usage

```vlp
// Immutable integer
var[SOLID]::int max = 100;

// Shared pointer to Point
var[PTR(SHARED)]::Point shared_pt = ...;

// Array of 3 floats
var[ARRAY(3)]::float coords = [1.0, 2.0, 3.0];

// Optional string
var[OPTION]::string nickname = None;

// In-scope lambda function
var[FX] print_twice = (s: string) => {
    print(s);
    print(s);
};
```

---

### Best Practices

- Use only the modifiers needed for your intent—avoid stacking without purpose.
- `SOLID` for true constants, `PTR` for references, `FX` for lambdas/functions.
- For more advanced patterns, combine modifiers (e.g., `[SOLID, PTR(UNIQUE)]`).

---

> **Summary:**  
> Modifiers let you tailor the behavior and type of variables and functions in Vulpes—giving you flexibility with clear, explicit intent.
