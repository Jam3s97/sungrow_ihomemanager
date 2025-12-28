# sungrow_ihomemanager
Sungrow YAML to communicate with iHomeManager using modbus.
This was created to access grid import/export entities which are not available in the inverter modbus when an iHomeManager is added to a Sungrow system.
The second purpose is to access EV charger entities which is commonly why an iHomeManager would be installed.

This is very BETA currently.
Additional registers will be added as time permits. Feel free to contribute.
Ability to set holding registers is WIP.

EV charger used for testing AC22E-01

Based loosely on the way the inverter YAML is written in https://github.com/mkaiser/Sungrow-SHx-Inverter-Modbus-Home-Assistant

TI_20253104_Communication Protocol of iHomeManager_V1.0.1_EN.pdf was used to determine registers, however it is clear this document is out of date.
