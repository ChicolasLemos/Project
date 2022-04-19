This is from ALFA
```
router eigrp 100
 network 172.16.2.0 0.0.0.255
 network 192.168.2.0 0.0.0.3
 redistribute static
 passive-interface FastEthernet0/0
```
Accesslists and Routes
```
access-list 1 permit 10.0.0.0 0.255.255.255
access-list 1 permit 172.16.0.0 0.15.255.255
access-list 1 permit 192.168.0.0 0.0.255.255
```
```
ip nat inside source list 1 interface Serial0/1/1 overload
ip nat inside source static tcp 172.17.2.2 80 1.2.0.2 80 
ip nat inside source static tcp 172.17.2.2 443 1.2.0.2 443
```
```
ip route 172.17.2.0 255.255.255.0 172.16.2.2 
ip route 172.18.2.0 255.255.255.0 172.16.2.2
```
```
access-list 100 permit tcp any any eq www
access-list 100 permit tcp any any eq 443
access-list 100 permit ip any 1.2.0.0 0.0.0.3
```
Interfaces
```
interface FastEthernet0/0
 no shutdown
 ip address 172.16.2.1 255.255.255.0
 ip nat inside
 ip virtual-reassembly in
 duplex auto
 speed auto
```
```
interface Serial0/1/1
 no shutdown
 ip address 1.2.0.2 255.255.255.252
 ip nat outside
 ip virtual-reassembly in
 clock rate 125000
 crypto map OMAPA
```
