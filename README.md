# sungrow_ihomemanager
Sungrow YAML for Home Assistant to communicate with iHomeManager using Modbus.
This was created to access grid import/export entities which are not available in the inverter Modbus when an iHomeManager is added to a Sungrow system.
The second purpose is to access EV charger entities which is commonly why an iHomeManager would be installed.

This is currently BETA and in development/testing.
Current Status
Home Assistant entities are created for most registers (some seem irrelevant or are undocumented and have currently been left out)
Abilty to set holding registers added
e.g set
EMS mode
Battery forced charge/discharge mode and rate
EV charger mode

There is no dashboard template created (yet)
Additional registers will be added as time permits. Feel free to contribute.

EV charger used for testing AC22E-01

Based loosely on the way the inverter YAML is written in https://github.com/mkaiser/Sungrow-SHx-Inverter-Modbus-Home-Assistant

TI_20253104_Communication Protocol of iHomeManager_V1.0.1_EN.pdf was used to determine registers, however it is clear this document is out of date.


Installation notes:
Assuming you are already using Modbus for your inverter the installation is the same method.

Modbus port 502 was already enabled on my iHomeManager but didn't work for me (I suspect the EV charger was already communicating on this port, and there is a limit of one connection per port).
I enabled port 503 on isolarcloud website.
Requires installer level access.(https://github.com/mkaiser/Sungrow-SHx-Inverter-Modbus-Home-Assistant/wiki/FAQ:-iSolarCloud-installer-account
Device >  iHomeManager > Settings > Common Settings > System parameters > Modbus TCP 503 port on/off

<img width="2093" height="1114" alt="image" src="https://github.com/user-attachments/assets/a4fe8ceb-ea8a-48e6-998f-e729553eb74c" />

