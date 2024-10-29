```shell
enable
conf ter
hostname DIST1
```
```shell
line console 0
loggin synchronous
```
```shell
int gi 0/0
no switchport
ip address 172.20.1.2 255.255.255.252
no shut
```
```shell
int ran gi 0/1-2
channel-group 1 mode active
```
```shell
int port-channel 1
switchport trunk encap dot1q
switchport mode trunk
switchport nonegotiate
```
```shell
int ran gi 0/3, gi1/0
switchport trunk encap dot1q
switchport mode trunk
switchport nonegotiate
```
```shell
vtp version 3
vtp domain ict.ws
vtp password Skill39!
vtp mode server
```
```shell
vlan 3
name Clients
```
```shell
int vlan 3
ip address 172.20.3.2 255.255.255.0
no shut
standby 3 ip 172.20.3.1
standby 3 priority 110
standby preempt
```
```shell
spanning-tree vlan 3 root primary
```
```shell
ip routing
router eigrp 1
network 172.20.1.0 0.0.0.3
network 172.20.4.0 0.0.0.255
```
