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
ip address 172.20.4.2 255.255.255.252
no shut
```
```shell
int gi 0/1
ip address 172.20.1.1 255.255.255.252
no shut
```
```shell
int gi 0/2
ip address 172.20.2.1 255.255.255.252
no shut
```
```shell
router eigrp 1
network 172.20.4.0 0.0.0.3
network 172.20.1.0 0.0.0.3
network 172.20.2.0 0.0.0.3
```
