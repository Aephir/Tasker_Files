# Tasker_Files
Files, profiles and tasks for Tasker and Kustom (KWGT).

Many integrate with my [Home Assistant](https://github.com/Aephir/Home_Assistant), and utilize my [appdaemon python scripts](https://github.com/Aephir/Home_Assistant-Accessory-files/tree/master/appdaemon_scripts).

Files include:

## Tasker Profiles
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

### Latest_Notification.prf.xml

Receives a message from Home Assistant via AutoRemote with message. This message is then used to set a variable. In this version, I receive the name of a door, e.g. `Basement` or `Front`.

It then sets an array (local array, can only be used within the specific task, all data that is used outside of this task is then set into a global variable), `%array` to `%arcomm, door, was, opened, at, %TIME`. Splitter is set to `,` (comma). `%arcomm` is what is sent, to the left of the `=:=`.

The it uses variable join on `%array`. `Joiner`is set to ( ) `whitespace`. This creates a string; `%arcomm door was opened at %TIME`.

The global variable, `%Latest_notification` is set to this joined array. Now we can discard the local variable, `%array`, since we have saved what we need in the globabl variable.

Lastly, the sctring `%arcomm door was opened at %TIME` is sent to Kustom via `KWGT send variable` in the `Latest_notification` variable. This is then used to display info on my widget.

![Kustom_widget](https://github.com/Aephir/Images/blob/master/Kusotm_(KWGT)_widget_0.1.jpg)
This widget can be found [here](https://github.com/Aephir/Tasker_Files/blob/master/KWGT/KWGT_20181031.kwgt)


## Tasker Tasks
___
### Espresso_On.tsk.xml and Espresso_Off.tsk.xml

Sends a POST message through RESTask to Home Assistant, using webhook id in an automation. This automation turns on/off the espresso machine switch.

It then:
* Sets a global variable in Tasker (`%ESPRESSO`) to on/off.
* Sends the variable `%arcomm` (whatever is right of the =:=, i.e. `on` or `off`) to the KWGT variable, `Espresso_state`, which is used to control the color of the Espresso Machine button on the KWGT (Kustom) widget.
___
### Kitchen_Lights_On.tsk.xml and Kitchen_Lights_Off.tsk.xml

Sends a POST message through RESTask to Home Assistant, using webhook id in an automation. This automation turns on/off the kitchen lights.

It then:
* Sets a global variable in Tasker (`%KITCHEN_LIGHTS_STATE`) to on/off.
* Sends the variable `%arcomm` (whatever is right of the =:=, i.e. `on` or `off`) to the KWGT variable, `Kitchen_lights_state`, which is used to control the color of the Espresso Machine button on the KWGT (Kustom) widget.
___

Again, the same procudure can be used for many other lights and switches.
___
### Notification_From_Home_Assistant.tsk.xml


