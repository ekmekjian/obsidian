- depending on the device data can be sent in different orders. There's [[Big Endian]] and [[Little Endian]]
  [[Big Endian]]  is called the Network byte order because it is the preferred method for sending data and because it sends data sequentialy

-   [[Little Endian]]- sends data in reverse order
	-   two byte hex number b34f would be stored 4f then b3d be stored 4f then b3
-   It's not always possible to know the byte order when receiving/sending data so by default some programs will convert the data into a preferred order and to do that functions are created to just that
-   Function Description
	-   htons() host to network short
	-   htonl() host to network long	
	-   ntohs() network to host short
	-   ntohl() network to host long
    

-   All conversions are done before they get on the wire