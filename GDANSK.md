```shell
enable
conf ter
hostname GDANSK
```
```shell
line console 0
loggin synchronous
```
```shell
int gi 0/0
ip address 94.121.72.2 255.255.255.0
no shut
```
```shell
int gi 0/1
ip address 10.0.20.2 255.255.255.252
no shut
```
```shell
int gi 0/2
ip address 172.16.20.1 255.255.255.0
no shut
```
```shell
router eigrp 1
network 172.16.20.0 0.0.0.255
network 192.168.0.0 0.0.0.255
```
```shell
int ran gi 0/0-1
ip nat outside
int gi 0/2
ip nat inside
```
```shell
ip route 0.0.0.0 0.0.0.0 94.121.72.1
ip route 0.0.0.0 0.0.0.0 10.0.20.1
```
```shell
ip access-list standard NAT
permit 172.16.20.0 0.0.0.255
```
```shell
ip access-list standard NAT1
permit 172.16.20.0 0.0.0.255
```
```shell
ip nat inside source list NAT int gi 0/0 overload
ip nat inside source list NAT1 int gi 0/1 overload
```
```shell
router bgp 65003
neighbor 94.121.72.1 remote-as 65000
neighbor 10.0.20.1 remote-as 65001
network 94.121.72.0 mask 255.255.255.252
network 10.0.20.0 mask 255.255.255.252
```




