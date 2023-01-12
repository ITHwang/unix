## 1. Boot

### 1.1. Booting process
1. **BIOS**(Basic Input/Output System) or **UEFI**(Unified Extensible Firmware Interface) runs the power-on self-test(**POST**).
	- verify the hardware components and peripherals.
	- carry out tests to ensure that the computer is in proper working condition.
2. The BIOS/UEFI selects **a boot device**, <u>in the first sector of which <b>the boot loader</b> located.</u>
	- **The boot loader** is a small program that loads the operating system.
	- **GRUB2**, the most widely used boot loader, 
		1. takes over from BIOS or UEFI  at boot time.
		2. loads itself.
		3. inserts **the Linux kernel** into memory.
		4. turns over execution to the kernel.
3. The kernel takes over from the boot loader and <u>now the OS controls access to the computer resources.</u>
	- First, The kernel goes through the following steps:
		1. decompress itself in place.
		2. perform hardware checks.
		3. gain access to vital peripheral hardware.
		4. run **the init process**.
4. **Systemd**, recently used init process, performs a range of tasks:
	1. probe all remaining hardware.
	2. mount **filesystems**
	3. initiate and terminate services.
	4. manage essential system process like **user login**.
	5. run a desktop environment.
5. Run Levels
	- **The run level** stands for the current state of the operating system.
	- Now, `.target` files replace run levels in Systemd.
	- To check the default target, `systemctl get-default`.
	- Each target file is interpreted as follows.
		- `poweroff.target`, run level 0: turn off the computer.
		- `rescue.target`, run level 1: initiate a rescue shell process.
		- `multi-user.target`, run level 3: configure the system as a non-graphical multi-user environment.
		- `graphical.target`, run level 5: establish a graphical multi-user interface with network services.
		- `reboot.target`, run level 6: restart the machine.
		- `emergency.target`: emergency run level.

> For more details, [Guide to the Boot Process of a Linux System](https://www.baeldung.com/linux/boot-process)

## 2. Shut down and Reboot

### 2.1. *shutdown*
- without any options: **power-off** the machine in one minute.
- *-r* option: **reboot** instead of powering off the machine.
- *-H* option: **halt** the system.
> halt: terminate all running processes and shut down all CPUs
> 
> power off: the same as halt, and then <u>attempts to cut power from system.</u>
- schedule *shutdown*
	- absolute time: *shutdown 09:30*
	- relative time: *shutdown +30*
	- immediately: *shutdown now*
- *-c*: cancel the *shutdown* process.

### 2.2. *reboot*
- *reboot*
- *halt --reboot*
- *poweroff --reboot*

### 2.3. *halt*
- *halt*
- *reboot --halt*
- *poweroff --halt*

### 2.4. *poweroff*
- *poweroff*
- *reboot -p*
- *halt -p*

### 2.5. *-f* option
- All three commands support a *-f* option which do the machine **forcibly.**

> For more details, [Shut Down and Reboot Linux Systems From the Terminal](https://www.baeldung.com/linux/shutdown-reboot-from-terminal)

## 3. User Management

### 3.1. */etc/passwd*
- manage accounts.
- Each row in the file shows a user information.
- format: `{login ID}:{password}:{UID}:{GID}:{description}:{home directory}:{login shell}`
- ex. *root:x:0:0:Super-User:/root:/usr/bin/bash*
- Usually the password field is shadowed by "x" and the password is saved in */etc/shadow* only root can read.

### 3.2. *useradd*
- format: `useradd {options} {login ID}`
- options
	- -u {uid}: assign UID
	- -g {gid}: assign GID
	- -d {dir}: assign the absolute path of **the home directory.**
	- -m: create **the user home directory** if it not exists.
	- -s {shell}: assign the absolute path of **the login shell.**
	- -c {comment}: describe the user information.

### 3.3. *usermod*
- format: `usermod {options} {login ID}`
- options
	- -u {uid}: change UID
	- -g {gid}: change GID
	- -d {dir}: change the absolute path of **the home directory.**
	- -s {shell}: change the absolute path of **the login shell.**
	- -c {comment}: describe the user information.
	- -l {login ID}: change **login ID**.

### 3.4. *userdel*
- format: `userdel {options} {login ID}`
- options:
	- -r: remove the user home directory.

## 4. Group Management

### 4.1. */etc/group*
- manage groups.
- Each row in the file shows a group information.
- format: `{group name}:{password}:{GID}:{the list of users in the group}`
- ex. *root::0:root*
- Usually the group password(second field) doesn't be used.

### 4.2. *groupadd*
- format: `groupadd {options} {group name}`
- options:
	- -g {GID}: assign a GID value.(optional)

### 4.3. *groupmod*
- format: `groupmod {options} {group name}`
- options:
	- -g {GID}: change the GID value.
	- -n {new group name}: change the group name.

### 4.4. *groupdel*
- format: `groupdel {group name}`