# Lab 001 - ARP and ICMP Packet Walk

## Objective
Observe ARP resolution and ICMP traffic between a Windows host and its default gateway.

## Environment
- Windows workstation
- Ethernet LAN
- Wireshark
- Default gateway: 192.168.1.1

## Procedure
1. Examined ARP cache.
2. Removed gateway ARP entry.
3. Started Wireshark capture.
4. Pinged default gateway.
5. Observed ARP request/reply.
6. Observed ICMP echo request/reply.
7. Repeated test using remote destination 8.8.8.8.

## Key Findings
- ARP requests use Layer-2 broadcast.
- ARP replies identify the MAC address associated with a local IPv4 address.
- Hosts ARP for the next-hop gateway when the destination is outside the local subnet.
- Hosts do not ARP directly for remote Internet destinations.
- Layer-2 addressing changes between hops while Layer-3 addressing identifies the end hosts. 

## Results

- Successfully removed the default gateway entry from the ARP cache.
- Observed an ARP broadcast requesting the MAC address for 192.168.1.1.
- Observed the gateway respond with a unicast ARP reply.
- Verified ICMP Echo Request and Echo Reply traffic between the workstation and default gateway.
- When pinging 8.8.8.8, the workstation resolved the MAC address of the default gateway rather than attempting to resolve the remote destination directly.

## Key Takeaway

For destinations outside the local subnet, the host forwards the Layer 2 frame to the default gateway while maintaining the remote host as the Layer 3 destination.