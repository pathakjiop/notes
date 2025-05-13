##  **1. Introduction to Arrays**

### 🔹 Definition:

An **array** is a collection of **homogeneous** and **finite** elements stored in **contiguous memory locations**.

- Elements are accessed via **index (or subscript)**.
    
- **Length = UB – LB + 1**, where UB = Upper Bound, LB = Lower Bound
    

---

##  **2. Memory Representation**

### 🔹 Address Calculation:

```
Loc(A[k]) = BASE(A) + w × (k - LB)
```

- `BASE(A)` → Address of the first element
    
- `w` → No. of memory cells per element
    

### Example:

```
AAA(5:50), BASE(AAA)=300, w=4
Loc(AAA[15]) = 300 + 4 × (15 – 5) = 340
```

---

##  **3. Array Operations & Algorithms**

### 🔹 Traversal

```pseudocode
TRAVERSE (LA, LB, UB)
Step 1: Repeat Step 2 for I = LB to UB
Step 2: Process LA[I]
Step 3: Return
```

---

### 🔹 Insert (with Overflow Check)

```pseudocode
INSERT(LA, N, K, ITEM, UB)
1. If N ≥ UB → Write "Overflow", Exit
2. Set I := N
3. Repeat Steps 4–5 while I ≥ K
4. LA[I+1] := LA[I]
5. I := I - 1
6. LA[K] := ITEM
7. N := N + 1
8. Exit
```

---

### 🔹 Delete (with Underflow Check)

```pseudocode
DELETE(LA, N, K, ITEM, LB)
1. If N < LB → Write "Underflow", Exit
2. ITEM := LA[K]
3. Repeat for I = K to N-1
4. LA[I] := LA[I+1]
5. N := N - 1
6. Exit
```

---

### 🔹 Find Even & Odd Sums

```pseudocode
NUMBERS(EVEN_S, ODD_S, DATA, N)
1. EVEN_S := 0, ODD_S := 0, K := 1
2. Repeat Step 3–4 while K ≤ N
3. If DATA[K] mod 2 = 0 → EVEN_S += DATA[K]
   Else → ODD_S += DATA[K]
4. K := K + 1
5. Output EVEN_S, ODD_S
6. Exit
```

---

### 🔹 Find Largest Element Location

```pseudocode
LARGEST(LOC, MAX, DATA, N)
1. K := 2, LOC := 1, MAX := DATA[1]
2. Repeat Step 3–4 while K ≤ N
3. If MAX < DATA[K] → MAX := DATA[K], LOC := K
4. K := K + 1
5. Output LOC, MAX
6. Exit
```

---

##  **4. Sorting Algorithm: Bubble Sort**

### 🔹 Description:

- Repeatedly compares and swaps adjacent elements
    
- Time complexity: **O(n²)**
    

### 🔹 Algorithm:

```pseudocode
BUBBLE_SORT(A, n)
Repeat I from 0 to n-1
  Repeat J from 0 to n-1-I
    If A[J] > A[J+1]
      Swap A[J] and A[J+1]
Display A
```

---

##  **5. Searching Algorithms**

### 🔸 **Linear Search**

- Time Complexity: O(n)
    

```pseudocode
LINEAR_SEARCH(DATA, N, ITEM)
1. I := 1, LOC := 0
2. While I ≤ N and LOC = 0
   If DATA[I] = ITEM → LOC := I
   I := I + 1
3. Output LOC or "Not Found"
```

---

### 🔸 **Binary Search**

- Works only on **sorted arrays**
    
- Time Complexity: O(log n)
    

```pseudocode
BINARY_SEARCH(DATA, LB, UB, ITEM)
1. BEG := LB, END := UB
2. Repeat while BEG ≤ END and DATA[MID] ≠ ITEM
   MID := INT((BEG + END)/2)
   If ITEM < DATA[MID] → END := MID - 1
   Else → BEG := MID + 1
3. If DATA[MID] = ITEM → LOC := MID
   Else → LOC := NULL
4. Return LOC
```

---

##  **6. Multi-Dimensional Arrays**

### 🔹 2D Arrays (Matrices)

- Example: A[1:3,1:3]
    
- Addressing (Row Major):
    

```
LOC(A[J,K]) = BASE(A) + w × [N(J–1) + (K–1)]
```

- Addressing (Column Major):
    

```
LOC(A[J,K]) = BASE(A) + w × [M(K–1) + (J–1)]
```

---

### 🔹 General nD Array (Row Major Example)

```
LOC(B[K1,K2,...KN]) = BASE(B) + w × [E1×L2 + E2×L3 + ... + EN-1×LN + EN]
Ei = Ki – LowerBound
```

---

##  **7. Matrix Operations (for Square Matrices)**

### a. Count Non-zero Elements

```pseudocode
NUM := 0
For I = 1 to N
  For J = 1 to N
    If A[I,J] ≠ 0 → NUM += 1
```

### b. Sum Above Diagonal (I < J)

```pseudocode
SUM := 0
For J = 2 to N
  For I = 1 to J–1 → SUM += A[I,J]
```

### c. Sum Below Diagonal (I > J)

```pseudocode
SUM := 0
For I = 2 to N
  For J = 1 to I–1 → SUM += A[I,J]
```

### d. Product of Diagonal Elements

```pseudocode
PROD := 1
For K = 1 to N → PROD := PROD × A[K,K]
```

---

##  **8. Pointer Arrays**

### 🔹 Definition:

A pointer stores address of another variable.

### 🔹 Syntax:

```c
int *ptr = arr;  // Points to first element of array
```

### 🔹 Usage:

- Efficient access to array elements
    
- Useful in **dynamic and multi-dimensional** array manipulation
    

---

##  **9. Records**

- A user-defined data structure with **different data types**
    
- Similar to structs in C/C++
    
- Used in **databases**, more flexible than arrays
    

---

##  **10. Sparse Matrices**

### 🔹 Definition:

A matrix with **mostly 0 elements** is called sparse.

### 🔹 Representations:

- **Array**: Store only non-zero values with row and column info.
- **Linked List**: Each node stores row, column, value.

