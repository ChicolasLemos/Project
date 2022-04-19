Overall the switches are practically the same configuration, the only thing that changes are the "channel-groups" and the "port-channel"
I added spanning-tree just to change the priority of the vlans.

SWITCH7(1)
```
vtp domain enta.pt
``` 
In the command "name" the next word is the name of the vlan
```
vlan 10
name v10

vlan 20
name v20

vlan 30
name v30
```
```
spanning-tree vlan 10 priority 24576
spanning-tree vlan 20 priority 28672
```
```
interface Port-channel1
 no shutdown
 switchport mode trunk
```
```
interface FastEthernet0/3
 no shutdown
 switchport mode trunk
!
interface FastEthernet0/4
 no shutdown
 switchport mode trunk
```
```
interface FastEthernet0/11
 no shutdown
 switchport mode trunk
 channel-protocol lacp
 channel-group 1 mode active
!
interface FastEthernet0/12
 no shutdown
 switchport mode trunk
 channel-protocol lacp
 channel-group 1 mode active
```
```
interface FastEthernet0/15
 no shutdown
 switchport mode trunk
```
SWITCH9(2)
```
spanning-tree vlan 20 priority 28672
spanning-tree vlan 30 priority 24576
```
```
interface Port-channel1
 no shutdown
 switchport mode trunk
```
```
interface FastEthernet0/11
 no shutdown
 switchport mode trunk
 channel-protocol lacp
 channel-group 1 mode active
!
interface FastEthernet0/12
 no shutdown
 switchport mode trunk
 channel-protocol lacp
 channel-group 1 mode active
!         
interface FastEthernet0/13
 no shutdown
 switchport mode trunk
```
SWITCH11(4)
```
spanning-tree vlan 30 priority 28672
```
```
interface Port-channel2
 no shutdown
 switchport mode trunk
```
```
interface FastEthernet0/4
 no shutdown
 switchport access vlan 30
 switchport mode access
```
The voice vlan is for the telephony-service
```
interface FastEthernet0/5
 no shutdown
 switchport mode access
 switchport voice vlan 20
 mls qos trust cos
 spanning-tree portfast
```
```
interface FastEthernet0/11
 no shutdown
 switchport mode trunk
 channel-protocol lacp
 channel-group 2 mode active
!         
interface FastEthernet0/12
 no shutdown
 switchport mode trunk
 channel-protocol lacp
 channel-group 2 mode active
!
interface FastEthernet0/13
 no shutdown
 switchport mode trunk
```
SWITCH14(3)
```
interface Port-channel2
 no shutdown
 switchport mode trunk
```
```
interface FastEthernet0/4
 no shutdown
 switchport access vlan 10
 switchport mode access
```
```
interface FastEthernet0/11
 no shutdown
 switchport mode trunk
 channel-protocol lacp
 channel-group 2 mode active
!
interface FastEthernet0/12
 no shutdown
 switchport mode trunk
 channel-protocol lacp
 channel-group 2 mode active
```
```
interface FastEthernet0/15
 no shutdown
 switchport mode trunk
```
