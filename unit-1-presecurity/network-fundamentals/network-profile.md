Network Profile - Desktop-xxxxxx

Q1
 
Windows PowerShell command = ipconfig /all

IPv4-osoite =  192.168.x.xxx
subnet mask = 255.255.255.0
MAC-osoite = xx-xx-xx-xx-xx-xx

Q2

What is the difference in private and public ip-adresses

A private IP address: works only within a local network and is not directly accessible from the internet. 
A public IP address: identifies a network or device on the internet. 
A home router: uses private IP addresses for internal device communication and manages their connection to the internet via a public IP address.


Q3

What is the difference between your IP address and your MAC address?

An IP address identifies a device on a network and can change depending on the network or DHCP settings. 
A MAC address identifies a network interface at OSI Layer 2, it is usually tied to the hardware but can be changed or spoofed. 
IP operates at Layer 3, while MAC operates at Layer 2.

Q4

How many addresses does your subnet contain?

My subnet mask is 255.255.255.0, which is /24 in CIDR notation.

A /24 subnet contains 256 total IP addresses.

Of these, 254 addresses are usable for devices, 
because the first address is reserved as the network address and the last address is reserved as the broadcast address.

My IPv4 address is 192.168.x.xxx/24.

The network address is 192.168.x.0.

The broadcast address is 192.168.x.255.

Answers
Subnet mask: 255.255.255.0
CIDR notation: /24
Total addresses: 256
Usable addresses: 254
Network address: 192.168.x.0
Broadcast address: 192.168.x.255


Q5

What is your default gateway's IP address? Is it on the same subnet as your machine?

My default gateway is 192.168.x.1.

Yes, the default gateway is on the same subnet as my computer. My computer's IPv4 address is 192.168.x.xxx/24, and the gateway is 192.168.x.1. With a /24 subnet, devices with the same first three parts of the IP address are normally on the same local network.

The ping test also confirmed that the gateway is reachable. All 4 packets were received with 0% packet loss, and the average round-trip time was 0 ms.

Default gateway: 192.168.x.1
Same subnet: Yes
Packet loss: 0%
Average ping to gateway: 0 ms

Q6

What was the average round-trip time to your gateway versus to 1.1.1.1?

Gateway average:  0ms
1.1.1.1 average: 32ms

The gateway is usually faster because it is on my local network and is physically much closer to my computer. 
Traffic to 1.1.1.1 has to travel through my router and the internet, so it normally has a higher latency.

Q7: Ping using a domain name

What service made this possible?

The service that makes this possible is DNS (Domain Name System). 
DNS translates human-readable domain names such as example.com into IP addresses.

Q8

What DNS server(s) is your machine configured to use?

My computer is configured to use my local router as a DNS server. 
The IPv4 DNS server is 192.168.x.1, which is the same address as my default gateway.

My computer also has an IPv6 DNS server configured, but I have masked the IPv6 address for privacy.

Q9

I used the nslookup command to resolve domain names into IP addresses. 
I used my local DNS server at 192.168.x.1.

Results

example.com

IPv4: 172.66.147.243
IPv4: 104.20.23.154
IPv6: 2606:4700:10::ac42:93f3
IPv6: 2606:4700:10::6814:179a

facebook.com

IPv4: 157.240.205.35
IPv6: 2a03:2880:f113:81:face:b00c:0:25de

google.com

IPv4 addresses included:
64.233.161.102
64.233.161.139
64.233.161.101
64.233.161.100
64.233.161.138
64.233.161.113

IPv6 addresses were also returned.

The lookups show that some websites return multiple IP addresses. 
Large websites can use multiple IP addresses because they may have many servers, 
load balancing, redundancy and servers in different geographical locations. 
This can improve performance and reliability.

The first DNS lookup timed out because my computer initially tried to use an IPv6 DNS server that did not respond. I then selected my IPv4 DNS server, 192.168.x.1, and the DNS lookups worked successfully.

Q10 - DNS privacy

If someone could monitor my DNS traffic, 
they could potentially see which domain names my computer is trying to access. 
This could reveal information about the websites or online services I use, 
even when the actual website traffic is protected by HTTPS.

Q11 - Tracing the path

The trace reached the destination in 8 hops.

The first hop was:

2001-14bb-672-feba-dfd0-6749-b5a8-5b8a.rev.dnainternet.fi

Q12 - Some hops show * * *

Some hops may show * * * because the router or network device did not respond to the traceroute packets. 
This can happen because of firewall rules, filtering or rate limiting.

It does not necessarily mean that the connection is broken. 
If later hops or the final destination still respond, the connection can be working normally.

Q13 - Listening ports
 
LocalAddress  LocalPort
------------  ---------
::                49676
::1               49673
::                49672
::                49667
::                49666
::                49665
::                49664
::1               34616
::1               34615
::                 7680
::                 5357
::                  445
::                  135
127.0.0.1         50738
127.0.0.1         50735
127.0.0.1         49985
127.0.0.1         49976
127.0.0.1         49786
127.0.0.1         49782
127.0.0.1         49769
0.0.0.0           49676
0.0.0.0           49672
0.0.0.0           49667
0.0.0.0           49666
0.0.0.0           49665
0.0.0.0           49664
127.0.0.1         34616
127.0.0.1         34615
127.0.0.1         27060
0.0.0.0           27036
127.0.0.1          6463
127.0.0.1          6329
127.0.0.1          6328
127.0.0.1          6327
0.0.0.0            5040
192.168.1.107       139
0.0.0.0             135

Q14

Port 135 is commonly used for Windows RPC, while port 445 is used for SMB file and printer sharing.

A localhost-only port is normally accessible only from the same computer. 
A network-facing port can accept connections from other devices, 
so it has a larger security risk.

Q15

My computer has more network-facing services than I expected. 
Ports 135, 139 and 445 were listening on network interfaces, 
so I would investigate them further.




