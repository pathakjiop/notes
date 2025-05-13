  ###  **Data**
- Data are values or sets of values used for processing.

###  **Data Structure**
- Organized way to store and access data efficiently.

###  **Abstract Data Type (ADT)**
- A mathematical model:  
    **ADT = (D, F, A)**
    
    - **D** – Data objects
        
    - **F** – Set of functions
        
    - **A** – Set of rules (axioms)
        

---

##  2. Types of Data Structures

### 🔹 **Linear Data Structures**

Elements arranged sequentially

- **Array**
    
- **Linked List**
    
- **Stack** (LIFO)
    
- **Queue** (FIFO)
    

### 🔹 **Non-Linear Data Structures**

Elements do not follow a sequence

- **Tree**
    
- **Graph**
    

---

##  3. Data Structure Operations

|Operation|Description|
|---|---|
|Traversing|Visit all elements|
|Searching|Find location of a specific item|
|Insertion|Add a new item|
|Deletion|Remove an existing item|
|Sorting|Arrange items (ascending/descending)|
|Merging|Combine two sorted data structures|

---

##  4. Mathematical Functions & Notations

### 🔹 Floor & Ceiling

- `⌊x⌋` = Greatest integer ≤ x
    
- `⌈x⌉` = Least integer ≥ x
    

### 🔹 Modular Arithmetic

- `k mod m` = Remainder when k is divided by m
    

### 🔹 Summation

- `Σ ai` from i = 1 to n
    
- Example: Σ i from 1 to 3 = 1 + 2 + 3 = 6
    

### 🔹 Factorial

- `n! = 1 × 2 × ... × n`, with `0! = 1`
    

### 🔹 Absolute & Integer Value

- `|x|` = Absolute value of x
    
- `INT(x)` = Integer part of x
    

---

##  5. Algorithm and Sub-algorithms

###  **Algorithm Characteristics**

1. Input : Zero or more Quantities are externally supplied
2. Output : At least one quantity is produced
3. Definiteness : Each instruction is clear and unambiguous
4. Finiteness : If we trace out the instructions of an algorithm then for all cases the algorithm terminates after a finite number of steps.
5. Effectiveness : Every instruction must be very basic so that it can be carried out in principle by a person using pencil and paper.

###  **Notation**

- `Steps`
- `:=` for assignment
	  e.g. MAX:=6
- `Read`, `Write` for I/O
	- Read : variable names
	- Write : message
- `Go to step n`, `Exit`, `[Comments]`
- `Variable Names` 
	  e.g MAX ,DATA

###  **Approaches**

- **Top-down:** Break into subtasks
    
- **Bottom-up:** Solve parts then combine
    

###  **Sub-algorithms**

- **Function:** Returns a value
    
- **Procedure:** Performs steps and returns
    

---

##  6. Time & Space Complexity

### 🔹 Space Complexity

- Finding amount of memory space the program is going to consume. 
- It is calculated in terms of variables used in program

### 🔹 Time Complexity

- Time taken by code (frequency of steps)

### Cases:

- **Best Case TC**
- **Average Case TC**
- **Worst Case TC**

### 🔹 Notations

| Notation    | Meaning                    |
| ----------- | -------------------------- |
| **O(g(n))** | Upper bound (Worst case)   |
| **Ω(g(n))** | Lower bound (Best case)    |
| **Θ(g(n))** | Tight bound (Average case) |

---

##  7. String Processing

###  **What is a String?**

- Sequence of characters (A-Z, 0-9, symbols)
    

###  **Storage Methods**

1. **Fixed-length:** E.g., 80 chars
    
2. **Variable-length with fixed max**
    
    - **Sentinels: $ $** 
        
    - **Length listed:** Store length separately
        
    - **Concatenated with separators**
        
3. **Linked list storage**
    

---

##  8. String Operations
| Operation     | Syntax                              | Example                                    |
| ------------- | ----------------------------------- | ------------------------------------------ |
| **Substring** | SUBSTRING(String, Position, Length) | `SUBSTRING("THE END", 4, 4)` → "⎕END"      |
| **Index**     | INDEX(Text, Pattern)                | `INDEX("HIS FATHER", "THE")` → 7           |
| **Concat**    | S1 // S2                            | `'MARK' // 'ALLEN'` → `'MARKALLEN'`        |
| **Length**    | LENGTH(String)                      | `LENGTH("COMPUTER")` → 8                   |
| **Insert**    | INSERT(Text, Position, String)      | `INSERT("ABC", 2, "XYZ")` → "AXYZBC"       |
| **Delete**    | DELETE(Text, Position, Length)      | `DELETE("ABCDEFG", 3, 3)` → "ABFG"         |
| **Replace**   | REPLACE(Text, Old, New)             | `REPLACE("XABYABZ", "AB", "C")` → "XCYABZ" |

---

##  9. Pattern Matching Algorithms

### 🔹 **Naïve (Slow) Algorithm**

- Compare pattern P with each substring of text T
    
- **Time Complexity:** O((n−m+1) × m)
    

### 🔹 **Modified Naïve**

- If all characters in P are unique, slide by `j` (number of matches)
    

### 🔹 **KMP (Knuth-Morris-Pratt) Algorithm**

- Uses a **prefix function (π)** to skip unnecessary comparisons
    
- Efficient: avoids backtracking
    
- **Time Complexity:** O(n + m)
    

---

## ✍️ Example: Count 'A' in a String (Pseudocode)

```
COUNT(STRING, A, NUM)
Step 1: Set NUM := 0, L := LENGTH(STRING)
Step 2: Repeat for I := 1 to L
           If STRING[I] = A
               NUM := NUM + 1
Step 3: Exit
```

