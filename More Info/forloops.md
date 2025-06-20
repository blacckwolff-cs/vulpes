## For Loop Examples in Vulpes

### 1. Range-based for loop (inclusive lower, exclusive upper)

```vlp
// Prints numbers 0 through 4
for i in 0..5 {
    print(i);
}
```

---

### 2. Range with step

```vlp
// Prints even numbers from 0 to 8
for i in 0..10 step 2 {
    print(i);
}
```

---

### 3. Reverse range

```vlp
// Prints 5, 4, 3, 2, 1
for i in 5..0 step -1 {
    print(i);
}
```

---

### 4. Array iteration

```vlp
var fruits = ["apple", "banana", "cherry"];
for fruit in fruits {
    print(fruit);
}
```

---

### 5. Array iteration with index

```vlp
var colors = ["red", "green", "blue"];
for (i, color) in colors {
    print("Index " + i + ": " + color);
}
```

---

### 6. Iterating over map/dictionary (planned)

```vlp
var scores = {"sam": 90, "lee": 88, "jo": 77};
for (name, score) in scores {
    print(name + ": " + score);
}
```

---

### 7. Early exit with `break` and skipping with `continue`

```vlp
for i in 0..10 {
    if (i == 5) {
        break; // Stop at 5
    }
    if (i % 2 == 0) {
        continue; // Skip even numbers
    }
    print(i);
}
```

---

### 8. Nested for-loops (matrix/grid)

```vlp
for x in 0..3 {
    for y in 0..3 {
        print("(" + x + ", " + y + ")");
    }
}
```

---

### 9. Iterating custom collections (with iterator protocol, planned)

```vlp
kit Range {
    start: int,
    end: int
}

var my_range = Range { start: 10, end: 15 };
for x in my_range {
    print(x);
}
```

---

> 🦊 **Tip:**  
> Vulpes for-loops are flexible—work with any iterable, including ranges, arrays, strings, collections, and your own types!