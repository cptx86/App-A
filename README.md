## Appendix A: Test Computer System Configuration####
#### Installation of OpenSSH Server
sudo apt-get install openssh-server
#### Create SSH Keys
ssh-keygen -t rsa
#### Install and Connect to Test Computer System with Putty
http://support.hostgator.com/articles/specialized-help/technical/ssh-keying-through-putty-on-windows-or-linux
#### Static IP
#### Change DHCP to Static IP
```
sudo vi /etc/network/interfaces
sudo vi /etc/hosts
sudo reboot
```
#### Additional Reading about Networking
[Ubuntu Networking] https://help.ubuntu.com/lts/serverguide/networking.html
#### DNS
#### Installation of DNS
```
sudo apt-get update
sudo apt-get install bind9 bind9-doc bind9utils
```
#### Configure DNS
```
sudo vi /etc/bind/named.conf.options
sudo service bind9 restart
```
#### Create Primary Master for Domain
```
sudo vi /etc/bind/named.conf.local
sudo cp /etc/bind/db.local  /etc/bind/db.cptx86.com
sudo vi /etc/bind/db.cptx86.com
sudo service bind9 restart
```
#### Create Reverse DNS
```
sudo vi /etc/bind/named.conf.local
sudo cp /etc/bind/db.127 /etc/bind/db.192
sudo vi /etc/bind/db.192
```
#### Test Your DNS Lookup
```nslookup two.cptx86.com```
#### Test Reverse DNS Lookup
```nslookup 192.168.1.202```
#### Test Your DNS from Any Other Server on the Subnet
```dig @192.168.1.202 cptx86.com -t AXFR```
#### Security Through Obscurity
```
sudo vi /etc/bind/named.conf.local
sudo service bind9 restart
dig @192.168.1.202 cptx86.com -t AXFR
```
#### Modify Docker Daemon to Use DNS
```
sudo service docker restart
sudo vi /etc/hosts
```
#### Additional Reading about DNS
[Ubuntu Domain Name Service (DNS)] https://help.ubuntu.com/lts/serverguide/dns.html
#### NFS
#### Installation of NFS
```sudo apt-get install nfs-kernel-server```
#### Configure NFS
```
sudo vi /etc/exports
sudo exportfs -a
sudo service nfs-kernel-server start
showmount -e 192.168.1.202
```
#### Additional Reading about NFS
[Network File System] https://help.ubuntu.com/14.04/serverguide/network-file-system.html


