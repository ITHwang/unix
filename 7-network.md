## 1. host

- `hostname`: checks host name.
- `nslookup`: searches ip address corresponding to domain name.
- `ping`: checks if connected to the host.(this command may be blocked because of security)
- `finger`: checks the personal information of local host or remote host.(this command may be blocked because of security)
	- columns
		1. login name
		2. real name of user
		3. home directory path of user
		4. default shell of user
		5. mail address of user
		6. last accessed time
		7. terminal name
		8. ip address of external host(terminal)
		9. etc.

## 2. FTP(File Transfer Protocol)

1. Check if ftp server is running as a background process.
```bash
systemctl list-unit-files | grep ftp
```
2. Connect via ftp.
```bash
ftp [host name]
```
3. ftp commands
	- cd (remote directory): moves to remote directory.
	- !cd (local directory): moves to local directory.
	- pwd: prints remote working directory.
	- !pwd: prints local working directory.
	- ls or dir: prints the list of files in remote working directory.
	- !ls: prints the list of files in local working directory.
	- get (remote file): brings the remote file to a local file.
	- mget (remote files): brings multiple remote files.
	- put (local file): sends the local file to remote.
	- mput (local files): sends multiple local files.
	- ascii: changes to ascii mode.
	- bin: changes to binary mode.(binary is default mode.)
	- bye: exits