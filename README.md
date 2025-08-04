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
