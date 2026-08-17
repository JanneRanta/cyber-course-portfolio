# Network Profile — Desktop-xxxxxx

## Identity

- IPv4 address: 192.168.x.xxx
- Subnet mask / CIDR: 255.255.255.0 /24
- MAC address: xx-xx-xx-xx-xx-xx
- Network address: 192.168.x.0
- Broadcast address: 192.168.x.255

## Gateway and reachability

- Default gateway: 192.168.x.1
- Ping to gateway (avg): 0 ms
- Ping to 1.1.1.1 (avg): 34 ms

The gateway is faster because it is on my local network, while 1.1.1.1 is reached through the internet.

## DNS

- Configured DNS server(s): 192.168.x.1 and an IPv6 DNS server (masked)
- example.com resolves to:
  - IPv4: 172.66.147.243
  - IPv4: 104.20.23.154
  - IPv6: 2606:4700:10::ac42:93f3
  - IPv6: 2606:4700:10::6814:179a

Multiple IP addresses can be used for load balancing, redundancy and better performance.

## Path to the internet

- Hops to example.com: 8
- First hop: 2001-14bb-672-feba-dfd0-6749-b5a8-5b8a.rev.dnainternet.fi

The traceroute used IPv6. Some hops did not respond, but this does not necessarily mean that the connection was broken.

## Listening ports

| Port | Protocol | Interface (localhost / all) | Common use |
|------|----------|------------------------------|------------|
| 135 | TCP | All interfaces | Windows RPC |
| 139 | TCP | 192.168.x.xxx | NetBIOS / Windows file sharing |
| 445 | TCP | All interfaces | SMB file and printer sharing |
| 5040 | TCP | All interfaces | Windows/application service |
| 5357 | TCP | All interfaces | Windows network discovery |
| 7680 | TCP | All interfaces | Windows Delivery Optimization |
| 27036 | TCP | All interfaces | Application/game service |
| 49664 | TCP | All interfaces | Windows dynamic RPC |
| 49665 | TCP | All interfaces | Windows dynamic RPC |
| 49666 | TCP | All interfaces | Windows dynamic RPC |
| 49667 | TCP | All interfaces | Windows dynamic RPC |
| 49672 | TCP | All interfaces | Windows dynamic RPC |
| 49676 | TCP | All interfaces | Windows dynamic RPC |
| 6327 | TCP | Localhost only | Local application |
| 6328 | TCP | Localhost only | Local application |
| 6329 | TCP | Localhost only | Local application |
| 6463 | TCP | Localhost only | Local application |
| 34615 | TCP | Localhost only | Local application |
| 34616 | TCP | Localhost only | Local application |
| 49769 | TCP | Localhost only | Local application |
| 49782 | TCP | Localhost only | Local application |
| 49786 | TCP | Localhost only | Local application |
| 49976 | TCP | Localhost only | Local application |
| 49985 | TCP | Localhost only | Local application |
| 50735 | TCP | Localhost only | Local application |
| 50738 | TCP | Localhost only | Local application |

## Reflection

What surprised me most was how many network ports were listening on my computer. I expected only a few services, but the scan showed several network-facing ports as well as many localhost-only ports.

The ports I would investigate first are 135, 139 and 445 because they are related to Windows networking services such as RPC, NetBIOS and SMB. These services can increase the attack surface if they are unnecessarily accessible from the network.

The command I think I will use most often is `ipconfig /all` because it quickly shows important network information such as my IP address, subnet mask, default gateway and DNS servers. I also found `tracert` useful because it shows the path traffic takes to a destination.

This exercise helped me understand that a computer can have many network services running even when I am not actively using them. It also showed me why it is important to know which ports are accessible from the network and which are limited to localhost.
