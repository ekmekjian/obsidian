#networking
---

# What is Networking


Networking is organized using one of two methods:Open Systems Interconnections(OSI), Transmission Control Protocol/Internet Protocol (TCP/IP)

*   A simple network is one that has all computers on a network connected to one switch

**OSI:**

*   uses numeric layers to define each part of a network
    *   Layer 7 Application
    *   Layer 6 Presentation
    *   Layer 5 Session
    *   Layer 4 Transport
    *   Layer 3 Network
    *   Layer 2 Data Link
    *   Layer 1 Physical

Layer 1 **Physical**\- referring to hardware.
Layer 2 **Data Link**\- referring to frames and how they travel.

*   any device that uses MAC address is a part of this layer
*   is the only layer with 2 sub layers LLC and MAC

Layer 3 **Network** - uses containers called packets for transporting data from one network to another
Layer 4 **Transport** - the segmentation and reassembly layer.

*   This layer is responsible for chopping data into something that can be transported into a packet then frame.
*   must send packets in correct order for the receiving system to correctly rebuild
*   In segmentation the data is broken into chucks called **segments(TCP)** or **datagrams(UDP)** and given a sequence number
    *   datagrams don't get sequence numbers
*   receiving systems can make requests when packets were not received in good order
*   **segments** - Destination port|Source port|Sequence number|Checksum|Flags|Acknowledgement|Data

Layer 5 **Session** - Handles all sessions that connects application to application over the network. ex: printer job to printer system

Layer 6 **Presentation** - converts data for application layer from lower layers and vice versa

Layer 7 **Application** - end user side.

**TCP/IP(Transmission Control Protocol/Internet Protocol):**

*   has four layers that consilidate some of the OSI layers
    *   **Application** - Application|Presentation|Session
        *   Sessions on TCP/IP protocols is a connection of two IPs on their own ports talking to each other.
    *   **Transport** - Transport
    *   **Internet** - Network - deals with packets
    *   **Link/Network Interface** - Data Link|Physical - dealing with frames
*   are a collection of network protocols that:
    *   creates a unique identifier for each system
    *   sets rules for issues such as how to handle packets how they travel between subnets
*   **IP**
    *   primary logical addressing protocol
    *   is responisible for sending data where it needs to go
    *   gives each system a unique identifier known as IP address
    *   known as a logical address to distinguish it from physical addresses
    *   uses dotted decimal notation(dotted-octet) based on four 8-bit numbers
    *   each number ranges 0-255. format:###.###.###.###
    *   no two system share the same ip address if some reason they do there can be problems with communicating with the network
*   **UDP(User Datagram Protocol)** - Destination port|Source port|Length|Checksum|Data
    *   Has less checks and measures than tcp and is less worried about delivering the data

**Port** - a number between 1 and 65,536. Is a logical value assiigned to specific applications or services

**Netmask** -  the network portion of an IP address

*   if an address 192.168.0.2 had the netmask of 255.255.255.0 each 255 represents what part of the ip is the network the 0 being that spot is used to assign devices such as that .2 and 192.168.0.0 is the network

**Packets-** a wrapper that allows data to travel between networks

*   is wraps around data that contains Destiniation IP address | Source IP address | Data
*   the most consistent wrapper for data. As the packet travels through the network every device it passes through strips the frame read the packet then places it in a new frame and sends it where it needs to go.

**Frames** - a container/wrapper for a chunk of data moving across a network.

*   there are different types of frames
    *   DOCSIS
*   All NICs must transmit the same frame type or they won't be able to communicate with each other
*   A frame carries: Recipients MAC address|Senders MAC address|Type|Data|FCS
    *   The first two are self explanatory
    *   Type tells whats inside the frame
    *   Data is the purpose of our transmission(what we are actually sending)
    *   FCS is a frame check sequence and is used by the NIC to determine if the frame came in intact
*   Over a wired connection frames can hold up to 1500 bytes of data anything bigger is chopped up into frame size. The data chopping is handled by the system's software
    *   Thanks to this size limit other NICs on the network are able to transmit their frames with out trouble from big files.

