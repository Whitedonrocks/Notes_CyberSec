Subnetting Part 1 please explain in details all this topics 
    IPv4 Address CLasses 
        IANA INternet assigned numbers authority assigns IPV4 addresses networks to companies based on their size 
    Point to point network 


    CIDR Classless inter domain routing 
        with CIDR the req of 
            class A=/8
            class B= /16
            class C =/24
                were removed 
        this allowed larger networks to be split into smaller netwroks allwing greater efficiency 
        these smaller netowrks are called subnetworks or subnets
        | Dotted Decimal | CIDR Notation |Total Adderss|No of Subnets|
            |---|---|----|----|
            | 255.255.255.128 | /25 |128|2|
            | 255.255.255.192 | /26 |64|4|
            | 255.255.255.224 | /27 |32|8|
            | 255.255.255.240 | /28 |16|16|
            | 255.255.255.248 | /29 |8|32|
            | 255.255.255.252 | /30 |4|64|
            | 255.255.255.254 | /31 |2|128|
            | 255.255.255.255 | /32 |1|256|
             

Subnetting Part 2
        2^x number of subnets
            x=number of borrowed bits


    SUbnetting Class B network 
        give full examples  live the class c one above 