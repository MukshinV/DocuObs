**In terms of performance overhead, Blueprints are approaching Python-level slowness. By mid-development, they typically consume 30-50% of frame time instead of the acceptable 10-15%. We need a lightweight code analysis tool that identifies inefficient code segments and their locations during development. To achieve this, we're implementing separate notation conventions for C++ and Blueprints.**

### **Naming Rules for Variables and Functions Exposed in Unreal Editor**

When naming variables and functions visible in the Unreal Editor, the following conventions must be followed:

- **`@`** – Global/public variable
    Example: **`@InitialPosition`**
- **`#`** – Input parameter of a function
    Example: **`#NewPosition`**
- **`&`** – Local variable (visible only inside a function)
    Example: **`&LocalPosition`**
- **`()`** – Empty parentheses, used to distinguish functions from events
    Example: **`UpdatePosition()`**
- **`!`** – Project-specific functionality, isolated from shared code
    Example: **`!Foo()`**, **`!OnBeginCallback`**
- **`?`** – Library/utility functionality
    Example: **`?RegisterCriticalError`**
- **`(Virtual)`** – Polymorphic function marked as extensible
    Example: **`!ProcessNewData(Virtual)`**
- **`(Const)`** – Indicates a constant (read-only) variable
    Example: **`@InitialPosition(Const)`**
- **`(Internal)`**
    - Example: **`!ProcessNewData(Internal)`**
- **`(Deprecated)`**
    - Example: **`!ProcessNewData(Deprecated)`**

