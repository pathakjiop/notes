##  1. Introduction

### 🔹 **Definition:**

- A **linked list** is a linear collection of **nodes**, where each node has:
    
    - **INFO**: stores data
        
    - **LINK (PTR)**: stores address of the next node
        

### 🔹 **Types of Linked Lists:**

1. **Singly Linked List**
    
2. **Doubly (Two-way) Linked List**
    
3. **Circular Linked List**
    
4. **Header Linked List**
    

---

##  2. Basic Concepts

|Term|Meaning|
|---|---|
|`START`|Pointer to the first node|
|`NULL`|Indicates the end of the list|
|`AVAIL`|Pointer to available/free node|

---

##  3. Linked List Operations & Algorithms

---

### 🔹 **Traversal**

```pseudocode
TRAVERSE(INFO, LINK, PTR)
1. PTR := START
2. While PTR ≠ NULL:
    - Process INFO[PTR]
    - PTR := LINK[PTR]
3. Exit
```

---

### 🔹 **Count Nodes**

```pseudocode
COUNT(INFO, LINK, START, NUM)
1. NUM := 0
2. PTR := START
3. While PTR ≠ NULL:
    - NUM := NUM + 1
    - PTR := LINK[PTR]
4. Return
```

---

### 🔹 **Search in Unsorted List**

```pseudocode
SEARCH(INFO, LINK, START, ITEM, LOC)
1. PTR := START
2. While PTR ≠ NULL:
   If ITEM = INFO[PTR]:
      LOC := PTR, Exit
   PTR := LINK[PTR]
3. LOC := NULL (not found)
```

---

### 🔹 **Search in Sorted List**

```pseudocode
SEARCH(INFO, LINK, START, ITEM, LOC)
1. PTR := START
2. While PTR ≠ NULL:
   If ITEM < INFO[PTR] → Exit
   If ITEM = INFO[PTR] → LOC := PTR, Exit
3. LOC := NULL
```

---

### 🔹 **Add Value to Each Node**

```pseudocode
1. PTR := START
2. While PTR ≠ NULL:
   INFO[PTR] := INFO[PTR] + K
   PTR := LINK[PTR]
```

---

### 🔹 **Count Occurrences of ITEM**

```pseudocode
1. NUM := 0, PTR := START
2. While PTR ≠ NULL:
   If INFO[PTR] = ITEM → NUM := NUM + 1
   PTR := LINK[PTR]
```

---

##  4. Insertion Algorithms

---

### 🔹 Insert at Beginning

```pseudocode
INSERT_FIRST(INFO, LINK, ITEM, AVAIL, START)
1. If AVAIL = NULL → Overflow, Exit
2. NEW := AVAIL, AVAIL := LINK[AVAIL]
3. INFO[NEW] := ITEM
4. LINK[NEW] := START
5. START := NEW
```

---

### 🔹 Insert After a Node (LOC)

```pseudocode
INSERT_LOC(INFO, LINK, ITEM, START, LOC, AVAIL)
1. If AVAIL = NULL → Overflow
2. NEW := AVAIL, AVAIL := LINK[AVAIL]
3. INFO[NEW] := ITEM
4. If LOC = NULL → LINK[NEW]:=START, START:=NEW
   Else → LINK[NEW]:=LINK[LOC], LINK[LOC]:=NEW
```

---

### 🔹 Insert into Sorted List

```pseudocode
FINDA(INFO, START, LINK, ITEM, LOC)
1. If START = NULL or ITEM ≤ INFO[START] → LOC := NULL
2. SAVE := START, PTR := LINK[START]
3. While PTR ≠ NULL:
   If ITEM < INFO[PTR] → LOC := SAVE
   SAVE := PTR, PTR := LINK[PTR]

INSERT(INFO, LINK, START, ITEM, AVAIL)
1. CALL FINDA()
2. CALL INSERT_LOC()
```

---

##  5. Deletion Algorithms

---

### 🔹 Delete First Node

```pseudocode
DEL_FIRST(INFO, LINK, START, AVAIL, ITEM)
1. If START = NULL → Underflow
2. TEMP := START, START := LINK[START]
3. LINK[TEMP] := AVAIL, AVAIL := TEMP
```

---

