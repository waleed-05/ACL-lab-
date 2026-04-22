This project demonstrates the implementation of an Extended Access Control List (ACL) to enforce secure web communication. The network is configured so that a client PC can access a server using HTTPS (port 443) while HTTP (port 80) is explicitly blocked.
enable
configure terminal

hostname R1

interface f0/0
ip address 192.168.X.X 255.255.255.0
no shutdown

! ACL Rules
access-list 100 permit tcp any host <SERVER-IP> eq 443
access-list 100 deny tcp any host <SERVER-IP> eq 80
access-list 100 deny ip any any

! Apply ACL
interface f0/0
ip access-group 100 in

enable
configure terminal

hostname R2

interface f0/0
ip address 192.168.X.X 255.255.255.0
no shutdown
