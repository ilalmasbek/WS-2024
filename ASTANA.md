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
