## 1. Overview
- UNIX can execute multiple processes which are consist of **system process** and **user process**.
- When booting UNIX, **init process**(ancestor process) is executed and then this process create other processes that are required for UNIX system.

## 2. Types of processes

### 2.1. Daemon process
- A program that runs continuously as **a background process** executed by **unix kernel**
- ex. httpd process
- Daemon usually waits for requests in wait status and when requests come in, it is alerted to provide the service.

### 2.2. Parent process
- create other processes(child process)
- All processes have a parent process, <u>except init process(No.1 process)</u>

### 2.3. Child process
- created by a parent process
- A child process is done, it returns to the parent process and completes its execution.

### 2.4. Orphan process
- A process whose parent process was terminated.
- When a orphan process is created, No.1 process can be assign to its parent process, which is called **re-parenting**.
- Init process asks the kernel for cleaning of the PCB of the orphan process and waits till the child completes its execution.

### 2.5. Zombie process
- A process that has completed its execution but its entry in the process table.
- This is because the parent process usually does its subsequent job and cannot call `wait()` system call which is used for removal of zombie processes.
- The OS has one process table of finite size, so lots of zombie processes will results in a full process table, <u>which prevents the OS from creating new processes when required.</u>
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

## 4. Foreground & Background

### 4.1. Overview
- Shell manages processes as **jobs** which are operated <u>in foreground or background way.</u>
- Foreground process works **serially**, whereas background process works **parallelly**.
- Default is foreground way, background process is executed by adding **"&"(ampersand)** to the end of the command line.

### 4.2. Job Control
#### 4.2.1. jobs (%job number|+|-)
- columns of `jobs`
	1. job number
	2. order
		- +: latest
		- -: just before latest
	3. status
		- running
		- done: completed normally
		- terminated: completed abnormally
		- stopped
	4. command
#### 4.2.2. Placing a foreground job into the background
1. ctrl + z: suspend the foreground job.
2. bg (%job number): place the suspended job in the background.(default: the job whose order is +)
#### 4.2.3. Bringing a background job to the foreground
1. fg (%job number): reconnect the background job to the terminal.(default: the job whose order is +)

> For more details about foreground and background process, [How to Foreground a Background Process in Linux](https://www.baeldung.com/linux/foreground-background-process)

#### 4.2.4. nohup
- makes the background job keep going til the job is completed even after logout.

## 5. user info

### 5.1. `users`
- print **names** of users logging in.

### 5.2. `who`
- print **names and details** of users  logging in.
- columns of `who`
	1. user name
	2. tty(ex. pts/1)
	3. access time
	4. connected ip address
- `who -b`: latest reboot time

### 5.3. `w`
- print **names and details and running jobs** of users logging in.
- columns of `w`
	1. USER
	2. TTY
	3. FROM: connected ip address
	4. LOGIN@: access time
	5. IDLE: idle time
	6. JCPU: the amount of time **the entire process** used CPU
	7. PCPU: the amount of time **the running process** users CPU
	8. WHAT: the running command

### 5.4. My info
- `who am i`: my name and details
- `whoami`: only my name
- `id`: user name, uid, gid, groups

### 5.5. Switch user
- su (user name)
	- with "-": executes the init file of the user and change working directory.
	- without user name: switches to root