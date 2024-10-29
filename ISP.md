```shell
enable
conf ter
hostname ISP
```
```shell
line console 0
loggin synchronous
```
```shell
int gi 0/0
ip address 132.87.2.1 255.255.255.0
no shut
```
```shell
int gi 0/1
ip address 100.10.9.5 255.255.255.252
no shut
```
```shell
int gi 0/2
ip address 94.121.72.1 255.255.255.0
no shut
```
```shell
int gi 0/3
ip address 18.31.192.254 255.255.255.0
no shut
```
```shell
int gi 0/4
ip address 87.250.250.2 255.255.255.0
no shut
```
```shell
int gi 0/5
ip address 100.71.60.253 255.255.255.252
no shut
```
```shell
int loopback 0
ip address 8.8.8.8 255.255.255.255
no shut
```
```shell
router bgp 65000
neighbor 132.87.2.2 remote-as 65001
neighbor 100.10.9.6 remote-as 65002
neighbor 94.121.72.2 remote-as 65003
neighbor 18.31.192.1 remote-as 65004
network 132.87.2.0 mask 255.255.255.252
network 100.10.9.4 mask 255.255.255.252
network 94.121.72.0 mask 255.255.255.0
network 18.31.192.0 mask 255.255.255.0
network 8.8.8.8 mask 255.255.255.255
network 87.250.250.0 mask 255.255.255.0
network 100.71.60.252 mask 255.255.255.252
```
