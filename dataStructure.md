# 7. Data Structures

Vulpes offers rich data structures for organizing, storing, and manipulating values—balancing flexibility, clarity, and power.

---

## 7.1 Arrays & Slices

- Arrays are fixed-size, ordered collections of elements of the same type.
- Declared with `[ARRAY(n)]` modifier or using array type parameters.

```vlp
var[ARRAY(4)]::int numbers = [1, 2, 3, 4];
var::array(float, 3) coords = [1.0, 2.0, 3.0];
```

- Access elements by zero-based index: `numbers[0]`.
- Slices (views into arrays) may be supported (planned).

---

## 7.2 Kits (Structs)

- Kits are user-defined record types, grouping named fields together.

```vlp
kit Point {
    x: float,
    y: float
}

var origin = Point { x: 0.0, y: 0.0 };
```

- Access fields with dot notation: `origin.x`.

---

## 7.3 Enums (Variants)

- Enums define a type that can be one of several named variants.
- Variants can be plain or carry data (like sum types / tagged unions).

```vlp
enum Color {
    Red,
    Green,
    Blue,
    Rgb(r: int, g: int, b: int)
}

var c = Color::Rgb(128, 64, 255);
```

---

## 7.4 Tuples

- Tuples are fixed-size, ordered collections of values of possibly different types.

```vlp
var pair = (3, "fox", true);
var x = pair.0; // 3
var y = pair.1; // "fox"
```

- Access elements by position (`.0`, `.1`, etc.).

---

## 7.5 Option & Result Types

- **Option:** Represents “value or none.”
    ```vlp
    var maybe_age = Some(30);
    var nothing = None;
    ```
- **Result:** Encodes “success or error.”
    ```vlp
    var status = Ok("done");
    var err = Err("failed");
    ```
- Commonly used with pattern matching to handle absence or errors.

---

## 7.6 Pattern Matching & Destructuring

- Decompose arrays, kits, enums, and tuples using `match` or direct destructuring.

```vlp
match c {
    Color::Red => print("Red!"),
    Color::Rgb(r, g, b) => print("RGB: " + r + "," + g + "," + b),
    _ => print("Other color"),
}
```

- Destructure directly in assignments (planned):

```vlp
var (a, b, c) = (1, 2, 3);
var Point { x, y } = origin;
```

---

## 7.7 Collections (Planned)

- Future versions may support dynamic collections:
    - Vectors (dynamic arrays)
    - Maps (key-value dictionaries)
    - Sets (unique values)
- These may be part of the standard library.

---

## 7.8 Examples

```vlp
// Array of floats
var[ARRAY(3)]::float triangle = [0.0, 1.0, 2.0];

// Kit for a rectangle
kit Rect {
    x: float,
    y: float,
    w: float,
    h: float
}
var box = Rect { x: 0, y: 0, w: 10, h: 5 };

// Enum for file results
enum FileResult {
    Ok(data: string),
    Err(msg: string)
}
var result = FileResult::Ok("file contents");
```

---

<!--
TODO:
- Finalize syntax for destructuring assignment
- Document standard library collections when available
- Expand on slice/view types for arrays
- Consider supporting generic kits/enums
-->

---

> **Summary:**  
> Vulpes data structures let you build expressive, type-safe programs—whether you’re modeling simple values or complex systems.
