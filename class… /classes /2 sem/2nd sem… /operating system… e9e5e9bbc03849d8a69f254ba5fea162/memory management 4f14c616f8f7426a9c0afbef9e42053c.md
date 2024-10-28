# memory management

## memory management:

- contiguous allocation
    
    **What is it?**
    
    Contiguous memory allocation is a technique where each process is assigned a single, contiguous block of memory in the main memory. This means all the memory locations used by the process are consecutive and adjacent to each other.
    
    **Advantages:**
    
    - **Simple to implement:** The operating system only needs to keep track of the starting address and size of each allocated block.
    - **Fast access:** Memory access is faster because there's no need for address translation or scattered memory locations.
    - **Efficient for simple applications:** Works well for applications with predictable memory needs and no frequent memory requests.
    
    **Disadvantages:**
    
    - **Internal fragmentation:** Unused memory within a process's allocated block is wasted.
    - **External fragmentation:** Even if there's enough total free memory, it might be scattered in small blocks, preventing allocation of larger processes.
    - **Compaction:** Requires moving processes around in memory to consolidate free space, which is time-consuming and can lead to performance overhead.
    - **Limited scalability:** Difficult to manage memory efficiently for a large number of processes with varying memory requirements.
    
    **Variations:**
    
    - **Fixed-size partitions:** Memory is divided into fixed-size blocks, regardless of process size. Leads to internal fragmentation but simplifies allocation.
        - first fit
        - best fit
        - worst fit
    - **Dynamic partitions:** Blocks are allocated dynamically based on process size, reducing internal fragmentation but increasing complexity.
    
    **Comparison with other allocation methods:**
    
    - **Non-contiguous allocation (e.g., paging, segmentation):** Avoids internal fragmentation but introduces overhead for address translation and potential external fragmentation.
    - **Virtual memory:** Allows processes to use more memory than physically available by swapping data between main memory and secondary storage (e.g., disk).
    
    **When to use contiguous allocation:**
    
    - Simple applications with predictable memory usage.
    - Real-time systems where fast memory access is critical.
    - Embedded systems with limited memory and processing power.
    
    **Modern operating systems:**
    
    - Typically use combinations of contiguous and non-contiguous allocation techniques.
    - Often employ virtual memory to overcome limitations of pure contiguous allocation.
