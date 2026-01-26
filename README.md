![alt text](https://github.com/GunzyPunzy/Gunnajs-Playbook-OSCP/blob/main/anfader-oscp.jpg)

Got you — **clean copy‑paste block**, no commentary, GitHub‑ready.

````md
# Reconnaissance

<details>
  <summary><strong>Nmap</strong></summary>

  <details>
    <summary>Basic Scan</summary>

```bash
nmap -sC -sV <target>
````

  </details>

  <details>
    <summary>Full TCP Scan</summary>

```bash
nmap -p- -sS -sV <target>
```

  </details>

  <details>
    <summary>UDP Scan</summary>

```bash
nmap -sU --top-ports 100 <target>
```

  </details>

```bash
# Use if host blocks ICMP / appears down
nmap -Pn <target>
```

</details>

<details>
  <summary><strong>Banner Grabbing</strong></summary>

```bash
nc <target> <port>
```

```bash
version
```

</details>

<details>
  <summary><strong>enum4linux</strong></summary>

```bash
enum4linux -a <target>
```

</details>
```

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
