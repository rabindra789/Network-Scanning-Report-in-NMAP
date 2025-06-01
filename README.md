## Overview 
#### Target: 
- `192.168.29.158` (Metasploitable 2 VM) 
- **Date**: 2025-06-01 
- **Tool**: Nmap 7.95
## Initialisation
- Here i am using my physical computer which have Kali Linux (attacker) and for Metasploitable (victim) in a Virtual Box and connected two PC with bridge network for connection like real world.
- This is for educational purpose only and remember when you scan a website or a another device using nmap many of this Intrusion Detection systems of Firewalls it can see your IP also if you get found out that's it, it's `GAME OVER` for you.
## Here is the `nmap -h` command:

```nmap -h                          
Nmap 7.95 ( https://nmap.org )
Usage: nmap [Scan Type(s)] [Options] {target specification}
TARGET SPECIFICATION:
  Can pass hostnames, IP addresses, networks, etc.
  Ex: scanme.nmap.org, microsoft.com/24, 192.168.0.1; 10.0.0-255.1-254
  -iL <inputfilename>: Input from list of hosts/networks
  -iR <num hosts>: Choose random targets
  --exclude <host1[,host2][,host3],...>: Exclude hosts/networks
  --excludefile <exclude_file>: Exclude list from file
HOST DISCOVERY:
  -sL: List Scan - simply list targets to scan
  -sn: Ping Scan - disable port scan
  -Pn: Treat all hosts as online -- skip host discovery
  -PS/PA/PU/PY[portlist]: TCP SYN, TCP ACK, UDP or SCTP discovery to given ports
  -PE/PP/PM: ICMP echo, timestamp, and netmask request discovery probes
  -PO[protocol list]: IP Protocol Ping
  -n/-R: Never do DNS resolution/Always resolve [default: sometimes]
  --dns-servers <serv1[,serv2],...>: Specify custom DNS servers
  --system-dns: Use OS's DNS resolver
  --traceroute: Trace hop path to each host
SCAN TECHNIQUES:
  -sS/sT/sA/sW/sM: TCP SYN/Connect()/ACK/Window/Maimon scans
  -sU: UDP Scan
  -sN/sF/sX: TCP Null, FIN, and Xmas scans
  --scanflags <flags>: Customize TCP scan flags
  -sI <zombie host[:probeport]>: Idle scan
  -sY/sZ: SCTP INIT/COOKIE-ECHO scans
  -sO: IP protocol scan
  -b <FTP relay host>: FTP bounce scan
PORT SPECIFICATION AND SCAN ORDER:
  -p <port ranges>: Only scan specified ports
    Ex: -p22; -p1-65535; -p U:53,111,137,T:21-25,80,139,8080,S:9
  --exclude-ports <port ranges>: Exclude the specified ports from scanning
  -F: Fast mode - Scan fewer ports than the default scan
  -r: Scan ports sequentially - don't randomize
  --top-ports <number>: Scan <number> most common ports
  --port-ratio <ratio>: Scan ports more common than <ratio>
SERVICE/VERSION DETECTION:
  -sV: Probe open ports to determine service/version info
  --version-intensity <level>: Set from 0 (light) to 9 (try all probes)
  --version-light: Limit to most likely probes (intensity 2)
  --version-all: Try every single probe (intensity 9)
  --version-trace: Show detailed version scan activity (for debugging)
SCRIPT SCAN:
  -sC: equivalent to --script=default
  --script=<Lua scripts>: <Lua scripts> is a comma separated list of
           directories, script-files or script-categories
  --script-args=<n1=v1,[n2=v2,...]>: provide arguments to scripts
  --script-args-file=filename: provide NSE script args in a file
  --script-trace: Show all data sent and received
  --script-updatedb: Update the script database.
  --script-help=<Lua scripts>: Show help about scripts.
           <Lua scripts> is a comma-separated list of script-files or
           script-categories.
OS DETECTION:
  -O: Enable OS detection
  --osscan-limit: Limit OS detection to promising targets
  --osscan-guess: Guess OS more aggressively
TIMING AND PERFORMANCE:
  Options which take <time> are in seconds, or append 'ms' (milliseconds),
  's' (seconds), 'm' (minutes), or 'h' (hours) to the value (e.g. 30m).
  -T<0-5>: Set timing template (higher is faster)
  --min-hostgroup/max-hostgroup <size>: Parallel host scan group sizes
  --min-parallelism/max-parallelism <numprobes>: Probe parallelization
  --min-rtt-timeout/max-rtt-timeout/initial-rtt-timeout <time>: Specifies
      probe round trip time.
  --max-retries <tries>: Caps number of port scan probe retransmissions.
  --host-timeout <time>: Give up on target after this long
  --scan-delay/--max-scan-delay <time>: Adjust delay between probes
  --min-rate <number>: Send packets no slower than <number> per second
  --max-rate <number>: Send packets no faster than <number> per second
FIREWALL/IDS EVASION AND SPOOFING:
  -f; --mtu <val>: fragment packets (optionally w/given MTU)
  -D <decoy1,decoy2[,ME],...>: Cloak a scan with decoys
  -S <IP_Address>: Spoof source address
  -e <iface>: Use specified interface
  -g/--source-port <portnum>: Use given port number
  --proxies <url1,[url2],...>: Relay connections through HTTP/SOCKS4 proxies
  --data <hex string>: Append a custom payload to sent packets
  --data-string <string>: Append a custom ASCII string to sent packets
  --data-length <num>: Append random data to sent packets
  --ip-options <options>: Send packets with specified ip options
  --ttl <val>: Set IP time-to-live field
  --spoof-mac <mac address/prefix/vendor name>: Spoof your MAC address
  --badsum: Send packets with a bogus TCP/UDP/SCTP checksum
OUTPUT:
  -oN/-oX/-oS/-oG <file>: Output scan in normal, XML, s|<rIpt kIddi3,
     and Grepable format, respectively, to the given filename.
  -oA <basename>: Output in the three major formats at once
  -v: Increase verbosity level (use -vv or more for greater effect)
  -d: Increase debugging level (use -dd or more for greater effect)
  --reason: Display the reason a port is in a particular state
  --open: Only show open (or possibly open) ports
  --packet-trace: Show all packets sent and received
  --iflist: Print host interfaces and routes (for debugging)
  --append-output: Append to rather than clobber specified output files
  --resume <filename>: Resume an aborted scan
  --noninteractive: Disable runtime interactions via keyboard
  --stylesheet <path/URL>: XSL stylesheet to transform XML output to HTML
  --webxml: Reference stylesheet from Nmap.Org for more portable XML
  --no-stylesheet: Prevent associating of XSL stylesheet w/XML output
MISC:
  -6: Enable IPv6 scanning
  -A: Enable OS detection, version detection, script scanning, and traceroute
  --datadir <dirname>: Specify custom Nmap data file location
  --send-eth/--send-ip: Send using raw ethernet frames or IP packets
  --privileged: Assume that the user is fully privileged
  --unprivileged: Assume the user lacks raw socket privileges
  -V: Print version number
  -h: Print this help summary page.
EXAMPLES:
  nmap -v -A scanme.nmap.org
  nmap -v -sn 192.168.0.0/16 10.0.0.0/8
  nmap -v -iR 10000 -Pn -p 80
SEE THE MAN PAGE (https://nmap.org/book/man.html) FOR MORE OPTIONS AND EXAMPLES
```
## For finding IP of my all the devices across my network:

