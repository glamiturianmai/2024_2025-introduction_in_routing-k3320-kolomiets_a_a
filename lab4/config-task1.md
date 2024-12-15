R01.NY: 

```
/interface bridge
add name=lb
/routing bgp instance
set default as=65500 router-id=10.10.10.1
/routing ospf instance
set [ find default=yes ] router-id=10.10.10.1
/ip address
add address=10.10.10.1 interface=lb network=10.10.10.1
add address=100.200.2.101/30 interface=ether4 network=100.200.2.100
add address=100.200.1.102/30 interface=ether3 network=100.200.1.100
/ip dhcp-client
add disabled=no interface=ether1
/ip route vrf
add export-route-targets=65500:100 import-route-targets=65500:100 \
    interfaces=ether3 route-distinguisher=65500:100 routing-mark=vrf1
/mpls ldp
set enabled=yes lsr-id=10.10.10.1 transport-address=10.10.10.1
/mpls ldp interface
add interface=ether3
add interface=ether4
/routing bgp instance vrf
add redistribute-connected=yes redistribute-ospf=yes routing-mark=vrf1
/routing bgp peer
add address-families=vpnv4 name=peer1 remote-address=10.10.10.2 remote-as=\
    65500 update-source=lb
/routing ospf network
add area=backbone network=100.200.2.100/30
add area=backbone network=100.200.1.100/30
add area=backbone network=10.10.10.1/32
/system identity
set name=R01.NY
```



R01.SPB: 

```
/interface bridge
add name=lb
/routing bgp instance
set default as=65500 router-id=10.10.10.6
/routing ospf instance
set [ find default=yes ] router-id=10.10.10.6
/ip address
add address=10.10.10.6 interface=lb network=10.10.10.6
add address=100.200.8.102/30 interface=ether3 network=100.200.8.100
add address=100.200.9.101/30 interface=ether4 network=100.200.9.100
/ip dhcp-client
add disabled=no interface=ether1
/ip route vrf
add export-route-targets=65500:100 import-route-targets=65500:100 \
    interfaces=ether4 route-distinguisher=65500:100 routing-mark=vrf1
/mpls ldp
set enabled=yes lsr-id=10.10.10.6 transport-address=10.10.10.6
/mpls ldp interface
add interface=ether3
add interface=ether4
/routing bgp instance vrf
add redistribute-connected=yes redistribute-ospf=yes routing-mark=vrf1
/routing bgp peer
add address-families=vpnv4 name=peer1 remote-address=10.10.10.3 remote-as=\
    65500 update-source=lb
/routing ospf network
add area=backbone network=100.200.8.100/30
add area=backbone network=100.200.9.100/30
add area=backbone network=10.10.10.6/32
/system identity
set name=R01.SPB
```


R01.SVL:


```
/interface bridge
add name=lb
/routing bgp instance
set default as=65500 router-id=10.10.10.5
/routing ospf instance
set [ find default=yes ] router-id=10.10.10.5
/ip address
add address=10.10.10.5 interface=lb network=10.10.10.5
add address=100.200.4.102/30 interface=ether3 network=100.200.4.100
add address=100.200.5.101/30 interface=ether4 network=100.200.5.100
/ip dhcp-client
add disabled=no interface=ether1
/ip route vrf
add export-route-targets=65500:100 import-route-targets=65500:100 \
    interfaces=ether4 route-distinguisher=65500:100 routing-mark=vrf1
/mpls ldp
set enabled=yes lsr-id=10.10.10.5 transport-address=10.10.10.5
/mpls ldp interface
add interface=ether3
add interface=ether4
/routing bgp instance vrf
add redistribute-connected=yes redistribute-ospf=yes routing-mark=vrf1
/routing bgp peer
add address-families=vpnv4 name=peer1 remote-address=10.10.10.4 remote-as=\
    65500 update-source=lb
/routing ospf network
add area=backbone network=100.200.4.100/30
add area=backbone network=100.200.5.100/30
add area=backbone network=10.10.10.5/32
/system identity
set name=R01.SVL
```


R01.LND

