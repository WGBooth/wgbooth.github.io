---
title: "Packet Scavenger Hunt"
last_modified_at: 2026-10-01T10:09:06-05:00
categories:
  - Blog
tags:
  - networking
  - packet analysis
  - wireshark
---

Using Wireshark, I collected and analyzed network packets.

## Highlights

- Captured and analyzed network packets using Wireshark
- TCP handshake discussion with an analogy

## The Long Story

In my virtual lab environment, I captured network packets to see how data travels between devices on a network. I am using Wireshark to monitor traffic on my VM running Ubuntu.

### The Types of Packets (and Briefly What They Mean)

- **DNS (Domain Name System)**: Converts a readable domain name, like williamgbooth.com and translates it to an IP address that devices on a network can use.
- **HTTP (Hypertext Transfer Protocol)**: Moves assets between servers and clients, like web pages.
- **HTTPS (Hypertext Transfer Protocol Secure)**: Moves assets between servers and clients securely, encrypting the data to protect it from being read by 3rd parties who shouldn't be able to.
- **TCP (Transmission Control Protocol)**: Uses a "handshake" process to establish reliable connections. Ensures that data is not lost along the way.
- **UDP (User Datagram Protocol)**: Sends data without ensuring a connection first.
- **ICMP (Internet Control Message Protocol)**: Issues error messages in a connectionless manner.
- **DHCP (Dynamic Host Configuration Protocol)**: Assigns local IP addresses, subnet masks, and other details for devices.
- **ARP (Address Resolution Protocol)**: Uses a devices MAC address (hardware address) to match it with an available IP address on the local network.

### What's Going on in Wireshark

Wireshark captures all the network traffic that the network interface on my VM sends and receives. I chose to use a VM for this to safely analyze packets and reduce privacy concerns. The MAC address in Wireshark is not my real hardware MAC address, adding an extra layer of privacy while I study network traffic. I then export the .pcapng file onto my host machine for analysis. I was able to observe all the packets listed above in my captures.

### Preliminary Observations

TCP: In this screenshot, the threeway handshake is visible. I have redacted the IP address of the server for privacy reasons (I'm being overkill). My IP address is visible because it is a local address on my VM. The [SYN, SYN-ACK, ACK] sequence on the right of the screenshot shows the steps of the handshake process.

![TCP Handshake Screenshot](../../assets/images/tcp-handshake.png)

Here are the steps of a TCP handshake:

1. My computer requests a connection to the server by sending a SYN (synchronize) packet.
2. The server responds with a SYN-ACK (synchronize-acknowledge) packet to acknowledge the request.
3. My computer sends an ACK (acknowledge) packet back to the server, completing the handshake and establishing a reliable connection.

It's kind of like the exchange of rings during a wedding ceremony: one spouse offers a ring (SYN), the other accepts it and offers their own ring in return (SYN-ACK), and finally the first spouse acknowledges the exchange (ACK).
