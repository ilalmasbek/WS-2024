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
