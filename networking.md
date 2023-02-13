## networking
--------------
1. ### ip address**:-
------------------
* unique number to identify a device on the network
* IP Address = Network Id + Host Id
* execute ipconfig we can see network detailes of the system 
  - ipaddress:  192.168.0.102
  - subnetmask:  255.255.255.0
  - defualt gatway(router):  192.168.0.1


2. ### Network interface**:
-------------------------
* This device enables network connectivity to the system
* The number of network interfaces can be multiple


3. ### Networking Priciple**:
---------------------------- 
* A device in a network can communicate to any other device in the same network


4. ### subnetmask:
------------------
* A subnet mask is a 32-bit number used in IP networking to divide an IP address into two parts: the network portion and the host portion. The subnet mask is used in conjunction with the IP address to determine which portion of the address represents the network and which portion represents the host.
* Subnet mask also helps in identifying size of network

5. ### ipv4
------------
* Lets look at IPV4. This is a 32 bit number.
* IP is broken into 4 octets x.x.x.x
* Range is 0.0.0.0 to 255.255.255.255

6. ### Router
--------------
* Router is a device which forwards packets from one network to another.
* Router is shown as default gateway in ipconfig

7. ### DNS (Domain Name System.)
--------------------------------
* Network packets dont understand names.
* Network interfaces tries to resolve the name by its ip address and generally this information (name to ip) is present in DNS servers

8. ### network types
---------------------
* There are two types of networks
 - **Public Network**:
   * This network is accessible over internet
   * There are two types of networks
Public Network:
This network is accessible over internet

 - **private network**
    * This the network for intranet (internal) usage
    * Private networks have ip address ranges
    ```
       10.0.0.0 to 10.255.255.255 
       172.16.0.0 to 172.31.255.255
       192.168.0.0 to 192.168.255.255
   ```

9. ### possible subnet masks that can be used to create a network**
--------------------------------------------------

```
255.255.255.0
255.255.0.0
255.0.0.0
````
10. ## Designing Networks**
----------------------------
* #### Create a network which can have 200 devices connected to it

```
private network ranges
10.0.0.0 to 10.255.255.255
172.16.0.0 to 172.31.255.255
192.168.0.0 to 192.168.255.255

Subnet Masks
    255.255.255.0
    255.255.0.0
    255.0.0.0

SM => 255.255.255.0 => 1 (Variable) => 8 bits => 2^8 =>256
   => 255.255.0.0 => 2 octets => 16 bits =>2^16 => 65536
   => 255.0.0.0 => 3 Octects => 24 bits => 2^24 => 16777216

Size => 200


Possibilities
IP = 192.168.0.x
SM = 255.255.255.0

IP = 10.0.0.x
SM = 255.255.255.0

IP = 172.16.0.x
SM = 255.255.255.0

IP = 10.100.101.x
SM = 255.255.255.0

IP = 172.18.10.x
SM = 255.255.255.0
````

11. ### IP Addressing**
---------------------
* There are two ways of IP Addressing
  * classfull nerworking
  * classless networking

  ## Classful networking:
  --------------------------

* A Class A network has a network portion of 8 bits and a host portion of 24 bits. An example of a Class A IP address is 10.0.0.0, where the first 8 bits represent the network portion and the remaining 24 bits represent the host portion.

* A Class B network has a network portion of 16 bits and a host portion of 16 bits. An example of a Class B IP address is 172.16.0.0, where the first 16 bits represent the network portion and the remaining 16 bits represent the host portion.

* A Class C network has a network portion of 24 bits and a host portion of 8 bits. An example of a Class C IP address is 192.168.1.0, where the first 24 bits represent the network portion and the remaining 8 bits represent the host portion.

# Classless networking (CIDR):
--------------------------------

* A /24 CIDR block uses 24 bits for the network portion and 8 bits for the host portion. An example of a /24 CIDR block IP address is 192.168.1.0/24, where the first 24 bits represent the network portion and the remaining 8 bits represent the host portion.

* A /16 CIDR block uses 16 bits for the network portion and 16 bits for the host portion. An example of a /16 CIDR block IP address is 10.0.0.0/16, where the first 16 bits represent the network portion and the remaining 16 bits represent the host portion.

* A /8 CIDR block uses 8 bits for the network portion and 24 bits for the host portion. An example of a /8 CIDR block IP address is 172.16.0.0/8, where the first 8 bits represent the network portion and the remaining 24 bits represent the host portion.

