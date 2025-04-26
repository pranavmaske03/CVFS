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
  1. **Boot block:** Its a block of 1kb size which contains the information used to start the operating system. When we press ON button of laptop
     or desktop the code from boot block gets executed.
  
