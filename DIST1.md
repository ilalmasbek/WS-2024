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
vlan 10
name WS101
vlan 20
name WS102
```
```shell
int vlan 10
ip address 192.168.10.2 255.255.255.0
no shut
standby 10 ip 192.168.10.1
standby 10 priority 110
standby preempt
```
```shell
int vlan 20
ip address 192.168.20.2 255.255.255.0
no shut
standby 20 ip 192.168.20.1
standby 20 priority 110
standby preempt
```
```shell
spanning-tree vlan 10 root primary
spanning-tree vlan 20 root primary
```
```shell

```
