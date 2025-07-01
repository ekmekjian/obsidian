Machine: 10.129.219.193

### Initial Scan
![[Screenshot 2025-06-30 at 11.35.50 PM.png]]
- `microsoft-ds` port: 445 is the SMB needed
### Listing Shares are available
![[Screenshot 2025-06-30 at 11.48.58 PM.png]]
### Finding which Share doesn't require password for access
![[Screenshot 2025-06-30 at 11.50.29 PM.png]]
- `smbclient \\\\10.129.219.193\\IPC$` required no password for access

