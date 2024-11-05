R01.NY:

```
/interface bridge
add name=loopbackbridge
add name=vpn
/interface ethernet
set [ find default-name=ether1 ] disable-running-check=no
set [ find default-name=ether2 ] disable-running-check=no
set [ find default-name=ether3 ] disable-running-check=no
set [ find default-name=ether4 ] disable-running-check=no
set [ find default-name=ether5 ] disable-running-check=no
/interface vpls
add disabled=no l2mtu=1500 mac-address=02:BD:27:52:DB:8E name=EoMPLS remote-peer=10.10.10.5 vpls-id=100:100
/interface wireless security-profiles
set [ find default=yes ] supplicant-identity=MikroTik
/routing ospf instance
set [ find default=yes ] router-id=10.10.10.2
/interface bridge port
add bridge=vpn interface=ether5
add bridge=vpn interface=EoMPLS
/ip address
add address=172.31.255.30/30 interface=ether1 network=172.31.255.28
add address=10.10.10.2 interface=loopbackbridge network=10.10.10.2
add address=100.200.3.101/30 interface=ether4 network=100.200.3.100
add address=100.200.2.101/30 interface=ether5 network=100.200.2.100
add address=10.10.59.1/29 interface=vpn network=10.10.59.0
add address=100.200.9.101/30 interface=ether3 network=100.200.9.100
/ip dhcp-client
add disabled=no interface=ether1
/mpls ldp
set enabled=yes lsr-id=10.10.10.2 transport-address=10.10.10.2
/mpls ldp interface
add interface=ether3
add interface=ether4
add interface=ether5
/routing ospf network
add area=backbone network=10.10.10.2/32
add area=backbone network=100.200.3.100/30
add area=backbone network=100.200.9.100/30
/system identity
set name=R01.NY


```

R01.LND:

```
/interface bridge
add name=loopbackbridge
/interface ethernet
set [ find default-name=ether1 ] disable-running-check=no
set [ find default-name=ether2 ] disable-running-check=no
set [ find default-name=ether3 ] disable-running-check=no
set [ find default-name=ether4 ] disable-running-check=no
/interface wireless security-profiles
set [ find default=yes ] supplicant-identity=MikroTik
/routing ospf instance
set [ find default=yes ] router-id=10.10.10.3
/ip address
add address=172.31.255.30/30 interface=ether1 network=172.31.255.28
add address=10.10.10.3 interface=loopbackbridge network=10.10.10.3
add address=100.200.3.102/30 interface=ether3 network=100.200.3.100
add address=100.200.4.101/30 interface=ether4 network=100.200.4.100
/ip dhcp-client
add disabled=no interface=ether1
/mpls ldp
set enabled=yes lsr-id=10.10.10.3 transport-address=10.10.10.3
/mpls ldp interface
add interface=ether3
add interface=ether4
/routing ospf network
add area=backbone network=10.10.10.3/32
add area=backbone network=100.200.3.100/30
add area=backbone network=100.200.4.100/30
/system identity
set name=R01.LND


```


R01.HKI

```
/interface bridge
add name=loopbackbridge
/interface ethernet
set [ find default-name=ether1 ] disable-running-check=no
set [ find default-name=ether2 ] disable-running-check=no
set [ find default-name=ether3 ] disable-running-check=no
set [ find default-name=ether4 ] disable-running-check=no
set [ find default-name=ether5 ] disable-running-check=no
/interface wireless security-profiles
set [ find default=yes ] supplicant-identity=MikroTik
/routing ospf instance
set [ find default=yes ] router-id=10.10.10.4
/ip address
add address=172.31.255.30/30 interface=ether1 network=172.31.255.28
add address=10.10.10.4 interface=loopbackbridge network=10.10.10.4
add address=100.200.4.102/30 interface=ether3 network=100.200.4.100
add address=100.200.5.101/30 interface=ether5 network=100.200.5.100
add address=100.200.10.101/30 interface=ether4 network=100.200.10.100
/ip dhcp-client
add disabled=no interface=ether1
/mpls ldp
set enabled=yes lsr-id=10.10.10.4 transport-address=10.10.10.4
/mpls ldp interface
add interface=ether3
add interface=ether4
add interface=ether5
/routing ospf network
add area=backbone network=10.10.10.4/32
add area=backbone network=100.200.4.100/30
add area=backbone network=100.200.5.100/30
add area=backbone network=100.200.10.100/30
/system identity
set name=R01.HKI

```

R01.SPB:

