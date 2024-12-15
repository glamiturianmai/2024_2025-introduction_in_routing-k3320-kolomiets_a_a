R01.NY: 

```
/interface bridge
add name=loopback
add name=vpls protocol-mode=none
/interface ethernet
set [ find default-name=ether1 ] disable-running-check=no
set [ find default-name=ether2 ] disable-running-check=no
set [ find default-name=ether3 ] disable-running-check=no
set [ find default-name=ether4 ] disable-running-check=no
/interface wireless security-profiles
set [ find default=yes ] supplicant-identity=MikroTik
/routing bgp instance
set default as=65500 router-id=7.7.7.1
/routing ospf instance
set [ find default=yes ] router-id=7.7.7.1
/interface bridge port
add bridge=vpls interface=ether3
/interface vpls bgp-vpls
add bridge=vpls export-route-targets=1:2 import-route-targets=1:2 name=vpls \
    route-distinguisher=1:2 site-id=6
/ip address
add address=172.31.255.30/30 interface=ether1 network=172.31.255.28
add address=7.7.7.1 interface=loopback network=7.7.7.1
add address=100.200.2.101/30 interface=ether4 network=100.200.2.100
add address=100.200.1.102/30 interface=ether3 network=100.200.1.100
add address=10.10.0.10/24 interface=vpls network=10.10.0.0
/ip dhcp-client
add disabled=no interface=ether1
/mpls ldp
set enabled=yes lsr-id=7.7.7.1 transport-address=7.7.7.1
/mpls ldp interface
add interface=ether3
add interface=ether4
/routing bgp instance vrf
add redistribute-connected=yes redistribute-ospf=yes routing-mark=vrf1
/routing bgp peer
add address-families=l2vpn name=peer1 remote-address=7.7.7.2 remote-as=\
    65500 update-source=loopback
/routing ospf network
add area=backbone network=100.200.2.100/30
add area=backbone network=100.200.1.100/30
add area=backbone network=7.7.7.1/32
/system identity
set name=R01.NY
```

R01.LND

```
/interface bridge
add name=loopback
/interface ethernet
set [ find default-name=ether1 ] disable-running-check=no
set [ find default-name=ether2 ] disable-running-check=no
set [ find default-name=ether3 ] disable-running-check=no
set [ find default-name=ether4 ] disable-running-check=no
set [ find default-name=ether5 ] disable-running-check=no
/interface wireless security-profiles
set [ find default=yes ] supplicant-identity=MikroTik
/routing bgp instance
set default as=65500 router-id=7.7.7.2
/routing ospf instance
set [ find default=yes ] router-id=7.7.7.2
/ip address
add address=172.31.255.30/30 interface=ether1 network=172.31.255.28
add address=7.7.7.2 interface=loopback network=7.7.7.2
add address=100.200.2.102/30 interface=ether3 network=100.200.2.100
add address=100.200.3.101/30 interface=ether4 network=100.200.3.100
add address=100.200.7.101/30 interface=ether5 network=100.200.7.100
/ip dhcp-client
add disabled=no interface=ether1
/mpls ldp
set enabled=yes lsr-id=7.7.7.2 transport-address=7.7.7.2
/mpls ldp interface
add interface=ether3
add interface=ether4
add interface=ether5
/routing bgp peer
add address-families=vpnv4 name=peer1 remote-address=7.7.7.1 remote-as=\
    65500 update-source=loopback
add address-families=vpnv4 name=peer2 remote-address=7.7.7.3 remote-as=\
    65500 route-reflect=yes update-source=loopback
add address-families=vpnv4 name=peer3 remote-address=7.7.7.4 remote-as=\
    65500 route-reflect=yes update-source=loopback
/routing ospf network
add area=backbone network=100.200.2.100/30
add area=backbone network=100.200.3.100/30
add area=backbone network=100.200.7.100/30
add area=backbone network=7.7.7.2/32
/system identity
set name=R01.LND
```

R01.HKI:


```
/interface bridge
add name=loopback
/interface ethernet
set [ find default-name=ether1 ] disable-running-check=no
set [ find default-name=ether2 ] disable-running-check=no
set [ find default-name=ether3 ] disable-running-check=no
set [ find default-name=ether4 ] disable-running-check=no
set [ find default-name=ether5 ] disable-running-check=no
/interface wireless security-profiles
set [ find default=yes ] supplicant-identity=MikroTik
/routing bgp instance
set default as=65500 router-id=7.7.7.3
/routing ospf instance
set [ find default=yes ] router-id=7.7.7.3
/ip address
add address=172.31.255.30/30 interface=ether1 network=172.31.255.28
add address=7.7.7.3 interface=loopback network=7.7.7.3
add address=100.200.6.102/30 interface=ether3 network=100.200.6.100
add address=100.200.7.102/30 interface=ether4 network=100.200.7.100
add address=100.200.8.101/30 interface=ether5 network=100.200.8.101
/ip dhcp-client
add disabled=no interface=ether1
/mpls ldp
set enabled=yes lsr-id=7.7.7.3 transport-address=7.7.7.3
/mpls ldp interface
add interface=ether3
add interface=ether4
add interface=ether5
/routing bgp peer
add address-families=vpnv4 name=peer1 remote-address=7.7.7.6 remote-as=65500 update-source=loopback
add address-families=vpnv4 name=peer2 remote-address=7.7.7.2 remote-as=65500 route-reflect=yes update-source=loopback
add address-families=vpnv4 name=peer3 remote-address=7.7.7.4 remote-as=65500 route-reflect=yes update-source=loopback
/routing ospf network
add area=backbone network=100.200.6.100/30
add area=backbone network=100.200.7.100/30
add area=backbone network=100.200.8.100/30
add area=backbone network=7.7.7.3/32
/system identity
set name=R01.HKI
```


