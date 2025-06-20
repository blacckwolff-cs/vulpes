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
