# 17. Roadmap & Vision

Vulpes is just getting started. Here’s where we’re headed—and how you can help shape the language.

---

## 17.1 Philosophy

- **Accessible systems programming:**  
  Vulpes aims to bring the power of C, C++, and Rust to everyone—without the footguns or steep learning curve.
- **Zero surprises:**  
  Syntax, semantics, and tooling are designed to be clear, explicit, and easy to reason about.
- **“Batteries included, footguns removed”:**  
  A practical, expressive standard library, powerful error handling, and first-class tooling.
- **Community-driven:**  
  Feedback, ideas, and contributions are always welcome.

---

## 17.2 Immediate Priorities

- Complete the core language implementation (compiler, VM, and parser/lexer).
- Finalize the Foxhole build system and package registry.
- Stabilize standard library modules (`io`, `math`, `str`, `array`, `graphics`, etc.).
- Robust error reporting and developer tooling (formatter, linter, doc generator).
- Official VSCode extension and language server.
- Design and implement opt-in garbage collection and pointer flavors.

---

## 17.3 Near-term Goals

- Cross-platform standard library support (Windows, Linux, Mac).
- Async/await and concurrency primitives.
- Rich collections (`vec`, `map`, `set`, `queue`, etc.).
- Raylib-inspired graphics/audio APIs for game and creative coding.
- Reflection, macros, and attribute trinket expansion.
- Ecosystem: docs site, package index, forums, and real-world tutorials.

---

## 17.4 Mid- to Long-term Vision

- Compile-to-native code (self-hosted, with JIT/AOT options).
- Advanced debugging: breakpoints, watches, step-by-step tracing, profiler.
- Hot reload and scripting for games and live tools.
- WebAssembly and embedded support.
- Seamless FFI (calling C/C++/Rust/Python from Vulpes).
- Internationalization and accessibility features.
- Community-driven governance and transparent RFC process.

---

## 17.5 How to Get Involved

- Try out the language and send feedback.
- File bug reports and feature requests.
- Contribute code, tests, docs, and examples.
- Join the Discord, forum, or GitHub Discussions to share ideas.
- Help shape the language—Vulpes is *by* and *for* its users.

---

## 17.6 Project Links

- [GitHub](https://github.com/vulpes-lang/vulpes) (planned)
- [Official website](https://vulpes-lang.org) (planned)
- [Community chat & forums](https://forum.vulpes-lang.org) (planned)
- [Docs](https://vulpes-lang.org/docs) (planned)

---

## 17.7 The Future

# The Vulpes Project Ecosystem

Vulpes is more than a language—it’s an integrated, “batteries-included” platform.  
Here’s how all the official tools, helpers, and next-gen features work together to create a seamless developer experience.

---

## Core Components

| Name     | Description                              | Command / Prefix          |
|----------|------------------------------------------|--------------------------|
| **Vulpes** | The core programming language             | N/A                      |
| **Foxhole** | Build system & project/package manager   | `foxhole build`, `foxhole run` |
| **Ninetail** | Version control system for Vulpes       | `nt init`, `nt commit`   |
| **MrFox**  | AI assistant for compile errors and suggestions | Integrated with Foxhole |
| **Clever** | Linter for catching bugs & suggesting fixes | `foxhole lint`         |
| **Kitsune** | Language server for IDE integration       | Provides LSP support     |
| **Burrow** | Code formatter for consistent style        | `foxhole fmt`           |
| **Tricky** | Documentation generator from code comments | `foxhole doc`           |
| **Fennec** | REPL for interactive Vulpes coding         | `foxhole repl`          |
| **NineOS** | Operating system written in Vulpes         | Built with Foxhole       |

---

## What Each Tool Does

### **Vulpes**
- The language itself: safe, expressive, and fast for every domain.

### **Foxhole**
- Build your project, run code, manage dependencies, and publish packages.
- Handles project scaffolding, compilation, and builds (including `NineOS`!).

### **Ninetail**
- Git-like VCS, but with Vulpes-first features.
- Track history, branch, and merge with full integration into Foxhole and language-level semantics.
- CLI: `nt init`, `nt status`, `nt commit`, etc.

### **MrFox**
- Your AI-powered error explainer and code mentor.
- Integrated with Foxhole: on any compile or lint error, MrFox offers suggestions, fixes, and learning resources.

### **Clever**
- Static linter: detects common bugs, unused code, stylistic issues, and recommends idiomatic fixes.
- Run as `foxhole lint` or in your IDE.

### **Kitsune**
- Language Server Protocol implementation.
- Enables autocompletion, go-to-definition, type info, symbol search, and more in your favorite editors.

### **Burrow**
- Consistent code style with zero hassle.
- `foxhole fmt` auto-formats your code on save, commit, or demand.

### **Tricky**
- Generates docs from code comments and trinkets.
- Output: beautiful HTML, Markdown, or IDE tooltips. Used via `foxhole doc`.

### **Fennec**
- A REPL for Vulpes: experiment, learn, and debug interactively.
- `foxhole repl` launches an interactive shell with instant feedback.

### **NineOS**
- Ambitious long-term project: a whole OS written in Vulpes.
- Showcases Vulpes’ power “from userland to kernel,” built using the same Foxhole workflow.

---

## How It All Fits Together

- **Write code** in Vulpes, get live IDE feedback from Kitsune, auto-format with Burrow, and auto-lint with Clever.
- **Build and run** with Foxhole. If you hit errors, MrFox helps explain and fix them.
- **Document** your work with Tricky. Share and publish packages via Foxhole and (future) Foxden.
- **Track changes** with Ninetail—native VCS with semantic awareness.
- **Explore and experiment** live with Fennec.
- **Deploy anywhere:** from cross-platform binaries to the eventual NineOS.

---

## Why This Matters

> The Vulpes ecosystem is built to make you productive, safe, and happy—whether you’re building a quick script, a massive system, or the next great OS.  
> Each tool is tightly integrated for a smooth, “no boilerplate” workflow, with world-class error messages, docs, and learning support.

---

> **Summary:**  
> Vulpes is moving fast, with big plans—join us in making a language that’s truly “Nine Tails Ahead.”
