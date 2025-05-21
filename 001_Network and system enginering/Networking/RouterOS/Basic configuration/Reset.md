#### Reset From RouterOS
Run the command **"/system reset-configuration"** from a command-line interface;

#### Using Reset Button
RouterBOARD devices are fitted with a reset button which has several functions:

- **Loading the backup RouterBOOT loader**  
	Hold this button before applying power, and release it after three seconds since powering, to load the backup boot loader. This might be necessary if the device is not operating because of a failed RouterBOOT upgrade. When you have started the device with the backup loader, you can either set RouterOS to _force backup loader_ in the RouterBOARD settings or have a chance to reinstall the failed RouterBOOT from a ".fwf" file (total of **3 seconds**)

- **Resetting the RouterOS configuration**  
    Hold this button until the LED light starts flashing, and release the button to reset RouterOS configuration to default.

- **Enabling CAPs mode**  
    To connect this device to a wireless network managed by CAPsMAN, keep holding the button for 5 more seconds, LED turns solid, release now to turn on CAPs mode. It is also possible to enable CAPs mode via the command line, to do so run the command **"/system reset-configuration caps-mode=yes"**;

- **Starting the RouterBOARD in Netinstall mode**  
    Or keep holding the button for 5 more seconds until the LED turns off, then release it to make the RouterBOARD look for Netinstall servers. You can also simply keep the button pressed until the device shows up in the Netinstall program on Windows.

*You can also do the previous three functions without loading the backup loader, simply push the button immediately after you apply power. You might need the assistance of another person to push the button and also plug in the power supply at the same time!*

*If you wait until the LED stops flashing, and only then release the button - this will instead launch Netinstall mode, to reinstall RouterOS.*