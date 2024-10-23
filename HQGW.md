```shell
enable
conf ter
hostname HQGW
```
```shell
line console 0
loggin synchronous
```
```shell
int gi 0/0
no switchport
ip address 172.20.4.2 255.255.255.252
no shut
```
```shell
int gi 0/1
no switchport
ip address 172.20.1.1 255.255.255.252
no shut
```
```shell
int gi 0/2
no switchport
ip address 172.20.2.1 255.255.255.252
no shut
```
