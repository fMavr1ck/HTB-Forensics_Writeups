### **What is `LD_PRELOAD` Hijacking?**

`LD_PRELOAD` hijacking is a **Linux/Unix technique** where attackers (or developers) **force a program to load a malicious shared library** before any other libraries, allowing them to **override functions** (e.g., `printf()`, `strcpy()`) and manipulate program behavior.

---

## **How It Works**

1. **`LD_PRELOAD` Environment Variable**
    
    - Normally used for debugging or customizing library behavior.
        
    - Tells the dynamic linker (`ld.so`) to **load a specified shared library (.so file) first**.
        
2. **Hijacking Legitimate Functions**
    
    - A malicious `.so` file can **replace standard functions** (e.g., `open()`, `system()`, `getenv()`) with malicious code.
        
    - Example: Overriding `strcmp()` to bypass password checks.
        
3. **Execution Flow Manipulation**
    
    - When the target program runs, it **unknowingly uses the malicious code** instead of the real library functions.