* In classful networking, the size of the network portion is fixed for each class, making the allocation of IP addresses inflexible. In classless networking, the size of the network portion can be defined arbitrarily, making the allocation of IP addresses more flexible and efficient.


### Classless Interdomain routing (CIDR):
------------------------------------------

* CIDR Notation is a way of ip addressing where we write range in the form of x.x.x.x/f

```
192.168.0.0/24

fixed = 24
variable = 32-24 = 8

ip: 192.168.0.xxxxxxxx
SM: 11111111.11111111.11111111.00000000

range = 192.168.0.0 to 192.168.0.255

192.168.10.0/23

fixed = 23
variable = 9

IP:           192.168.0000101x.xxxxxxxx
SM= 11111111.11111111.11111110.00000000

range: 192.168.10.0 - 192.168.11.255

10.128.0.0/12

fixed = 12
variable = 20

IP:       10.1000xxxx.xxxxxxxx.xxxxxxxx     
SM= 11111111.11110000.00000000.00000000

range: 10.128.0.0 to 10.143.255.255

192.168.192.0/21

fixed = 21
variable = 11

IP:           192.168.11000xxx.xxxxxxxx
SM= 11111111.11111111.11111000.00000000

range: 192.168.192.0 to 192.168.199.255

172.16.0.0/12

fixed = 12
variable = 20

IP:      172.0001xxxx.xxxxxxxx.xxxxxxxx      
SM= 11111111.11110000.00000000.00000000

range: 172.16.0.0 to 172.31.255.255


00010000 => 16
00011111 => 31
```

12. ## Design a network with 2 subnets of 200 devices each
-----------------------------------------------------
* Subnets = 2
* Subnet size = 200
* Network = 2 * 200
* Solution

```
private:

192.168.0.0/16
10.0.0.0/8
172.16.0.0/12

Network

Size ~= 400

2^v  ~= 400

variable = 9
fixed = 32-9 = 23

CIDR = 172.16.0.0/23
SM:    11111111.11111111.11111110.00000000

Subnet: 

Size ~= 200

2^v ~= 200
variable =8
fixed = 24


SM: 11111111.11111111.11111111.00000000

Network SM: 11111111.11111111.11111110.00000000
Subnet SM:  11111111.11111111.11111111.00000000
------------------------------------------------
                       172.16.0000000y.xxxxxxxx
             subnet 1: 172.16.00000000.xxxxxxxx  = 172.16.0.0/24
             subnet 2: 172.16.00000001.xxxxxxxx  = 172.16.1.0/24
             Network: 172.16.0.0/23
```

13. ## Design a network with 4 subnets of 100 devices each
------------------------------------------------------
* subnets = 4
* each subnet = 100
* network = 400
* private:
```
192.168.0.0/16
10.0.0.0/8
172.16.0.0/12

Network

size = 400

2^v ~= 400
v= 9
fixed = 23

network: 192.168.0.0/23
SM: 11111111.11111111.11111110.00000000

Subnet:
size = 100

2^v ~= 100
v=7
fixed = 25

Network SM: 11111111.11111111.11111110.00000000
Subnet  SM: 11111111.11111111.11111111.10000000
-------------------------------------------------
                                     y.y
            Subnet 1: 192.168.00000000.0xxxxxxx = 192.168.0.0/25
            Subnet 2: 192.168.00000000.1xxxxxxx = 192.168.0.128/25
            Subnet 3: 192.168.00000001.0xxxxxxx = 192.168.1.0/25
            Subnet 4: 192.168.00000001.1xxxxxxx = 192.168.1.128/25
Design a Network with 4 subnets size 1000
subnets = 4
subnet size = 1000
network size = 4000
Solution
private:

192.168.0.0/16
10.0.0.0/8
172.16.0.0/12

Network

size = 4000

2^v ~= 4000
v= 12
fixed = 20

ip:             10.0.0.0/20
SM: 11111111.11111111.11110000.00000000

Subnet:
size = 1000

2^v ~= 1000
v=10
fixed 

= 22

Network SM: 11111111.11111111.11110000.00000000
Subnet  SM: 11111111.11111111.11111100.00000000
-------------------------------------------------
                                  yy
               Subnet 1: 10.0.000000xx.xxxxxxxx => 10.0.0.0/22
               Subnet 2: 10.0.000001xx.xxxxxxxx => 10.0.4.0/22
               Subnet 3: 10.0.000010xx.xxxxxxxx => 10.0.8.0/22
               Subnet 4: 10.0.000011xx.xxxxxxxx => 10.0.12.0/22

```


