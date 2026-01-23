#nat 
***Network Address Translation(NAT)*** 

1. It's a service that operates on a router or edge platform to connect private networks to public networks like the internet.
2. NAT translates private IP addresses in an internal network to a public IP address before packets are sent to an external network. 
3. To access the Internet, one public IP address is needed, but we can use a private IP address in our private network.    
4. The idea of NAT is to allow multiple devices to access the Internet through a single public address. To achieve this, the translation of a private IP address to a public IP address is required.    
5. NAT generally operates on a router or firewall.

***Types of NAT*** IPv4

1. Static NAT
2. Dynamic NAT
3. Port Address Translation (PAT)

*Static NAT*
	In a organization we map the each device with the separate public IP address,
*Dynamic NAT*
	There are the some number of public IP address will be register in a pool the first come user will access the IP,(first come First serve)
	e.g...( if there are 50ip have registered, the first 50 members to access the internet, the 51th member cant able to access it)
*PAT*
	 The every device have it own private IP and all of the IP will be map to the PORTS with the same Public IP address.
	 ![[Pasted image 20240611180151.png]]
**Public IP address**
	**IPv4**
	1. 32bit, with 4number of separated periods(190.15.45.23), 
	2. The each separation is known as octa, the each octa number is between (0-255)
	3. so it can produce 4billion unique IP address are registered in the internet, the public IP address are limited only.
Private 
	The private IP address is not Publicly registered, so we cant able to access the internet.
	it only used internally (in a organization)
NAT IPv6
	1. It allows 128 bit address allowing.
	2. It use both alphabets and numerical in the IP address.
	e.g..( 76DC:4F59:34CF:71CD:9DC6:86CD:45D6:67A2 )
	**IPv6**
	The IPv6 can produce a public IP address for each device in the world, which it have the amount of 340 undecillion IP address. 
**Source Network Address Translation (SNAT) :**  
	1. SNAT, as name suggests, is a technique that translates source IP address generally when connecting from private IP address to public IP address.
	2. It maps source client IP address in a request to a translation defined on BIG-IP device. It is most common form of NAT that is used when internal host needs to initiate session to an external host or public host.
	![[Pasted image 20240711185111.png]]
**Destination Network Address Translation (DNAT) :**  
	1. DNAT, as name suggests, is a technique that translates destination IP address generally when connecting from public IP address to private IP address. 
	2. It is generally used to redirect packets destined for specific IP address or specific port on IP address, on one host simply to a different address mostly on different host.
	![[Pasted image 20240711185200.png]]
	![[Pasted image 20240711185311.png]]