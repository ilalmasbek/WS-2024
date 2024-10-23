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
