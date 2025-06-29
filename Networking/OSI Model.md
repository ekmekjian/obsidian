## Open Systems Interconnection Model
-   uses numeric layers to define each part of a network
-   Layer 7 Application
-   Layer 6 Presentation
-   Layer 5 Session
-   Layer 4 Transport
-   Layer 3 Network
-   Layer 2 Data Link
-   Layer 1 Physical

Layer 1 **Physical** - referring to hardware.
Layer 2 **Data Link** - referring to frames and how they travel.
-   any device that uses MAC address is a part of this layer
-   is the only layer with 2 sub layers LLC and MAC

Layer 3 **Network** - uses containers called packets for transporting data from one network to another

Layer 4 **Transport** - the segmentation and reassembly layer.
-   This layer is responsible for chopping data into something that can be transported into a packet then frame.
-   must send packets in correct order for the receiving system to correctly rebuild
-   In segmentation the data is broken into chucks called **segments([[TCP]])** or **datagrams([[UDP]])** and given a sequence number
- datagrams don't get sequence numbers
-   receiving systems can make requests when packets were not received in good order
-   **segments** - Destination port|Source port|Sequence number|Checksum|Flags|Acknowledgement|Data
Layer 5 **Session** - Handles all sessions that connects application to application over the network. ex: printer job to printer system
Layer 6 **Presentation** - converts data for application layer from lower layers and vice versa

  

Layer 7 **Application** - end user side.
