Switch Interfaces 

    sh ip int br 
    Interface   IP address ok? method status protocol

    sh intercafes status
    Port    Name    Status  Vlan    Duplex  speed   type


    configuring interface speed and duplex

    conf t 
    int f0/1
    speed ?
    spped 100
    duplex ?
    duplex full
    decription ##to R1##


    interface range f0/5 -12  can also do  int range f0/5-6 , f0/9-12
    descirption not in use
    shutdown 


    Full and Half duplex
        half duplex device cannot send and receive data at the same time if it is receiving frame it must wait before sending 
        full duplex device can send and receive data at teh same time doesnot have to wait 


    Lan hubs 1 collision domain explain this 


    CSMA/CD
        carrier sense multiple access with collision detection 
            before sending frames devices listen to the collision domain until thye detect that other devices are not sending 
            if a collision does occur the device sends a jamming signal to inform the other devices that a collision happened 
            each device will wait a random period of time before sending frames again 
            the process repats


    Collision domains exaplin with respect to switch and hubs


    SPeed Duplex Autonegotiation
        interfaces that can runn at different speed have default seetiing of speed auto and duplex auto 
        interfaces advertise their capabilities to the neighbouring devices and they negotiate the best speed and duplex setting thye are both capable of 
         

         what if auto negotiation is disabled on the device connected to the switch
         speed the weitch will try to sense the speed that the other device is operating at if fails to sense will use the slowest supported 
         duplex if speed is 10 or 100 use half duplex 
         if speed is 1000 or grater use full duplex 

    Interfaces errors 
        show interfaces 

        runts frames that are smaller then the minimum frame size 64 bytes
        giants frames that are larger then the maximum frame size 1518 bytes 
        CRC frame that failed the CRC check in the ethernet FCS trailer
        frame 
        inourt error 
        output errors 

Configuring interfaces- Lab  