Inside Unreal Editor:
- **`@`** – Global/public variable  
    Example: `@InitialPosition`
- **`#`** – Input parameter of a function  
    Example: `#NewPosition`
- **`&`** – Local variable (visible only inside a function)  
    Example: `&LocalPosition`
- **`()`** – Empty parentheses, used to distinguish functions from events  
    Example: `UpdatePosition()`
- **`!`** – Project-specific functionality, isolated from shared code  
    Example: `!Foo()`, `!OnBeginCallback`
- **`?`** – Library/utility functionality  
    Example: `?RegisterCriticalError`
- **`(Virtual)`** – Polymorphic function marked as extensible  
    Example: `!ProcessNewData(Virtual)`
- **`(Const)`** – Indicates a constant (read-only) variable  
    Example: `@InitialPosition(Const)`