# Kali Linux: Beginner's Guide

Kali Linux is a free, Debian-based operating system built for penetration testing and security research. It comes with 600+ security tools preinstalled.

> ⚠️ **Use these tools only on systems you own or have written permission to test.** Unauthorised access is a crime under the IT Act 2000 (Sections 43 and 66) in India.

---

## 1. Install Kali the safe way (Virtual Machine)

Running Kali inside a VM keeps your main PC safe and lets you take snapshots.

1. Install **VirtualBox** (free) or **VMware Workstation Player**.
2. Download the ready-made **Kali VM image** from the official site: https://www.kali.org/get-kali/
3. Import the image (VirtualBox: *File → Import Appliance*, or open the `.vbox` file).
4. Give it at least **2 CPU cores, 4 GB RAM, 30 GB disk**.
5. Default login for the VM image: `kali` / `kali`. **Change the password immediately:**
   ```bash
   passwd
   ```

Other options: Live USB (use Rufus or balenaEtcher), WSL on Windows (`wsl --install -d kali-linux`), or Kali NetHunter for Android.

---

## 2. First things to do after install

```bash
sudo apt update && sudo apt full-upgrade -y   # update everything
sudo apt install -y kali-linux-default          # make sure the standard toolset is present
sudo reboot
```

Take a VM **snapshot** now so you can roll back if something breaks.

---

## 3. Linux commands you must know

| Command | What it does |
|---|---|
| `pwd` | Show current folder |
| `ls -la` | List files, including hidden ones |
| `cd /path` | Change folder |
| `mkdir name` | Create a folder |
| `cp`, `mv`, `rm` | Copy, move, delete |
| `cat file` / `nano file` | Read / edit a file |
| `sudo command` | Run as administrator |
| `ip a` | Show your IP addresses |
| `ping 8.8.8.8` | Check network connectivity |
| `chmod +x script.sh` | Make a file executable |
| `man command` | Read the manual for any command |

---

## 4. Essential tools (by category)

### Information gathering
- **Nmap** – network and port scanner
  ```bash
  nmap -sV 192.168.1.10        # find open ports and service versions
  nmap -sn 192.168.1.0/24      # find live hosts on your own network
  ```
- **whois**, **dig**, **theHarvester** – domain and OSINT lookups

### Web application testing
- **Burp Suite (Community)** – intercept and inspect web traffic
- **Nikto** – scan a web server for known issues
  ```bash
  nikto -h http://192.168.1.10
  ```
- **Gobuster / Dirb** – find hidden folders on a website

### Network analysis
- **Wireshark** – capture and inspect packets
- **tcpdump** – command-line packet capture

### Password auditing
- **John the Ripper**, **Hashcat** – test the strength of password hashes you own
- **Hydra** – test login strength on your own lab services

### Wireless (needs a compatible USB Wi-Fi adapter)
- **Aircrack-ng suite** – audit **your own** Wi-Fi network security

### Exploitation framework
- **Metasploit** – test known vulnerabilities in a lab
  ```bash
  sudo msfdb init
  msfconsole
  ```

---

## 5. Build a legal practice lab

Never practise on random websites or networks. Use these instead:

- **Metasploitable 2** – intentionally vulnerable Linux VM
- **DVWA** (Damn Vulnerable Web App) – practise web attacks
- **OWASP Juice Shop** – modern vulnerable web app
- **TryHackMe** – guided rooms, great for beginners
- **Hack The Box** – challenge machines
- **VulnHub** – downloadable vulnerable VMs

Put Kali and the vulnerable VM on a **Host-only / Internal network** in VirtualBox so the lab is isolated from the internet.

---

## 6. Suggested learning path

1. Linux basics and the command line
2. Networking (IP, TCP/UDP, ports, DNS, HTTP)
3. Nmap and reconnaissance
4. Web basics + Burp Suite + OWASP Top 10
5. Metasploit on Metasploitable
6. Write reports of what you found and how to fix it
7. Certifications later: CEH, eJPT, OSCP

---

## 7. Safety tips

- Keep Kali updated: `sudo apt update && sudo apt full-upgrade`
- Don't use Kali as your daily OS
- Never run tools against IPs or sites you don't own
- Use snapshots before risky experiments

---

*Maintained by King Computer Services, Delhi. For learning and authorised testing only.*
