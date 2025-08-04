# Network Port Scanning – Task 1

## Objective
The goal of this task was to perform a **TCP SYN scan** using **Nmap** on my local network to:
- Discover active devices.
- Identify open ports and the services running on them.
- Understand the potential security risks of exposed services.

This exercise helps build **basic network reconnaissance skills** and awareness of **service exposure risks**.

---

## Tools Used
- **Nmap** (for port scanning)  
- **Linux Terminal** (for commands)  
- **Wireshark** *(optional)* (for analyzing captured packets)

---

## Steps Taken

### 1. Installed Nmap
Installed Nmap on my system:
```bash
sudo apt update
sudo apt install nmap
nmap --version
```
### 2.Identified My Local Network Range
```bash
ip addr
```
### 3. Performed a TCP SYN Scan
```bash
sudo nmap -sS 10.70.139.0/24 -oN scan_results.txt
```
Open scan_results.txt to see the detected hosts and open ports.

### Scan Results
Devices Found:
- **10.70.139.110** – Port 5060/tcp (SIP)
- **10.70.139.168 (gateway)** – Port 53/tcp (DNS)
- **10.70.139.197** – All ports filtered (likely firewall-protected)
- **10.70.139.195 (My Machine)** – Ports 21 (FTP), 80 (HTTP), 111 (RPCbind), 3389 (RDP)

### Common Services Running on Open Ports
| IP Address    | Port | Service | Description                                                            |
| ------------- | ---- | ------- | ---------------------------------------------------------------------- |
| 10.70.139.110 | 5060 | SIP     | Session Initiation Protocol, typically used for VoIP communications.   |
| 10.70.139.168 | 53   | DNS     | Domain Name System, resolves domain names to IP addresses.             |
| 10.70.139.195 | 21   | FTP     | File Transfer Protocol, used for transferring files (unencrypted).     |
| 10.70.139.195 | 80   | HTTP    | Hypertext Transfer Protocol, serves web content.                       |
| 10.70.139.195 | 111  | RPCbind | Remote Procedure Call, used by some services for remote communication. |
| 10.70.139.195 | 3389 | RDP     | Remote Desktop Protocol, allows remote access to a Windows machine.    |


### Potential Security Risks of These Ports
Port 21 (FTP): Data is transferred in plain text, making it vulnerable to sniffing and brute-force attacks.

Port 80 (HTTP): Unencrypted traffic; susceptible to man-in-the-middle attacks and information leakage.

Port 111 (RPCbind): Could allow attackers to enumerate available RPC services and exploit vulnerabilities.

Port 3389 (RDP): Often targeted for brute-force attacks; if compromised, full system access can be obtained.

Port 53 (DNS): Open DNS resolvers can be abused for DNS amplification DDoS attacks.

Port 5060 (SIP): Exposed VoIP services can be exploited for toll fraud, call interception, or DoS attacks.

## Conclusion
This scan identified multiple open ports on devices in the local network.  
The results highlight the need for:
- Closing unused ports.
- Securing critical services with encryption and authentication.
- Using firewalls to restrict external access.
