# Solutions to 10 Must-Know Loop Problems in C

This document provides solutions to 20 must-know loop problems in C, ranging from basic to advanced levels. Each problem is solved using different approaches (basic, optimized, and advanced). These solutions are ideal for both learning and interviews.

---

## List of Problems

1. Print Numbers from 1 to N
2. Sum of Array Elements
3. Count Even Numbers
4. Find Maximum in Array
5. Reverse an Array
6. Find Missing Number
7. Move Zeroes
8. Rotate an Array
9. Find All Duplicates in an Array
10. Longest Continuous Increasing Subsequence


---

## **7. Move Zeroes**

### **Problem**
Move all zeroes in an array to the end while maintaining the relative order of non-zero elements.

### **Input**
- An integer array and its size.

### **Output**
- Modifies the array in place to move all zeroes to the end.

### **Example**
**Input:**
```
arr = [0, 1, 0, 3, 12]
```
**Output:**
```
[1, 3, 12, 0, 0]
```

### **Basic Implementation**
```c
#include <stdio.h>

void moveZeroes(int arr[], int size) {
    int index = 0;
    for (int i = 0; i < size; i++) {
        if (arr[i] != 0) {
            arr[index++] = arr[i];
        }
    }
    while (index < size) {
        arr[index++] = 0;
    }
}

int main() {
    int arr[] = {0, 1, 0, 3, 12};
    int size = sizeof(arr) / sizeof(arr[0]);
    moveZeroes(arr, size);
    printf("Array after moving zeroes: ");
    for (int i = 0; i < size; i++) {
        printf("%d ", arr[i]);
    }
    return 0;
}
```

---

## **8. Rotate an Array**

### **Problem**
Rotate the elements of an array `k` steps to the right.

### **Input**
- An integer array, its size, and the number of steps `k`.

### **Output**
- Modifies the array in place to rotate it by `k` steps.

### **Example**
**Input:**
```
arr = [1, 2, 3, 4, 5]
k = 2
```
**Output:**
```
[4, 5, 1, 2, 3]
```

### **Basic Implementation**
```c
#include <stdio.h>

void rotateArray(int arr[], int size, int k) {
    int temp[size];
    k = k % size;
    for (int i = 0; i < size; i++) {
        temp[(i + k) % size] = arr[i];
    }
    for (int i = 0; i < size; i++) {
        arr[i] = temp[i];
    }
}

int main() {
    int arr[] = {1, 2, 3, 4, 5};
    int size = sizeof(arr) / sizeof(arr[0]);
    int k = 2;
    rotateArray(arr, size, k);
    printf("Rotated array: ");
    for (int i = 0; i < size; i++) {
        printf("%d ", arr[i]);
    }
    return 0;
}
```

### **Advanced Version (In-place)**
```c
#include <stdio.h>

void reverse(int arr[], int start, int end) {
    while (start < end) {
        int temp = arr[start];
        arr[start] = arr[end];
        arr[end] = temp;
        start++;
        end--;
    }
}

void rotateArrayInPlace(int arr[], int size, int k) {
    k = k % size;
    reverse(arr, 0, size - 1);
    reverse(arr, 0, k - 1);
    reverse(arr, k, size - 1);
}

int main() {
    int arr[] = {1, 2, 3, 4, 5};
    int size = sizeof(arr) / sizeof(arr[0]);
    int k = 2;
    rotateArrayInPlace(arr, size, k);
    printf("Rotated array (In-place): ");
    for (int i = 0; i < size; i++) {
        printf("%d ", arr[i]);
    }
    return 0;
}
```

---

## **9. Find All Duplicates in an Array**

### **Problem**
Find all elements that appear twice in an array.

### **Input**
- An integer array where elements are between 1 and `n`, inclusive, with `n` as the size of the array.

### **Output**
- Returns a list of duplicate elements.

### **Example**
**Input:**
```
arr = [4, 3, 2, 7, 8, 2, 3, 1]
```
**Output:**
```
[2, 3]
```

### **Basic Implementation**
```c
#include <stdio.h>
#include <stdlib.h>

int* findDuplicates(int* nums, int size, int* returnSize) {
    int* result = (int*)malloc(size * sizeof(int));
    *returnSize = 0;
    for (int i = 0; i < size; i++) {
        int index = abs(nums[i]) - 1;
        if (nums[index] < 0) {
            result[(*returnSize)++] = abs(nums[i]);
        } else {
            nums[index] = -nums[index];
        }
    }
    return result;
}

int main() {
    int arr[] = {4, 3, 2, 7, 8, 2, 3, 1};
    int size = sizeof(arr) / sizeof(arr[0]);
    int returnSize;
    int* duplicates = findDuplicates(arr, size, &returnSize);
    printf("Duplicates: ");
    for (int i = 0; i < returnSize; i++) {
        printf("%d ", duplicates[i]);
    }
    free(duplicates);
    return 0;
}
```

---

## **10. Longest Continuous Increasing Subsequence**

### **Problem**
Find the length of the longest continuous increasing subsequence in an array.

### **Input**
- An integer array and its size.

### **Output**
- Returns the length of the longest continuous increasing subsequence.

### **Example**
**Input:**
```
arr = [1, 3, 5, 4, 7]
```
**Output:**
```
3
```

### **Basic Implementation**
```c
#include <stdio.h>

int findLengthOfLCIS(int* nums, int size) {
    if (size == 0) return 0;
    int maxLength = 1, currentLength = 1;
    for (int i = 1; i < size; i++) {
        if (nums[i] > nums[i - 1]) {
            currentLength++;
            if (currentLength > maxLength) {
                maxLength = currentLength;
            }
        } else {
            currentLength = 1;
        }
    }
    return maxLength;
}

int main() {
    int arr[] = {1, 3, 5, 4, 7};
    int size = sizeof(arr) / sizeof(arr[0]);
    printf("Length of LCIS: %d\n", findLengthOfLCIS(arr, size));
    return 0;
}
```

---



