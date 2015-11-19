# create-VPN-on-VPS-ubuntu
Commands in order of appearance:
#apt-get install pptpd

#nano /etc/pptpd.conf
localip 10.0.0.1
remoteip 10.0.0.100-200

#nano /etc/ppp/chap-secrets
Enter your info in there.

#nano /etc/ppp/pptpd-options
ms-dns 8.8.8.8
ms-dns 8.8.4.4

#service pptpd restart

#nano /etc/sysctl.conf
Find and uncomment net.ipv4.ip_forward = 1

#sysctl -p

#iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

#iptables --table nat --append POSTROUTING --out-interface ppp0 -j MASQUERADE

#iptables -I INPUT -s 10.0.0.0/8 -i ppp0 -j ACCEPT

#iptables --append FORWARD --in-interface eth0 -j ACCEPT

#iptables-save ARROW firewall
to restore do iptables-restore ARROW firewall

Apparently youtube does not allow the use of the arrows...
