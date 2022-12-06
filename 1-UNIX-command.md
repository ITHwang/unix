## 1. ls

### 1.1. Options
- -a: print the list of all files including hidden files
- -l: print the details of a file
- -i: print inode number
- -F: denote the type of file(\*: file, /: directory, @: symbolic link)
- -R: print to the subdirectories
- -d: print the information of given directory
- ll: ls -alF

## 2. file

### 2.1. Options
- -i: print file mime

## 3. mkdir

### 3.1. Options
- -p: if intermediate directories(one or more) don't exists, create them.

## 4. cat

### 4.1. Options
- -n: print with row numbers

## 5. more

### 5.1. Description
**more** is a filter for paging through text one screenful at a time.

## 6. tail

### 6.1. Description
Print the last 10 lines of each FILE to standard output.

### 6.2. Options
- -\[NUM\]: output the last NUM lines
- -f: output appended data as the file grows.

## 7. rm

### 7.1. Furthermore
- When you use `rm FILE`, it reduces the number of the hard link of the `FILE` by one.
- If the hard the number equals to zero, the file name, the inode and the data block that the inode refers to are removed.

## 8. mv

### 8.1. move multiple files to a directory
- mv (SRC1) (SRC2) ... (SRCn) (DST dicrectory)

## 9. ln

### 9.1. DESC
- make links between files(hard links or symbolic links)

### 9.2. how to make hard links
- ln (src file name) (hard link name)
- It can be possible to attach two or more names to one file and the names are called **hard link**
- Hard link files have a same inode number.
- When the number of hard link is reduced to zero, the data block which the inode refers to is removed.

### 9.3. how to make symbolic links
- ln -s (src file name) (symbolic link name)
- **Symbolic link file** is a special file for accessing original file and have the path of the original file.(it's like shortcut icon in Windows.)
- The inode number of a symbolic link file differs from that of the original file that the sysbolic link file refer to.
- If the original file is removed, the symbolic link cannot be used no longer.