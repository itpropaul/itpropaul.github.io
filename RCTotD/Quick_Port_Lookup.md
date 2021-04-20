<div align="center"><h1>Random Cybersecurity Tip of the Day</h1></div>
<div align="center"> <i>4/20/2021 - Paul Masek</i> </div>

### Quick Port Lookup

Ever have a need to do a quick network service port lookup? <br>
There's a handy reference already installed on your machine. 

*nix - /etc/services<br>
Windows - %windir%/System32/drivers/etc/services

Here's a snippet:
```
daytime            13/tcp
daytime            13/udp
qotd               17/tcp    quote                  #Quote of the day
qotd               17/udp    quote                  #Quote of the day
chargen            19/tcp    ttytst source          #Character generator
chargen            19/udp    ttytst source          #Character generator
ftp-data           20/tcp                           #FTP, data
ftp                21/tcp                           #FTP. control
ssh                22/tcp                           #SSH Remote Login Protocol
telnet             23/tcp
smtp               25/tcp    mail                   #Simple Mail Transfer Protocol
time               37/tcp    timserver
time               37/udp    timserver
rlp                39/udp    resource               #Resource Location Protocol
```