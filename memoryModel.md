# 8. Memory Model

Vulpes gives you explicit, predictable control over memory, inspired by modern safe systems languages but without unnecessary complexity.  
You can write code that’s both powerful and safe—no hidden allocations, leaks, or surprises.

---

## 8.1 Ownership & Lifetime

- **Variables “own” their values** by default.
- A value’s lifetime is limited to the scope in which it is defined.
- When a variable goes out of scope, its memory is reclaimed automatically.
- No implicit garbage collection for primitive values; memory safety is enforced by design.

```vlp
fx demo() => unit {
    var x = 42; // x owns this int
    // x is destroyed at end of scope
}
```

---


## 8.2 References & Pointers

- Vulpes uses `[PTR]` as a modifier to indicate a pointer/reference type.
- **Pointer “flavors”** can be specified as parameters to `[PTR]` for precise control over ownership and sharing:

| Flavor   | Description                                    | Example Syntax                        |
|----------|------------------------------------------------|---------------------------------------|
| `UNIQUE` | Single owner (moves, not copies); safe mutation| `var[PTR(UNIQUE)]::kit ptr = ...;`    |
| `SHARED` | Reference-counted shared ownership             | `var[PTR(SHARED)]::kit ptr = ...;`    |
| `STRONG` | Strong reference; prevents collection          | `var[PTR(STRONG)]::kit ptr = ...;`    |
| `WEAK`   | Weak reference; does not prevent collection    | `var[PTR(WEAK)]::kit ptr = ...;`      |

- **Examples:**

```vlp
// Unique (owning) pointer
var[PTR(UNIQUE)]::Point p1 = ...;

// Shared reference (reference counted)
var[PTR(SHARED)]::Point p2 = ...;

// Weak reference (does not keep object alive)
var[PTR(WEAK)]::Point maybe = ...;
```

- Flavors are checked at compile time, and pointer operations are limited by their flavor:
    - `UNIQUE` pointers cannot be copied, only moved.
    - `SHARED` and `WEAK` support cloning and reference-counting.
    - `STRONG` prevents garbage collection, while `WEAK` does not.

---

## 8.2.1 Pointer Flavor Reference Table

| Flavor   | Copy? | Move? | Auto-cleanup? | Prevents GC? | Mutable? |
|----------|-------|-------|---------------|--------------|----------|
| UNIQUE   |   ❌   |  ✔️   |      ✔️      |     ✔️       |   ✔️     |
| SHARED   |   ✔️   |  ✔️   |      ✔️      |     ✔️       |   Conditional |
| STRONG   |   ✔️   |  ✔️   |      ✔️      |     ✔️       |   Conditional |
| WEAK     |   ✔️   |  ✔️   |      ✔️      |     ❌       |   ❌     |

---

## 8.2.2 Garbage Collection Trinket

- Use a trinket to enable **automatic garbage collection** for a value or kit:
    ```vlp
    #[gc] var[PTR(SHARED)]::Point p = ...;
    ```
- The `#[gc]` trinket signals that this variable or kit should participate in the automatic garbage collector, if present.
- This allows hybrid memory management—use GC where convenient, deterministic RAII where you want full control.

> **Tip:**  
> By default, Vulpes uses explicit lifetimes and deterministic cleanup. GC is opt-in and never required for all values.

---

## 8.2.3 Example

```vlp
kit Node {
    value: int,
    next: [PTR(WEAK)]::Node
}

// Use shared references for graph structures
#[gc]
var[PTR(SHARED)]::Node root = Node { value: 1, next: null };

// Weak references prevent cycles/leaks
var[PTR(WEAK)]::Node maybe = root.next;
```

---

## 8.2.4 Philosophy

- **Memory management is explicit, flexible, and safe.**
- Pointer flavors make ownership and lifetime clear in code.
- Opt-in GC supports high-level programming *without sacrificing performance or predictability for system-level code.*

---

<!--
TODO:
- Document flavor-specific errors at compile-time (e.g., copying UNIQUE)
- Specify how garbage collector interacts with #[gc] trinket and pointer flavors
- Provide recipes for common memory patterns (linked lists, trees, graphs, etc.)
-->

---

## 8.3 Stack vs Heap Allocation

- **Stack allocation:**  
  - Most values (primitives, small kits, arrays) are stack-allocated for speed.
  - Lifetime is tied to the enclosing scope/block.
- **Heap allocation:**  
  - Large arrays, dynamic collections, and certain complex types may be heap-allocated.
  - Managed via explicit constructors/destructors or standard library containers.

> 🦊 **Tip:**  
> The Vulpes memory model defaults to stack allocation for performance, with heap only when needed—no accidental memory leaks or bloated garbage collection.

---

## 8.4 Mutability & Sharing

- **Mutable by default:** Any variable (except `[SOLID]`) can be changed.
- **Multiple references:** Allowed, but may be restricted if it would create unsafe aliasing or data races (see Concurrency section).

---

## 8.5 Resource Management

- Vulpes encourages **RAII** (Resource Acquisition Is Initialization): acquire resources in constructors, release in destructors.
- Kits can implement destructor-like methods for cleanup.
- No implicit garbage collection for most user-defined types (future: opt-in GC for complex cases?).

---

## 8.6 Unsafe Operations *(Planned)*

- For low-level power users, Vulpes may support `unsafe` blocks or attributes, allowing unchecked pointer arithmetic, manual memory management, etc.
- Use with caution; required for FFI and certain optimizations.

---

## 8.7 Example

```vlp
var[PTR]::int ptr = null;
{
    var n = 99;
    ptr = &n;
    print(*ptr); // OK: n is alive
}
// ptr is now dangling—accessing it is an error!
```

---

## 8.8 Philosophy

- **No hidden costs:** Memory allocation and deallocation are explicit or predictable.
- **Safety first:** Dangerous memory operations are clearly marked and discouraged.
- **Predictable performance:** No surprise pauses or unpredictable resource usage.

---

<!--
TODO:
- Finalize dereference and address-of syntax
- Specify error messages for invalid memory access
- Document standard library containers’ allocation strategies
- Add details for FFI/unsafe blocks when ready
-->

---

> **Summary:**  
> The Vulpes memory model is designed for power *and* safety—giving you low-level control without the footguns of legacy systems languages.