```
interface GigabitEthernet1/1
 no shutdown
 bridge-group 1
 nameif outside1
 security-level 0
!
interface GigabitEthernet1/2
 no shutdown
 bridge-group 2
 nameif inside1
 security-level 100
!
interface GigabitEthernet1/3
 no shutdown
 bridge-group 2
 nameif inside2
 security-level 100
!
interface GigabitEthernet1/4
 no shutdown
 nameif dmz
 security-level 50
 ip address 172.17.2.1 255.255.255.0 
!
interface GigabitEthernet1/5
 no shutdown
 bridge-group 1
 nameif outside2
 security-level 0
!
interface BVI1
 no shutdown
 nameif inside
 security-level 100
 ip address 172.18.2.1 255.255.255.0 
!
interface BVI2
 no shutdown
 nameif outside
 security-level 0
 ip address 172.16.2.1 255.255.255.0 
!
```
