
<!-- Your monitor number = #$34T# -->


## ⛅ Warm Up for Day 2.
*"Repetition is the mother of all skills"*

<br>

### 🔧 Setup cabling for your Day 1 BUT DO NOT configure any device.

&nbsp;
---
&nbsp;

## Network Automation
*From Shell Scripting to Automation management tools.*

Shell scripting
Output Hello
~~~
@linux
nano hello.sh

///Edit hello.sh
echo "hello world"
///

chmod 500 hello.sh
./hello.sh
~~~


Create Multi users
~~~
@linux
nano add_user.sh

///add_user.sh
adduser m_user1
echo "m_user1:C1sc0123" | chpasswd

adduser m_user2
echo "m_user2:C1sc0123" | chpasswd

adduser m_user3
echo "m_user3:C1sc0123" | chpasswd
///

chmod 500 add_user.sh
./add_user.sh
~~~

### Configuration and Infrastructure Management Tools. (Ansible, Terraform, Puppet, & Chef)

&nbsp;
---
&nbsp;

### Programming for Network Engineers via Python

&nbsp;
---
&nbsp;

## Network Orchestration
Multitenancy - One or more clients can be hosted with the same phyhsical or virtual infrastructure
Scalability - Resources can be added and removed as needed to support current workload and task
Workload Movement - Tasks can be migrated to different physical locations to increase efficiency or reduce cost.
On Demand  - Resources are dedicated only when necessary instead of on a premanent
Resiliency - Tasks and data residing on a failed server can be seamlessly migrated to other phhysical resources.

Traditional Networking - Distributed Management
Software Defined Networking - Centralized Management

### Meraki Access

<br>
<br>

---
&nbsp;

## OSI Model 
Interpret and Explain the OSI Model

### Layer 1:
Speed is measured in bits, while data is measured in Bytes

### Layer 2:
MAC Address: OUI | NIC
Switching "How Switches Forward Packets"

@Linux
arp -a

@Windows
arp -a

@Cisco
arp -a

Broadcast Storm
- STP 802.1d
- - RSTP 802.1w
 
- L3
  - Routing
  - IP Packet Filtering
 
- L4
  - Open Ports
  - FTP
  - HTTP
  - DNS
  - Chargen

- L5
  - RTP
  - TCP/UDP
  - SPAN (Port Mirror)
  
- L6
  - Stegheide
  - Alternate Data Stream

- L7
  - NetFlow


 

OSI vs TCP/IP Model

L7,L6,L5 = Application Layer
L4 = Transport Layer
L3 = Network Layer
L2, L1 = Data Link Layer


---

3. Port Security

4. HSRP 

5. Routing

Static Routing
Default Routing
EIGRP
OSPF
BGP

IGP
Link-State : OSPF (110) ISIS (115)

Distance Vector : RIP (120) , EIGRP (90)

EGP
BGP (WAN)


Configure

@EDGE OSPF AREA 0
OSPF AREA M

@CoreBABA 
OSPF AREA M
EIGRP 1

@CUCM
OSPF AREA M

EXBGP 20
INTBGP 200


---

6. ACL

7. NAT

8. IAM ACCESS MANAGEMENT Crypto Keys

9. RADIUS

10. STP


  
