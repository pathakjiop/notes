
# 1. File-System Interface

## File Concept

- Logical collection of related information stored on secondary storage.
    
- **File types**: numeric, character, binary, program files.
    

## File Structure

- **Simple structure**: sequence of words/bytes.
    
- **Record structure**: fixed-length or variable-length records.
    
- **Complex structure**: formatted documents, relocatable files.
    

## File Attributes

- Name, type, location, size, protection (permissions), time/date/user ID.
    

## File Operations

- Creation, writing, reading, repositioning (seek), deleting, truncating, opening, closing.
    

## Access Methods

- **Sequential Access**: Read/write one by one.
    
- **Direct Access**: Access any block directly (relative block number).
    

## Directory Structure

- Stores metadata of files: name, type, address, size, etc.
    
- **Operations**: search, create, delete, list, rename, traverse.
    

### Types of Directory Structures

- Single-Level: One directory for all files.
    
- Two-Level: Separate directory for each user.
    
- Tree-Structured: Hierarchical organization (parent-child directories).
    
- Acyclic-Graph: Shared subdirectories/files.
    
- General Graph: Can lead to cycles (requires cycle detection).
    

## File-System Mounting

- Before use, a filesystem must be mounted at a mount point.
    

## File Sharing

- Sharing of files among multiple users.
    
- In distributed systems, Network File Systems (NFS) are used.
    

## Protection

- Control over who can read/write/execute.
    
- Access lists (owner, group, public) and permission bits.
    

---

# 2. File Management

## File

- A named collection of data.
    
- Attributes: Name, identifier, type, location, size, protection, timestamps.
    

## File Operations

- Creation, reading, writing, deleting, truncating.
    

## Access Methods

- Sequential and Direct access.
    

## Directory

- Contains file information: name, location, type, size.
    

### Operations on Directory

- Search, create, delete, list, rename, traverse.
    

### Directory Structures

- **Single-Level Directory**: Simple but naming problems.
    
- **Two-Level Directory**: Each user has a separate directory.
    
- **Tree-Structured Directory**: Hierarchical.
    
- **Acyclic Graph Directory**: Shared files/subdirectories.
    

### Directory Implementation

- **Linear List**: Simple but slow search.
    
- **Hash Table**: Faster search using hashing.
    

---

# 3. File-System Structure and Implementation

## File-System Structure

- File system organized into layers.
    
- Uses **File Control Block (FCB)**: metadata about a file.
    

## Virtual File Systems (VFS)

- Abstract layer allowing multiple filesystem types.
    
- Provides a unified API.
    

## Allocation Methods

- How disk blocks are allocated to files:
    
    - Contiguous Allocation
        
    - Linked Allocation
        
    - Indexed Allocation
        

## Free Space Management

- Methods to track free blocks.
    

## Efficiency and Performance

- Influenced by disk allocation method, cache use (disk cache, read-ahead, etc).
    

## Recovery

- **Consistency checking**: Verify directory vs data blocks.
    
- **Backup and Restore** procedures.
    

## Log-Structured File Systems

- Every update written to a log first.
    
- Recovery uses the log.
    

## NFS (Network File System)

- Access remote files over LAN or WAN.
    
- Stateless servers; use RPC and XDR protocols.
    

---

# 4. Allocation Methods

## Contiguous Allocation

- Files occupy contiguous disk blocks.
    
- **Advantages**: Simple, fast direct access.
    
- **Disadvantages**: External fragmentation, inflexible file growth.
    

## Linked Allocation

- Files are linked lists of blocks.
    
- **Advantages**: No external fragmentation.
    
- **Disadvantages**: Only sequential access, pointers add overhead.
    

## Indexed Allocation

- Each file has an index block containing all pointers.
    
- **Advantages**: Supports random access.
    
- **Disadvantages**: Overhead for small files.
    

## Performance

- Contiguous: 1 access per block.
    
- Linked: i accesses for ith block.
    
- Indexed: Depends on level of indexing.
    

---

# 5. Free-Space Management

## Methods

### Bit Vector

- 1 bit per block: 0 = allocated, 1 = free.
    
- **Advantages**: Easy to find free blocks.
    
- **Disadvantages**: Needs memory for bitmap.
    

### Linked List

- Free blocks linked together.
    
- **Disadvantage**: Slow traversal.
    

### Grouping

- First free block contains addresses of n free blocks.
    

### Counting

- Keep address of first free block + number of contiguous free blocks.
    
