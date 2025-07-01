
### Scanning open ports
Machine: 10.129.111.162
```
namp -sV 10.129.111.162
```
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