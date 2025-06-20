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

We actively avoid declaring functions and variables in Blueprints, as this creates significant migration challenges when porting logic to C++ later. 
Instead, we enforce strict data locality - all elements must be implemented in their architecturally correct C++ location from the outset. Maintaining hard references to such objects provides extreme performance benefits.

### Reference Management Solution

**"Blueprint reference organization issues are mitigated by implementing lightweight C++ interface wrappers marked with 'C' suffix. These provide safe access patterns while maintaining performance."**

---

### File Naming Convention (Metadata-First Approach)

We prioritize information density over redundant type indicators. Metadata is appended to avoid prefix clutter while preserving header readability.

|Type|Blueprint Format|C++ Format|Notes|
|---|---|---|---|
|**Actor Component**|`SomeClass_AC`|`SomeClass_ACC`|`AC` = Unsafe BP reference  <br>`ACC` = Lightweight C++ implementation|
|**Scene Component**|`SomeClass_SC`|`SomeClass_SCC`|`SC` = Standard BP component  <br>`SCC` = Optimized C++ variant|
|**Actor**|`SomeClass_A`|`SomeClass_CA`|Base actor types  <br>`_Actor` suffix reserved for complex BP actors|

### **Additional Benefits of Our Naming Convention System**

#### **1. Clear Separation of Business Logic from Engine Code**

- **Visual distinction** between game-specific systems (`_AC`, `_SC`) and engine-level components (`_ACC`, `_SCC`)
    
- **Reduced coupling** – Business logic remains in Blueprints, while performance-critical code stays in C++
    
- **Easier debugging** – Immediate identification of whether a component is BP-dependent or pure C++
    

#### **2. Error-Proof Access to Expected Functionality**

- **No guesswork** – Developers instantly know if a class is safe for hard references (`_ACC`, `_SCC`) or requires soft refs (`_AC`, `_SC`)
    
- **Compile-time safety** – Attempting to use an unsafe Blueprint reference (`_AC`) in a hard-referenced context triggers warnings
    
- **Consistent behavior** – All `_C`-suffixed classes guarantee lightweight C++ interfaces
    

#### **3. Enhanced Readability & Information Density**

- **No wasted prefix space** – Critical metadata is placed at the end (`SomeClass_ACC` vs. `BP_SomeClass_Component`)
    
- **Self-documenting names** – File suffixes immediately convey:
    
    - **Type** (Actor, Component, etc.)
        
    - **Implementation** (Blueprint vs. C++)
        
    - **Reference safety** (Hard vs. Soft)
        
- **Faster asset discovery** – Search filters like `*_ACC` quickly isolate optimized C++ components
    

---

### **Practical Example: Inventory System**

|**Class Type**|**File Name**|**Reference Safety**|**Use Case**|
|---|---|---|---|
|Blueprint Component|`Inventory_AC`|❌ Soft Ref Only|UI-Driven Logic (Events, FX)|
|C++ Wrapper|`Inventory_ACC`|✅ Hard Ref Safe|Data Processing, Network Sync|
|Base Actor (BP)|`Player_A`|❌ Soft Ref|Game-Specific Behavior|
|Core Actor (C++)|`Player_CA`|✅ Hard Ref|Movement, Physics, Core Systems|

---

### **Why This Matters**

✅ **Prevents performance pitfalls** by making unsafe references visually obvious  
✅ **Speeds up refactoring** with clear migration paths (`_AC` → `_ACC`)  
✅ **Reduces documentation overhead** – Naming conventions encode critical usage rules

Would you like a **Cheat Sheet PDF** for the team or an **Editor Script** to auto-validate these rules?
   ![[Pasted image 20250620135553.png]]![[Pasted image 20250620140029.png]]![[Pasted image 20250620140116.png]]
4. 