```nmap -sn 192.168.29.0/24  
Starting Nmap 7.95 ( https://nmap.org ) at 2025-06-01 18:28 IST
Nmap scan report for reliance.reliance (192.168.29.1)
Host is up (0.0063s latency).
MAC Address: A8:DA:0C:B9:08:40 (Servercom (India) Private Limited)
Nmap scan report for 192.168.29.158
Host is up (0.0014s latency).
MAC Address: 08:00:27:2E:32:7A (PCS Systemtechnik/Oracle VirtualBox virtual NIC)
Nmap scan report for 192.168.29.234
Host is up (0.59s latency).
MAC Address: 46:7E:7D:2D:E5:68 (Unknown)
Nmap scan report for 192.168.29.238
Host is up (0.59s latency).
MAC Address: 7C:7B:1C:4C:03:F8 (Motorola Mobility, a Lenovo Company)
Nmap scan report for 192.168.29.248
Host is up (0.44s latency).
MAC Address: 68:FC:CA:CA:AE:3A (Samsung Electronics)
Nmap scan report for 192.168.29.77
Host is up.
Nmap done: 256 IP addresses (6 hosts up) scanned in 5.30 seconds
```
In this scan `-sn` means No port scan. This help us to find the victim's device for potentially target later on. For this report we will target `192.168.29.158`.
## For the normal scanning the victim's IP is `192.168.29.158`:

```nmap 192.168.29.158     
Starting Nmap 7.95 ( https://nmap.org ) at 2025-06-01 18:35 IST
Nmap scan report for 192.168.29.158
Host is up (0.00030s latency).
Not shown: 977 closed tcp ports (reset)
PORT     STATE SERVICE
21/tcp   open  ftp
22/tcp   open  ssh
23/tcp   open  telnet
25/tcp   open  smtp
53/tcp   open  domain
80/tcp   open  http
111/tcp  open  rpcbind
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
512/tcp  open  exec
513/tcp  open  login
514/tcp  open  shell
1099/tcp open  rmiregistry
1524/tcp open  ingreslock
2049/tcp open  nfs
2121/tcp open  ccproxy-ftp
3306/tcp open  mysql
5432/tcp open  postgresql
5900/tcp open  vnc
6000/tcp open  X11
6667/tcp open  irc
8009/tcp open  ajp13
8180/tcp open  unknown
MAC Address: 08:00:27:2E:32:7A (PCS Systemtechnik/Oracle VirtualBox virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 0.31 seconds
```

This is the whole scan report of the victim's IP. For our need this is not sufficient so now we scan with `-sV` so it can find the service version so we are able to look up and see if their ==common vulnerability exposure== available for target against that service.

## For version scanning on victim's IP:

```nmap -sV 192.168.29.158 
Starting Nmap 7.95 ( https://nmap.org ) at 2025-06-01 18:42 IST
Nmap scan report for 192.168.29.158
Host is up (0.00029s latency).
Not shown: 977 closed tcp ports (reset)
PORT     STATE SERVICE     VERSION
21/tcp   open  ftp         vsftpd 2.3.4
22/tcp   open  ssh         OpenSSH 4.7p1 Debian 8ubuntu1 (protocol 2.0)
23/tcp   open  telnet      Linux telnetd
25/tcp   open  smtp        Postfix smtpd
53/tcp   open  domain      ISC BIND 9.4.2
80/tcp   open  http        Apache httpd 2.2.8 ((Ubuntu) DAV/2)
111/tcp  open  rpcbind     2 (RPC #100000)
139/tcp  open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
445/tcp  open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
512/tcp  open  exec        netkit-rsh rexecd
513/tcp  open  login
514/tcp  open  tcpwrapped
1099/tcp open  java-rmi    GNU Classpath grmiregistry
1524/tcp open  bindshell   Metasploitable root shell
2049/tcp open  nfs         2-4 (RPC #100003)
2121/tcp open  ftp         ProFTPD 1.3.1
3306/tcp open  mysql       MySQL 5.0.51a-3ubuntu5
5432/tcp open  postgresql  PostgreSQL DB 8.3.0 - 8.3.7
5900/tcp open  vnc         VNC (protocol 3.3)
6000/tcp open  X11         (access denied)
6667/tcp open  irc         UnrealIRCd
8009/tcp open  ajp13       Apache Jserv (Protocol v1.3)
8180/tcp open  http        Apache Tomcat/Coyote JSP engine 1.1
MAC Address: 08:00:27:2E:32:7A (PCS Systemtechnik/Oracle VirtualBox virtual NIC)
Service Info: Hosts:  metasploitable.localdomain, irc.Metasploitable.LAN; OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 11.64 seconds
```

## Generate a report in XML:
- I use nmap with 
	- `-T5`: Set the timing template to "insane", prioritising speed over stealth.
	- `-A`: Enable aggressive scanning.
	- `-v`: increases verbosity, showing more details.
	- `-oX`: Save the output in XML.
	- `192.168.29.158`: Target IP, in my case the Metasploitable which is running on virtual box.
	
