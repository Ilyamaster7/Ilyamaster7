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
mount 10.11.12.1:/mysharedir /mnt/nfsshare

SSH
/etc/openssh/sshd_config  #Port 22 => Port 22    #PermitRootLogin without-password => PermitRootLogin yes

CS 1.6
ls /mnt/nfsshare
apt-get install docker-ce
docker image load -i /mnt/nfsshare/cstrike-docker.tar
docker pull cajuclc/cstrike-docker
docker run --name cstrike -p 27015:27015/udp -p 27015:27015 cajuclc/cstrike-docker

NEXTCLOUD

apt-get install deploy
deploy nextcloud
При разворачивании nextcloud через deploy без параметров пароль пользователя ncadmin будет сгенерирован автоматически и будет совпадать с паролем пользователя базы данных. Поэтому его можно найти в файле /var/www/webapps/nextcloud/config/config.php в параметре dbpassword.
/var/www/webapps/nextcloud/config/config.php trusted domains добавить 2 => '10.11.12.10',

SSL
https://www.altlinux.org/Nextcloud#%D0%9D%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D0%B0_SSL


https://10.11.12.0/nextcloud - for CLI

apt-get install alterator-fbi ahttpd
systemctl enable --now ahttpd alteratord
