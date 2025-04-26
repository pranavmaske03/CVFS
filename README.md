# Customised Virtual File System

**Technologies Used:** C++ Programming Language.

**Operating System Used:** As this project executes on primary storage (i.e., RAM), there is no special requirement for an operating system (we can use Linux, Windows, macOS).

**Description:** 
- This project is the virtual representation of a file system.
- A file system is considered the way of storing information about files and the data from the files into a secondary storage device (hard disk).
- Every operating system has its own type of file system (NTFS, FAT32, FAT16, UFS). In this project, we implement the layout of a complete file system in RAM.
- In this project, we implement almost every related system call used in file manipulation activities, along with some important commands.
- This is a research-based project developed to understand the internals of an operating system and explore data structures implementation in C programming.

## File System Layout (Hard Disk)
![File System structure-harddisk](images/cvfs-structure.jpeg)

#### The above diagram indicates the file system layout on the hard disk.
- The file system is divided into four parts.

1. **Boot Block:** It's a block of 1 KB size that contains the information used to start the operating system. When we press the ON button on a laptop or desktop, the code from the boot block gets executed.
2. **Super Block:** It's a block of 1 KB size that contains information about the entire file system. This block contains information about the total number of inodes, used inodes, free inodes, total number of blocks, free blocks, used blocks, etc.
3. **Disk Inode List Block (DILB):** It is a linked list of inodes. An inode is considered a structure that contains information about a file. For every file, there is a separate inode. The operating system accesses the file by using the information stored inside the inode.
    - Inode contains the following:
      - Inode number
      - Name of the file
      - Size of the file (allocated memory)
      - Actual size of the file (size of data)
      - Permission of the file
      - Last access and modification time
      - Link count
      - Block number allocated to the file
4. **Data Block:** This is one of the largest sections of the file system. The data block contains the actual data stored inside the file. Each block in the data block is of 1 KB size (1024 bytes). Inside the data block, there is no information about the file.

#### This concept of a file system is applicable to any type of operating system. All the above information relates to the hard disk only.

## Data Structures of the File Subsystem in RAM
![File System structure-ram](images/filesystem-ram.jpeg)

## 1. UAREA
- It is called the **User AREA**.
- For every running process, a separate UAREA is created.

## 2. UFDT
- It is called the **User File Descriptor Table (UFDT)**.
- It is considered an array of pointers, where each pointer points to an entry in the file table.
- In the UFDT, the first three entries are reserved: one for stdin (keyboard), one for stdout (monitor), and one for stderr (monitor).

## 3. File Table
- This table contains information about opened files.
- It contains the offset from where we can read or write and the mode in which the file is open.
- It contains a field named `count` associated with new process creation and a pointer pointing to the IIT.

## 4. IIT
- It is called the **Incore Inode Table**.
- This table holds all the inodes whose files are opened by the running processes.
- The actual inodes are stored in the DILB, but when any process opens a file, its inode gets loaded into the RAM and is stored inside the **Incore Inode Table**.
- The inode from the IIT contains information like the name of the file, its inode number, size of the file, actual size, reference count, and the block number from the data block.

# Structure of the CVFS
![File System structure-harddisk](images/filesystem-hardisk.jpeg)

#### The above diagram represents the complete internal structure of the Customised Virtual File System (CVFS). 
It shows the relationship between the User File Descriptor Table (UFDT), File Tables, Inodes, and Buffers in RAM. 
Each file's metadata and content flow is mapped, starting from the UFDT entries pointing to the File Table, which then links to Inodes and finally to the actual data in Buffers. 
This diagram also highlights the role of the Superblock and macros, maintaining system-wide information like total inodes and file sizes.

## Conclusion
This project provides an in-depth understanding of the internal structures of a file system and how system calls operate behind the scenes. It simulates an operating system's file subsystem in RAM, making it easier to visualize and learn the real-world architecture and data flow within an operating system.

