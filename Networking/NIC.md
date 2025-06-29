## Network Interface Card

-   the piece of hardware that connect a pc to the network.
-   Although its hardware that connects to the network it's considered in Layer 2 Data Link
-   All NIC come burned into a chip their [[MAC address]].
-   No two NICs ever share the same MAC address EVER.
-   NICs were originally used to transmit data, those ones and zeros, through pluses of electricity were as now and days data can be received and transmitted through radio and light
-   Is also responsible for wrapping the data into frames before transmitting and vice versa for receiving
-   Doesn't pay attention to what the actual is the data that a [frame](Frames) carries
-   When the NIC needs to send data to another NIC and it's never made contact before will send a broadcast on the network using FF-FF-FF-FF-FF-FF as a MAC address(known as the broadcast address)
-   The broadcast address is contained within a frame which all NICs on the network will process then the device with the requested MAC address sends a return signal confirming that that address is in fact on the network
-   there are two aspects of a NIC LLC(Logical Link Control) and MAC(Media Access Control)
-   LLC is in charge with communicating with the system's OS through a driver as well as manage network protocols and provides flow control
-   MAC is in charge of creating the frames and addressing them with sender and recipient parts of a frame as well as adds and checks the [[FCS]] then sends down the cable