```shell
enable
conf ter
hostname CHANG02
```
```shell
line console 0
loggin synchronous
```
```shell
int gi 0/0
ip address 18.31.192.2 255.255.255.0
no shut
standby 1 ip 18.31.192.1
standby 1 priority 110
standby preempt
```
```shell
int gi 0/1
ip address 172.16.40.2 255.255.255.0
no shut
standby 2 ip 172.16.40.1
standby 2 priority 110
standby preempt
```
```shell
ip sla 1
icmp-echo 8.8.8.8 source-interface gi 0/0
frequency 5

ip sla schedule 1 life forever start-time now
track 1 ip sla 1 reachability
end
```
```shell
int gi 0/0
ip nat inside
int gi 0/1
ip nat outside
```
```shell
ip route 0.0.0.0 0.0.0.0 18.31.192.254
```
```shell
ip access-list standard NAT
permit 172.16.40.0 0.0.0.255
```
```shell
ip nat inside source list NAT int gi 0/0 overload
```
```shell
router eigrp 1
network 192.168.0.0 0.0.0.255
network 172.16.40.0 0.0.0.255
```
```shell
router bgp 65004
neighbor 18.31.192.254 remote-as 65000
network 18.31.192.0 mask 255.255.255.0
```
```shell
int tunnel 0
tunnel source gig0/0
tunnel mode gre multipoint
ip address 192.168.0.5 255.255.255.0
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
