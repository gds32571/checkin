# check_lightning

Programs to connect to lightning server and read probability of a damaging
lightning strike.  If probability is 100%, this program will connect to the
UPS supporting this RPi computer and send a power off command.

Turning the main UPS power off shuts down the RPi and turns it off, and also the ESP8266
controller.  It also deenergizes the relay on the Disconnector1 board, which
disconnects the 12 volt wall wart to the UPS input.  So, the UPS is physically
disconnected from the wall power.

If instead of a full-blown UPS, a microUPS might be used along with a Sonoff
switch. This program will send an MQTT message which turns off the sonoff switch.  
Not great protection from a damaging surge but better than nothing.  The
microUPS will ensure that the Rpi is shutdown safely.

## check_lightning:

Program that does the actual query of the lightning manager and directs the
power off sequence if lightning is imminent. It contains a dictionary object
named "map" which identifies the correct UPS or Sonoff switch to talk too. 
It also does a periodic connection to the UPS to make sure that it can be
reached.

## update_all:

This script will copy (update)  the check_lightning file to all RPi computers which
participate in the lightning detection system. The master program is kept
and edited on a computer named rp5 and updates distributed from there.
.


   

