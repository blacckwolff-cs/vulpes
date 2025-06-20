# 9. Modules & Namespaces

Modules in Vulpes allow you to organize code into logical units—making large projects manageable, reusable, and easy to navigate.  
Namespaces prevent naming conflicts and promote clear, explicit code organization.

---

## 9.1 Module Basics

- **One module per `.vlp` file**.  
  File name (minus `.vlp`) is the default module name.

    ```
    main.vlp     // module 'main'
    math.vlp     // module 'math'
    net/io.vlp   // module 'net::io'
    ```

- The entry point is usually the `main.vlp` file, which contains `fx main()`.

---

## 9.2 Directory and Namespace Structure

- Directories mirror module namespaces.
- Use double colons (`::`) to separate nested namespaces/modules.

    ```
    src/
      main.vlp          // module main
      math/
        trig.vlp        // module math::trig
        stats.vlp       // module math::stats
      net/
        io.vlp          // module net::io
    ```

---

## 9.3 Importing Modules

- Use `import` to bring a module’s exported items into scope.

    ```vlp
    import math::trig;
    import net::io;
    ```

- You can import an entire module or specific items:

    ```vlp
    import math::trig::{sin, cos};
    ```

- **Aliasing:** Use `as` to import a module or item with a new local name.

    ```vlp
    import net::io as netio;
    netio::read();
    ```

---

## 9.4 Exporting from Modules

- Use `export` on functions, kits, enums, or variables to make them accessible from other modules.

    ```vlp
    // In math/trig.vlp
    export fx sin(x: float) => float { ... }
    export fx cos(x: float) => float { ... }
    ```

- Non-exported items are private to their module.

---

## 9.5 Visibility Control

- **export** (or `pub`): Item is visible outside the module.
- **priv**: Explicitly marks an item as private (optional; private is default).

    ```vlp
    export kit Point { ... }
    priv fx helper() => unit { ... }
    ```

- Module-level visibility can be set with trinkets or attributes (future).

---

## 9.6 Module Initialization & Import Order

- Modules are initialized in dependency order.
- Circular imports are discouraged; the compiler will report an error if detected.
- Initialization code in a module runs once, at first import.

---

## 9.7 Example: Project Layout

```
myapp/
  src/
    main.vlp
    math/
      trig.vlp
      stats.vlp
    net/
      io.vlp
  myapp.kit
```

**Sample usage:**

```vlp
import math::trig;
import net::io as nio;

fx main() => unit {
    var x = trig::sin(1.57);
    nio::read();
}
```

---

## 9.8 Best Practices

- Use directories and namespaces for logical separation, not just file size.
- Export only what you want public—keep implementation details private.
- Prefer explicit imports; avoid “wildcard” imports unless necessary.
- Document your module’s public API with doc comments.

---

<!--
TODO:
- Specify whether relative imports (./foo) are allowed
- Finalize rules for cyclic dependencies and initialization
- Document module-level trinkets/attributes for visibility
- Standardize import aliasing syntax
-->

---

> **Summary:**  
> Modules and namespaces in Vulpes enable large, maintainable, and reusable codebases—keep your project clean and your APIs clear!
