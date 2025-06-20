# Foxden: The Vulpes Package Registry & Ecosystem

Foxden is the official package registry and community hub for Vulpes modules, libraries, tools, and apps.  
It powers sharing, discovering, and reusing code—keeping the Vulpes ecosystem “nine tails ahead.”

---

## 1. Philosophy & Goals

- **Accessible:** Anyone can publish, discover, and use packages easily.
- **Secure:** Verified authorship, version checks, and audit logs protect users.
- **Composable:** Packages work together cleanly with minimal conflicts.
- **Community-driven:** Contributions and ratings help surface quality code.

---

## 2. Workflow Overview

1. **Author** writes and tests a Vulpes module/library.
2. **Publish** to Foxden with a single command.
3. **Other users** discover and add the package to their `.kit` file.
4. **Foxhole** handles downloading, building, and version resolution.
5. **Updates** are checked and managed automatically or manually.

---

## 3. Publishing Packages

- **Command:**
    ```bash
    foxhole publish
    ```
- Prompts for login if not already authenticated.
- Reads package metadata from `.kit` (name, version, description, authors, license, keywords, etc.).
- Validates code builds and tests pass before upload.
- Assigns a unique package name in the global namespace.

---

## 4. Using Packages

- **Add dependency:**
    - Edit your `.kit` file:
        ```toml
        [dependencies]
        foxlib = "1.2.3"
        graphics = ">=0.5.0"
        ```
    - Or use the CLI:
        ```bash
        foxhole add graphics
        ```
- **Import in code:**
    ```vlp
    import graphics::window;
    ```

---

## 5. Discovering Packages

- **Web portal:**  
  [foxden.vulpes-lang.org](https://foxden.vulpes-lang.org)  
  - Browse by category, search by name/tag, read docs, check popularity/stars, and see author info.
- **CLI search:**  
    ```bash
    foxhole search audio
    ```

---

## 6. Versioning & Updates

- **Semantic Versioning:**  
  - Format: `MAJOR.MINOR.PATCH`
  - Breaking changes bump MAJOR.
  - New features bump MINOR.
  - Fixes bump PATCH.
- **Upgrade with CLI:**
    ```bash
    foxhole upgrade graphics
    foxhole upgrade --all
    ```
- **Lockfiles:**  
  Foxhole supports lockfiles to guarantee reproducible builds.

---

## 7. Security & Trust

- All packages are signed by the author’s Foxden key.
- Packages are scanned for malware and suspicious code patterns.
- Audit logs available for all downloads/updates.
- Deprecated and yanked versions clearly flagged.

---

## 8. Docs, Ratings, and Community

- Each package gets an auto-generated docs page from its comments and trinkets.
- Users can rate, comment, and report issues directly on the registry.
- “Foxes of the Week” highlight trending or high-quality packages.

---

## 9. Example: Publishing a New Package

```bash
foxhole new fast_math
cd fast_math
# ...write code, tests, docs...
foxhole test
foxhole doc
foxhole publish
```
- Fills in `.kit` file with metadata.
- All published packages must have a license.

---

## 10. Best Practices

- **Keep packages small and focused**—single responsibility.
- **Document public APIs** with comments and `#[doc]` trinkets.
- **Version early, version often.**
- **Never break existing users** without a major version bump.
- **Respond to issues and reviews.**
- **Avoid name squatting or typosquatting**—respect the ecosystem.

---

## 11. Advanced (Planned)

- **Private registries** for organizations or internal sharing.
- **Scoped packages:** `@user/foo` or `org::foo`
- **Pre/post build hooks** and custom scripts.
- **Monorepo/multi-package workspaces.**
- **Continuous integration with cloud builders and test runners.**

---

> **Summary:**  
> Foxden is how the Vulpes ecosystem grows, connects, and stays safe.  
> It’s your launchpad for reusable, discoverable, and community-tested code.

