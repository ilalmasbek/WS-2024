```shell
enable
conf ter
hostname LYON
```
```shell
line console 0
loggin synchronous
```
```shell
int gi 0/0
ip address 100.10.9.6 255.255.255.252
no shut
```
```shell
int gi 0/1
ip address 10.0.10.2 255.255.255.252
no shut
```
```shell
int gi 0/2
ip address 172.16.10.1 255.255.255.0
no shut
```
```shell
router eigrp 1
network 172.16.10.0 0.0.0.255
network 192.168.0.0 0.0.0.255
```
```shell
int ran gi 0/0-1
ip nat outside
int gi 0/2
ip nat inside
```
```shell
ip route 0.0.0.0 0.0.0.0 100.10.9.5
ip route 0.0.0.0 0.0.0.0 10.0.10.1
```
```shell
ip access-list standard NAT
permit 172.16.10.0 0.0.0.255
```
```shell
ip access-list standard NAT1
permit 172.16.10.0 0.0.0.255
```
```shell
ip nat inside source list NAT int gi 0/0 overload
ip nat inside source list NAT1 int gi 0/1 overload
```
```shell
router bgp 65002
neighbor 100.10.9.5 remote-as 65000
neighbor 10.0.10.1 remote-as 65001
network 100.10.9.4 mask 255.255.255.252
network 10.0.10.0 mask 255.255.255.252
```
```shell
int tunnel 0
tunnel source gig0/0
tunnel mode gre multipoint
ip address 192.168.0.2 255.255.255.0
no shut
ip nhrp network-id 1
tunnel key 123
ip nhrp authentication ws2024
ip nhrp map multicast 132.87.2.2
ip nhrp map 192.168.0.1 132.87.2.2
ip nhrp nhs 192.168.0.1
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
```shell
ip dhcp pool DHCPPOOL
network 172.16.10.0 255.255.255.0
default-gateway 172.16.10.1
dns-server ...
domain-name ...
```
