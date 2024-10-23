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
ip address - 255.255.255.0
no shut
```
