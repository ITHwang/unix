## 1. Permission Value

### 1.1. Linux System Default Permission Values
- executable files & folders: **777**(rwxrwxrwx)
- normal files: **666**(rw-rw-rw-)

### 1.2. Default Umask Values
- default mask **for a non-root user** is **002**.
	- executable files & folders: **775**(rwxrwxr-x)
	- normal files: **664**(rw-rw-r--)
- default mask **for a root user** is **022**.
	- executable files & folders: **755**(rwxr-xr-x)
	- normal files: **644**(rw-r--r--)
- Default umask values can be changed by `umask [mask value]`. 

## 2. Searching

### 2.1. grep
- Definition: Global Regular Expressions Print
- Format: grep \[option\] \[pattern\] \[file name\]
- Options
	- -i: search both upper case letters and lower case letters.
	- -l: print the names of files that include the pattern.
	- -n: print row number
	- -v: print rows that don't include the pattern.
	- -c: print row count
	- -w: search only pattern as a word.

> UNIX uses wildcard(glob pattern) to extend file name that is slightly different from regex.
> 
> Therefore, wrapping regex with single or double quote helps grep understand the regex.

### 2.2. find
- format: find \[path\] \[option\] \[execution\]
- options
	- -name (file): if file name is (file)
	- -type (file type): if file type is (file type)
	- -mtime (+|-)n: last modified time of the file 
	- -atime (+|-)n: last access time
	- -user (loginID): if file owner name is (loginID)
	- -size (+|-)n: if file size is higher than n or lower than n
	- -newer (file): if the file is lastly modified after (file) was modified
- The result of find command can be saved using **std in/out redirection**

### 2.3. which
- description: print absolute path of the command.
- format: which (command)