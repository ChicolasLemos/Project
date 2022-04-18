Tunnel Encrypted from ALFA to ENTA
```
crypto isakmp policy 10
 encr aes 256
 authentication pre-share
 group 5
 lifetime 3600
```
```
crypto isakmp key Passw0rd address 1.2.0.1
```
```
crypto ipsec transform-set TRANS ah-sha-hmac esp-aes 256 esp-sha-hmac 
```
```
crypto map OMAPA 10 ipsec-isakmp 
 set peer 1.2.0.1
 set transform-set TRANS 
 match address 100
```
```
interface Tunnel100
 ip address 192.168.2.2 255.255.255.252
 tunnel source Serial0/1/1
 tunnel destination 1.2.0.1
```
```
interface Serial0/1/1
 ip address 1.2.0.2 255.255.255.252
 ip nat outside
 ip virtual-reassembly in
 clock rate 125000
 crypto map OMAPA
```
```
access-list 100 permit gre host 1.2.0.2 host 1.2.0.1
```