### 🔹 Delete Specific Node by Location

```pseudocode
DEL(INFO, LINK, START, AVAIL, LOC, LOCP)
1. If LOCP = NULL → START := LINK[START]
   Else → LINK[LOCP] := LINK[LOC]
2. LINK[LOC] := AVAIL, AVAIL := LOC
```

---

### 🔹 Delete by ITEM Value

```pseudocode
FINDB(INFO, LINK, START, ITEM, LOC, LOCP)
1. If START = NULL → LOC & LOCP := NULL
2. If ITEM = INFO[START] → LOC := START, LOCP := NULL
3. SAVE := START, PTR := LINK[START]
4. While PTR ≠ NULL:
   If ITEM = INFO[PTR] → LOC := PTR, LOCP := SAVE
   Else → SAVE := PTR, PTR := LINK[PTR]

DELETECALL:
1. CALL FINDB()
2. If LOC = NULL → "ITEM NOT FOUND"
3. Delete using DEL()
```

---

### 🔹 Delete Last Node

```pseudocode
DELLIST(INFO, LINK, START, AVAIL)
1. If START = NULL → Underflow
2. If LINK[START] = NULL → AVAIL := START, START := NULL
3. PTR := LINK[START], SAVE := START
4. While LINK[PTR] ≠ NULL → SAVE := PTR, PTR := LINK[PTR]
5. LINK[SAVE] := NULL
6. LINK[PTR] := AVAIL, AVAIL := PTR
```

---

##  6. Header Linked Lists

### 🔹 Types:

1. **Grounded Header**: Ends with NULL
    
2. **Circular Header**: Last node points back to header
    

### 🔹 Advantage of Circular Header:

- No `NULL` → all pointers are valid
    
- Easier algorithm design
    
- Uniform traversal (every node has a predecessor)
    

---

##  7. Doubly Linked List (DLL)

### 🔹 Structure:

```c
struct node {
  int data;
  struct node *next;
  struct node *prev;
}
```

### 🔹 Advantages:

- Traversal in both directions
    
- Efficient insertion/deletion (if location given)
    
- Easy undo/redo functionality
    

### 🔹 Disadvantages:

- Extra memory for `prev` pointer
    
- More complex logic
    
- Slower access than arrays
    

---

### 🔹 DLL Insert Operation

```pseudocode
INST_DL(INFO, FORW, BACK, START, AVAIL, LOCA, LOCB, ITEM)
1. If AVAIL = NULL → Overflow
2. NEW := AVAIL, AVAIL := FORW[AVAIL]
3. INFO[NEW] := ITEM
4. If LOCA = NULL → START := NEW
5. BACK[NEW] := LOCA, FORW[NEW] := LOCB
6. FORW[LOCA] := NEW, BACK[LOCB] := NEW
```

---

### 🔹 DLL Delete Operation

```pseudocode
DEL_DL(INFO, FORW, BACK, AVAIL, LOC, START)
1. If START = NULL → Underflow
2. If BACK[LOC] = NULL → START := FORW[LOC]
3. FORW[BACK[LOC]] := FORW[LOC]
   BACK[FORW[LOC]] := BACK[LOC]
4. FORW[LOC] := AVAIL, AVAIL := LOC
```

---

##  8. Circular Linked Lists

### 🔹 Features:

- Last node points back to the first
    
- Can traverse from any node
    
- Implemented in singly or doubly linked form
    

---

### 🔹 Concatenation of Two Circular Lists

```pseudocode
1. If X = NULL → Z := Y
2. If Y = NULL → Z := X
3. PTR := X, Z := X
4. While LINK[PTR] ≠ X → PTR := LINK[PTR]
5. LINK[PTR] := Y
6. PTR := LINK[Y]
7. While LINK[PTR] ≠ Y → PTR := LINK[PTR]
8. LINK[PTR] := Z
```

---

##  9. Garbage Collection

### 🔹 What is it?

- Automatic memory management
    
- Reclaims memory no longer used
    

### 🔹 Techniques:

|Method|Description|
|---|---|
|Reference Counting|Deletes when count = 0|
|Mark & Sweep|Marks reachable, deletes rest|
|Stop & Copy|Copies active to new space|
|Generational GC|Categorizes objects by age|
