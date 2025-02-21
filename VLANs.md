# VLANS - CISCO PACKET TRACER

## CREAR VLAN (VLAN10 - VLAN20)

- Switches
    - Switch0 (rangos)
        - VLAN10 - FA0/10 - fa0/19
        - VLAN10 - FA0/20 - fa0/24

- PCs
    - PC0 - 192.168.10.10 (VLAN10) fa0/10
    - PC1 - 192.168.10.20 (VLAN20) fa0/20

Config vlan:

1. Switch - CLI - CREATE & ENABLE
    - ENABLE
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
    - ENABLE
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

## VLANs con dos Switches (trunker)

Usar dos Switches y configurar VLANS que se comparten entre los dos.


- Switches
    - Switch1
        - VLAN10 - FA0/10

- PCs
    - PC2 - 192.168.10.13 (VLAN10)

1. Switches Connection
    - Cable: Copper cross over
    - Ports: SW0 fa0/2 -- SW1 fa0/3
2. Set up VLAN10 on SW1 (sin rangos)
    1. Switch - CLI - CREATE, ENABLE, set Ports
        - ENABLE
        - CONFIgure TErminal 
        - VLAN 10
        - NAME VLAN10
        - INTERface F0/10
        - EXIT
        - SWitchport MODe ACcess
        - SWitchport ACcess Vlan 10
        - EXIT
        - EXIT
        - SHOW VLAN
3. Set up connection (TRUNK) between bith Switches
    1. Switch1 CLI
        - ENABLE
        - CONFIGURE TERMINAL
        - INTERface F0/3
        - SWitchport MODe TRUNK
        - EXIT
    2. Switch0 CLI
    - ENABLE
    - CONFIGURE TERMINAL
    - INTERface F0/2
    - SWitchport MODe TRUNK
    - EXIT

