## 1. Overview
- UNIX can execute multiple processes which are consist of **system process** and **user process**.
- When booting UNIX, **init process**(ancestor process) is executed and then this process create other processes that are required for UNIX system.

## 2. Types of processes

### 2.1. Daemon process
- A program that runs continuously as **a background process** executed by **unix kernel**(ex. httpd process)
- Daemon usually waits for requests in wait status and when requests come in, it is alerted to provide the service.

### 2.2. Parent process
- create other processes(child process)
- All processes have a parent process, <u>except init process(No.1 process)</u>

### 2.3. Child process
- created by a parent process
- A child process is done, it returns to the parent process and terminates.

### 2.4. Orphan process
- A process whose parent process was terminated.
- When a orphan process is made, No.1 process can be assign to its parent process, which is called **re-parenting**.
- Init process asks the kernel for cleaning of the PCB of the orphan process and waits till the child completes its execution.

### 2.5. Zombie process
- A process that has completed its execution but its entry in the process table.
- This is because the parent process usually does its subsequent job and cannot call `wait()` system call which is used for removal of zombie processes.
- The OS has one process table of finite size, so lots of zombie processes will results in a full process table, which prevents the OS from creating new processes when required.
- solutions
	1. send a SIGCHLD signal to the parent for dealing with the child process.
	2. terminate the parent to make the zombie process the orphan process.
	
> For more details about orphan and zombie process, [Zombie and Orphan Process in OS](https://www.scaler.com/topics/operating-system/zombie-and-orphan-process-in-os)

## 3. Process Management

### 3.1. ps
- options
	- -e: print all running processes in the system.
	- -f: print details.
	- -u (uid): print all processes for a specific user.
- columns of `ps -ef`
	- UID
	- PID
	- PPID
	- C: priority of process
	- STIME: start time, `hh:mm:ss`
	- TTY: type of terminal and number. if "?", it's system process.(usually daemon process)
	- CMD

### 3.2. kill
- signals
	- -9: SIGKILL, force quit but zombie process may not die.
	- -15(default): SIGTERM, some process may not die. 
	











