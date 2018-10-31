# Tasker_Files
Files, profiles and tasks for Tasker.

Many integrate with my [Home Assistant](https://github.com/Aephir/Home_Assistant), and utilize my [appdaemon python scripts](https://github.com/Aephir/Home_Assistant-Accessory-files/tree/master/appdaemon_scripts).

Files include:
___
### Espresso_Machine_State.prf.xml

Receives a message from Home Assistant via AutoRemote with message 
```
espresso_machine_state_is=:=on
```
or
```
espresso_machine_state_is=:=off
```
It then:
* Sets a global variable in Tasker (`%ESPRESSO`) to on/off.
* Sends the variable `%arcomm` (whatever is right of the =:=, i.e. `on` or `off`) to the KWGT variable, `Espresso_state`, which is used to control the color of the Espresso Machine button on the KWGT (Kustom) widget.
___
### Fountain_State.prf.xml

Receives a message from Home Assistant via AutoRemote with message 
```
fountain_state_is=:=on
```
or
```
fountain_state_is=:=off
```
It then:
* Sets a global variable in Tasker (`%FOUNTAIN`) to on/off.
* Sends the variable `%arcomm` (whatever is right of the =:=, i.e. `on` or `off`) to the KWGT variable, `Fountain_state`, which is used to control the color of the Espresso Machine button on the KWGT (Kustom) widget.
___
### Kitchen_Lights_State.prf.xml

Receives a message from Home Assistant via AutoRemote with message 
```
kitchen_lights_state_is=:=on
```
or
```
kitchen_lights_state_is=:=off
```
It then:
* Sets a global variable in Tasker (`%KITCHEN_LIGHTS_STATE`) to on/off.
* Sends the variable `%arcomm` (whatever is right of the =:=, i.e. `on` or `off`) to the KWGT variable, `Kitchen_lights_state`, which is used to control the color of the Espresso Machine button on the KWGT (Kustom) widget.
___

Similar can be done for many different types of switches, lights, input_boolean, binary_sensors, etc.

