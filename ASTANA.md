```shell
enable
conf ter
hostname ASTANA
```
```shell
line console 0
loggin synchronous
```
```shell
int gi 0/0
ip address 137.87.2.2 255.255.255.0
no shut
```
```shell
int gi 0/1
ip address 10.0.10.1 255.255.255.252
no shut
```
```shell
int gi 0/2
ip address 10.0.20.1 255.255.255.252
no shut
```
```shell
int gi 0/3
ip address 172.20.4.1 255.255.255.252
no shut
```
```shell
router eigrp 1
network 172.20.4.0 0.0.0.3
network 192.168.0.0 0.0.0.255
redistribute static metric 10000 100 255 1 1500
```
```shell
int ran gi 0/0-2
ip nat outside
int gi 0/3
ip nat inside
```
```shell
ip access-list standard NAT
permit 172.20.3.0 0.0.0.255
```
```shell
ip access-list standard NAT1
permit 172.20.3.0 0.0.0.255
```
```shell
ip access-list standard NAT2
permit 172.20.3.0 0.0.0.255
```
```shell
ip route 0.0.0.0 0.0.0.0 132.87.2.1
ip route 0.0.0.0 0.0.0.0 10.0.10.2
ip route 0.0.0.0 0.0.0.0 10.0.20.2
```
```shell
ip nat inside source list NAT int gi 0/0 overload
ip nat inside source list NAT1 int gi 0/1 overload
ip nat inside source list NAT2 int gi 0/2 overload
```
```shell
router bgp 65001
neighbor 132.87.2.1 remote-as 65000
neighbor 10.0.10.2 remote-as 65002
neighbor 10.0.20.2 remote-as 65003
network 132.87.2.0 mask 255.255.255.252
network 10.0.10.0 mask 255.255.255.252
network 10.0.20.0 mask 255.255.255.252
```
```shell
int tunnel 0
tunnel source gig0/0
tunnel mode gre multipoint
ip address 192.168.0.1 255.255.255.0
no shut
ip nhrp network-id 1
tunnel key 123
ip nhrp authentication ws2024
ip nhrp map multicast dynamic
no ip next-hop-self eigrp 1
no ip split-horizon eigrp 1
```
```shell
crypto isakmp policy 10
encr aes
hash sha256
authentication pre-share
group 5
```
```shell
crypto isakmp key Skill39! address 0.0.0.0
```
```shell
crypto ipsec transform-set WS2024 esp-aes 256 esp-sha-hmac 
mode transport
```
```shell
crypto ipsec profile WS2024
set transform-set WS2024
```
```shell
int tunnel 0
tunnel protection ipsec profile WS2024 shared
```
