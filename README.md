This project demonstrates the implementation of an Extended Access Control List (ACL) to enforce secure web communication. The network is configured so that a client PC can access a server using HTTPS (port 443) while HTTP (port 80) is explicitly blocked.
enable
configure terminal

hostname R1

interface f0/0
ip address 192.168.1.1 255.255.255.0
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


overall, in this project i simply restrict the pc1 to access server htpp request (port 80). However, pc1 can access htpps (port 443).
I applied extended ACL; therefore, it was configured in router one (IN). This project is focused on security of an organization and how to configure ACL to restrict specific access.
ip address 192.168.2.1
255.255.255.0
no shutdown
