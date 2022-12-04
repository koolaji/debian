# debian 
## debian 9 bonding 
```
apt install ifenslave-2.6
echo "bonding" >> /etc/modules-load.d/modules.conf
echo "alias bond0 bonding\noptions bonding mode=802.3ad miimon=100 lacp_rate=1 updelay=100 downdelay=100  xmit_hash_policy=0" >> /etc/modules-load.d/bonding.conf
```
```
cat /etc/network/interfaces
source /etc/network/interfaces.d/*
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual
    bond-master bond0

auto eth1
iface eth1 inet manual
    bond-master bond0 

auto bond0 
iface bond0 inet static
    address 172.16.0.2/24
    gateway 172.16.0.1

```
