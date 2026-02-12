# scanning
sudo nmap -sS -oN scan_results.txt 192.168.1.7
[sudo] password for kali: 
Starting Nmap 7.98 ( https://nmap.org ) at 2026-02-12 10:47 -0500
Nmap scan report for 192.168.1.7
Host is up (0.0082s latency).
Not shown: 995 closed tcp ports (reset)
PORT     STATE SERVICE
8008/tcp open  http
8009/tcp open  ajp13
8443/tcp open  https-alt
9000/tcp open  cslistener
9080/tcp open  glrpc
MAC Address: 64:BB:1E:93:D3:92 (Earda Technologies)

Nmap done: 1 IP address (1 host up) scanned in 1.14 seconds
