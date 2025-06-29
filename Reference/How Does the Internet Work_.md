---

tags: 
- '#internet'

---

# How Does the Internet Work?


## **History:**

*   Started in 1960s as US army funded research project
*   Evolved in 1980s when Universities and public Companies need a way to share data across great distance

## **Deep Dive:**

*   Computer communicate through two methods
    *   Physically ([Ethernet cable](https://en.wikipedia.org/wiki/Ethernet_crossover_cable))
    *   Wirelessly ([WiFi](https://en.wikipedia.org/wiki/Wi-Fi),[Bluetooth](https://en.wikipedia.org/wiki/Bluetooth))
*   What is a network?
    *   A collection of connected computers
*   What is the internet?
    *   A large network of computers connected committed to keeping them all connected.
*   What is an IP address?
    *   All devices are identified on a network with an IP Address
    *   This is used to as a shipping address so data know where to go
*   What is a router?
    *   The median between data from the outside world to your computer
    *   This device makes sure that packets make it to the correct computer
*   What is an ISP?
    *   Internet Service Provider
    *   Connects client computers to the internet
*   What are packets and how are they used to transfer data?
    *   Data broken into 6 bits and sent down numerous routes
    *   Packets contain ip address of the sender(the server) and receiver (your device) as well as sequence numbers so that the data can be assembled in order
    *   If any packets were failed to make it your device can make a request for the missing data
*   What is a client?
    *   A computer not connected directly to the Internet but through and ISP
*   What is a server?
    *   A computer directly connected to the internet
*   What is a web page?
    *   Documents that can be displayed in a browser
*   What is a web server?
    *   A computer that hosts a website
    *   In order to host the site a server will have all a website’s pages within itself
*   What is a web browser?
    *   Web browsers are how we make DNS requests and connect to websites
    *   Used to view web pages
*   What is a search engine?
*   What is a DNS request?
    *   A phonebook with a collection of domain names and their associated IP address this is needed because not everyone can remember IP numbers
    *   When you enter a domain name then the browser sends a request to the DNS server (handled by ISP) to return the IP address
*   What browser are you currently using?
    *   Google Chrome 96
*   In your own words, explain what happens when you run a search on [google.com](http://google.com).
    *   A request is made and the search engine looks within its own database to pull the web pages most relevant to the search

## **What happens when you type a web address into a browser?**

1.  A DNS request is made from the client browser to ISP DNS server for the address
2.  The browser then uses HTTP to request a copy of the site sending a receiving data over TCP/IP
3.  “200 OK” means that the site can be received and begins sending packets caring bits of the site
4.  The browser receives the packets and assembles them to view the website

