# 12. Concurrency & Parallelism

Vulpes provides built-in tools for writing efficient, safe concurrent and parallel code—whether you’re running threads, handling async I/O, or coordinating tasks across CPUs.

---

## 12.1 Philosophy

- **Safety first:** No data races by default. Shared mutable state must be made explicit.
- **Simple and explicit:** Concurrency features are opt-in, clear, and ergonomic.
- **Composable primitives:** Threads, async, and channels can be mixed and matched.

---

## 12.2 Threads

- Use the `thread` module to spawn new threads.

```vlp
import thread;

fx work() => unit {
    print("Working in a thread!");
}

var t = thread::spawn(work);
t.join(); // Wait for the thread to finish
```

- Threads can be spawned with lambdas or `[FX]` functions.

---

## 12.3 Async & Await *(planned)*

- Vulpes supports asynchronous code for I/O, timers, and scalable parallelism.
- Use `async` functions and `await` expressions (planned):

```vlp
fx fetch_url(url: string) => async result(string) {
    // Async network fetch
}

fx main() => unit {
    var content = await fetch_url("https://example.com");
    print(content);
}
```

---

## 12.4 Channels & Message Passing

- Channels enable safe communication between threads and tasks.

```vlp
import thread;

var (sender, receiver) = thread::channel(int);

thread::spawn(|| {
    sender.send(42);
});

var x = receiver.recv();
print("Received: " + x);
```

- Channels can be typed, buffered, or unbuffered.

---

## 12.5 Shared State & Synchronization

- Vulpes provides standard synchronization primitives (planned):
    - Mutexes (mutual exclusion locks)
    - Semaphores
    - Atomic values
    - Barriers

```vlp
import thread;

var counter = thread::atomic_int(0);

fx increment() => unit {
    for i in 0..1000 {
        counter.inc();
    }
}

var t1 = thread::spawn(increment);
var t2 = thread::spawn(increment);
t1.join();
t2.join();
print(counter.get());
```

---

## 12.6 Pointer Flavors & Concurrency

- Use pointer flavors (`SHARED`, `WEAK`, `UNIQUE`, `STRONG`) to guarantee thread safety:
    - Only `SHARED` and `WEAK` pointers are safe to share between threads by default.
    - The compiler prevents data races by checking pointer flavor and ownership.

---

## 12.7 Best Practices

- Avoid shared mutable state when possible—prefer message passing and immutability.
- Use `join` to wait for threads to finish; always handle thread errors.
- Use `await` for async tasks to avoid blocking the main thread.
- Document concurrency expectations in public APIs.

---

## 12.8 Examples

```vlp
// Threaded parallel computation
import thread;

fx calc_square(n: int) => int {
    return n * n;
}

var results = [0, 0, 0, 0];
for i in 0..4 {
    var t = thread::spawn(|| {
        results[i] = calc_square(i);
    });
    t.join();
}
print(results);
```

---

<!--
TODO:
- Finalize async/await and event loop semantics
- Document thread pool and parallel iterator patterns
- Expand on synchronization and atomic operations
- Provide recipes for safe concurrent data structures
-->

---

> **Summary:**  
> Concurrency in Vulpes is fast, safe, and modern—powerful primitives for every task, and safety checks to keep you out of trouble.
