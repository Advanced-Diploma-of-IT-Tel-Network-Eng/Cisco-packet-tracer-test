# CREAR VLAN (VLAN10 - VLAN20)

- Switch0
    - VLAN10 - FA0/10
    - VLAN10 - FA0/20

- PCs
    - PC0 - 192.168.10.10 (VLAN10)
    - PC1 - 192.168.10.20 (VLAN20)

Config vlan:

1. Switch - CLI - CREATE & ENABLE
    - ENA
    - CONFIgure TErminal 
    - VLAN 10
    - NAME VLAN10
    - EXIT
    - VLAN 20
    - NAME VLAN20
    - EXIT
    - EXIT
    - SHOW VLAN
2. Switch - CLI - SET UP ACCESS PORT (RANGO -> [A,B))
    - ENA
    - CONFIGURE TERMINAL
    - INTERface RANge F0/10-20
    - SWitchport MODe ACcess
    - SWitchport ACcess Vlan 10
    - EXIT
    - INterface RANge F0/20-24
    - SWitchport MODe ACcess
    - SWitchport ACcess VLan 20
    - EXIT
    - EXIT
    - SHOW VLAN
3. 


