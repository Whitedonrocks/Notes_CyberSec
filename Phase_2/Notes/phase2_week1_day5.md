IPV4 Addressing part 1

    nwtowrk layer
        provides conneftivity between end host on different netowrks 
        provides logical addressing ip addrresses 
        provides path selection between source and destionation 
        router operates at layer 3 

    Routing 


    IPv4 header 
        Version  header length TOS Total length
        Identification         Flag Fragment offset
        TTL Protocol            headershecksum
                    Source Add
                    Dest Add
                    Options 
                    Data



    Ip address are 32 bits or 4 bytes
     192.168.1.254
     8.8.8.8 bits 
     11000000 10101000 00000001 11111110
     written in dotted decimals 
     8 bit groups called octets 


     Conversion 
     Binary to Decimal -> 1 vako ma value add garni 
     Decimal to binary ->try subtracting from aagadi 


     /24 represents that the first 24 bits of the address represent host bits 



     IPV4 Address Classs 
        Class   First OCtet     First octet numeric range                               Prefix Length
        A       0xxxxxxxx           0-126    127=local host                                  /8
        B       10xxxxxx            128-191                                                  /16
        C       110xxxxx            192-223                                                     /24
        D       1110xxxx            224-239         multicast addresss
        E       1111xxxx            240-255         resewrved (experminatal)


    Loopback addresses
        address range 127.0.0.0-127.255.255.255
        usewd to test the network stack think OSI,TCp/IP model on the local device 


        first address of nwtowrk= network address           host portion of the adress is all 0's       cannot be assigned to a host 
        last address of network = broadcast address         host portino of the address is all 1's      cannot be assigned to a host 

    Netmask
        Class A: /8     255.0.0.0
        Class B: /16    255.255.0.0
        Class C: /24    255.255.255.0

    