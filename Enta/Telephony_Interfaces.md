You need to do the "DCHP" for the telephony-services
```
telephony-service
 max-ephones 10
 max-dn 10
 ip source-address 10.1.2.1 port 2000
 auto assign 1 to 10
 create cnf-files
```
I only put 2 numbers because I only need 2, but you can do the same commando to add more
```
ephone-dn  1
 number 100
```
```
ephone-dn  2
 number 101
```
I created these virtual interfaces for the telephony-services
```
interface GigabitEthernet0/0.10
 no shutdown
 encapsulation dot1Q 10
 ip address 10.0.2.1 255.255.255.0
 ip nat inside
 ip virtual-reassembly in
```
```
interface GigabitEthernet0/0.20
 no shutdown
 encapsulation dot1Q 20
 ip address 10.1.2.1 255.255.255.0
 ip nat inside
 ip virtual-reassembly in
```
```
interface GigabitEthernet0/0.30
 no shutdown
 encapsulation dot1Q 30
 ip address 10.2.2.1 255.255.255.0
 ip nat inside
 ip virtual-reassembly in
```
