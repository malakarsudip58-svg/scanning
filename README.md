# scanning_details_set1
To understand a SYN scan, you first need to know how a normal TCP connection is established, known as the "Three-Way Handshake":

SYN: The client sends a TCP packet with the SYN (Synchronize) flag set to the server, saying, "I want to start a connection."

SYN-ACK: The server responds with a packet that has both the SYN and ACK (Acknowledgment) flags set, saying, "Okay, I'm ready. Let's talk."

ACK: The client sends back a packet with the ACK flag set, confirming the connection. The connection is now ESTABLISHED.

A TCP SYN Scan exploits the first two steps of this handshake.

What is a TCP SYN Scan (-sS)? A TCP SYN Scan is a "half-open" scan because it doesn't complete the three-way handshake. Instead, it leaves the server hanging after step 2.

Here's how it works:

Nmap sends a SYN packet to the target port, just like a normal client would.

Nmap analyzes the response:

If the port is OPEN: The target responds with a SYN/ACK packet. Nmap immediately knows the port is open.

If the port is CLOSED: The target responds with a RST (Reset) packet. This is a hard "no, go away" signal.

Nmap does NOT complete the handshake. Upon receiving a SYN/ACK (indicating an open port), Nmap sends a RST packet back to tear down the connection attempt before it's fully established.

flowchart TD A[Nmap sends SYN packet] --> B{Analyze Response} B -- SYN/ACK --> C[Send RST to break handshake] B -- RST --> D[Port is Closed] B -- No Response ICMP Error --> E[Port is Filtered by firewall] C --> F[Port is Open]
