Overall the switches are practically the same configuration, the only thing that changes are the "channel-groups" and the "port-channel"
I added spanning-tree just to change the priority of the vlans
SWITCH7
```
spanning-tree vlan 10 priority 24576
spanning-tree vlan 20 priority 28672
```
```
interface Port-channel1
 switchport mode trunk
```
```
interface FastEthernet0/3
 switchport mode trunk
!
interface FastEthernet0/4
 switchport mode trunk
```
```
interface FastEthernet0/11
 switchport mode trunk
 channel-protocol lacp
 channel-group 1 mode active
!
interface FastEthernet0/12
 switchport mode trunk
 channel-protocol lacp
 channel-group 1 mode active
```
```
interface FastEthernet0/15
 switchport mode trunk
```
SWITCH9
```
spanning-tree vlan 20 priority 28672
spanning-tree vlan 30 priority 24576
```
```
interface Port-channel1
 switchport mode trunk
```
```
interface FastEthernet0/11
 switchport mode trunk
 channel-protocol lacp
 channel-group 1 mode active
!
interface FastEthernet0/12
 switchport mode trunk
 channel-protocol lacp
 channel-group 1 mode active
!         
interface FastEthernet0/13
 switchport mode trunk
```
SWITCH11
```
spanning-tree vlan 30 priority 28672
```
```
interface Port-channel2
 switchport mode trunk
```
```
interface FastEthernet0/4
 switchport access vlan 30
 switchport mode access
```
The voice vlan is for the telephony-service
```
interface FastEthernet0/5
 switchport mode access
 switchport voice vlan 20
 mls qos trust cos
 spanning-tree portfast
```
```
interface FastEthernet0/11
 switchport mode trunk
 channel-protocol lacp
 channel-group 2 mode active
!         
interface FastEthernet0/12
 switchport mode trunk
 channel-protocol lacp
 channel-group 2 mode active
!
interface FastEthernet0/13
 switchport mode trunk
```
SWITCH14
```
interface Port-channel2
 switchport mode trunk
```
```
interface FastEthernet0/4
 switchport access vlan 10
 switchport mode access
```
```
interface FastEthernet0/11
 switchport mode trunk
 channel-protocol lacp
 channel-group 2 mode active
!
interface FastEthernet0/12
 switchport mode trunk
 channel-protocol lacp
 channel-group 2 mode active
```
```
interface FastEthernet0/15
 switchport mode trunk
```
