# Wireless-Ignition
Wireless ignition code and frames for OSU Rocketry Teams


1. main.py is the source python code for the main.exe gui, using kivy.
2. main.cpp is the arduino code driving the igniter.
3. frames_list.xml is the list of XCTU frames ready to send to the igniter.
4. igniter_gui.py is a demo for enabling xbee communication from the command line.

For the igniter, plug in all cables, connectors (maybe with the exception of the igniter leads), and the antennae on the igniter box prior to the batteries. This is to avoid attempting any radio communication without a plugged in antennae, which could damage the radio module. Upon plugging in the batteries, the user with the computer should see a startup message sent from the igniter module, "Waiting for command". The system is now ready to use.

On the igniter module box, do not forget to toggle the physical arming switch as well. Have a great launch!

Demonstration of the GUI, which can be downloaded at the following box link (so you dont have to compile it) https://oregonstate.box.com/s/kmph8c4jaymfs09kotc6fktzpphtrlqv

GUI
![Main](https://github.com/fernancode/Wireless-Ignition/blob/master/screencap1.JPG)

Pinging the Igniter Receiver
![ping](https://github.com/fernancode/Wireless-Ignition/blob/master/screencap2.JPG)

Attempting to launch when the digital arm command has not been sent
![false_attempt](https://github.com/fernancode/Wireless-Ignition/blob/master/screencap3.JPG)

Successful sequence
![success](https://github.com/fernancode/Wireless-Ignition/blob/master/screencap4.JPG)

To use with XCTU software (https://www.digi.com/resources/documentation/digidocs/90001526/tasks/t_download_and_install_xctu.htm) and find the radio module. Use the "add new module" as opposed to "discover new module" option and make sure to check the box indicating the radio is programmable. Once the radio has been found, switch to the console working mode (Alt+C) and "Open" the communication. Be sure to load the frames list which are packets to be sent to the igniter module. The radio on the computer(user) end is now active.

There are five frames (packets) which can be sent to the igniter module:
1. "arm" - arms the igniter for 60 seconds and returns to a disarmed configuration after 60 seconds.
2. "disarm" - Disarms the igniter module immediately. Also commands "relay_off" if sent to the igniter module.
3. "relay_on" - Turns on the igniter relay only if the arm command has been sent to the igniter less than 60 seconds prior. If a "relay_on" has been sent when the igniter is disarmed, the igniter will send a message back to the user indicating it was not digitally armed.
4. "relay_off" - Turns off the igniter relay.
5. "ping" - Requests the igniter module to return a message to the user, "ping received" - for confirming radio communication is active and functioning norminally.

Fernando A de la Fuente 2/2020
