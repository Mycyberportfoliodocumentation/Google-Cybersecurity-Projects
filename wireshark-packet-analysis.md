🦈 Network Security Lab: Analyzing Packet Captures with Wireshark & tcpdump
📝 Activity Description
In this lab, I applied protocol analysis techniques to inspect live and recorded network traffic. Using tcpdump via the command line and Wireshark's graphical interface, I filtered packet capture (PCAP) files to isolate security incidents, analyze protocol layers, and dissect packet headers to identify unusual network behavior and verify secure configurations.

🛠️ Tools & Technologies Used
Wireshark (GUI Network Protocol Analyzer)

tcpdump (CLI Packet Sniffer)

Network Protocols: TCP, UDP, IP, DNS, HTTP, ICMP

Packet Capture Analysis: Display Filters, Packet Dissection

💻 Step-by-Step Breakdown & Tasks
Task 1: Command-Line Packet Capture with tcpdump
I initiated a packet capture using the Linux command line to intercept live interface traffic and write the raw packets into a file for deeper inspection.

sudo tcpdump -i eth0 -v -w raw_traffic.pcap

Purpose: Collects raw byte streams traveling through the network interface (eth0), saving them directly to a standard PCAP file while providing verbose status updates.

Task 2: Applying Display Filters in Wireshark
To quickly triage thousands of captured packets, I opened the file in Wireshark and isolated specific protocol exchanges related to a suspected web intrusion.

http.request.method == "POST" || tcp.port == 80

Purpose: Filters out background chatter and isolates unencrypted web traffic where an attacker might be attempting to submit unauthorized data or exploit web vulnerabilities.

Task 3: Analyzing Protocol Headers and Handshakes
I analyzed the standard TCP three-way handshake (SYN ➔ SYN-ACK ➔ ACK) to look for signs of port scanning or denial-of-service attempts.

Header Inspection: Reviewed source and destination IP addresses, verified sequence numbers, and audited TCP flags to ensure connections were being properly established and closed.

🎯 Summary & Security Impact
Packet analysis is one of the most reliable ways to verify what is actually happening on a network. This lab reinforced several critical incident response workflows:

Malware & C2 Detection: Identifying suspicious outbound traffic patterns, unusual ports, or unverified external IP communication.

Data Leakage Audits: Inspecting application layers (like plain-text HTTP or FTP) to ensure sensitive business credentials are not exposed in transit.

Evidence Collection: Utilizing standard PCAP formatting to capture cryptographic evidence of network attacks for legal or internal compliance.
