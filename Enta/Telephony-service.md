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
