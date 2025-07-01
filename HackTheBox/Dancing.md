Machine: 10.129.219.193

### Initial Scan
![[Screenshot 2025-06-30 at 11.35.50 PM.png]]
- `microsoft-ds` port: 445 is the SMB needed
### Listing Shares are available
![[Screenshot 2025-06-30 at 11.48.58 PM.png]]
### Finding which Share doesn't require password for access
![[Screenshot 2025-06-30 at 11.50.29 PM.png]]
- `smbclient \\\\10.129.219.193\\IPC$` required no password for access
	- `dir` and `ls` produced no results
- `smbclient \\\\10.129.219.193\\WorkShares` required no password for access
	- `ls` produced: ![[Screenshot 2025-06-30 at 11.56.05 PM.png]]
	- James.P was the only folder to containt `flag.txt`
### Get Flag
![[Screenshot 2025-06-30 at 11.57.54 PM.png]]