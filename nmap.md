# Guide to nmap tool of kali linux

- Nmap stands for network mapper/mapping 
- It is a linux tool used to mapping / scanning a network
- When a computer runs a network service, it opens a networking construct called a “port” to  receive the connection.
- Every computer has a total of 65535 available ports;
- 1024 ports are considered as well known ports

## Some terminologies

- Network Segment : A group of computers connected using shared medium.
- The medium may be Ethernet switch or WiFi access point.
- Sub Network

# Important NMAP switches

- -h : for help
- -sS : for secure / syn scan
- -sU : for UDP scan
- -st : for TCP scan
- -o : for OS detection
- -sv : for version detection of services running on this machine
- -v : to increase verbosity
- -oA : to save the nmap results in three major formats
- oN : to save the nmap results in normal format
- oG : to save the nmap results in grepable format
- -a : aggresive scan
- -p : select the ports to scan
- -p- : scan all ports
- --script : to activate the script from nmap scripting library
- -f : used to fragment a packet making it less likely to be detected by the firewall
- -mtu : alternative to -f switch, provides more control over size of the fragment
- --scan-delay : used to add a delay between packets sent, very useful when network is unstable
- -badsum : used to generate in invalid checksum for packets. Firewalls may respond to these types of requests. Thus it is used for firewall detection

# Important types of scans

1. TCP Connect Scan

- -sT switch to use it
- it performs a complete tcp three way handshake with the target ip
- if port is closed then reset is send as response
- if port is open then syn/ack is sent as response
- firewalls drop the SYN requests so we recieve nothing back and port is considered filtered

2. SYN / Stealth / Half-open scans

- sS switch to use it
- doesnot complete the 3 way handshake
- it bypasses older intrusion detection systems
- faster than connect scans
- applications listening to the port doesn't log the half open requests thus makes it more stealthy
- only runs in sudo permissions
- default scan type when using sudo permissions 

3. UDP scans

- sU switch can be used to use it
- open port sends no response and is considered as open|filtered
- closed port sends an ICMP ping packet
- slower
- almost no use

4. NULL scan

- sN switch can be used to use it
- stealthier 
- sends a TCP request with no flag
- target host responds with a RST flag if port is closed

5. FIN scan

- sF switch can be used to use it
- sends a TCP request with FIN flag
- expects a RST if port is closed

6. XMAS scan

- sX switch can be used to use it
- sends a TCP request with PSH, URG, FIN flags
- sends a malformed packet and expects a RST if port is closed
- windows responds with a RST to any malformed TCP packet regardless of port is open or closed

Last 3 scans are used for firewall evasion because firewall drops syn packets.

# ICMP Network Scanning

- nmap sends an ICMP packet to each possible IP address for specified network.
- if it responds then it is marked as alive.
- also called ping sweep
- -sn switch to use it



# NMAP Scripting Enginde (NSE)

- written in Lua Programming Language
- many categories of scripts are there like safe, brute etc.
- --script switch to use scripts


# Firewall Evasion

- by doing NULL, FIN or XMAS scans
- typical windows firewall blocks all ICMP packets
- nmap as default, marks the firewalled system as dead and doesnot scan it at all.
- -Pn switch of nmap tells it not to bother pinging the target before scanning it
- nmap treats the host as alive
- if the host is dead then nmap still checks all the ports 

- if you are already inside the network then you can use ARP requests to determine user activity.