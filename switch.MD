# CONFIGURAÇÃO SWITCH

### VLAN
```
EN
CONF T
HOST SW-BH

VLAN 5
NAME TI
VLAN 10
NAME COMERCIAL
VLAN 20
NAME COMUNICACAO

INT R F0/1-8
SW ACC VLAN 5
INT R F0/9-16
SW ACC VLAN 10
INT R F0/17-23
SW ACC VLAN 20

EXIT
EXIT
SH VL
WR
```

### MODO TRUNK
```
EN
CONF T
INT F0/24
SW M T
EXIT
EXIT
SH R
WR
```

### VTP
### Switch Core
```
EN
CONF T
HOST SW-CORE

VLAN 5
NAME TI
VLAN 10
NAME COM
VLAN 15
NAME FIN
VLAN 20
NAME ADM

VTP MODE SERVER
VTP DOMAIN XPTO
VTP PASSWORD 123456
VTP VERSION 2

INT F0/24
SW M T

EXIT
EXIT
SH VL
SH VTP S
SH R
WR
RELOAD
```
obs: colocar todas as portas conectadas no SW-CORE no modo trunk e fazer reload no equipamento.

### Switch Client
```
EN
CONF T
HOST SW1

INT RANGE F0/23-24
SW M T

VTP MODE CLIENT
VTP PASSWORD 123456

EXIT
EXIT
SH VL
WR
RELOAD
```
obs: colocar todas as portas conectadas no SW-CLIENT no modo trunk e fazer reload no(s) equipamento(s).