**FCS**\- 4 bytes in a frame that's used to check the integrity of a frame

*   The FCS uses a special math for checking known as CRC (Cyclic Redundancy Check)
    *   This check is used by the NIC to check each frame by taking the data that comes in from a frame and divides it by a key that the NIC has with it. If the divisions results equal to the FCS's CRC then the frame is good, if not the frame is dropped.

**MAC(Media Access Control) address** -a unique identifier that is used to identify a specific piece of hardware

*   also known as a physical address
*   no two devices share the same address
*   companies will request MAC address from the IEEE(Institute of Electrical and Electronics Engineers) . Each one is unique and will tied only to the NIC its burned into. No other manufacture will have the same addresses as others.
*   Some devices have MAC address visibly printed on their surface.Will be printed as ######-######
*   MAC address format: ##-##-##-##-##-##
*   the first six digits represent the number of the NIC manufacturer also know as Organizationally Unique Identifyer (OUI)
*   the last six are the manufacturer's unique serial numer for that NIC also known as "device ID"
*   The name space for this format was orginally called MAC-48(48 refering to how many bits the MAC address will be comprised of) but was later changed to EUI-48 because the IEEE could trademark it but its still widely refered to as MAC
*   MAC addresses are typically used on smaller network partly because a network of thousands of computers sending broadcast signals or even just hundreds would take so much of the networks bandwith barely any data of value would get through

**NIC(Network Interface Card)**

*   the piece of hardware that connect a pc to the network.
*   Although its hardware that connects to the nework it's considered in Layer 2 Data Link
*   All NIC come burned into a chip their MAC address.
*   NICs were originally used to transmit data, those ones and zeros, through pluses of electricity were as now and days data can be recieved and transmitted through radio and light
*   Is also resposible for wrappingthe data into frames before transmitting and vice versa for recieving
*   Doesn't pay attention to what the actual is the data that a frame carries
*   When the NIC needs to send data to another NIC and it's never made contact before will send a broadcast on the network using FF-FF-FF-FF-FF-FF as a MAC address(known as the broadcast address)
    *   The broadcast address is contained within a frame which all NICs on the network will proccess then the device with the requested MAC address sends a return signal confirming that that address is in fact on the network
*   there are two aspects of a NIC LLC(Locgical Link Control) and MAC(Media Access Control)
    *   LLC is in charge with communicating with the system's OS through a driver as well as manage network protocols and provides flow control
    *   MAC is in charge of creating the frames and addressing them with sender and recipient parts of a frame as well as adds and checks the FCS thens sends down the cable

**Router**

*   connects to subnets
*   uses IP to direct data not MAC address
*   this device working with tcp/ip is what allows systems to communicate without ethernet

**Central Box**

*   Frames from NICs are sent here for transportation
*   On early versions of a central box they were called 'hubs' and when a frame was a received the hub would make a copy of the frame and send it to all ports except the port the frame was received from but only the device with the same MAC address as the recipients address inside a frame will be able to actually process  the frame
*   Hubs were replaced by switches which, unlike a hub, sends frames to the port that has that matches the MAC address in the frames

**Sockets -** a way to speak to other programs using the standard Unix file descriptor

**Byte Order** \- depending on the device data can be sent in different orders. There's **Big Endian**(**Network Byte Order)** and **Little Endian**(**Host Byte Order**)

*   **Big Endian** is called the Network byte order because it is the preferred method for sending data and because it sends data sequentialy
    *   two byte hex number b34f would be b3 then 4f
*   **Little Endian** \- sends data in reverse order
    *   two byte hex number b34f would be stored 4f then b3
*   It's not always possible to know the byte order when receiving/sending data so by default some programs will convert the data into a preferred order and to do that functions are created to just that
*   Function Description
    *   htons() host to network short
    *   htonl() host to network long
    *   ntohs() network to host short
    *   ntohl() network to host long
*   All conversions are done before they get on the wire

