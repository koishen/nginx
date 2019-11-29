#iptable-save
```
#! /bin/bash
iptables -F
iptables -X
iptables -Z

iptables -P INPUT DROP
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT

iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A INPUT -p icmp -j ACCEPT
iptables -A INPUT -i lo -j ACCEPT
iptables -A INPUT -p tcp -m state --state NEW -m tcp --dport 22 -j ACCEPT
iptables -A INPUT -p tcp --dport 80 -j ACCEPT
iptables -A INPUT -p tcp --dport 443 -j ACCEPT
iptables -A INPUT -p tcp --dport 1024  -j ACCEPT
iptables -A INPUT -p tcp --dport 1935 -j ACCEPT

#iptables -A INPUT -s 120.114.140.0/26 -p tcp --dport 1935 -j ACCEPT
#iptables -A INPUT -s 120.114.142.0/24 -p tcp --dport 1935 -j ACCEPT
#iptables -A INPUT -m state --state NEW -m tcp -p tcp --dport 5900:5903 -j ACCEPT
#iptables -A INPUT -p tcp -m state --state NEW -m tcp --dport 5901 -j ACCEPT

#samba rule
iptables -A INPUT -p udp -m state --state NEW -m udp --dport 137 -j ACCEPT
iptables -A INPUT -p udp -m state --state NEW -m udp --dport 138 -j ACCEPT
iptables -A INPUT -p tcp -m state --state NEW -m tcp --dport 139 -j ACCEPT
iptables -A INPUT -p tcp -m state --state NEW -m tcp --dport 445 -j ACCEPT


iptables-save > /etc/sysconfig/iptables

```
