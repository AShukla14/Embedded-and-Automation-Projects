# Types of Loops in C: Usage, Code Examples, Optimization, and Interview Questions

In C, loops are categorized into three main types: `for`, `while`, and `do-while` loops. Each type has specific use cases, advantages, and considerations, particularly in systems programming and embedded development. Here's an in-depth guide to understanding, optimizing, and mastering loops for interviews and real-world applications.

---

## **1. `for` Loop**
### **Usage**
- Best suited for situations where the number of iterations is known beforehand.
- Commonly used for iterating through arrays, generating patterns, or performing mathematical computations.

### **Syntax**
```c
for (initialization; condition; increment/decrement) {
    // Code block
}
```

### **Example**
#### Basic Example: Printing Numbers
```c
for (int i = 1; i <= 10; i++) {
    printf("%d\n", i);
}
```

#### Optimized Example: Accessing an Array
```c
int arr[] = {1, 2, 3, 4, 5};
for (int i = 0, n = sizeof(arr) / sizeof(arr[0]); i < n; i++) {
    printf("%d\n", arr[i]);
}
```

---

## **2. `while` Loop**
### **Usage**
- Ideal when the number of iterations is not fixed and depends on dynamic conditions.
- Commonly used for polling hardware registers, waiting for events, or processing user input until a termination condition is met.

### **Syntax**
```c
while (condition) {
    // Code block
}
```

### **Example**
#### Basic Example: Reading Input Until Zero
```c
int num;
while (scanf("%d", &num) && num != 0) {
    printf("You entered: %d\n", num);
}
```

#### Optimized Example: Infinite Loops with Break
```c
while (1) {
    if (checkCondition()) {
        break;
    }
    performTask();
}
```

---

## **3. `do-while` Loop**
### **Usage**
- Ensures the code block executes at least once, regardless of the condition.
- Often used in menu-driven programs or situations where an initial action must precede the condition check.

### **Syntax**
```c
do {
    // Code block
} while (condition);
```

### **Example**
#### Basic Example: Menu Implementation
```c
int choice;
do {
    printf("1. Option 1\n2. Option 2\n3. Exit\n");
    scanf("%d", &choice);
} while (choice != 3);
```

#### Optimized Example: Input Validation
```c
int num;
do {
    printf("Enter a positive number: ");
    scanf("%d", &num);
} while (num <= 0);
```

---

## **4. Nested Loops**
### **Usage**
- Used for multidimensional array processing, generating patterns, or solving matrix-related problems.

### **Example**
#### Printing a Multiplication Table
```c
for (int i = 1; i <= 10; i++) {
    for (int j = 1; j <= 10; j++) {
        printf("%d x %d = %d\t", i, j, i * j);
    }
    printf("\n");
}
```

---

## **5. Loop Control Statements**
### **`break`**
- Exits the loop immediately.
- Commonly used when a specific condition is met or an error occurs.

### **`continue`**
- Skips the current iteration and proceeds to the next.
- Useful for skipping specific values in a loop.

### **Example: Skipping Even Numbers**
```c
for (int i = 1; i <= 10; i++) {
    if (i % 2 == 0) {
        continue;
    }
    printf("%d\n", i);
}
```

---

## **6. Optimization Techniques for Loops**
### **a. Minimize Loop Overhead**
- Avoid recomputing values within the loop.

#### Example
```c
// Inefficient
for (int i = 0; i < strlen(str); i++) {
    printf("%c", str[i]);
}

// Optimized
int len = strlen(str);
for (int i = 0; i < len; i++) {
    printf("%c", str[i]);
}
```

### **b. Unrolling Loops**
- Reduces loop overhead by processing multiple elements per iteration.

#### Example
```c
for (int i = 0; i < n; i += 2) {
    process(arr[i]);
    if (i + 1 < n) {
        process(arr[i + 1]);
    }
}
```

---

## **7. Interview-Level Questions**
### **a. Basic Questions**
1. Write a program to reverse an array using a loop.
2. Find the factorial of a number using a loop.
3. Print the Fibonacci series up to a given number.

### **b. Intermediate Questions**
1. Detect a cycle in an array using a loop.
2. Implement matrix multiplication using nested loops.
3. Generate all permutations of a string using loops.

### **c. Advanced Questions**
1. Optimize a loop to compute the sum of an array's subarray in `O(n)` time.
2. Implement a loop to process data from a hardware buffer without stalling the CPU.
3. Solve problems requiring efficient use of `break`, `continue`, and nested loops.

---

## **8. Summary**
### **When to Use Which Loop?**
- Use a `for` loop when the number of iterations is known.
- Use a `while` loop for dynamic conditions.
- Use a `do-while` loop when the code block must execute at least once.

### **Key Takeaways**
- Understand the trade-offs between different loop types.
- Optimize loops to reduce time and space complexity.
- Practice advanced problems to build confidence for interviews and real-world applications.

