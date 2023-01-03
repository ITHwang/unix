## 1. Booting and Shutdown

### 1.1. Booting process
1. BIOS(Basic Input/Output System) or UEFI(Unified Extensible Firmware Interface) runs the power-on self-test(POST).
	- verify the hardware components and peripherals.
	- carry out tests to ensure that the computer is in proper working condition.
2. The BIOS/UEFI selects a boot device, in the first sector of which the boot loader located.
	- The boot loader is a small program that loads the operating system.
	- GRUB2, the most widely used boot loader, 
		1. takes over from BIOS or UEFI  at boot time.
		2. loads itself.
		3. inserts the Linux kernel into memory.
		4. turns over execution to the kernel.
3. Kernel
> todo: write it down
4. Systemd
> todo: write it down
5. Run Levels
> todo: write down

> For more details, [Guide to the Boot Process of a Linux System](https://www.baeldung.com/linux/boot-process)

1. Turn on devices around the system.
2. Turn on the system.
3. BOOTPROM phase: BOOTPROM check if hardwares and devices around the system are correctly operate.(Power On Self Test)
4. Boot Program phase: load boot program and kernel.
5. Kernel initialization phase: initialize the kernel along with /etc/system
6. initialization phase: init process execute rc scripts and display login window.

### 1.2. Shutdown

## 2. User Management
### 2.1. `/etc/passwd`
### 2.2. `useradd`
### 2.3. `usermod`
### 2.4. `userdel`
## 3. Group Management
### 3.1. `groupadd`
### 3.2. `groupmod`
### 3.3. `groupdel`
