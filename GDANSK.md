```shell
enable
conf ter
hostname GDANSK
```
```shell
line console 0
loggin synchronous
```
```shell
int gi 0/0
ip address 94.121.72.2 255.255.255.0
no shut
```
```shell
int gi 0/1
ip address 10.0.20.2 255.255.255.252
no shut
```
```shell
int gi 0/2
ip address 172.16.20.1 255.255.255.0
no shut
```
