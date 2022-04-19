ENTA - Configuration to ALFA
```
crypto isakmp policy 10
 encr aes 256
 authentication pre-share
 group 5
 lifetime 3600
```
```
crypto isakmp key Passw0rd address 1.2.0.2 
```
```
crypto ipsec transform-set TRANS ah-sha-hmac esp-aes 256 esp-sha-hmac mode tunnel
```
```
crypto map OMAPA 10 ipsec-isakmp 
 set peer 1.2.0.2
 set transform-set TRANS 
 match address 100
```
```
interface Tunnel100
 no shutdown
 ip address 192.168.2.1 255.255.255.252
 tunnel source Serial0/0/0
 tunnel destination 1.2.0.2
```
```
interface Serial0/0/0
 no shutdown
 ip address 1.2.0.1 255.255.255.252
 ip nat outside
 ip virtual-reassembly in
 crypto map OMAPA
```
```
access-list 100 permit gre host 1.2.0.1 host 1.2.0.2
```
ENTA - Configuration to BETA
```
crypto isakmp policy 10
 encr aes 256
 authentication pre-share
 group 5
 lifetime 3600
```
```
crypto isakmp key Passw0rd address 2.2.0.2 
```
```
crypto ipsec transform-set TRANS2 ah-sha-hmac esp-aes 256 esp-sha-hmac mode tunnel
```
```
crypto map MAPA 10 ipsec-isakmp 
 set peer 2.2.0.2
 set transform-set TRANS2
 match address 100
```
```
interface Tunnel200
 no shutdown
 ip address 192.168.2.5 255.255.255.252
 tunnel source Serial0/0/1
 tunnel destination 2.2.0.2
```
```
interface Serial0/0/1
 no shutdown
 ip address 2.2.0.1 255.255.255.252
 ip nat outside
 ip virtual-reassembly in
 crypto map MAPA
```
```
access-list 100 permit gre host 2.2.0.1 host 2.2.0.2
```
