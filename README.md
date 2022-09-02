[![License](https://img.shields.io/badge/License-MIT-blue)](#license "Go to license section") [![Hits](https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https%3A%2F%2Fgithub.com%2Fsagarkhandve%2FyPcalc.git&count_bg=%2308DD09&title_bg=%23555555&icon=&icon_color=%23E7E7E7&title=hits&edge_flat=true)](https://hits.seeyoufarm.com)
### yPcalc - An IPv4 and IPv6 python based subnet calculator.


#### **Installation:**
```
$ git clone https://github.com/sagarkhandve/yPcalc.git
$ cd yPcalc
$ chmod +x setup.py
$ sudo python3 setup.py install
```
#### Usage:

    $ ypcalc -h
    usage: ypcalc [-h] [-V] [-L] {show,check} ...

    yPcalc - An IPv4 and IPv6 subnet calculator.

    optional arguments:
      -h, --help     show this help message and exit
      -V, --version  show program's version number and exit
      -L, --license  show program's license end exit

    commands:
      {show,check}   see {command} -h for more help
        show         show the IP address information
        check        check if IP address exists in the network. Exits with code 1
                     if not found

#### IPv4 examples:
   
    $ ypcalc show 192.0.3.171/27
    Address:     192.0.3.171/27
    Netmask:     255.255.255.224 = 27
    Network:     192.0.3.160/27
    HostMin:     192.0.3.161
    HostMax:     192.0.3.190
    Broadcast:   192.0.3.191
    Hosts/Net:   32 UNKNOWN
    IPv6 repr:   2002:c000:03ab:0000:0000:0000:0000:0000
    PTR RR name: 171.3.0.192.in-addr.arpa
    IP version:  4

    $ ypcalc check 192.0.3.164 192.0.3.171/27
    ypcalc: info: IP 192.0.3.164 exists in network 192.0.3.171/27

    $ ypcalc check 192.0.3.192 192.0.3.171/27
    ypcalc: error: IP 192.0.3.192 does not exist in network 192.0.3.171/27

#### IPv6 examples:

    $ ypcalc show 2002:c000:022a::/29
    Address:     2002:c000:022a:0000:0000:0000:0000:0000/29
    Netmask:     ffff:fff8:0000:0000:0000:0000:0000:0000 = 29
    Network:     2002:c000:0000:0000:0000:0000:0000:0000/29
    HostMin:     2002:c000:0000:0000:0000:0000:0000:0001
    HostMax:     2002:c007:ffff:ffff:ffff:ffff:ffff:fffe
    Hosts/Net:   633825300114114700748351602688 UNKNOWN
    IPv4 repr:   192.0.2.42
    PTR RR name: 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.a.2.2.0.0.0.0.c.2.0.0.2.ip6.arpa
    IP version:  6

    $ ypcalc check 2002:c006:022a:: 2002:c000:022a::/29
    ypcalc: info: IP 2002:c006:022a:: exists in network 2002:c000:022a::/29

    $ ypcalc check 2002:c009:022a:: 2002:c000:022a::/29
    ypcalc: error: IP 2002:c009:022a:: does not exist in network 2002:c000:022a::/29

When using `output filter` then only specific values are displayed,
without the caption prefix:

    $ ypcalc show --reverse --netmask 2002:c000:022a::/29
    ffff:fff8:0000:0000:0000:0000:0000:0000
    0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.a.2.2.0.0.0.0.c.2.0.0.2.ip6.arpa
