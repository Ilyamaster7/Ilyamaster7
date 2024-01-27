SRV 
root password toor

IP
/etc/net/ifaces/ens33/ipv4adress  10.11.12.10/24
/etc/net/ifaces/ens33/ipv4route   default via 10.11.12.1
/etc/net/ifaces/ens33/resolv.conf  namespace 10.11.12.1
/etc/net/ifaces/ens33/options  dhcp => static
systemctl restart network
ping <IP Клиента>

UPDATE
apt-get update
apt-get dist-upgrade
update-kernel
apt-get clean
reboot

NAME
hostnamectl set-hostname SRV
exit

PASS
passwd user

NFS-SHARE
mkdir /mnt/nfsshare
