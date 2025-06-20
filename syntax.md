# 2.1 Reserved Keywords in Vulpes

| Keyword   | Purpose / Notes                  | Use Now | Reserve (Future) | Never |
|-----------|----------------------------------|:-------:|:----------------:|:-----:|
| var       | Variable declaration             |   ✔     |                  |       |
| fx        | Function definition              |   ✔     |                  |       |
| enum      | Enumeration                      |   ✔     |                  |       |
| kit       | User-defined struct (Kits)       |   ✔     |                  |       |
| solid     | Const/immutable modifier         |   ✔     |                  |       |
| ptr       | Pointer modifier                 |   ✔     |                  |       |
| array     | Array modifier/type              |   ✔     |                  |       |
| option    | Optional type                    |   ✔     |                  |       |
| result    | Result/error type                |   ✔     |                  |       |
| unit      | Unit/void type                   |   ✔     |                  |       |
| true      | Boolean literal                  |   ✔     |                  |       |
| false     | Boolean literal                  |   ✔     |                  |       |
| None      | Empty/absent value (Option)      |   ✔     |                  |       |
| self      | Receiver in methods (if used)    |   ✔     |                  |       |
| super     | Parent kit/namespace (if needed) |         |        ✔         |       |
| if        | If statement                     |   ✔     |                  |       |
| else      | Else branch                      |   ✔     |                  |       |
| elif      | Else if (optional, for clarity)  |   ✔     |                  |       |
| match     | Pattern matching/switch          |   ✔     |                  |       |
| while     | While loop                       |   ✔     |                  |       |
| for       | For loop                         |   ✔     |                  |       |
| break     | Loop/control break               |   ✔     |                  |       |
| continue  | Continue next loop iteration     |   ✔     |                  |       |
| return    | Return from function             |   ✔     |                  |       |
| import    | Import modules/files             |   ✔     |                  |       |
| export    | Export modules/files             |   ✔     |                  |       |
| as        | Import aliasing                  |   ✔     |                  |       |
| pub       | Public visibility                |   ✔     |                  |       |
| priv      | Private visibility               |   ✔     |                  |       |
| internal  | Internal visibility (if needed)  |         |        ✔         |       |
| try       | Error handling (try block)       |   ✔     |                  |       |
| catch     | Error handling (catch block)     |   ✔     |                  |       |
| throw     | Error throwing                   |   ✔     |                  |       |
| panic     | Abort, unrecoverable error       |   ✔     |                  |       |
| async     | Async/await (concurrency)        |         |        ✔         |       |
| await     | Awaitable (concurrency)          |         |        ✔         |       |
| spawn     | Thread/task spawning             |         |        ✔         |       |
| inline    | Inline attribute/trinket         |   ✔     |                  |       |
| static    | Static/global modifier           |         |        ✔         |       |
| defer     | Cleanup/finalization             |         |        ✔         |       |
| yield     | Coroutines/generators            |         |        ✔         |       |
| macro     | Macro definition                 |         |        ✔         |       |
| trait     | Traits/Interfaces                |         |        ✔         |       |
| interface | Interface/contract               |         |        ✔         |       |
| override  | OOP/Inheritance                  |         |        ✔         |       |
| virtual   | OOP/Inheritance                  |         |        ✔         |       |
| type      | Type alias/definition            |         |        ✔         |       |
| operator  | Operator overloading             |         |        ✔         |       |
| dyn       | Dynamic typing                   |         |        ✔         |       |

## 2.2 Identifiers

Identifiers are names for variables, kits, enums, functions, modules, and other user-defined entities in Vulpes.

### Rules for Identifiers

- **Start:** Must begin with a letter (`a-z`, `A-Z`) or underscore (`_`)
- **Continue:** May contain letters, digits (`0-9`), or underscores
- **Case-sensitive:** `myVar`, `MyVar`, and `myvar` are all distinct
- **No reserved keywords:** Identifiers cannot use any [reserved keywords](#21-reserved-keywords-in-vulpes)
- **No special symbols:** `$`, `@`, `-`, etc. are *not* allowed

### Naming Conventions

| Use               | Convention    | Example          |
|-------------------|--------------|------------------|
| Variables         | `camelCase`  | `countDown`      |
| Functions         | `camelCase`  | `computeSum`     |
| Kits (Structs)    | `PascalCase` | `NetworkPacket`  |
| Enums             | `PascalCase` | `FileType`       |
| Constants         | `ALL_CAPS`   | `MAX_SIZE`       |

> **Tip:**  
> Following these conventions isn’t required by the compiler, but is highly recommended for clarity and “idiomatic” Vulpes code.

### Examples

Valid:
```vlp
counter
answer42
_fooBar
FileReader
parseFile
MAX_LENGTH