```
/interface bridge
add name=loopbackbridge
add name=vpn
/interface ethernet
set [ find default-name=ether1 ] disable-running-check=no
set [ find default-name=ether2 ] disable-running-check=no
set [ find default-name=ether3 ] disable-running-check=no
set [ find default-name=ether4 ] disable-running-check=no
set [ find default-name=ether5 ] disable-running-check=no
/interface vpls
add disabled=no l2mtu=1500 mac-address=02:96:AE:D1:9C:3F name=EoMPLS remote-peer=10.10.10.2 vpls-id=100:100
/interface wireless security-profiles
set [ find default=yes ] supplicant-identity=MikroTik
/routing ospf instance
set [ find default=yes ] router-id=10.10.10.5
/interface bridge port
add bridge=vpn interface=ether5
add bridge=vpn interface=EoMPLS
/ip address
add address=172.31.255.30/30 interface=ether1 network=172.31.255.28
add address=10.10.10.5 interface=loopbackbridge network=10.10.10.5
add address=192.168.0.2/24 interface=vpn network=192.168.0.0
add address=100.200.5.102/30 interface=ether3 network=100.200.5.100
add address=100.200.7.101/30 interface=ether4 network=100.200.7.100
add address=100.200.6.101/30 interface=ether5 network=100.200.6.100
/ip dhcp-client
add disabled=no interface=ether1
/mpls ldp
set enabled=yes lsr-id=10.10.10.5 transport-address=10.10.10.5
/mpls ldp interface
add interface=ether3
add interface=ether4
add interface=ether5
/routing ospf network
add area=backbone network=10.10.10.5/32
add area=backbone network=100.200.5.100/30
add area=backbone network=100.200.7.100/30
add area=backbone network=100.200.6.100/30
/system identity
set name=R01.SPB


```

R01.MSC:

```
/interface bridge
add name=loopbackbridge
/interface ethernet
set [ find default-name=ether1 ] disable-running-check=no
set [ find default-name=ether2 ] disable-running-check=no
set [ find default-name=ether3 ] disable-running-check=no
set [ find default-name=ether4 ] disable-running-check=no
/interface wireless security-profiles
set [ find default=yes ] supplicant-identity=MikroTik
/routing ospf instance
set [ find default=yes ] router-id=10.10.10.6
/ip address
add address=172.31.255.30/30 interface=ether1 network=172.31.255.28
add address=10.10.10.6 interface=loopbackbridge network=10.10.10.6
add address=100.200.7.102/30 interface=ether4 network=100.200.7.100
add address=100.200.8.102/30 interface=ether3 network=100.200.8.100
/ip dhcp-client
add disabled=no interface=ether1
/mpls ldp
set enabled=yes lsr-id=10.10.10.6 transport-address=10.10.10.6
/mpls ldp interface
add interface=ether3
add interface=ether4
/routing ospf network
add area=backbone network=10.10.10.6/32
add area=backbone network=100.200.7.100/30
add area=backbone network=100.200.8.100/30
/system identity
set name=R01.MSC

```

R01.LBN:

```
/interface bridge
add name=loopbackbridge
/interface ethernet
set [ find default-name=ether1 ] disable-running-check=no
set [ find default-name=ether2 ] disable-running-check=no
set [ find default-name=ether3 ] disable-running-check=no
set [ find default-name=ether4 ] disable-running-check=no
set [ find default-name=ether5 ] disable-running-check=no
/interface wireless security-profiles
set [ find default=yes ] supplicant-identity=MikroTik
/routing ospf instance
set [ find default=yes ] router-id=10.10.10.7
/ip address
add address=172.31.255.30/30 interface=ether1 network=172.31.255.28
add address=10.10.10.7 interface=loopbackbridge network=10.10.10.7
add address=100.200.9.102/30 interface=ether3 network=100.200.9.100
add address=100.200.10.102/30 interface=ether4 network=100.200.10.100
add address=100.200.8.101/30 interface=ether5 network=100.200.8.100
/ip dhcp-client
add disabled=no interface=ether1
/mpls ldp
set enabled=yes lsr-id=10.10.10.7 transport-address=10.10.10.7
/mpls ldp interface
add interface=ether3
add interface=ether4
add interface=ether5
/routing ospf network
add area=backbone network=10.10.10.7/32
add area=backbone network=100.200.8.100/30
add area=backbone network=100.200.9.100/30
add area=backbone network=100.200.10.100/30
/system identity
set name=R01.LBN

```

