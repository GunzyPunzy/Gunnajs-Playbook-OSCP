![alt text](https://github.com/GunzyPunzy/Gunnajs-Playbook-OSCP/blob/main/anfader-oscp.jpg)

# Challenge labs
<details>
  <summary><strong>Labs</strong></summary>

#### The following challenge labs were completed before the exam, and the notes are based on them.
- [ ] Challenge 0 - Secura
- [ ] Challenge 1 - Medtech
- [ ] Challenge 2 - Relia
- [ ] Challenge 3 - Skylark
- [ ] Challenge 4 - OSCP A
- [ ] Challenge 5 - OSCP B
- [ ] Challenge 6 - OSCP C
- [ ] Challenge 7 - Zeus
- [ ] Challenge 8 - Poseidon
- [ ] Challenge 9 - Feast
- [ ] Challenge 10 - Laser
</details>

# Reconnaissance

<details>
  <summary><strong>Nmap</strong></summary>

### Basic Scan
```bash
nmap -n -sT -A -Pn <target>
````

### Full Scan

```bash
nmap -n -sT -p- -T4 -Pn <target>
```

### UDP Scan

```bash
nmap -n -sU --top-ports 1000 <target>
```

</details>

<details>
  <summary><strong>Banner Grabbing</strong></summary>

```bash
nc <target> <port>
```

```bash
nmap --script banner -p <port> <target>
```

</details>

<details>
  <summary><strong>DNS</strong></summary>

  **# Basic DNS lookup**
  ```bash
  host www.megacorpone.com
  ```

  ```bash
  dnsrecon -d hostname.com -t std
  ```
  ### Wordlist
  https://github.com/danielmiessler/SecLists/tree/master/Discovery/DNS

  ```bash
  dnsrecon -d hostname.com -D ~/list.txt 
  ```
  
</details>

# Services

<details> <summary><strong>FTP</strong></summary>

### Login, use Anonymous for anonymous login
```bash
ftp <IP>
```

### Download file
```bash
get <file>
```

### Upload file
```bash
put <file>
```

### Brute force
```bash
hydra -L users.txt -P passwords.txt <IP> ftp
```

</details>

<details> <summary><strong>SSH</strong></summary>

### Basic login
```bash
ssh <user>@<IP>
```

### Public key authentication
```bash
ssh -i id_rsa <user>@<IP>
```

### Brute force
```bash
hydra -L users.txt -P passwords.txt ssh://<IP>
```

</details>

<details> <summary><strong>NFS</strong></summary>

### Identify NFS service and exports
```bash
nmap -p 2049 -sV --script=nfs-showmount <IP>
```

### List exported shares
```bash
showmount -e <IP>
```

Mount NFS share
```bash
mkdir /tmp/nfs
mount -t nfs <IP>:/<share> /tmp/nfs
```

</details>

<details> <summary><strong>RPC</strong></summary>

</details>

<details> <summary><strong>SNMP</strong></summary>

</details>

<details>
  <summary><strong>SMB</strong></summary>

### enum4linux
```bash
enum4linux -a <target>
```

</details>

<details> <summary><strong>SQL</strong></summary>

</details>

# Finding Exploits

</details>

<details> <summary><strong>searchsploit</strong></summary>

</details>

# WebApp

<details>
  <summary><strong>Content Discovery</strong></summary>

</details>

<details>
  <summary><strong>File Upload</strong></summary>

</details>

<details>
  <summary><strong>Local / Remote File Inclusion (LFI / RFI)</strong></summary>

</details>

<details>
  <summary><strong>Directory Traversal</strong></summary>

</details>

<details>
  <summary><strong>SQL Injection</strong></summary>

</details>

<details> <summary><strong>CMS</strong></summary>

## WordPress

## Joomla

## Drupal

</details>

# Pivoting

<details>
  <summary> Chisel </summary> 

  ### Creating a server
  ```shell
  chisel server --port <PORT> --reverse
  ```

  ### Edit /etc/proxychains4.conf
  ```shell
  [ProxyList]
  socks5 127.0.0.1 1080
  ```

  ### Connecting from the client

   ```shell
  .\chisel client <ATTACK_MACHINE_IP>:<PORT> R:socks
  ```

  ### Sending command via the tunnel
  ```shell
  proxychains -q <command>
  ```

</details> 

# File Transfers

<details> <summary><strong>HTTP</strong></summary>

</details>

<details> <summary><strong>FTP</strong></summary>

</details>

<details> <summary><strong>SSH</strong></summary>

</details>

<details> <summary><strong>evil-winrm</strong></summary>

</details>

<details> <summary><strong>SMB</strong></summary>

</details>

<details> <summary><strong>MSSQL</strong></summary>

</details>

# Windows 

<details>
  <summary><strong>Reverse Shells</strong></summary>
  
</details>

<details>
  <summary><strong>Enumeration</strong></summary>
</details>

<details>
  <summary><strong>Credential Hunting</strong></summary>
  
</details>

<details>
  <summary><strong>Privesc</strong></summary>
  
</details>

<details>
  <summary><strong>Post-Exploitation</strong></summary>
  
</details>

# Active Directory

<details>
  <summary><strong>Enumeration</strong></summary>

</details>

<details>
  <summary><strong>Credential Hunting</strong></summary>
  
</details>

<details>
  <summary><strong>MSSQL</strong></summary>

</details>

# Linux

<details>
  <summary><strong>Reverse Shells</strong></summary>
</details>

<details>
  <summary><strong>TTY / Shell Upgrade</strong></summary>
</details>

<details>
  <summary><strong>Enumeration</strong></summary>
</details>

<details>
  <summary><strong>Credential Hunting</strong></summary>
</details>

<details>
  <summary><strong>Privesc</strong></summary>

</details>
