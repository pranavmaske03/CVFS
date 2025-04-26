# Cusomised Virtual File System

**Technologies Used:** C++ Programming Language.

**Operating System Used:** As this project executes on a primary storage i.e RAM there is no special requirement of an operating system (we can use Linux,Windows,MacOS).

**Discription:** 
- This project is the virtual representation of file system.
- File system is considered as the way of storing the information about files & the data from the file into secondary storage device (hard disk).
- Every operating system has its own type of file system (NTFS, FAT32, FAT16, UFS). In this project, we implement the layout of a complete file system in RAM.
- In this project we implement almost every related system call used in file manipulation activity along with some important commands.
- This is research based project developed to understand internals of an operating system & explore the data structures implementation from c programming.

## FileSystem Layout (Hard disk)
![File System structure-hardisk](images/cvfs-structure.jpeg)


#### The above diagram indicates the file system layout on the hard disk.
- The FileSystem is divided into four parts.
  
  - **Boot Block:** Its a block of 1kb size which contains the information used to start the operating system. When we press ON button of laptop or desktop the code from boot block gets executed.
  - **Super Block:** Its a block of 1kb size which contains the information about whole file system. This block contains the information about total no. of Inodes, used Inodes, free Inodes, total no. of blocks free blocks, used blocks etc.
  - **Disk Inode List Block (DILB):** It is a LinkedList of Inodes. Inode is considered as a structure which contains information about the file. For every file there is saperate Inode. Operating system will access the file by considering the content stored inside an Inode.
  - Inode contains below in it -

1. Inode number.
2. Name of file.
3. Size of file (allocated memory).
4. Actual sizeof file (size of data).
5. Permission of that file.
6. Last access and modification time.
7. Link count.
8. Block number allocated to the file.

  - **Data Block:** This is one of the biggest section of file system. The data contains the actual data that we stored inside the file. Each block from data block is of 1kb size (1024 bytes). Inside the data block there is no information about the file.
 
    #### This concept of file system is applicable in any type of operating system. All the above information related to the hare disk only.


## Data Structures of file subsystem of RAM.
![File System structure-hardisk](images/filesystem-ram.jpeg)

## 1. UAREA
  - It is called as User AREA.
  - 
