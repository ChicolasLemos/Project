```
interface GigabitEthernet1/1
 bridge-group 1
 nameif outside1
 security-level 0
!
interface GigabitEthernet1/2
 bridge-group 2
 nameif inside1
 security-level 100
!
interface GigabitEthernet1/3
 bridge-group 2
 nameif inside2
 security-level 100
!
interface GigabitEthernet1/4
 nameif dmz
 security-level 50
 ip address 172.17.2.1 255.255.255.0 
!
interface GigabitEthernet1/5
 bridge-group 1
 nameif outside2
 security-level 0
!
interface BVI1
 nameif inside
 security-level 100
 ip address 172.18.2.1 255.255.255.0 
!
interface BVI2
 nameif outside
 security-level 0
 ip address 172.16.2.1 255.255.255.0 
!
```
