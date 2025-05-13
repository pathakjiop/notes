##  1. Stack (LIFO)

### 🔹 Operations:

- **PUSH:** Insert element at the top
    
- **POP:** Remove element from the top
    

---

### 🔹 Array Representation

#### PUSH Operation (Array)

```pseudocode
PUSH(STACK, TOP, MAX, ITEM)
1. If TOP = MAX → Write “OVERFLOW”, Return
2. TOP := TOP + 1
3. STACK[TOP] := ITEM
4. Return
```

#### POP Operation (Array)

```pseudocode
POP(STACK, TOP, ITEM)
1. If TOP = NULL → Write “UNDERFLOW”, Return
2. ITEM := STACK[TOP]
3. TOP := TOP - 1
4. Return
```

---

### 🔹 Linked List Representation

#### PUSH Operation (Linked)

```pseudocode
PUSH_LINKED(INFO, LINK, TOP, AVAIL, ITEM)
1. If AVAIL = NULL → OVERFLOW
2. NEW := AVAIL, AVAIL := LINK[AVAIL]
3. INFO[NEW] := ITEM
4. LINK[NEW] := TOP
5. TOP := NEW
6. Return
```

#### POP Operation (Linked)

```pseudocode
POP_LINKED(INFO, LINK, TOP, AVAIL, ITEM)
1. If TOP = NULL → UNDERFLOW
2. TEMP := TOP, ITEM := INFO[TOP]
3. TOP := LINK[TOP]
4. LINK[TEMP] := AVAIL, AVAIL := TEMP
5. Return
```

---

##  2. Arithmetic Expression Notations

|Notation|Example|
|---|---|
|Infix|A + B|
|Prefix|+ A B|
|Postfix|A B +|

---

### 🔹 Infix → Postfix Conversion

```pseudocode
1. Push ‘(’ to stack, Append ‘)’ to infix expression
2. Scan left to right:
   - Operand → Add to postfix
   - ‘(’ → Push
   - Operator → Pop all operators of ≥ precedence
   - ‘)’ → Pop till ‘(’
3. Exit
```

---

### 🔹 Example:

Infix: `A + (B * C) → Postfix: A B C * +`

---

### 🔹 Postfix → Infix Conversion

```pseudocode
1. Append ')' to postfix
2. Scan:
   - Operand → Push to stack
   - Operator → Pop top two → Combine → Push result
3. Top of stack = Final Infix
```

Example:  
Postfix: `AB-C*` → Infix: `(A - B) * C`

---

### 🔹 Postfix Evaluation

```pseudocode
1. Append ‘)’ to postfix
2. Scan:
   - Operand → Push to stack
   - Operator → Pop 2 elements, Evaluate, Push result
3. Final result on top of stack
```

Example:  
`5 6 2 + *` → 5 × (6+2) = **40**

---

##  3. Quick Sort (Using Stack)

### 🔹 Steps:

- Pick a pivot (e.g. A[1])
    
- Partition elements:
    
    - Left of pivot < pivot
        
    - Right of pivot > pivot
        
- Recursively apply to sublists
    

### 🔹 Time Complexity:

|Case|Time|
|---|---|
|Best/Average|O(n log n)|
|Worst|O(n²)|

---

##  4. Recursion

### 🔹 Types:

- **Direct Recursion** → Function calls itself
    
- **Indirect Recursion** → A → B → A
    

### 🔹 Conditions:

1. **Base case** must exist
    
2. Recursive call must move toward base case
    

---

### 🔹 Factorial Recursion

```pseudocode
FACTORIAL(N)
1. If N = 0 → Return 1
2. Else Return N × FACTORIAL(N–1)
```

---

### 🔹 Tower of Hanoi

```pseudocode
TOWER(n, BEG, END, AUX)
1. If n = 1 → BEG → END
2. Call TOWER(n–1, BEG, AUX, END)
3. Move BEG → END
4. Call TOWER(n–1, AUX, END, BEG)
```

---

##  5. Queue (FIFO)

### 🔹 Array Representation

#### Insertion

```pseudocode
QINSERT(QUEUE, N, FRONT, REAR, ITEM)
1. If FRONT = (REAR+1) MOD N → OVERFLOW
2. If FRONT = NULL → FRONT := 0, REAR := 0
   Else REAR := (REAR+1) MOD N
3. QUEUE[REAR] := ITEM
4. Return
```

#### Deletion

```pseudocode
QDELETE(QUEUE, N, FRONT, REAR, ITEM)
1. If FRONT = NULL → UNDERFLOW
2. ITEM := QUEUE[FRONT]
3. If FRONT = REAR → FRONT := NULL, REAR := NULL
   Else FRONT := (FRONT+1) MOD N
4. Return
```

---

### 🔹 Linked List Representation

#### Insertion (Rear End)

```pseudocode
LINK_Q_INSERT(INFO, LINK, FRONT, REAR, AVAIL, ITEM)
1. If AVAIL = NULL → OVERFLOW
2. NEW := AVAIL, AVAIL := LINK[AVAIL]
3. INFO[NEW] := ITEM, LINK[NEW] := NULL
4. If FRONT = NULL → FRONT := REAR := NEW
   Else LINK[REAR] := NEW, REAR := NEW
5. Return
```

#### Deletion (Front End)

```pseudocode
LINK_Q_DELETE(INFO, LINK, FRONT, REAR, AVAIL)
1. If FRONT = NULL → UNDERFLOW
2. TEMP := FRONT, ITEM := INFO[FRONT]
3. FRONT := LINK[FRONT]
4. LINK[TEMP] := AVAIL, AVAIL := TEMP
5. Return
```

---

##  6. Types of Queues

| Type                  | Features                                |
| --------------------- | --------------------------------------- |
| **Circular Queue**    | Rear = (Rear + 1) % MAX                 |
| **Deque**             | Insertion & Deletion at both ends       |
| **Input-Restricted**  | Insertion at one end, deletion at both  |
| **Output-Restricted** | Insertion at both ends, deletion at one |
| **Priority Queue**    | Higher priority items processed first   |

---

### 🔹 Priority Queue (Linked Representation)

- Each node has `INFO`, `PRIORITY`, and `LINK`
    
- Order by priority, then FIFO if equal priority
    

---

##  7. Applications of Stack & Queue

### 🔹 Stack:

- Expression conversion (infix ↔ postfix)
    
- Recursive calls
    
- Undo features
    
- Backtracking
    

### 🔹 Queue:

- Resource scheduling (CPU, printer)
    
- Job handling in OS
    
- Simulations
    
	