14. ### rules

* When we create any network we cannot use 2 ip addresses
   *  when all zeros in variable => Network id
   * when all ones in variable => broadcast id
* Forumla in general networks with v as variables bits

```
size = 2^v - 2
note:
in AWS this formual would be 2^v - 5 
```
* When we create network rules to forward the network packets or to block the network packets in firewalls we generally use cidr ranges. In these cidr ranges are used to figure out network id.
```
192.168.0.0/24 => Any ip with pattern 192.168.0.x
10.10.0.0/16 => Any ip with pattern 10.10.x.x
0.0.0.0/0 => Any ip address x.x.x.x
100.101.102.103/32 => Specific ip 100.101.102.103
```

15. ## AWS Global Infrastructure
--------------------------------
**Region**
--------
* Geographical location identified by AWS to build Datacenters
* This is collection of Availability Zones
* Every Region has a code `<continent>-<direction>-<number>`
* Examples: mumbai = ap-south-1, hyderabad ap-south-2
## Availability Zone:
-----------------
* This is a site within a Region
* In each Region you will multiple AZ’s
* Distance between AZ’s in a region will be around 30-60 kms
* Every AZ will have names `<region>[a-z]`
* Mumbai AZ’s ap-south-1a, ap-south-1b...
## Local Zone
--------------
* This is a Site built in different parts of the world
* This local zone can be added to some marked Regions
* Local Zone has parent region
## Edge Location:
This acts as Point of presence locations
## Wavelength Zone:
This was designed for 5G networks

16. ## AWS Networking Major Components
--------------------------------------
* VPC
* Subnet
* Internet Gateway
* Route Table
* Network Interface
* Elastic IP
* Security Group
* Network ACL

VPC (Virtual Private Cloud)
----------------------------

* is a virtual network which we can create in AWS
* belongs to a region
* We can create the private network of size required by using CIDR
* In every region AWS ensures you have a default VPC.

Subnet
------
* AWS Subnet is subnet of VPC
* belongs to AZ
* We can create resources and connect to subnet
* size is expressed in CIDR(classless inter domaine routing)


##Internet Gateway
-----------------
* This gives dual connectivity i.e. vpc can access internet and internet can access resources in vpc using public ip addressing
* If you want only one way connectivity then AWS has Egress only Internet Gateway

Route Table
-----------
* This will act as a Router
* Router is a device which forwards packets from one network to another
* When we create a vpc, aws will create a default route table
* By default AWS will allow connections between all the subnets

creating vpc
------------
* navigate to vpc in aws services
* create vpc
* give name to vps
* give ipv4 block
* give ipv4 range basees on our requirement
* after create genarate vpc id
add subnets to vpc
-------------------
* navigate to subnets then create subnet
* select vpc
* select availabilty zone
* give ipv4 cidr block
* we cant give tags(we can mnetion which environaments related this )
* for one more subnet we can go with add new subnet
* create subnet

**note**:

* If we want to view only our vpc resources
* navigate to filter vpc and select that particular vpc we can see only  that vpc related subnets.


17. # Create a vpc for ntier
------------------------

* aws ---(cloud)
* vpc--->( which is crerated region leavel )
* vps ---> (have subnets, created in zone leval)
* by using subnets we can create resources
ex: devsubnet haves dev envionament resources...like that.
* for internet acsess to vpc we create *internet gateway*
  * attach to vpc
  ---------------
  * in ingw go to action
  * select vpc
  *  then attach ingw
* With every vpc created we get a default
  * security group
  * network acl(Access Control List)
  * routetable
  -------------
* Now enable route between route table and internet gateway for public acsess

* Navigate to route table then routes
* edit routs --> give destination(cidir range) to target (internet gateway)


  ( default:-->In this vpc we have a default route table
 All the internal communications with in vpc is allowed)

 ### public subnet:
 ------------------
 * Public Subnet is associated with a route table which has route to internet gateway




 ### private subnet
 ------------------

 * Private subnet is associated with a route table which has no route to internet gateway


