VLANS Part 1 explain in detail 
    what is lan 
        a lan is a signle broadcast domain including all devices in theat brodcast doamin 
            a broadcast domain is the group of devices which will receive a broadcast frame destination MAC FFFF.FFFF.FFFF send by any one of the members


    what is VLan 
        are configured on switches on per interfaces basis
        logically speearate end hosts at layer 2 
        swichts do not fordward traffic directly between hosts in different VLans 
        switch will not fordward traffic between VLANs including broadcast unknown unicast traffic 

    Vlan COnfiguration
        sh vlan br

        an access port is a switch port which belongs to a single VLan and usually connects to end hosts like PCs
        switchport which carry multiple VLANS are called trunk portds

        int range g1/0-3
        int g1/0
        switchport mode access 
        switchport access vlan no

        vlan 10 [to create vlan ]
        name vlan_name

    Vlan part 1 lab 