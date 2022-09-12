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

## todo: chap.7
todo