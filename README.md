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
  
</details>

# Enumeration

<details> <summary><strong>FTP</strong></summary>

</details>

<details> <summary><strong>SSH</strong></summary>

</details>

<details> <summary><strong>SMTP</strong></summary>

</details>

<details>
  <summary><strong>HTTP / HTTPS</strong></summary>

  ### Virtual Hosts
  
</details>

<details> <summary><strong>NFS</strong></summary>

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

<details> <summary><strong>Databases</strong></summary>

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

<details> <summary><strong>mssql</strong></summary>

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
