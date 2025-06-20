# 14. Tooling & IDE Support

Great tooling is core to Vulpes’ mission—fast feedback, powerful builds, rich documentation, and a friendly environment for beginners and pros.

---

## 14.1 Build System: Foxhole

- **Foxhole** is Vulpes’ integrated build and package manager (like Cargo for Rust).
- Standard commands:
    - `foxhole build`: Compile your project
    - `foxhole run`: Build and run the main executable
    - `foxhole test`: Run tests
    - `foxhole check`: Static analysis/lint
    - `foxhole doc`: Generate documentation

- Project configuration lives in `.kit` files (TOML or custom syntax).
- Dependency management, versioning, and reproducible builds are first-class.

---

## 14.2 Language Server & Editor Extensions

- Vulpes has a language server (LSP) for IDE/editor integration:
    - **Features:** Autocomplete, jump-to-definition, error checking, type hints, symbol search, go-to references.
- **Official VSCode extension**: Syntax highlighting, file icons (`.vlp`, `.kit`, `.fox`, `.hole`), snippets, hover docs, and “run” support.
- Planned: Plugins for JetBrains IDEs, Neovim, Emacs.

---

## 14.3 Formatter & Linter

- Built-in code formatter (`foxhole fmt`) ensures consistent, idiomatic style.
- Linter highlights common mistakes, anti-patterns, and style issues.
- Both can be run on save in supported editors.

---

## 14.4 Documentation Generator

- Auto-generates HTML (and optionally Markdown) docs from comments and signatures.
- Supports doc comments (`///` or `/** ... */`), trinkets, and module-level summaries.
- Docs can be browsed in IDEs or served as static sites.

---

## 14.5 Testing & Coverage Tools

- Built-in test runner—mark tests with `#[test]` trinket.
- Coverage analysis and profiling tools planned for performance-conscious projects.

---

## 14.6 Debugging & Error Reporting

- Rich, colored error messages with suggestions (“Did you mean...?”)
- Stack traces and variable inspection on panic/assert failure.
- Planned: Step debugger, breakpoints, watch expressions (integrated with IDEs).

---

## 14.7 File Types & Icons

| Extension | Purpose                                    |
|-----------|--------------------------------------------|
| `.vlp`    | Vulpes source code                         |
| `.kit`    | Build configuration/project metadata       |
| `.fox`    | Compiled Vulpes executables/binaries       |
| `.hole`   | Structured config/data files (like JSON)   |

---

## 14.8 Extensibility & Ecosystem

- Package registry (planned): Search, publish, and install third-party libraries/modules.
- Plugins/hooks for custom build steps or IDE commands.
- Scaffolders and code generators for quick project start.

---

## 14.9 Example Workflow

```bash
foxhole new myproject
cd myproject
foxhole build
foxhole run
foxhole test
foxhole fmt
foxhole doc
```

- Open in VSCode for rich editing, debugging, and docs.

---

<!--
TODO:
- Finalize LSP/extension feature list
- Document Foxhole’s extensibility and hooks
- Integrate with cloud CI/CD (GitHub Actions, etc.)
-->

---

> **Summary:**  
> Vulpes is as much about great tools as it is about the language—foxhole, IDE plugins, and friendly docs mean less time fighting your setup and more time building cool stuff.
