A tunnel is an encapsulation of data from a network protocol to another one.
But first, I have to define encapsulation and OSI layers

// Encapsulation schema - page 2

Encapsulation is about grouping raw data in a "pack" of routines that makes them readable.
This principle is usually about hiding those raw data to not let the user skip the interface held in place for it.

OSI model or OSI layers (see shema)

Tunnels can be cyphered or not.
HTTP tunnel is a specific use-case were you use a not-allowed connection (SSH for example) go through a HTTP protocol (almost) always allowed.

Several kind of protocols for tunnels existed:

// Protocol Evolution shema - page 3

OSI layer 2 (Link Layer)
PPTP (Point-to-Point Tunneling Protocol) -> Protocol carrying PPP frame; developped by Microsoft, 3COM, Ascend, US Robotics & ECI Telematics
L2F (Layer Two Forwarding) -> Same as PPTP but developped by Cisco Systems, Nortel & Shiva
L2TP (Layer Two Tunneling Protocol) -> Merging of PPTP & L2F.

OSI Layer 3 (Network Layer)
IPsec -> Carrying cyphered (protected) data over IP network
L2TP/IPsec -> Merge of 2 protocols that makes PPP go over L2TP

SSL/TLS: It secure web surfing using HTTPS, make a web browser to be used as a VPN client (example: OpenVPN)

// IPsec - page 4

How IPsec is using data transfer:
Protocol 50 [ ESP - Encapsulating Security Payload ]: Gives privacy by using cryptography
Protocol 51 [ AH - Authentification Header ]: For Integrity & Authentification. Make unique packets to be marked

2 modes: Transport mode (Host to Host) & Tunnel mode:

In Tunnel Mode, the whole IP packet is cyphered &/or authenticated. Then packet is encapsulated inside a new IP packet with a new IP header.
This mode supports NAT (Network Address Translation: used for IP routing inside a network) go-through with ESP protocol.
Tunnel mode is used to create Virtual Private Network (VPN) to communicate network-to-network, Host to Network (distant access from a user) or host to host (private messenger).

What is SSH?
Let's begin with Telnet:
It was a simple, basic protocol created in the 80's & used to share simple messages between two machines.
But this protocol was too simple, datas were sent "in clear" without any cypher.
Since we can't completely block someone to get datas from internet, a good way to dodge this is to make the client & the server to communicate in a secure manner.


// SSH page 5

SSH encryption:

// SSH page 6

Symetrical & asymetrical (Public/Private keys) + varied cypher algorithm (AES, Blowfish, 3DES, IDEA)
First, asymetrical cypher is used to make a link, then symetrical cypher is used for the whole communication (lighter to use)

You use it for:
- A distant secure shell (Security System Administration)
- Port Forwarding / Tunneling (To go through a firewall)
- X11 (A shell for Unix based system) or VNC (Virtual Network Computing) session

// References page 7

