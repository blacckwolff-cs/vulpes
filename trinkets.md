## Trinkets (Attributes) in Vulpes

Trinkets add metadata, hints, or special behavior to declarations (functions, kits, variables, modules, etc.).  
Syntax: `#[trinket]` or `#[trinket(params...)]` directly above the declaration.

---

### Common and Planned Trinkets

| Trinket      | Parameters        | Applies To           | Purpose/Effect                            | Example                                       |
|--------------|------------------|----------------------|--------------------------------------------|-----------------------------------------------|
| `inline`     | (none)           | Functions            | Hint to compiler: inline this function     | `#[inline] fx fast_add() { ... }`             |
| `deprecated` | message (string) | Any                  | Mark as deprecated, show warning           | `#[deprecated("Use newFoo instead")]`         |
| `do`         | (none)           | `while` loops        | Run body once before checking condition    | `#[do] while (cond) { ... }`                  |
| `gc`         | (none)           | Kits, vars           | Enable opt-in garbage collection           | `#[gc] var[PTR(SHARED)] x = ...;`             |
| `test`       | (none)           | Functions            | Mark as test for test runner               | `#[test] fx test_add() { ... }`               |
| `main`       | (none)           | Functions            | Entry point (if not named `main`)          | `#[main] fx start() { ... }`                  |
| `export`     | (none)           | Any                  | Explicitly export item from module         | `#[export] var thing = ...;`                  |
| `priv`       | (none)           | Any                  | Explicitly mark as private                 | `#[priv] fx helper() { ... }`                 |
| `doc`        | string           | Any                  | Documentation, for tooltips/docs           | `#[doc("This function is...")]`               |
| `derive`     | traits/list      | Kits, enums          | Auto-implement traits (e.g., `Eq`, `Clone`)| `#[derive(Eq, Clone)] kit Point { ... }`      |
| `bench`      | (none)           | Functions            | Mark as benchmark for test runner          | `#[bench] fx bench_sort() { ... }`            |
| `cfg`        | config expr      | Any                  | Conditional compilation                    | `#[cfg(debug)] var x = ...;`                  |
| `entry`      | (none)           | Functions            | Alternate entry point for programs/tools   | `#[entry] fx cli() { ... }`                   |

---

### Custom/Experimental/Advanced

| Trinket         | Parameters           | Applies To      | Purpose/Effect                      | Example                                 |
|-----------------|---------------------|-----------------|-------------------------------------|-----------------------------------------|
| `ffi`           | C/Rust/Python info  | Functions, kits | Expose to, or import from, FFI      | `#[ffi("c")] fx c_add(x: int) { ... }`  |
| `no_mangle`     | (none)              | Functions       | Disable name mangling (for FFI)     | `#[no_mangle] fx c_fn() { ... }`        |
| `allow`         | warning type        | Any             | Suppress specific lint warning      | `#[allow(unused)] var unused = 0;`      |
| `deny`          | warning type        | Any             | Promote warning to error            | `#[deny(dead_code)]`                    |
| `unstable`      | (none)              | Any             | Mark feature as unstable/experimental | `#[unstable] fx cool_new_thing() {}`   |

---

### Trinket Syntax Summary

```vlp
#[trinket]
#[trinket(param1, param2)]
#[trinket = value]
```

---

### Example Usage

```vlp
#[deprecated("Use new_foo() instead.")]
fx old_foo() => unit { ... }

#[test]
fx test_math() => unit { ... }

#[doc("Stores a point in 2D space.")]
kit Point { x: float, y: float }

#[gc]
var[PTR(SHARED)]::Node node = ...;

#[do]
while (should_continue()) {
    // ...
}
```

---

> **Tip:**  
> Trinkets can be user-defined or added by libraries as Vulpes grows!  
> Tools like Foxhole and IDE extensions will surface and respect trinket metadata.
