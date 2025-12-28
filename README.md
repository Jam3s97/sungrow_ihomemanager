# sungrow_ihomemanager
Sungrow YAML to communicate with iHomeManager using modbus.
It was created to access grid import/export entities which are not availble in the inverter modbus when an iHomeManager is added to a Sungrow system.
The second purpose is to access EV charger entities which is commonly why an iHomeManager would be installed.
This is very BETA currently.

Based loosely on the way the inverter YAML is written in https://github.com/mkaiser/Sungrow-SHx-Inverter-Modbus-Home-Assistant
