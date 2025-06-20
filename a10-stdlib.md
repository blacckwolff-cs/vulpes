# 10. Standard Library & Built-ins

Vulpes ships with a powerful standard library (“stdlib”) and a set of built-in functions and operators—  
from basic I/O to advanced math, string/array handling, and cross-platform graphics inspired by Raylib.

---

## 10.1 Core Modules

| Module         | Purpose/Contents                                  |
|----------------|---------------------------------------------------|
| `io`           | Input/output (print, input, file read/write)      |
| `math`         | Math functions/constants (sin, cos, sqrt, PI, …)  |
| `str`          | String utilities and manipulation                 |
| `array`        | Array, slice, and sequence utilities              |
| `os`           | Operating system and environment interaction      |
| `fs`           | Filesystem utilities                              |
| `net`          | Networking (planned)                              |
| `time`         | Dates, times, durations, timers                   |
| `fmt`          | String formatting, interpolation                  |
| `thread`       | Threading, concurrency primitives (planned)       |
| `collections`  | Vectors, maps, sets, queues, stacks, etc. (planned) |
| `graphics`     | **2D/3D graphics, windowing, input—Raylib-style** |
| `audio`        | Sound/music support (planned)                     |
| `image`        | Image loading, manipulation (planned)             |

---

## 10.2 Raylib-style Graphics Module

The `graphics` module exposes powerful, cross-platform primitives for making games, visualizations, and creative tools.  
Modeled after Raylib—**simple, immediate, and fun.**

### 10.2.1 Example Usage

```vlp
import graphics;

fx main() => unit {
    graphics::init_window(800, 600, "Vulpes Raylib Demo");

    while (!graphics::window_should_close()) {
        graphics::begin_drawing();
        graphics::clear_background(graphics::Color::SkyBlue);

        graphics::draw_text("Hello, Vulpes!", 350, 280, 24, graphics::Color::Black);

        graphics::end_drawing();
    }
    graphics::close_window();
}
```

### 10.2.2 Key Features

- Window/context management (`init_window`, `close_window`, `window_should_close`)
- Drawing primitives (text, lines, rectangles, circles, polygons)
- Sprites, images, textures
- Mouse/keyboard/gamepad input
- Audio (future: music, sound effects)
- Asset loading (images, fonts, sounds)

> 🦊 **Tip:**  
> The graphics API is designed to be approachable for both beginners and experts—“get pixels on screen in one minute.”

---

## 10.3 Built-in Functions and Operators

Vulpes provides a robust set of built-in functions available in every scope, with standard operator support:

### 10.3.1 I/O

| Name                | Signature                             | Description                             |
|---------------------|---------------------------------------|-----------------------------------------|
| `print`             | `print(args...) => unit`              | Print text or values to standard output |
| `println`           | `println(args...) => unit`            | Print with newline                      |
| `input`             | `input(prompt: string = "") => string`| Read a line from standard input         |
| `debug`             | `debug(val: any) => unit`             | Print debug representation (type, value)|

### 10.3.2 Type & Introspection

| Name         | Signature                   | Description                           |
|--------------|-----------------------------|---------------------------------------|
| `type`       | `type(val: any) => string`  | Get the type name of a value          |
| `len`        | `len(val: array|str|map) => int` | Length of collection or string |
| `assert`     | `assert(cond: bool) => unit`| Panic if condition is false           |
| `clone`      | `clone(val: any) => any`    | Shallow copy (for option, array, kit) |

### 10.3.3 Math/Logic

| Name           | Signature                                | Description                   |
|----------------|------------------------------------------|-------------------------------|
| `abs`          | `abs(n: int|float) => int|float`         | Absolute value                |
| `min`, `max`   | `min(a, b) => a`, `max(a, b) => a`       | Minimum/maximum               |
| `sqrt`         | `sqrt(n: float) => float`                | Square root                   |
| `pow`          | `pow(base: float, exp: float) => float`  | Exponentiation                |
| `sin`, `cos`, ... | `sin(x: float) => float`              | Trig functions                |
| `rand`         | `rand() => float`                        | Random float 0..1             |

### 10.3.4 String/Array Manipulation

| Name           | Signature                                | Description                   |
|----------------|------------------------------------------|-------------------------------|
| `split`        | `split(s: string, sep: string) => array(string)` | Split string           |
| `join`         | `join(arr: array(string), sep: string) => string` | Join array          |
| `push`         | `push(arr: array, val: any) => unit`     | Append to array (mutable)     |
| `pop`          | `pop(arr: array) => any`                 | Remove last element (mutable) |
| `contains`     | `contains(coll, item) => bool`           | Membership test               |
| `reverse`      | `reverse(arr: array) => array`           | Return reversed array         |

### 10.3.5 System/Utility

| Name           | Signature                     | Description                  |
|----------------|------------------------------|------------------------------|
| `exit`         | `exit(code: int = 0) => unit`| Exit program with status code|
| `sleep`        | `sleep(ms: int) => unit`     | Pause execution              |

---

### 10.3.6 Operators

Vulpes supports a familiar set of operators:

- Arithmetic: `+`, `-`, `*`, `/`, `%`, `**` (power)
- Assignment: `=`, `+=`, `-=`, etc.
- Comparison: `==`, `!=`, `<`, `>`, `<=`, `>=`
- Logic: `&&`, `||`, `!`
- Indexing: `[]`
- Member access: `.`
- Function call: `()`
- (Planned: user-defined operator overloading)

---

## 10.4 Extensibility and Ecosystem

- Standard library is **modular and growing**—community packages are easy to publish/import.
- All stdlib functions are documented and tested.
- IDE integration supports auto-complete and documentation pop-ups for built-ins.

---

## 10.5 Example Usage

```vlp
import graphics;

fx main() => unit {
    graphics::init_window(640, 480, "Draw Demo");
    while (!graphics::window_should_close()) {
        graphics::begin_drawing();
        graphics::clear_background(graphics::Color::White);
        graphics::draw_circle(320, 240, 80, graphics::Color::Red);
        graphics::end_drawing();
    }
    graphics::close_window();
}
```
---

## 10.6 Extension & Ecosystem

- Standard library is extensible—users can import community packages.
- Core modules are versioned and stable for backward compatibility.
- All stdlib APIs are documented and tested.

---

## 10.7 Example Usage

```vlp
import io;
import math;

var value = math::sqrt(16.0);
print("The square root is " + value);

var data = io::input("Type something: ");
print("You said: " + data);
```

---

<!--
TODO:
- Finalize list of core modules and their APIs
- Document community package ecosystem and import rules
- Provide full list of built-in functions and operators
- Specify how built-ins interact with user-defined functions (shadowing/overriding)
-->

---

> **Summary:**  
> The Vulpes standard library is designed to cover everyday programming needs—no bloat, no boilerplate, and always growing with the community!
