IPv4 Header

        | Field |
        |---|
        | Version |
        | Header Length |
        | Type of Service (TOS) |
        | Total Length |
        | Identification |
        | Flags |
        | Fragment Offset |
        | TTL |
        | Protocol |
        | Header Checksum |
        | Source Address |
        | Destination Address |
        | Options |
        | Data |




        version     identifies the version of IP used only 2 ip IpV4 and Ipv6   4 bits 
        Header Length =indicated the total length of the header as the final field of header options is variable in length 
                specified the lenght of header in 4 byte increments min value is 5 =20 bytes max value 15 15x4=60 bytes

        TOS 
        DSCP Differentiated services code point length 6 bits 
        used for Qos 
        usewd to priority delay sensitive data 
        ECN Explicit Congestion Notification 2 bits
        provides end to end notification of netowrk congestion without dropping packet

        Total Length Field  !6 bits
        indicated the total length of the packet l3 header +l4 segment 
        measured in bytes  min value 20 max value 65535

        Identification length 16 bits
        if packet is gragmanted due to being too large this field us use to identify wihch packet the fragement belongs to 
        all fragments of the same value in this field 
        packet are fragmented if larger than MTU Maximum transmission unit is usally 1500

        Flags 3 bits
        used to control identify fragmeents
        bit 0 reserved always set to 0
        bit 1 dont fragment DF bit used to indicate a packet that should not be fragmeneted 
        but 2 more fragments MF bit set to 1 if there are more fragments in the packet set to 0 for the last fragments 

        Fragement offest 13 bits
        used to indicate the posotion of the fragmeent with the original unfragmetted packet 

        TTL 8 bits
        a router will drop a packet with a ttl of 0 
        used to prevent infinited loops 
        originally designed to indicated the packet maximum lifetime in seconds 
        in pratice indicated a hop count 

        Protocol 8 bits
        indicated tthe protocol of the encapsulated l4PDU  
        value of 6 TCP
        value of 17 UDP
        value of 1 ICMP
        value of 89 OSPF Dynamic routing protocol 

        Headercheck sum 16 bits
        a calculated checksum used to check for errors in the Ipv4 header

        Source IP destination IP length 32 bit each 

        optional : 0-320 bits
        rarely used 
        if HL field is greated then 5 it meanins that option are present 

        Wireshark Packet Capture 



Routing Fundamentals   (part 1)
    waht is routing 
        the process theat th router use to determine the path theat ip packets take over a network to reach their destination 
                routing table explain 

        Dynamic routing     share oruting info automatically and build their routing table
        static routing  a admin manually configures routes on the router 
    
        a router tells the trouter ro send a packet to destination x and you shoul dsne dthe packet to next hop YU
                                                 
        Two types of route automatically added to routing tablke 
            show ip route to view the routing table

            when you configure an IP address on aninterface and ewnable it with no shutdown 2 touter per interface will acutomaitcally be addded to routing tbale
            a connected route 
            a local route
                • A connected route is a route to the network the interface is connected to.
                • R1 G0/2 IP = 192.168.1.1/24
                • Network Address = 192.168.1.0/24
                • It provides a route to all hosts in that network (ie. 192.168.1.10, 192.168.1.100, 192.168.1.232, etc.)
                • R1 knows: “If I need to send a packet to any host in the 192.168.1.0/24 network, I should send it out of G0/2”.

                • A local route is a route to the exact IP address configured on the interface.
                • A /32 netmask is used to specify the exact IP address of the interface.
                 → /32 means all 32 bits are “fixed”, they can’t change.
                • Even though R1’s G0/2 is configured as 192.168.1.1/24, the connected route is to 192.168.1.1/32.
                • R1 knows: “If I receive a packet destined for this IP address, the message is for me”.

        a route matches a packet destination if the packets destination IP address is part of the netwrok specified in the route 

    Route Slection
        a packet destined for 192.1638.1.1 is matched by both routes
            192.168.1.0/24
            192.168.1.1/32
        which route will R! used for a packet destined for 192.168.1.1
            it will choose the most specific matching route 


Static Routing (part 2 )
    Routing Packets: default Gateway
        end host like pc1 and pc4 can send packets directly to destinations in their connected netowrk
        to send packets to destination outside of thier local network they must send the packets to their default gateway
        default gateway configuraion is also called default route

    Static Route Configuration
        each router in the path needds tow routes   : a route to 192.168.1.0/24 and a route to 192.168.4.0/24

        static route configuration 
            ip route ip address netmask next hop 
        
        static route configuration with exit interface 
            ip route ip address netmask exit interface 
        
        static route configuration with exit interace and next hop
            ip route inaddress netmask exitinterface next hop
        

    Default Route 
        a default route is a route to 0.0.0.0/0
            it is the leaast specific route possible inclueds every possible destination IP address 



Configuring Static ROutes Lab


TroubleShooting Static Routes Lab