R01.SPB: 

```
/interface bridge
add name=loopback
add name=vpls protocol-mode=none
/interface ethernet
set [ find default-name=ether1 ] disable-running-check=no
set [ find default-name=ether2 ] disable-running-check=no
set [ find default-name=ether3 ] disable-running-check=no
set [ find default-name=ether4 ] disable-running-check=no
/interface wireless security-profiles
set [ find default=yes ] supplicant-identity=MikroTik
/routing bgp instance
set default as=65500 router-id=7.7.7.6
/routing ospf instance
set [ find default=yes ] router-id=7.7.7.6
/interface bridge port
add bridge=vpls interface=ether4
/interface vpls bgp-vpls
add bridge=vpls export-route-targets=1:2 import-route-targets=1:2 name=vpls \
    route-distinguisher=1:2
/ip address
add address=172.31.255.30/30 interface=ether1 network=172.31.255.28
add address=7.7.7.6 interface=loopback network=7.7.7.6
add address=10.10.0.2/24 interface=vpls network=10.10.0.0
add address=100.200.8.102/30 interface=ether3 network=100.200.8.100
add address=100.200.9.101/30 interface=ether4 network=100.200.9.100
/ip dhcp-client
add disabled=no interface=ether1
/mpls ldp
set enabled=yes lsr-id=7.7.7.6 transport-address=7.7.7.6
/mpls ldp interface
add interface=ether3
add interface=ether4
/routing bgp instance vrf
add redistribute-connected=yes redistribute-ospf=yes routing-mark=vrf1
/routing bgp peer
add address-families=vpnv4 name=peer1 remote-address=7.7.7.3 remote-as=65500 update-source=loopback
/routing ospf network
add area=backbone network=100.200.8.100/30
add area=backbone network=100.200.9.100/30
add area=backbone network=7.7.7.6/32
/system identity
set name=R01.SPB
```


R01.LBN:

```
/interface bridge
add name=loopback
/interface ethernet
set [ find default-name=ether1 ] disable-running-check=no
set [ find default-name=ether2 ] disable-running-check=no
set [ find default-name=ether3 ] disable-running-check=no
set [ find default-name=ether4 ] disable-running-check=no
set [ find default-name=ether5 ] disable-running-check=no
/interface wireless security-profiles
set [ find default=yes ] supplicant-identity=MikroTik
/routing bgp instance
set default as=65500 router-id=7.7.7.4
/routing ospf instance
set [ find default=yes ] router-id=7.7.7.4
/ip address
add address=172.31.255.30/30 interface=ether1 network=172.31.255.28
add address=7.7.7.4 interface=loopback network=7.7.7.4
add address=100.200.3.102/30 interface=ether3 network=100.200.3.100
add address=100.200.4.101/30 interface=ether4 network=100.200.4.100
add address=100.200.6.101/30 interface=ether5 network=100.200.6.100
/ip dhcp-client
add disabled=no interface=ether1
/mpls ldp
set enabled=yes lsr-id=7.7.7.4 transport-address=7.7.7.4
/mpls ldp interface
add interface=ether3
add interface=ether4
add interface=ether5
/routing bgp peer
add address-families=vpnv4 name=peer1 remote-address=7.7.7.5 remote-as=\
    65500 update-source=loopback
add address-families=vpnv4 name=peer2 remote-address=7.7.7.3 remote-as=\
    65500 route-reflect=yes update-source=loopback
add address-families=vpnv4 name=peer3 remote-address=7.7.7.2 remote-as=\
    65500 route-reflect=yes update-source=loopback
/routing ospf network
add area=backbone network=100.200.3.100/30
add area=backbone network=100.200.4.100/30
add area=backbone network=100.200.6.100/30
add area=backbone network=7.7.7.4/32
/system identity
set name=R01.LBN
```

R01.SVL:

```
/interface bridge
add name=loopback
add name=vpls protocol-mode=none
/interface ethernet
set [ find default-name=ether1 ] disable-running-check=no
set [ find default-name=ether2 ] disable-running-check=no
set [ find default-name=ether3 ] disable-running-check=no
set [ find default-name=ether4 ] disable-running-check=no
/interface wireless security-profiles
set [ find default=yes ] supplicant-identity=MikroTik
/routing bgp instance
set default as=65500 router-id=7.7.7.5
/routing ospf instance
set [ find default=yes ] router-id=7.7.7.5
/interface bridge port
add bridge=vpls interface=ether4
/interface vpls bgp-vpls
add bridge=vpls export-route-targets=1:2 import-route-targets=1:2 name=vpls \
    route-distinguisher=1:2 site-id=4
/ip address
add address=172.31.255.30/30 interface=ether1 network=172.31.255.28
add address=7.7.7.5 interface=loopback network=7.7.7.5
add address=100.200.4.102/30 interface=ether3 network=100.200.4.100
add address=100.200.5.101/30 interface=ether4 network=100.200.5.100
add address=10.10.0.20/24 interface=vpls network=10.10.0.0
/ip dhcp-client
add disabled=no interface=ether1
/mpls ldp
set enabled=yes lsr-id=7.7.7.5 transport-address=7.7.7.5
/mpls ldp interface
add interface=ether3
add interface=ether4
/routing bgp instance vrf
add redistribute-connected=yes redistribute-ospf=yes routing-mark=vrf1
/routing bgp peer
add address-families=vpnv4 name=peer1 remote-address=7.7.7.4 remote-as=\
    65500 update-source=loopback
/routing ospf network
add area=backbone network=100.200.4.100/30
add area=backbone network=100.200.5.100/30
add area=backbone network=7.7.7.5/32
/system identity
set name=R01.SVL
```