**note:**
 * we conect a instence which is created in publick route table connected public subnet.(becouse publicrt have a route to ingw)
 * but it is not possible with praivate subnet created ec2 instence
 (becouse praivate rt don't have a route to ingw)


 * and it is not possible with conecting pb instence to private instence by coping .pemkey in to public instence (cd to penkey locketed folder and login with sftp do get .pem key)
 * now loging with using private ip 
 * For all the internal communications in vpc use private ips not public ip.
 * we can login into private ec2 but we dont have internet.
* it is possibe with **NATGATEWAY**




18. ## NAT gate way
--------------------

* In AWS, to provide internet access to private subnets, we need to use NAT.
* There are two ways of using NAT in AWS
   * **NAT instance**:
     - An ec2 instance with NAT server in it
   * **NAT Gateway**:
     - NAT as a service by AWS
* NAT should be present in public subnet and router to the private subnets should have a route to the NAT and NAT should have a public ip (Elastic IP)


### **creating nat gate way**:
--------------------------
* navigate nat gate ways
* give name
* must give a public subnet
* ellocate a elastic ip

**next:**---> 
 * next add a route to NAT gateway form private subnet.

 ## Egress only Internet Gateway
 ------------------------------
 *  If all your subnets are private and if they need internet access, then we can use egress-only internet gateway


 ## Multiple VPCs
 ----------------
 * Consider a scenario where we create two vpcs in two regions
 * The only way for establishing connection is using public ip address
 * To solve these kind of issues we have vpn **(Virtual Private Networks)** to be very specific Site to Site VPN
 ## peering connection
 --------------------
 * AWS has peering connection facility to connect vpcs
 * Rules for connecting are there should not be overlapping cidr ranges
 
 # Creating a peering connection from any vpc to other:
 --------------------------------------------------------

 * navigate to peering connections
 * give name
 * Select a local VPC to peer with
 * Select another VPC to peer with (my acount or Another acount)
 * select region and give vpc id
 * create peering connection.
  ### in another region

  * Accept the peering request
  * go to peering connection 
  * go to action 
  * acsept the request.

  ### in both regions
  * Now modify route tables to forward the request to pco when you have access other vpc’s cidr rnage

  # Security Groups and Network ACLs:
  -----------------------------------

  * Security groups and Network ACLs can filter the network traffic.
  * Security group operates at "network interface level", where as Network ACL operates at "subnet level"
  * Network ACL
    * when a vpc is create a default NACL will be created
    * the default nacl rules allow all incoming and outgoing traffic.
  * Security Group:
    * The default rule is deny all
    * Depending on what we need to allow we create rules



    # Network ACL(acsess control list)
    ----------------------------------

    * The following fields exist for every rule
      * rule number one: lower the number higher the priority
      * protocall
      * port number
      * Source/Destination
      * allow/denny
  * whenever a packet is recieved the rules in inbound are evaluated in the order of priority
  * whenever a packet is sent the rules in outbound are evaluated in the order of priority

  ## Create a vpc as shown below

* Ensure web subnet allows incoming
   * within vpc on any traffic
   * external sources for only 22, 80, 443
* Ensure db and app subnets allow incoming within vpc on any traffic no external communication is allowed

```
web 

100  TCP  22  0.0.0.0/0  Allow
110  TCP  80  0.0.0.0/0  Allow
120  TCP  443  0.0.0.0/0  Allow
130  All traffic  *  192.168.0.0/16  Allow
*    All traffic *      Deny

outbound

100  All traffic  *  0.0.0.0/0  Allow
*    All traffic *      Deny


db & app => NACL

100  All traffic  *  192.168.0.0/16  Allow
*    All traffic *      Deny

app
100  All traffic  *  0.0.0.0/0  Allow
*    All traffic *      Deny



```



## creating NACL
-----------------
* navigate networking NACL
* give a name
* select vpc
* create network acl
   - next stpes:--->
* give inbound and out bound rules
* do subnets association to NACL

# aws-networking-workshops
---------------------------
* for [referhere](https://directdevops.blog/2023/02/12/aws-classroomnotes-12-feb-2023/) for 12/feb/2023 part-1 classnotes
* for [referhere](https://directdevops.blog/2023/02/12/aws-classroomnotes-12-feb-2023-2/) for 12/feb/2023  part-2 classnotes





 



 