- non-contiguous allocation
    - Paging:
        
        ![https://media.geeksforgeeks.org/wp-content/uploads/20230703093831/paging.webp](https://media.geeksforgeeks.org/wp-content/uploads/20230703093831/paging.webp)
        
        Paging is a memory management technique used in operating systems to efficiently allocate physical memory to processes. It divides both physical memory (RAM) and logical memory (address space) into fixed-size blocks called frames and pages, respectively.
        
        **Here's a breakdown of key concepts:**
        
        - **Frames:** Fixed-size blocks of physical memory (RAM). All frames have the same size, typically a power of 2 (e.g., 4 KB, 8 KB).
        - **Pages:** Fixed-size blocks of logical memory (process address space). They also have the same size as frames.
        - **Page Table:** A data structure maintained by the Memory Management Unit (MMU) that maps virtual page numbers to physical frame numbers. Each process has its own page table.
        
        **How Paging Works:**
        
        1. **Process Address Space:** A process's logical memory is divided into pages.
        2. **Physical Memory:** Physical memory is divided into frames.
        3. **Page Table Mapping:** The page table keeps track of where each page of a process is located in physical memory (i.e., which frame it occupies).
        4. **Loading Pages:** Initially, only a subset of a process's pages are loaded into physical memory. The rest remain on secondary storage (e.g., hard disk).
        5. **Address Translation:** When a program tries to access a memory location, the MMU uses the virtual address to translate it into a physical address. It does this by:
            - **Extracting the page number** from the virtual address.
            - **Looking up the page number** in the page table to find the corresponding **frame number**.
            - **Combining the frame number** with the **offset** (within the page) to get the **physical address** in RAM.
        6. **Page Faults:** If the MMU encounters a virtual address that points to a page not currently in memory, a page fault occurs. The operating system then:
            - Suspends the process.
            - Loads the required page from secondary storage into a free frame in physical memory.
            - Updates the page table.
            - Resumes the process and allows it to continue execution.
        
        **Benefits of Paging:**
        
        - **Eliminates External Fragmentation:** Paging allows for non-contiguous allocation of physical memory to processes. This is because pages can be placed in any available frames, regardless of their location.
        - **Simpler Memory Management:** Paging simplifies memory management by providing a fixed-size unit (page) for allocation.
        - **Protection:** Page tables can be used to define access permissions (read-only, read-write) for each page, enhancing memory protection.
        - **Virtual Memory:** Paging forms the foundation for virtual memory, which allows processes to have a larger virtual address space than available physical memory.
        
        **Drawbacks of Paging:**
        
        - **Internal Fragmentation:** Within a frame, there can be wasted space if the process code or data doesn't perfectly fit the entire frame size.
        - **Translation Overhead:** The MMU needs to translate virtual addresses to physical addresses, which adds some overhead to memory access.
        
        **Overall, paging is a widely used memory management technique that offers efficient memory allocation, simplifies memory management, and enables virtual memory. However, it's important to consider its trade-offs, particularly internal fragmentation and address translation overhead.**
        
        ![photo_2024-03-15_10-48-33.jpg](memory%20management%204f14c616f8f7426a9c0afbef9e42053c/photo_2024-03-15_10-48-33.jpg)
        
    
    ---
    
    consider a logical space of 8 pages of 1024 words each map on to physical memory of 32 frames find number of bits in the logical address and the bits in physical address 
    
    - logical address space = page number * page size
        - 8*1024
            - 2^3 * 2^10 = 2^13
                - 13 bits
    - physical address space = frame number * frame size
        - 32 * 2^10
            - 2^5 * 2^10 = 2^15
                - 15 bit

---

### segmentation :

![https://media.geeksforgeeks.org/wp-content/uploads/20230703104323/ezgifcom-gif-maker-(15).webp](https://media.geeksforgeeks.org/wp-content/uploads/20230703104323/ezgifcom-gif-maker-(15).webp)

Segmentation is a memory management technique used in operating systems to organize the logical address space of a process into variable-sized blocks called segments. This approach contrasts with paging, which divides memory into fixed-size blocks.

**Here are some key points about segmentation in OS:**

- **Advantages:**
    - **Flexibility:** Segments can be tailored to the logical structure of a program, allowing efficient memory allocation for different program parts (code, data, stack).
    - **Protection:** Segmentation allows defining access permissions for each segment, enhancing security by preventing unauthorized access to different program sections.
    - **Reduced Internal Fragmentation:** Unlike paging, segmentation avoids internal fragmentation within segments, as they can be any size to fit the program's needs.
- **Disadvantages:**
    - **External Fragmentation:** Unused memory gaps can appear between segments in memory, leading to external fragmentation. This can be an issue if the OS needs to allocate memory for a new process and no contiguous free space is available.
    - **Increased Overhead:** Managing segment tables and keeping track of segment boundaries adds some overhead to memory management compared to paging.
- **Components:**
    - **Segment:** A variable-sized block of contiguous memory allocated to a process.
    - **Segment Table:** A data structure maintained by the OS that stores information about each segment, including its base address, limit (size), and access permissions.
    - **Segment Register:** A hardware register that holds the base address of the currently active segment.
- **Process of Accessing Memory using Segmentation:**
1. The program generates a logical address.
2. The logical address is divided into two parts: a segment number and an offset within the segment.
3. The segment number is used to index the segment table and retrieve the base address of the corresponding segment.
4. The offset is added to the base address to get the physical address in memory.
5. The OS checks the access permissions associated with the segment to ensure valid access.
- **Comparison with Paging:**

| **Feature** | **Segmentation** | **Paging** |
| --- | --- | --- |
| Memory Division | Variable-sized segments | Fixed-sized pages |
| Fragmentation | External fragmentation possible | Internal fragmentation possible, no external |
| Protection | Easier to implement per-segment protection | Requires additional mechanisms for protection |
| Overhead | Higher overhead due to segment table management | Lower overhead |

segment table

| segment | base | length |
| --- | --- | --- |
| 0 | 219 | 600 |
| 1 | 2300 | 14 |
| 2 | 90 | 100 |
| 3 | 1327 | 580 |
| 4 | 1952 | 96 |

### virtual memory and demand paging :

![https://media.geeksforgeeks.org/wp-content/uploads/20230711080029/ezgifcom-gif-maker-(22).webp](https://media.geeksforgeeks.org/wp-content/uploads/20230711080029/ezgifcom-gif-maker-(22).webp)