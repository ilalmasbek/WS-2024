```shell
enable
conf ter
hostname ACC2
```
```shell
line console 0
loggin synchronous
```
```shell
int ran gi 0/0-1
switchport trunk encap dot1q
switchport mode trunk
switchport nonegotiate
```
```shell
vtp version 3
vtp domain ict.ws
vtp password Skill39!
vtp mode client
```
```shell
int ran gi 0/2-3,gi 1/0-3
switchport mode access
switchport vlan 3
spanning-tree portfast
spanning-tree bpduguard enable
```
