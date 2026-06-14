# The Stack vs. The Heap

In languages like Python or Java, you don't really worry about where variables "live." In C, understanding the difference between **Stack** memory and **Heap** memory is the difference between a stable program and a crash.

Think of your computer's RAM as a warehouse with two different storage sections.

## 1. The Stack (Automatic Storage)

The Stack is like a **Post-it note** on your desk. It's incredibly fast to use, but it’s small and temporary.

-   **Management:** Automatic. When a function starts, its variables are "pushed" onto the stack. When the function ends, they are "popped" off and vanish forever.
-   **Size:** Small (usually a few megabytes).
-   **Usage:** Local variables and function calls.

**Example:**
```c
void my_func() {
    int x = 10; // This lives on the Stack.
} // x is automatically deleted here.
```

---

## 2. The Heap (Dynamic Storage)

The Heap is like a **Storage Unit** across town. You have to call the manager to rent a space, and you have to call them again to give it back.

-   **Management:** Manual. You (the programmer) must request space using `malloc()` and return it using `free()`.
-   **Size:** Large (can use almost all available RAM).
-   **Usage:** Large arrays, data that needs to stay alive after a function ends.

**Example:**
```c
int *ptr = malloc(sizeof(int)); // Request space on the Heap
*ptr = 42;
// ... use ptr ...
free(ptr); // You MUST return the space manually!
```

---

## The Danger: Memory Leaks

If you keep calling `malloc()` but never call `free()`, your program will slowly consume more and more RAM until the computer runs out. This is called a **Memory Leak**.

On the other hand, if you try to use memory on the Stack after its function has ended, your program will crash because that memory has already been "popped" and assigned to someone else.

## Summary Comparison

| Feature | The Stack | The Heap |
| :--- | :--- | :--- |
| **Speed** | Very Fast. | Slower. |
| **Management** | Automatic (OS). | Manual (You!). |
| **Lifetime** | Temporary (Function scope). | Long-term (Until freed). |
| **Fragmentation** | No. | Yes. |
| **Size Limit** | Fixed/Small. | Flexible/Large. |

## Practice Problems

??? question "Practice Problem 1: Lifetime Test"

    You want to load a high-resolution image file (50MB) and keep it in memory while the user navigates between different menus in your app. Where should you store the image data?

    ??? tip "Solution"
        **The Heap.**
        
        The image is too large for the small Stack (which might only be 2MB or 8MB total). Additionally, you need the data to stay alive across multiple function calls, so automatic stack cleanup would delete it too early.

??? question "Practice Problem 2: Automatic vs Manual"

    If you declare `int counts[100];` inside a function, is that Stack or Heap?

    ??? tip "Solution"
        **The Stack.**
        
        Unless you see the keyword `malloc`, memory allocation in C is automatic and happens on the Stack.

## Key Takeaways

-   Use the **Stack** for simple, local variables that are small and temporary.
-   Use the **Heap** for large data structures or data that needs a long life.
-   **Never forget to `free()`** what you `malloc()`!

---

Managing memory is the greatest responsibility of a C programmer. By mastering the Stack and the Heap, you move from being a user of tools to a builder of tools, gaining the power to write high-performance software that uses every byte of hardware efficiently.