```nmap -T5 -A -v 192.168.29.158/24 -oX network-map.xml
Starting Nmap 7.95 ( https://nmap.org ) at 2025-06-01 21:06 IST
NSE: Loaded 157 scripts for scanning.
NSE: Script Pre-scanning.
Initiating NSE at 21:06
Completed NSE at 21:06, 0.00s elapsed
Initiating NSE at 21:06
Completed NSE at 21:06, 0.00s elapsed
Initiating NSE at 21:06
Completed NSE at 21:06, 0.00s elapsed
Initiating ARP Ping Scan at 21:06
Scanning 255 hosts [1 port/host]
Completed ARP Ping Scan at 21:06, 2.32s elapsed (255 total hosts)
Initiating Parallel DNS resolution of 5 hosts. at 21:06
Completed Parallel DNS resolution of 5 hosts. at 21:06, 0.03s elapsed
Nmap scan report for 192.168.29.0 [host down]
Nmap scan report for 192.168.29.2 [host down]
Nmap scan report for 192.168.29.3 [host down]
Nmap scan report for 192.168.29.4 [host down]
Nmap scan report for 192.168.29.5 [host down]
Nmap scan report for 192.168.29.6 [host down]
Nmap scan report for 192.168.29.7 [host down]
Nmap scan report for 192.168.29.8 [host down]
Nmap scan report for 192.168.29.9 [host down]
Nmap scan report for 192.168.29.10 [host down]
Nmap scan report for 192.168.29.11 [host down]
Nmap scan report for 192.168.29.12 [host down]
Nmap scan report for 192.168.29.13 [host down]
Nmap scan report for 192.168.29.14 [host down]
Nmap scan report for 192.168.29.15 [host down]
Nmap scan report for 192.168.29.16 [host down]
Nmap scan report for 192.168.29.17 [host down]
Nmap scan report for 192.168.29.18 [host down]
Nmap scan report for 192.168.29.19 [host down]
Nmap scan report for 192.168.29.20 [host down]
Nmap scan report for 192.168.29.21 [host down]
Nmap scan report for 192.168.29.22 [host down]
Nmap scan report for 192.168.29.23 [host down]
Nmap scan report for 192.168.29.24 [host down]
Nmap scan report for 192.168.29.25 [host down]
Nmap scan report for 192.168.29.26 [host down]
Nmap scan report for 192.168.29.27 [host down]
Nmap scan report for 192.168.29.28 [host down]
Nmap scan report for 192.168.29.29 [host down]
Nmap scan report for 192.168.29.30 [host down]
Nmap scan report for 192.168.29.31 [host down]
Nmap scan report for 192.168.29.32 [host down]
Nmap scan report for 192.168.29.33 [host down]
Nmap scan report for 192.168.29.34 [host down]
Nmap scan report for 192.168.29.35 [host down]
Nmap scan report for 192.168.29.36 [host down]
Nmap scan report for 192.168.29.37 [host down]
Nmap scan report for 192.168.29.38 [host down]
Nmap scan report for 192.168.29.39 [host down]
Nmap scan report for 192.168.29.40 [host down]
Nmap scan report for 192.168.29.41 [host down]
Nmap scan report for 192.168.29.42 [host down]
Nmap scan report for 192.168.29.43 [host down]
Nmap scan report for 192.168.29.44 [host down]
Nmap scan report for 192.168.29.45 [host down]
Nmap scan report for 192.168.29.46 [host down]
Nmap scan report for 192.168.29.47 [host down]
Nmap scan report for 192.168.29.48 [host down]
Nmap scan report for 192.168.29.49 [host down]
Nmap scan report for 192.168.29.50 [host down]
Nmap scan report for 192.168.29.51 [host down]
Nmap scan report for 192.168.29.52 [host down]
Nmap scan report for 192.168.29.53 [host down]
Nmap scan report for 192.168.29.54 [host down]
Nmap scan report for 192.168.29.55 [host down]
Nmap scan report for 192.168.29.56 [host down]
Nmap scan report for 192.168.29.57 [host down]
Nmap scan report for 192.168.29.58 [host down]
Nmap scan report for 192.168.29.59 [host down]
Nmap scan report for 192.168.29.60 [host down]
Nmap scan report for 192.168.29.61 [host down]
Nmap scan report for 192.168.29.62 [host down]
Nmap scan report for 192.168.29.63 [host down]
Nmap scan report for 192.168.29.64 [host down]
Nmap scan report for 192.168.29.65 [host down]
Nmap scan report for 192.168.29.66 [host down]
Nmap scan report for 192.168.29.67 [host down]
Nmap scan report for 192.168.29.68 [host down]
Nmap scan report for 192.168.29.69 [host down]
Nmap scan report for 192.168.29.70 [host down]
Nmap scan report for 192.168.29.71 [host down]
Nmap scan report for 192.168.29.72 [host down]
Nmap scan report for 192.168.29.73 [host down]
Nmap scan report for 192.168.29.74 [host down]
Nmap scan report for 192.168.29.75 [host down]
Nmap scan report for 192.168.29.76 [host down]
Nmap scan report for 192.168.29.78 [host down]
Nmap scan report for 192.168.29.79 [host down]
Nmap scan report for 192.168.29.80 [host down]
Nmap scan report for 192.168.29.81 [host down]
Nmap scan report for 192.168.29.82 [host down]
Nmap scan report for 192.168.29.83 [host down]
Nmap scan report for 192.168.29.84 [host down]
Nmap scan report for 192.168.29.85 [host down]
Nmap scan report for 192.168.29.86 [host down]
Nmap scan report for 192.168.29.87 [host down]
Nmap scan report for 192.168.29.88 [host down]
Nmap scan report for 192.168.29.89 [host down]
Nmap scan report for 192.168.29.90 [host down]
Nmap scan report for 192.168.29.91 [host down]
Nmap scan report for 192.168.29.92 [host down]
Nmap scan report for 192.168.29.93 [host down]
Nmap scan report for 192.168.29.94 [host down]
Nmap scan report for 192.168.29.95 [host down]
Nmap scan report for 192.168.29.96 [host down]
Nmap scan report for 192.168.29.97 [host down]
Nmap scan report for 192.168.29.98 [host down]
Nmap scan report for 192.168.29.99 [host down]
Nmap scan report for 192.168.29.100 [host down]
Nmap scan report for 192.168.29.101 [host down]
Nmap scan report for 192.168.29.102 [host down]
Nmap scan report for 192.168.29.103 [host down]
Nmap scan report for 192.168.29.104 [host down]
Nmap scan report for 192.168.29.105 [host down]
Nmap scan report for 192.168.29.106 [host down]
Nmap scan report for 192.168.29.107 [host down]
Nmap scan report for 192.168.29.108 [host down]
Nmap scan report for 192.168.29.109 [host down]
Nmap scan report for 192.168.29.110 [host down]
Nmap scan report for 192.168.29.111 [host down]
Nmap scan report for 192.168.29.112 [host down]
Nmap scan report for 192.168.29.113 [host down]
Nmap scan report for 192.168.29.114 [host down]
Nmap scan report for 192.168.29.115 [host down]
Nmap scan report for 192.168.29.116 [host down]
Nmap scan report for 192.168.29.117 [host down]
Nmap scan report for 192.168.29.118 [host down]
Nmap scan report for 192.168.29.119 [host down]
Nmap scan report for 192.168.29.120 [host down]
Nmap scan report for 192.168.29.121 [host down]
Nmap scan report for 192.168.29.122 [host down]
Nmap scan report for 192.168.29.123 [host down]
Nmap scan report for 192.168.29.124 [host down]
Nmap scan report for 192.168.29.125 [host down]
Nmap scan report for 192.168.29.126 [host down]
Nmap scan report for 192.168.29.127 [host down]
Nmap scan report for 192.168.29.128 [host down]
Nmap scan report for 192.168.29.129 [host down]
Nmap scan report for 192.168.29.130 [host down]
Nmap scan report for 192.168.29.131 [host down]
Nmap scan report for 192.168.29.132 [host down]
Nmap scan report for 192.168.29.133 [host down]
Nmap scan report for 192.168.29.134 [host down]
Nmap scan report for 192.168.29.135 [host down]
Nmap scan report for 192.168.29.136 [host down]
Nmap scan report for 192.168.29.137 [host down]
Nmap scan report for 192.168.29.138 [host down]
Nmap scan report for 192.168.29.139 [host down]
Nmap scan report for 192.168.29.140 [host down]
Nmap scan report for 192.168.29.141 [host down]
Nmap scan report for 192.168.29.142 [host down]
Nmap scan report for 192.168.29.143 [host down]
Nmap scan report for 192.168.29.144 [host down]
Nmap scan report for 192.168.29.145 [host down]
Nmap scan report for 192.168.29.146 [host down]
Nmap scan report for 192.168.29.147 [host down]
Nmap scan report for 192.168.29.148 [host down]
Nmap scan report for 192.168.29.149 [host down]
Nmap scan report for 192.168.29.150 [host down]
Nmap scan report for 192.168.29.151 [host down]
Nmap scan report for 192.168.29.152 [host down]
Nmap scan report for 192.168.29.153 [host down]
Nmap scan report for 192.168.29.154 [host down]
Nmap scan report for 192.168.29.155 [host down]
Nmap scan report for 192.168.29.156 [host down]
Nmap scan report for 192.168.29.157 [host down]
Nmap scan report for 192.168.29.159 [host down]
Nmap scan report for 192.168.29.160 [host down]
Nmap scan report for 192.168.29.161 [host down]
Nmap scan report for 192.168.29.162 [host down]
Nmap scan report for 192.168.29.163 [host down]
Nmap scan report for 192.168.29.164 [host down]
Nmap scan report for 192.168.29.165 [host down]
Nmap scan report for 192.168.29.166 [host down]
Nmap scan report for 192.168.29.167 [host down]
Nmap scan report for 192.168.29.168 [host down]
Nmap scan report for 192.168.29.169 [host down]
Nmap scan report for 192.168.29.170 [host down]
Nmap scan report for 192.168.29.171 [host down]
Nmap scan report for 192.168.29.172 [host down]
Nmap scan report for 192.168.29.173 [host down]
Nmap scan report for 192.168.29.174 [host down]
Nmap scan report for 192.168.29.175 [host down]
Nmap scan report for 192.168.29.176 [host down]
Nmap scan report for 192.168.29.177 [host down]
Nmap scan report for 192.168.29.178 [host down]
Nmap scan report for 192.168.29.179 [host down]
Nmap scan report for 192.168.29.180 [host down]
Nmap scan report for 192.168.29.181 [host down]
Nmap scan report for 192.168.29.182 [host down]
Nmap scan report for 192.168.29.183 [host down]
Nmap scan report for 192.168.29.184 [host down]
Nmap scan report for 192.168.29.185 [host down]
Nmap scan report for 192.168.29.186 [host down]
Nmap scan report for 192.168.29.187 [host down]
Nmap scan report for 192.168.29.188 [host down]
Nmap scan report for 192.168.29.189 [host down]
Nmap scan report for 192.168.29.190 [host down]
Nmap scan report for 192.168.29.191 [host down]
Nmap scan report for 192.168.29.192 [host down]
Nmap scan report for 192.168.29.193 [host down]
Nmap scan report for 192.168.29.194 [host down]
Nmap scan report for 192.168.29.195 [host down]
Nmap scan report for 192.168.29.196 [host down]
Nmap scan report for 192.168.29.197 [host down]
Nmap scan report for 192.168.29.198 [host down]
Nmap scan report for 192.168.29.199 [host down]
Nmap scan report for 192.168.29.200 [host down]
Nmap scan report for 192.168.29.201 [host down]
Nmap scan report for 192.168.29.202 [host down]
Nmap scan report for 192.168.29.203 [host down]
Nmap scan report for 192.168.29.204 [host down]
Nmap scan report for 192.168.29.205 [host down]
Nmap scan report for 192.168.29.206 [host down]
Nmap scan report for 192.168.29.207 [host down]
Nmap scan report for 192.168.29.208 [host down]
Nmap scan report for 192.168.29.209 [host down]
Nmap scan report for 192.168.29.210 [host down]
Nmap scan report for 192.168.29.211 [host down]
Nmap scan report for 192.168.29.212 [host down]
Nmap scan report for 192.168.29.213 [host down]
Nmap scan report for 192.168.29.214 [host down]
Nmap scan report for 192.168.29.215 [host down]
Nmap scan report for 192.168.29.216 [host down]
Nmap scan report for 192.168.29.217 [host down]
Nmap scan report for 192.168.29.218 [host down]
Nmap scan report for 192.168.29.219 [host down]
Nmap scan report for 192.168.29.220 [host down]
Nmap scan report for 192.168.29.221 [host down]
Nmap scan report for 192.168.29.222 [host down]
Nmap scan report for 192.168.29.223 [host down]
Nmap scan report for 192.168.29.224 [host down]
Nmap scan report for 192.168.29.225 [host down]
Nmap scan report for 192.168.29.226 [host down]
Nmap scan report for 192.168.29.227 [host down]
Nmap scan report for 192.168.29.228 [host down]
Nmap scan report for 192.168.29.229 [host down]
Nmap scan report for 192.168.29.230 [host down]
Nmap scan report for 192.168.29.231 [host down]
Nmap scan report for 192.168.29.232 [host down]
Nmap scan report for 192.168.29.233 [host down]
Nmap scan report for 192.168.29.235 [host down]
Nmap scan report for 192.168.29.236 [host down]
Nmap scan report for 192.168.29.237 [host down]
Nmap scan report for 192.168.29.239 [host down]
Nmap scan report for 192.168.29.240 [host down]
Nmap scan report for 192.168.29.241 [host down]
Nmap scan report for 192.168.29.242 [host down]
Nmap scan report for 192.168.29.243 [host down]
Nmap scan report for 192.168.29.244 [host down]
Nmap scan report for 192.168.29.245 [host down]
Nmap scan report for 192.168.29.246 [host down]
Nmap scan report for 192.168.29.247 [host down]
Nmap scan report for 192.168.29.249 [host down]
Nmap scan report for 192.168.29.250 [host down]
Nmap scan report for 192.168.29.251 [host down]
Nmap scan report for 192.168.29.252 [host down]
Nmap scan report for 192.168.29.253 [host down]
Nmap scan report for 192.168.29.254 [host down]
Nmap scan report for 192.168.29.255 [host down]
Initiating Parallel DNS resolution of 1 host. at 21:06
Completed Parallel DNS resolution of 1 host. at 21:06, 0.00s elapsed
Initiating SYN Stealth Scan at 21:06
Scanning 5 hosts [1000 ports/host]
Discovered open port 23/tcp on 192.168.29.158
Discovered open port 443/tcp on 192.168.29.1
Discovered open port 80/tcp on 192.168.29.158
Discovered open port 80/tcp on 192.168.29.1
Discovered open port 3306/tcp on 192.168.29.158
Discovered open port 53/tcp on 192.168.29.158
Discovered open port 139/tcp on 192.168.29.158
Discovered open port 25/tcp on 192.168.29.158
Discovered open port 111/tcp on 192.168.29.158
Discovered open port 22/tcp on 192.168.29.158
Discovered open port 5900/tcp on 192.168.29.158
Discovered open port 445/tcp on 192.168.29.158
Discovered open port 21/tcp on 192.168.29.158
Discovered open port 2121/tcp on 192.168.29.158
Discovered open port 512/tcp on 192.168.29.158
Discovered open port 8080/tcp on 192.168.29.1
Discovered open port 1099/tcp on 192.168.29.158
Discovered open port 6000/tcp on 192.168.29.158
Discovered open port 514/tcp on 192.168.29.158
Discovered open port 5432/tcp on 192.168.29.158
Discovered open port 513/tcp on 192.168.29.158
Discovered open port 2049/tcp on 192.168.29.158
Discovered open port 8180/tcp on 192.168.29.158
Discovered open port 1524/tcp on 192.168.29.158
Discovered open port 8009/tcp on 192.168.29.158
Discovered open port 6667/tcp on 192.168.29.158
Completed SYN Stealth Scan against 192.168.29.158 in 0.28s (4 hosts left)
Discovered open port 53/tcp on 192.168.29.1
Completed SYN Stealth Scan against 192.168.29.238 in 1.82s (3 hosts left)
Completed SYN Stealth Scan against 192.168.29.234 in 2.91s (2 hosts left)
Discovered open port 7443/tcp on 192.168.29.1
Discovered open port 1900/tcp on 192.168.29.1
Discovered open port 8443/tcp on 192.168.29.1
Completed SYN Stealth Scan against 192.168.29.1 in 12.20s (1 host left)
Completed SYN Stealth Scan at 21:06, 18.66s elapsed (5000 total ports)
Initiating Service scan at 21:06
Scanning 30 services on 5 hosts
Completed Service scan at 21:07, 37.05s elapsed (30 services on 5 hosts)
Initiating OS detection (try #1) against 5 hosts
Retrying OS detection (try #2) against 4 hosts
NSE: Script scanning 5 hosts.
Initiating NSE at 21:07
NSE: [ftp-bounce] PORT response: 500 Illegal PORT command.
Completed NSE at 21:07, 22.21s elapsed
Initiating NSE at 21:07
Completed NSE at 21:07, 3.01s elapsed
Initiating NSE at 21:07
Completed NSE at 21:07, 0.00s elapsed
Nmap scan report for reliance.reliance (192.168.29.1)
Host is up (0.012s latency).
Not shown: 990 filtered tcp ports (no-response)
PORT     STATE  SERVICE             VERSION
22/tcp   closed ssh
53/tcp   open   domain              dnsmasq 2.45
| dns-nsid: 
|_  bind.version: dnsmasq-2.45
80/tcp   open   http                lighttpd
|_http-server-header: Web Server
|_http-title: Jio Centrum Home Gateway : 
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-favicon: Unknown favicon MD5: 955BF3F5D769035F6B81B5EE39B10019
443/tcp  open   ssl/http            lighttpd
|_http-server-header: Web Server
| http-methods: 
|_  Supported Methods: POST OPTIONS
|_ssl-date: TLS randomness does not represent time
| ssl-cert: Subject: commonName=RILSELFCERT/organizationName=Reliance Jio Infocomm Limited
| Issuer: commonName=RILSELFCERT/organizationName=Reliance Jio Infocomm Limited
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2022-04-27T05:58:11
| Not valid after:  2032-04-24T05:58:11
| MD5:   a76e:5228:501b:8751:28e4:f298:1d29:679f
|_SHA-1: 1305:0966:c605:336f:43fd:7c97:0042:8056:24c5:8910
|_http-title: Jio Centrum Home Gateway : 
1900/tcp open   upnp
| fingerprint-strings: 
|   FourOhFourRequest, GetRequest: 
|     HTTP/1.1 404 Not Found
|     Server: Linux UPnP/1.0 DLNADOC/1.50 AccessTwine/1.0-RAS Device/reliance.reliance
|     Content-Length: 48
|     Content-Type: text/html
|     <HTML><BODY><H1>404 Not Found</H1></BODY></HTML>
|   HTTPOptions: 
|     HTTP/1.1 405 Method Not Allowed
|     Server: Linux UPnP/1.0 DLNADOC/1.50 AccessTwine/1.0-RAS Device/reliance.reliance
|     Content-Length: 57
|     Content-Type: text/html
|_    <HTML><BODY><H1>405 Method Not Allowed</H1></BODY></HTML>
2869/tcp closed icslap
7443/tcp open   ssl/oracleas-https?
|_ssl-date: TLS randomness does not represent time
| fingerprint-strings: 
|   FourOhFourRequest: 
|     HTTP/1.0 400 Bad Request
|     Content-Length: 11
|     Content-Type: text/html
|     Connection: close
|     Server: JCOW404/JUICEJFV-1.3.31
|     Request
|   GetRequest: 
|     HTTP/1.0 503 Service Unavailable
|     Content-Length: 19
|     Content-Type: text/html
|     Connection: close
|     Server: JCOW404/JUICEJFV-1.3.31
|     Service Unavailable
|   HTTPOptions: 
|     HTTP/1.0 501 Not Implemented
|     Content-Length: 15
|     Content-Type: text/html
|     Connection: close
|     Server: JCOW404/JUICEJFV-1.3.31
|_    implemented
| ssl-cert: Subject: commonName=jiofiber.local.html/organizationName=Jio Platforms Limited/stateOrProvinceName=KA/countryName=IN
| Issuer: commonName=jiofiber.local.html/organizationName=Jio Platforms Limited/stateOrProvinceName=KA/countryName=IN
| Public Key type: rsa
| Public Key bits: 4096
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2021-11-22T04:56:50
| Not valid after:  2121-10-29T04:56:50
| MD5:   a019:7a21:48b4:29a2:e252:bf01:b35a:ca7f
|_SHA-1: 2192:8072:a6f2:3814:73d8:c9ed:b6c1:6b18:cfc8:b66e
8080/tcp open   http-proxy          JCOW404/JUICEJFV-1.3.31
|_http-server-header: JCOW404/JUICEJFV-1.3.31
| fingerprint-strings: 
|   FourOhFourRequest: 
|     HTTP/1.0 400 Bad Request
|     Content-Length: 11
|     Content-Type: text/html
|     Connection: close
|     Server: JCOW404/JUICEJFV-1.3.31
|     Request
|   GetRequest: 
|     HTTP/1.0 503 Service Unavailable
|     Content-Length: 19
|     Content-Type: text/html
|     Connection: close
|     Server: JCOW404/JUICEJFV-1.3.31
|     Service Unavailable
|   HTTPOptions: 
|     HTTP/1.0 501 Not Implemented
|     Content-Length: 15
|     Content-Type: text/html
|     Connection: close
|     Server: JCOW404/JUICEJFV-1.3.31
|_    implemented
|_http-title: Site doesn't have a title (text/html).
| http-methods: 
|_  Supported Methods: GET
8200/tcp closed trivnet1
8443/tcp open   ssl/https-alt       JCOW404/JUICEJFV-1.3.31
|_ssl-date: TLS randomness does not represent time
|_http-server-header: JCOW404/JUICEJFV-1.3.31
| ssl-cert: Subject: commonName=jiofiber.local.html/organizationName=Jio Platforms Limited/stateOrProvinceName=KA/countryName=IN
| Issuer: commonName=jiofiber.local.html/organizationName=Jio Platforms Limited/stateOrProvinceName=KA/countryName=IN
| Public Key type: rsa
| Public Key bits: 4096
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2021-11-22T04:56:50
| Not valid after:  2121-10-29T04:56:50
| MD5:   a019:7a21:48b4:29a2:e252:bf01:b35a:ca7f
|_SHA-1: 2192:8072:a6f2:3814:73d8:c9ed:b6c1:6b18:cfc8:b66e
| fingerprint-strings: 
|   DNSStatusRequestTCP, JavaRMI, NCP, RPCCheck, SMBProgNeg, TerminalServer, WMSRequest, X11Probe, ms-sql-s, oracle-tns: 
|     (null) 400 Bad Request
|     Content-Length: 11
|     Content-Type: text/html
|     Connection: close
|     Request
|   FourOhFourRequest, GetRequest: 
|     HTTP/1.0 400 Bad Request
|     Content-Length: 11
|     Content-Type: text/html
|     Connection: close
|     Server: JCOW404/JUICEJFV-1.3.31
|     Request
|   HTTPOptions: 
|     HTTP/1.0 501 Not Implemented
|     Content-Length: 15
|     Content-Type: text/html
|     Connection: close
|     Server: JCOW404/JUICEJFV-1.3.31
|_    implemented
4 services unrecognized despite returning data. If you know the service/version, please submit the following fingerprints at https://nmap.org/cgi-bin/submit.cgi?new-service :
==============NEXT SERVICE FINGERPRINT (SUBMIT INDIVIDUALLY)==============
SF-Port1900-TCP:V=7.95%I=7%D=6/1%Time=683C739E%P=x86_64-pc-linux-gnu%r(Get
SF:Request,C9,"HTTP/1\.1\x20404\x20Not\x20Found\r\nServer:\x20Linux\x20UPn
SF:P/1\.0\x20DLNADOC/1\.50\x20AccessTwine/1\.0-RAS\x20Device/reliance\.rel
SF:iance\r\nContent-Length:\x2048\r\nContent-Type:\x20text/html\r\n\r\n<HT
SF:ML><BODY><H1>404\x20Not\x20Found</H1></BODY></HTML>")%r(HTTPOptions,DB,
SF:"HTTP/1\.1\x20405\x20Method\x20Not\x20Allowed\r\nServer:\x20Linux\x20UP
SF:nP/1\.0\x20DLNADOC/1\.50\x20AccessTwine/1\.0-RAS\x20Device/reliance\.re
SF:liance\r\nContent-Length:\x2057\r\nContent-Type:\x20text/html\r\n\r\n<H
SF:TML><BODY><H1>405\x20Method\x20Not\x20Allowed</H1></BODY></HTML>")%r(Fo
SF:urOhFourRequest,C9,"HTTP/1\.1\x20404\x20Not\x20Found\r\nServer:\x20Linu
SF:x\x20UPnP/1\.0\x20DLNADOC/1\.50\x20AccessTwine/1\.0-RAS\x20Device/relia
SF:nce\.reliance\r\nContent-Length:\x2048\r\nContent-Type:\x20text/html\r\
SF:n\r\n<HTML><BODY><H1>404\x20Not\x20Found</H1></BODY></HTML>");
==============NEXT SERVICE FINGERPRINT (SUBMIT INDIVIDUALLY)==============
SF-Port7443-TCP:V=7.95%T=SSL%I=7%D=6/1%Time=683C739F%P=x86_64-pc-linux-gnu
SF:%r(GetRequest,98,"HTTP/1\.0\x20503\x20Service\x20Unavailable\r\nContent
SF:-Length:\x2019\r\nContent-Type:\x20text/html\r\nConnection:\x20close\r\
SF:nServer:\x20JCOW404/JUICEJFV-1\.3\.31\r\n\r\nService\x20Unavailable")%r
SF:(HTTPOptions,90,"HTTP/1\.0\x20501\x20Not\x20Implemented\r\nContent-Leng
SF:th:\x2015\r\nContent-Type:\x20text/html\r\nConnection:\x20close\r\nServ
SF:er:\x20JCOW404/JUICEJFV-1\.3\.31\r\n\r\nNot\x20implemented")%r(FourOhFo
SF:urRequest,88,"HTTP/1\.0\x20400\x20Bad\x20Request\r\nContent-Length:\x20
SF:11\r\nContent-Type:\x20text/html\r\nConnection:\x20close\r\nServer:\x20
SF:JCOW404/JUICEJFV-1\.3\.31\r\n\r\nBad\x20Request");
==============NEXT SERVICE FINGERPRINT (SUBMIT INDIVIDUALLY)==============
SF-Port8080-TCP:V=7.95%I=7%D=6/1%Time=683C7399%P=x86_64-pc-linux-gnu%r(Get
SF:Request,98,"HTTP/1\.0\x20503\x20Service\x20Unavailable\r\nContent-Lengt
SF:h:\x2019\r\nContent-Type:\x20text/html\r\nConnection:\x20close\r\nServe
SF:r:\x20JCOW404/JUICEJFV-1\.3\.31\r\n\r\nService\x20Unavailable")%r(HTTPO
SF:ptions,90,"HTTP/1\.0\x20501\x20Not\x20Implemented\r\nContent-Length:\x2
SF:015\r\nContent-Type:\x20text/html\r\nConnection:\x20close\r\nServer:\x2
SF:0JCOW404/JUICEJFV-1\.3\.31\r\n\r\nNot\x20implemented")%r(FourOhFourRequ
SF:est,88,"HTTP/1\.0\x20400\x20Bad\x20Request\r\nContent-Length:\x2011\r\n
SF:Content-Type:\x20text/html\r\nConnection:\x20close\r\nServer:\x20JCOW40
SF:4/JUICEJFV-1\.3\.31\r\n\r\nBad\x20Request");
==============NEXT SERVICE FINGERPRINT (SUBMIT INDIVIDUALLY)==============
SF-Port8443-TCP:V=7.95%T=SSL%I=7%D=6/1%Time=683C739F%P=x86_64-pc-linux-gnu
SF:%r(GetRequest,88,"HTTP/1\.0\x20400\x20Bad\x20Request\r\nContent-Length:
SF:\x2011\r\nContent-Type:\x20text/html\r\nConnection:\x20close\r\nServer:
SF:\x20JCOW404/JUICEJFV-1\.3\.31\r\n\r\nBad\x20Request")%r(HTTPOptions,90,
SF:"HTTP/1\.0\x20501\x20Not\x20Implemented\r\nContent-Length:\x2015\r\nCon
SF:tent-Type:\x20text/html\r\nConnection:\x20close\r\nServer:\x20JCOW404/J
SF:UICEJFV-1\.3\.31\r\n\r\nNot\x20implemented")%r(FourOhFourRequest,88,"HT
SF:TP/1\.0\x20400\x20Bad\x20Request\r\nContent-Length:\x2011\r\nContent-Ty
SF:pe:\x20text/html\r\nConnection:\x20close\r\nServer:\x20JCOW404/JUICEJFV
SF:-1\.3\.31\r\n\r\nBad\x20Request")%r(RPCCheck,65,"\(null\)\x20400\x20Bad
SF:\x20Request\r\nContent-Length:\x2011\r\nContent-Type:\x20text/html\r\nC
SF:onnection:\x20close\r\n\r\nBad\x20Request")%r(DNSStatusRequestTCP,65,"\
SF:(null\)\x20400\x20Bad\x20Request\r\nContent-Length:\x2011\r\nContent-Ty
SF:pe:\x20text/html\r\nConnection:\x20close\r\n\r\nBad\x20Request")%r(SMBP
SF:rogNeg,65,"\(null\)\x20400\x20Bad\x20Request\r\nContent-Length:\x2011\r
SF:\nContent-Type:\x20text/html\r\nConnection:\x20close\r\n\r\nBad\x20Requ
SF:est")%r(X11Probe,65,"\(null\)\x20400\x20Bad\x20Request\r\nContent-Lengt
SF:h:\x2011\r\nContent-Type:\x20text/html\r\nConnection:\x20close\r\n\r\nB
SF:ad\x20Request")%r(TerminalServer,65,"\(null\)\x20400\x20Bad\x20Request\
SF:r\nContent-Length:\x2011\r\nContent-Type:\x20text/html\r\nConnection:\x
SF:20close\r\n\r\nBad\x20Request")%r(NCP,65,"\(null\)\x20400\x20Bad\x20Req
SF:uest\r\nContent-Length:\x2011\r\nContent-Type:\x20text/html\r\nConnecti
SF:on:\x20close\r\n\r\nBad\x20Request")%r(JavaRMI,65,"\(null\)\x20400\x20B
SF:ad\x20Request\r\nContent-Length:\x2011\r\nContent-Type:\x20text/html\r\
SF:nConnection:\x20close\r\n\r\nBad\x20Request")%r(WMSRequest,65,"\(null\)
SF:\x20400\x20Bad\x20Request\r\nContent-Length:\x2011\r\nContent-Type:\x20
SF:text/html\r\nConnection:\x20close\r\n\r\nBad\x20Request")%r(oracle-tns,
SF:65,"\(null\)\x20400\x20Bad\x20Request\r\nContent-Length:\x2011\r\nConte
SF:nt-Type:\x20text/html\r\nConnection:\x20close\r\n\r\nBad\x20Request")%r
SF:(ms-sql-s,65,"\(null\)\x20400\x20Bad\x20Request\r\nContent-Length:\x201
SF:1\r\nContent-Type:\x20text/html\r\nConnection:\x20close\r\n\r\nBad\x20R
SF:equest");
MAC Address: A8:DA:0C:B9:08:40 (Servercom (India) Private Limited)
Device type: general purpose|media device|phone|broadband router|WAP
Running (JUST GUESSING): Linux 3.X|4.X|2.6.X|5.X (98%), Amazon embedded (92%), Google Android 10.X (90%), Asus embedded (89%)
OS CPE: cpe:/o:linux:linux_kernel:3 cpe:/o:linux:linux_kernel:4 cpe:/o:linux:linux_kernel:2.6 cpe:/o:linux:linux_kernel:5.10 cpe:/o:google:android:10 cpe:/o:linux:linux_kernel:3.10 cpe:/o:linux:linux_kernel cpe:/h:asus:rt-ac66u
Aggressive OS guesses: Linux 3.10 - 4.11 (98%), Linux 3.2 - 4.14 (94%), Amazon Fire TV (92%), Linux 3.10 (92%), OpenWrt 19.07 (Linux 4.14) (92%), Linux 2.6.32 - 3.13 (91%), OpenWrt 22.03 (Linux 5.10) (91%), Linux 4.4 (91%), Linux 5.1 - 5.15 (91%), Linux 2.6.39 (91%)
No exact OS matches for host (test conditions non-ideal).
Uptime guess: 0.642 days (since Sun Jun  1 05:43:12 2025)
Network Distance: 1 hop
TCP Sequence Prediction: Difficulty=257 (Good luck!)
IP ID Sequence Generation: All zeros

TRACEROUTE
HOP RTT      ADDRESS
1   11.61 ms reliance.reliance (192.168.29.1)

Nmap scan report for 192.168.29.158
Host is up (0.00054s latency).
Not shown: 977 closed tcp ports (reset)
PORT     STATE SERVICE     VERSION
21/tcp   open  ftp         vsftpd 2.3.4
|_ftp-anon: Anonymous FTP login allowed (FTP code 230)
| ftp-syst: 
|   STAT: 
| FTP server status:
|      Connected to 192.168.29.77
|      Logged in as ftp
|      TYPE: ASCII
|      No session bandwidth limit
|      Session timeout in seconds is 300
|      Control connection is plain text
|      Data connections will be plain text
|      vsFTPd 2.3.4 - secure, fast, stable
|_End of status
22/tcp   open  ssh         OpenSSH 4.7p1 Debian 8ubuntu1 (protocol 2.0)
| ssh-hostkey: 
|   1024 60:0f:cf:e1:c0:5f:6a:74:d6:90:24:fa:c4:d5:6c:cd (DSA)
|_  2048 56:56:24:0f:21:1d:de:a7:2b:ae:61:b1:24:3d:e8:f3 (RSA)
23/tcp   open  telnet      Linux telnetd
25/tcp   open  smtp        Postfix smtpd
| sslv2: 
|   SSLv2 supported
|   ciphers: 
|     SSL2_RC2_128_CBC_WITH_MD5
|     SSL2_RC2_128_CBC_EXPORT40_WITH_MD5
|     SSL2_DES_192_EDE3_CBC_WITH_MD5
|     SSL2_DES_64_CBC_WITH_MD5
|     SSL2_RC4_128_WITH_MD5
|_    SSL2_RC4_128_EXPORT40_WITH_MD5
| ssl-cert: Subject: commonName=ubuntu804-base.localdomain/organizationName=OCOSA/stateOrProvinceName=There is no such thing outside US/countryName=XX
| Issuer: commonName=ubuntu804-base.localdomain/organizationName=OCOSA/stateOrProvinceName=There is no such thing outside US/countryName=XX
| Public Key type: rsa
| Public Key bits: 1024
| Signature Algorithm: sha1WithRSAEncryption
| Not valid before: 2010-03-17T14:07:45
| Not valid after:  2010-04-16T14:07:45
| MD5:   dcd9:ad90:6c8f:2f73:74af:383b:2540:8828
|_SHA-1: ed09:3088:7066:03bf:d5dc:2373:99b4:98da:2d4d:31c6
|_smtp-commands: metasploitable.localdomain, PIPELINING, SIZE 10240000, VRFY, ETRN, STARTTLS, ENHANCEDSTATUSCODES, 8BITMIME, DSN
|_ssl-date: 2025-06-01T15:38:56+00:00; +59s from scanner time.
53/tcp   open  domain      ISC BIND 9.4.2
| dns-nsid: 
|_  bind.version: 9.4.2
80/tcp   open  http        Apache httpd 2.2.8 ((Ubuntu) DAV/2)
|_http-server-header: Apache/2.2.8 (Ubuntu) DAV/2
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-title: Metasploitable2 - Linux
111/tcp  open  rpcbind     2 (RPC #100000)
| rpcinfo: 
|   program version    port/proto  service
|   100000  2            111/tcp   rpcbind
|   100000  2            111/udp   rpcbind
|   100003  2,3,4       2049/tcp   nfs
|   100003  2,3,4       2049/udp   nfs
|   100005  1,2,3      38965/tcp   mountd
|   100005  1,2,3      58988/udp   mountd
|   100021  1,3,4      43542/tcp   nlockmgr
|   100021  1,3,4      46171/udp   nlockmgr
|   100024  1          44958/tcp   status
|_  100024  1          45422/udp   status
139/tcp  open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
445/tcp  open  netbios-ssn Samba smbd 3.0.20-Debian (workgroup: WORKGROUP)
512/tcp  open  exec        netkit-rsh rexecd
513/tcp  open  login       OpenBSD or Solaris rlogind
514/tcp  open  tcpwrapped
1099/tcp open  java-rmi    GNU Classpath grmiregistry
1524/tcp open  bindshell   Metasploitable root shell
2049/tcp open  nfs         2-4 (RPC #100003)
2121/tcp open  ftp         ProFTPD 1.3.1
3306/tcp open  mysql       MySQL 5.0.51a-3ubuntu5
| mysql-info: 
|   Protocol: 10
|   Version: 5.0.51a-3ubuntu5
|   Thread ID: 94
|   Capabilities flags: 43564
|   Some Capabilities: SupportsTransactions, Support41Auth, LongColumnFlag, SwitchToSSLAfterHandshake, ConnectWithDatabase, Speaks41ProtocolNew, SupportsCompression
|   Status: Autocommit
|_  Salt: 'xLS9dkoh><P_jyAtHJy
5432/tcp open  postgresql  PostgreSQL DB 8.3.0 - 8.3.7
| ssl-cert: Subject: commonName=ubuntu804-base.localdomain/organizationName=OCOSA/stateOrProvinceName=There is no such thing outside US/countryName=XX
| Issuer: commonName=ubuntu804-base.localdomain/organizationName=OCOSA/stateOrProvinceName=There is no such thing outside US/countryName=XX
| Public Key type: rsa
| Public Key bits: 1024
| Signature Algorithm: sha1WithRSAEncryption
| Not valid before: 2010-03-17T14:07:45
| Not valid after:  2010-04-16T14:07:45
| MD5:   dcd9:ad90:6c8f:2f73:74af:383b:2540:8828
|_SHA-1: ed09:3088:7066:03bf:d5dc:2373:99b4:98da:2d4d:31c6
|_ssl-date: 2025-06-01T15:38:56+00:00; +59s from scanner time.
5900/tcp open  vnc         VNC (protocol 3.3)
| vnc-info: 
|   Protocol version: 3.3
|   Security types: 
|_    VNC Authentication (2)
6000/tcp open  X11         (access denied)
6667/tcp open  irc         UnrealIRCd
| irc-info: 
|   users: 1
|   servers: 1
|   lusers: 1
|   lservers: 0
|   server: irc.Metasploitable.LAN
|   version: Unreal3.2.8.1. irc.Metasploitable.LAN 
|   uptime: 0 days, 11:39:23
|   source ident: nmap
|   source host: C6A2CCD8.E5C4C5A1.FFFA6D49.IP
|_  error: Closing Link: zbybpxymy[192.168.29.77] (Quit: zbybpxymy)
8009/tcp open  ajp13       Apache Jserv (Protocol v1.3)
|_ajp-methods: Failed to get a valid response for the OPTION request
8180/tcp open  http        Apache Tomcat/Coyote JSP engine 1.1
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-title: Apache Tomcat/5.5
|_http-server-header: Apache-Coyote/1.1
|_http-favicon: Apache Tomcat
MAC Address: 08:00:27:2E:32:7A (PCS Systemtechnik/Oracle VirtualBox virtual NIC)
Device type: general purpose
Running: Linux 2.6.X
OS CPE: cpe:/o:linux:linux_kernel:2.6
OS details: Linux 2.6.9 - 2.6.33
Uptime guess: 0.483 days (since Sun Jun  1 09:33:01 2025)
Network Distance: 1 hop
TCP Sequence Prediction: Difficulty=201 (Good luck!)
IP ID Sequence Generation: All zeros
Service Info: Hosts:  metasploitable.localdomain, irc.Metasploitable.LAN; OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel

Host script results:
|_clock-skew: mean: 1h01m00s, deviation: 2h00m02s, median: 58s
| smb-os-discovery: 
|   OS: Unix (Samba 3.0.20-Debian)
|   Computer name: metasploitable
|   NetBIOS computer name: 
|   Domain name: localdomain
|   FQDN: metasploitable.localdomain
|_  System time: 2025-06-01T11:38:37-04:00
| nbstat: NetBIOS name: METASPLOITABLE, NetBIOS user: <unknown>, NetBIOS MAC: <unknown> (unknown)
| Names:
|   METASPLOITABLE<00>   Flags: <unique><active>
|   METASPLOITABLE<03>   Flags: <unique><active>
|   METASPLOITABLE<20>   Flags: <unique><active>
|   \x01\x02__MSBROWSE__\x02<01>  Flags: <group><active>
|   WORKGROUP<00>        Flags: <group><active>
|   WORKGROUP<1d>        Flags: <unique><active>
|_  WORKGROUP<1e>        Flags: <group><active>
|_smb2-time: Protocol negotiation failed (SMB2)
| smb-security-mode: 
|   account_used: guest
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)

TRACEROUTE
HOP RTT     ADDRESS
1   0.54 ms 192.168.29.158

Nmap scan report for 192.168.29.234
Host is up (0.016s latency).
Not shown: 999 closed tcp ports (reset)
PORT     STATE    SERVICE VERSION
5060/tcp filtered sip
MAC Address: 46:7E:7D:2D:E5:68 (Unknown)
Too many fingerprints match this host to give specific OS details
Network Distance: 1 hop

TRACEROUTE
HOP RTT      ADDRESS
1   16.25 ms 192.168.29.234

Nmap scan report for 192.168.29.238
Host is up (0.0075s latency).
Not shown: 999 closed tcp ports (reset)
PORT     STATE    SERVICE VERSION
5060/tcp filtered sip
MAC Address: 7C:7B:1C:4C:03:F8 (Motorola Mobility, a Lenovo Company)
Too many fingerprints match this host to give specific OS details
Network Distance: 1 hop

TRACEROUTE
HOP RTT     ADDRESS
1   7.47 ms 192.168.29.238

Nmap scan report for 192.168.29.248
Host is up (0.30s latency).
All 1000 scanned ports on 192.168.29.248 are in ignored states.
Not shown: 1000 filtered tcp ports (no-response)
MAC Address: 68:FC:CA:CA:AE:3A (Samsung Electronics)
Too many fingerprints match this host to give specific OS details
Network Distance: 1 hop

TRACEROUTE
HOP RTT       ADDRESS
1   303.95 ms 192.168.29.248
```

- After the scan report is save then you can use it for later analysis in tools like `Zenmap`, `scripts`.
- I open it on Firefox browser and saw that it is not human readable format so i changed the XML file to HTML format.

**Here is the network-map.xml file:**
[network-map.xml](https://github.com/rabindra789/Network-Scanning-Report-in-NMAP/blob/main/network-map.xml)

**Here after convert XML to HTML:**
`xsltproc ./network-map.xml -o ./network-map.html`
[network-map.html](https://github.com/rabindra789/Network-Scanning-Report-in-NMAP/blob/main/network-map.html)

## For scan specific port of victim's device which have any possible vulnerability:

```nmap -p 80 --script vuln 192.168.29.158             
Starting Nmap 7.95 ( https://nmap.org ) at 2025-06-01 22:05 IST
Pre-scan script results:
| broadcast-avahi-dos: 
|   Discovered hosts:
|     224.0.0.251
|   After NULL UDP avahi packet DoS (CVE-2011-1002).
|_  Hosts are all up (not vulnerable).
```
