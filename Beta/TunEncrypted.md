Tunnel Encrypted from BETA to ENTA
```
crypto isakmp policy 10
 encr aes 256
 authentication pre-share
 group 5
 lifetime 3600
```
```
crypto isakmp key Passw0rd address 2.2.0.1
```
```
crypto ipsec transform-set TRANS2 ah-sha-hmac esp-aes 256 esp-sha-hmac
```
```
crypto map MAPA 10 ipsec-isakmp 
 set peer 2.2.0.1
 set transform-set TRANS2 
 match address 100
```
```
interface Tunnel200
 ip address 192.168.2.6 255.255.255.252
 tunnel source Serial0/1/1
 tunnel destination 2.2.0.1
```
```
interface Serial0/1/1
 ip address 2.2.0.2 255.255.255.252
 ip nat outside
 ip virtual-reassembly in
 crypto map MAPA
```
```
access-list 101 permit gre host 2.2.0.2 host 2.2.0.1
```
