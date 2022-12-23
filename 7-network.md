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

> Besides FTP, there are protocols for file exchange.
> 
> FTP: proposed over 40 years ago and vulnerable to attacks because any data sent is unencrypted.
> 
> FTPS(FTP-SSL and FTP Secure): an extension to the FTP which protect data as it travels over the network using SSL(secure sockets layer) and now TLS(transport layer security).
> 
> SFTP(SSH FTP and Secure FTP): an extension to the SSH on which all data is transferred in specially formatted packets via a single connection and is encrypted through the use of public and private keys.
> 
> For more details, [Understanding Key Differences Between FTP, FTPS And SFTP](https://www.jscape.com/blog/understanding-key-differences-between-ftp-ftps-and-sftp) and [ftp, ftps, sftp(ssh) 개념 정리](https://nhj12311.tistory.com/76)