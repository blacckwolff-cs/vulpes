# 5. Functions

Functions in Vulpes encapsulate reusable logic.  
They are first-class values: assignable, passable, composable, and support both classic and functional programming patterns.

---

## 5.1 Function Declaration Syntax

- **Top-level functions** use the `fx` keyword.
- Functions specify parameter types and can declare return types (default is `unit` if omitted).
- Return types can be explicit, inferred, or tuple types.

```vlp
fx greet(name: string) => unit {
    print("Hello, " + name + "!");
}

fx add(x: int, y: int) => int {
    return x + y;
}

fx get_coords() => (float, float) {
    return (0.0, 1.0);
}
```

---

## 5.2 Parameters and Return Types

- **Parameters** must have types.
- **Return type** is optional—defaults to `unit` if omitted or if the function does not return a value.
- **Tuples** can be used for multiple return values.

```vlp
fx max_and_min(a: int, b: int) => (int, int) {
    if (a > b) {
        return (a, b);
    } else {
        return (b, a);
    }
}
```

---

## 5.3 Lambdas & Anonymous Functions

- Use `var[FX]` for in-scope anonymous functions (lambdas) or closures.

```vlp
var[FX] double = (x: int) => x * 2;
```

- Lambdas can be assigned, passed, or returned just like named functions.

---

## 5.4 Named Local Functions (First-Class)

- Use `var[FX] name(args...) => return_type { ... }` to define a named local function.
- These can be passed, assigned, and referenced as values.

```vlp
var[FX] subtract(a: int, b: int) => int {
    return a - b;
}

fx apply_twice(f: fn(int, int) => int, x: int, y: int) => int {
    return f(f(x, y), f(x, y));
}
apply_twice(subtract, 10, 3); // Returns 4
```

---

## 5.5 Closures

- Lambdas and named `[FX]` functions can **capture** variables from their enclosing scope.

```vlp
var multiplier = 3;
var[FX] triple = (x: int) => x * multiplier;
triple(5); // Returns 15
```

---

## 5.6 Recursion

- Functions can call themselves or each other (mutual recursion).

```vlp
fx factorial(n: int) => int {
    if (n <= 1) {
        return 1;
    }
    return n * factorial(n - 1);
}
```

---

## 5.7 Higher-Order Functions

- Functions can take other functions as arguments or return them.

```vlp
fx apply(f: fn(int)=>int, x: int) => int {
    return f(x);
}

var[FX] inc = (n: int) => n + 1;
apply(inc, 5); // Returns 6
```

---

## 5.8 Function Overloading & Default Parameters *(planned)*

> **TODO:**  
> Decide if function overloading (same name, different signatures) is supported.
>  
> Consider allowing default parameter values:  
> `fx greet(name: string = "world") => unit { ... }`

---

## 5.9 Error Handling in Functions

- Functions can return `option`, `result`, or use exceptions (see Error Handling).

```vlp
fx safe_div(a: int, b: int) => result(int) {
    if (b == 0) {
        return Err("divide by zero");
    }
    return Ok(a / b);
}
```

---

## 5.10 Best Practices

- Use descriptive names and types for clarity.
- Keep functions short and focused.
- Use lambdas or local `[FX]` functions for callbacks and closures.
- Prefer explicit return types for public APIs.

---

## 5.11 Examples

```vlp
// Top-level function
fx square(x: int) => int {
    return x * x;
}

// Lambda
var[FX] negate = (x: int) => -x;

// Named local function
var[FX] product(a: int, b: int) => int {
    return a * b;
}
```

---

<!--
TODO:
- Finalize overloading and default parameter rules
- Document varargs and named arguments (if any)
- Clarify visibility rules for local vs. top-level functions
- Add async/await/concurrency features in future section
-->

---

> **Summary:**  
> Vulpes functions are flexible, expressive, and first-class.  
> Write in a procedural, functional, or hybrid style—Vulpes adapts to your workflow!
