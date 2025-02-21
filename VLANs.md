# VLANS - CISCO PACKET TRACER

## CREAR VLAN (VLAN10 - VLAN20)

- Switches
    - Switch0 (rangos)
        - VLAN10 - FA0/10 - fa0/19
        - VLAN10 - FA0/20 - fa0/24

- PCs
    - PC0 - 192.168.10.10 (VLAN10) fa0/10
    - PC1 - 192.168.20.10 (VLAN20) fa0/20

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

## Misma VLAN con dos Switches diferentes (trunk)

Usar dos Switches y configurar VLANS que se comparten entre los dos.


- Switches
    - Switch1
        - VLAN10 - FA0/10

- PCs
    - PC2 - 192.168.10.13 (VLAN10)

1. Switches Connection
    - Cable: Copper cross over
    - interfaces: SW0 fa0/2 -- SW1 fa0/3
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

Routers
    - Router0 

1. Connections
    - Cable: Copper Straight through
    - interfaces: SW0 fa0/1 -- RT0 fa0/0
2. Router - Set up interfaces to share traffic
    - ENABLE
    - CONFIgure TErminal
    - interface fa0/0
    - no shutdown
    - EXIT
    - CREAR SUB INTERface VLAN10
        - se puede usar cualquier valor en fa0/1.X, se recomienda usar el ID de la VLAN a configurar.
            - interface fa0/0.10
        - usar el ID de la VLAN en dot1Q X
            - encapsulation dot1Q 10
        - asignar IP para identificar la VLAN
            - ip address 192.168.10.1 255.255.255.0
        - EXIT
    - CREAR SUB INTERface VLAN20
        - interface fa0/0.20
        - encapsulation dot1Q 20
        - ip address 192.168.20.1 255.255.255.0
        - EXIT
3. Switch - Set up trunk interface
    - CLI
    - ENABLE
    - CONFIgure TErminal
    - interface fa0/1
    - SWitchport MODe trunk
    - EXIT
    - EXIT
    - EXIT