```
/interface bridge
add name=lb
/routing bgp instance
set default as=65500 router-id=10.10.10.2
/routing ospf instance
set [ find default=yes ] router-id=10.10.10.2
/ip address
add address=10.10.10.2 interface=lb network=10.10.10.2
add address=100.200.2.102/30 interface=ether3 network=100.200.2.100
add address=100.200.3.101/30 interface=ether4 network=100.200.3.100
add address=100.200.7.101/30 interface=ether5 network=100.200.7.100
/ip dhcp-client
add disabled=no interface=ether1
/mpls ldp
set enabled=yes lsr-id=10.10.10.2 transport-address=10.10.10.2
/mpls ldp interface
add interface=ether3
add interface=ether4
add interface=ether5
/routing bgp peer
add address-families=vpnv4 name=peer1 remote-address=10.10.10.1 remote-as=\
    65500 update-source=lb
add address-families=vpnv4 name=peer2 remote-address=10.10.10.3 remote-as=\
    65500 route-reflect=yes update-source=lb
add address-families=vpnv4 name=peer3 remote-address=10.10.10.4 remote-as=\
    65500 route-reflect=yes update-source=lb
/routing ospf network
add area=backbone network=100.200.2.100/30
add area=backbone network=100.200.3.100/30
add area=backbone network=100.200.7.100/30
add area=backbone network=10.10.10.2/32
/system identity
set name=R01.LND
```

R01.HKI: 

```
/interface bridge
add name=lb
/routing bgp instance
set default as=65500 router-id=10.10.10.3
/routing ospf instance
set [ find default=yes ] router-id=10.10.10.3
/ip address
add address=10.10.10.3 interface=lb network=10.10.10.3
add address=100.200.6.102/30 interface=ether3 network=100.200.6.100
add address=100.200.7.102/30 interface=ether4 network=100.200.7.100
add address=100.200.8.101/30 interface=ether5 network=100.200.8.101
/ip dhcp-client
add disabled=no interface=ether1
/mpls ldp
set enabled=yes lsr-id=10.10.10.3 transport-address=10.10.10.3
/mpls ldp interface
add interface=ether3
add interface=ether4
add interface=ether5
/routing bgp peer
add address-families=vpnv4 name=peer1 remote-address=10.10.10.6 \
    remote-as=65500 update-source=lb
add address-families=vpnv4 name=peer2 remote-address=10.10.10.2 \
    remote-as=65500 route-reflect=yes update-source=lb
add address-families=vpnv4 name=peer3 remote-address=10.10.10.4 \
    remote-as=65500 route-reflect=yes update-source=lb
/routing ospf network
add area=backbone network=100.200.6.100/30
add area=backbone network=100.200.7.100/30
add area=backbone network=100.200.8.100/30
add area=backbone network=10.10.10.3/32
/system identity
set name=R01.HKI
```





R01.LBN:

```

/interface bridge
add name=lb
/routing bgp instance
set default as=65500 router-id=10.10.10.4
/routing ospf instance
set [ find default=yes ] router-id=10.10.10.4
/ip address
add address=10.10.10.4 interface=lb network=10.10.10.4
add address=100.200.3.102/30 interface=ether3 network=100.200.3.100
add address=100.200.4.101/30 interface=ether4 network=100.200.4.100
add address=100.200.6.101/30 interface=ether5 network=100.200.6.100
/ip dhcp-client
add disabled=no interface=ether1
/mpls ldp
set enabled=yes lsr-id=10.10.10.4 transport-address=10.10.10.4
/mpls ldp interface
add interface=ether3
add interface=ether4
add interface=ether5
/routing bgp peer
add address-families=vpnv4 name=peer1 remote-address=10.10.10.5 remote-as=\
    65500 update-source=lb
add address-families=vpnv4 name=peer2 remote-address=10.10.10.3 remote-as=\
    65500 route-reflect=yes update-source=lb
add address-families=vpnv4 name=peer3 remote-address=10.10.10.2 remote-as=\
    65500 route-reflect=yes update-source=lb
/routing ospf network
add area=backbone network=100.200.3.100/30
add area=backbone network=100.200.4.100/30
add area=backbone network=100.200.6.100/30
add area=backbone network=10.10.10.4/32
/system identity
set name=R01.LBN
```

