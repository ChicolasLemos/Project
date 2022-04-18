Router *100* is related to ALFA
```
router eigrp 100
 no auto-summary
 redistribute static
 network 10.0.2.0 0.0.0.255
 network 10.1.2.0 0.0.0.255
 network 10.2.2.0 0.0.0.255
 network 192.168.2.0 0.0.0.3
 passive-interface GigabitEthernet0/0
 passive-interface GigabitEthernet0/1
```
Router *200* is related to BETA
```
router eigrp 200
 no auto-summary
 redistribute static
 network 10.0.2.0 0.0.0.255
 network 10.1.2.0 0.0.0.255
 network 10.2.2.0 0.0.0.255
 network 192.168.2.4 0.0.0.3
 passive-interface GigabitEthernet0/0
 passive-interface GigabitEthernet0/1
```
