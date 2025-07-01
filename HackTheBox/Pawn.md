
### Scanning open ports
Machine: 10.129.111.162
```
namp -sV 10.129.111.162
```
#### Results
```
21.tcp open ftp vsftpd 3.0.3
service Info: OS: Unix
```

### Connecting to FTP Server
```
ftp -a 10.129.111.162
```
- -a allows anonymous login
### Searching FTP for Flag
```
ftp>dir
```
#### Results
![[Screenshot 2025-06-30 at 11.11.48 PM.png]]
### Dowloading flag.txt
```
ftp>get
```
![[Screenshot 2025-06-30 at 11.14.06 PM.png]]
- Downloads file to directory `ftp` was launched from
### Flag
![[Screenshot 2025-06-30 at 11.16.29 PM.png]]