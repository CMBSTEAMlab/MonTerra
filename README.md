# MonTerra Soil Moisture Monitoring Station Manual

## Overview

### About the MonTerra Soil Moisture Monitoring Station

The Children’s Museum of Bozeman’s STEAMlab is a hands-on, mentor-led learning environment where children from a wide variety of backgrounds and skill levels combine digital design, high-tech fabrication and simple electronics to construct meaningful projects, build skills, and unlock understanding.

In partnership with Montana State University’s Extended University and the Institute on Ecosystems, students in the STEAMlab engaged in a year-long project to design, prototype and test a variety of tools for measuring soil moisture. Each component of the MonTerra Soil Moisture Monitoring Station - from the 3D printed enclosure to the interior circuitry to the code that uploads moisture data to the web - was designed by high school kids in Bozeman for use by schoolchildren all around Montana.

The MonTerra Development Team is overseen by John Allwine and Richard Harjes of the Children’s Museum of Bozeman STEAMlab. Team members are Henry Barker, Gabriel Brokaw, Lucas Kearns, Owen Mitchell, Nic Rust, Harry Schwem, Ren Wall and Yufu Yoshimura.

### Measuring soil moisture with your MonTerra Soil Moisture Monitoring Station

#### What is soil moisture

Soil moisture is the water that is held in the spaces between soil particles. This moisture can enter the soil through surface precipitation - like rain and snow - and can also be absorbed from the surrounding soil, as water migrates to fill empty spaces between soil particles. Water can leave the soil through evaporation, as well as through drainage. Different types of soil absorb and retain moisture at different rates.

Many valuable nutrients are dissolved in this water, and are carried from one area of the soil to another. Water makes chemical reactions in the soil possible, and supplies microorganisms with the elements necessary for life.

#### Why is measuring soil moisture important?

Measuring the amount of water contained in soil yields valuable information that can be used to identify trends in plant health, local crop conditions, long-term weather patterns, and even global climate. Farmers, scientists, engineers, government agencies and private companies are all interested in data about soil moisture.

#### How does the MonTerra Soil Moisture Monitoring Station work?

The MonTerra uses a “capacitive” sensor, which measures the ability of a material (in this case, soil) to hold an electrical charge when a voltage is applied to it. The sensor in the MonTerra is the tiny purple circuit board at the end of the long wire that is attached to the Arduino controller inside the 3D printed housing. It will need to be carefully buried in the soil at a depth of 12 inches in order to function properly. The MonTerra is powered by six NiMH rechargeable batteries.

The Arduino controller acts as the “brain” of the MonTerra. The Arduino contains a tiny computer chip that can be programmed using the Arduino Integrated Development Environment (or IDE) to perform a wide variety of tasks. We’ve programmed the MonTerra’s Arduino to send an electrical current through the sensor that you’ve buried in the ground. The sensor contains two copper plates that work together to measure the amount of electrical charge that is held in the soil. The Arduino determines this charge by measuring how long it takes for voltage to travel from its “send” pin, through the sensor, and back to its “receive” pin. This measurement is directly related to the amount of water contained in the soil. If you hold the capacitor in the air, it returns a number to the Arduino between 8,000 and 9,000. If you place the capacitor in a glass or water, the number is closer to 100,000. So the higher the number, the more moisture is contained in the soil.

Touchscreens on iPads and smartphones use this exact same system to record the movements of your finger. Human skin is about 70% water. When your finger comes into contact with the touch screen, the screen measures the change in capacitance from low (air) to high (finger), and uses that data to determine your finger’s location.

The Arduino “brain” also uploads the sensor data to the wifi chip, and controls the sensor’s cycle of sleep/wakefulness. All of these activities are determined in the code (the computer program) that we’ve written for the Arduino. In order to get your MonTerra up and running, you’ll need to modify the code to connect it to your school’s wifi account. See below for instructions.

You can also modify the code to make other changes to the MonTerra, for example, to increase the number of measurements that the sensor records, add additional sensors, connect it to external devices, etc. You could code the MonTerra to run an automatic watering system for a houseplant or greenhouse; you could program it to communicate with other sensors to irrigate an entire farm.

### Components

The soil moisture monitoring station is composed of the following components:

#### MonTerra Soil Moisture Monitoring Board

This purple printed circuit board (PCB) has sockets for several of the components listed below and the necessary connections between them so that they can function as a soil moisture monitoring station. The modular design allows for easy removal and replacement of faulty components. It also allows for the use of the Arduino and XBee module in other projects.


#### Arduino - Pololu A-Star 32U4 Mini LV

This Arduino-compatible microcontroller was chosen for its efficient power regulator, which allows it to be powered from any power source between 2.7 and 11.8 volts. Other models of the Pololu A-Star 32U4 family have the same footprint and can be interchanged. The ULV model supports voltages from .5V to 5.5V and the SV model supports 5V to 36V. Having this flexibility allows for different battery configurations so further development can be made (such as designing for a solar charging station).

#### XBee Wifi Module

This module transmits the soil moisture data to the cloud. There are other kinds of XBee modules that could be interchanged to transfer data in different ways (such as point to point or mesh networks).

#### Bidirectional 3.3V to 5V level shifter

The Arduino runs at 5V, whereas the XBee module runs at 3.3V so to communicate with each other the voltage needs to be converted from one to the other.

#### MonTerra Soil Moisture Sensor

The sensor uses capacitive plates that can sense changes to the material surrounding it (called the dielectric). The plates in the sensor form a capacitor and it works by seeing how long it takes for the capacitor to charge. Wet soil takes longer to charge than dry soil.

#### Batteries

The MonTerra is powered using 6 NiMH rechargeable AA batteries, which provide a nominal voltage of 7.2V. The batteries will need to be charged weekly during standard deployment. The batteries should not be recharged at temperatures below 32 degrees Fahrenheit. If the batteries are cold, bring them indoors and allow them to come up to room temperature before recharging.

#### Enclosure

Your enclosure is either a white 3D printed enclosure mounted on a metal stake or a gray electrical box that will house all of the MonTerra’s electrical components.

## Setup

### Arduino IDE

1. Download Arduino IDE - https://www.arduino.cc/en/Main/Software
2. Install the Arduino IDE - https://learn.sparkfun.com/tutorials/installing-arduino-ide   
3. Install Pololu drivers and Arduino IDE settings by following steps 6.1-6.2 of the following document - https://www.pololu.com/docs/0J61/all#6
4. Run the Arduino IDE
5. Select the Pololu A-Star 32U4 Board under the Tools - Board menu
6. Select Pololu USB AVR Programmer under the Tools - Programmer menu
7. Connect the Pololu A-Star 32U4 Mini LV to your computer with the provided USB cable.
8. Select the USB port that corresponds to the Pololu A-Star 32U4 Mini LV under the Tools - Port menu (on Windows it will be COM# with the # replaced with the port number)

### Setup a Phant stream

1. In a browser, go to http://69.145.204.62:8080/
2. Click Create to create a data stream.
3. Fill in the title and description to identify your monitoring station.
4. Fill in the following for the Fields text box (make sure the case matches exactly):
5. Enter your location
6. Optionally, set an alias for the stream (this can make it easier to remember the URL of your stream)
7. You will be presented with a URL and a number of keys (public, private and delete). Write these keys down or save them to a file as you’ll need to program them into your soil moisture monitoring station.


### Configure your wifi network

1. Download the MonTerra project: https://github.com/CMBSTEAMlab/MonTerra/archive/master.zip
2. Unzip master.zip
3. Open the Arduino IDE
4. Click File - Open… and navigate arduino/MonTerra/MonTerra.ino
5. Replace <WiFi Network Name> with the name of your wifi network.
6. Replace <WiFi Password> with your wifi network’s password. If your network is open (doesn’t require a password), remove <WiFi Password>.
7. WPA2 is the most common authentication type, but if your network is different change WPA2 to one of NO_SECURITY, WPA, or WEP.
8. Replace <Station ID> with a descriptive name for your soil moisture monitoring station.
9. Replace <Phant public key> with the public key from step 7 of “Setup a Phant stream” above.
10. Replace <Phant private key> with the private key from step 7 of “Setup a Phant stream” above.
11. Connect the Pololu A-Star 32U4 Mini LV to your computer with the provided USB cable.
12. Click the Upload button in the upper left () or under the Sketch menu.
13. Wait for the the “Done uploading.” message in the lower left corner. See the troubleshooting section if you don’t see this message.

## Use Cases

### Deploy the MonTerra Soil Moisture Monitor

1. Place the soil moisture monitoring board in the enclosure and fit the cover over it, tightening all necessary screws.
2. Drive the metal stake into the ground where your soil moisture will be monitored
3. Affix the enclosure to metal stake, no more than 12 inches above the ground.
4. Carefully bury the soil moisture sensor in the ground at a depth of 12 inches.
5. Connect the battery pack to the wire inside the battery compartment. 
6. In a browser, go to the URL provided in step 7 of “Setup a Phant stream.”
7. You should see the soil moisture readings that are being transmitted from the monitoring station. The readings should be approximately in the range of 8,000-20,000.
8. The sensor reading frequency defaults to once a day and can be changed in the Arduino sketch.
9. With current default settings, the batteries will need to be recharged once a week. Batteries should not be recharged at temperatures below 32 degrees Fahrenheit, so allow the batteries to warm up to room temp before recharging.

### Indoor experimentation

In the zip file you downloaded in step 1 of the "Configure your wifi network" section, there is a simplified Arduino sketch that doesn’t use the wifi module, and doesn’t put the device to sleep to conserve energy. The sketch is useful for experimenting with the soil moisture sensor indoors. 

1. Open the Arduino IDE
2. Click File - Open… and navigate to the folder you extracted master.zip to.
3. Open the arduino/DebugSoilMoistureSensor/DebugSoilMoistureSensor.ino
4. Click the Upload button in the upper left () or under the Sketch menu.
5. Wait for the the “Done uploading.” message in the lower left corner. See the troubleshooting section if you don’t see this message.

### Advanced experimentation

The Pololu A-Star 32U4 Mini LV can be removed from the socket on the soil moisture monitoring board, and instead be plugged into a breadboard (not included). Wires (also not included) can be connected from the 9 pins shown in the images below. The pins used on the MonTerra Board are digital pins 0, 1, 6, 9, 10, and 13 along with 3V3, 5V and GND. If you want to power it with batteries, you also have to bring over BAT+ (BAT- is the same as GND).



You can now attach more inputs such as additional sensors for broadcasting more information to your Phant stream. You could also add outputs such as LEDs, servos or relays that react to the sensor information. After experimenting with different inputs and outputs, you could incorporate your changes into the MonTerra board using EAGLE CAD (see the “Further Resources” section below for more information about EAGLE CAD) and produce a new board that has your new inputs and outputs built-in.

## Troubleshooting

### My Arduino sketch won't upload

Things to check:
* If you’re using Windows, make sure you’ve installed the Pololu A-Star drivers. See step 3 of the "Arduino IDE" section above.
* Make sure you’ve properly connected the provided USB cable from your computer to the Pololu A-Star Mini.
* Make sure you’ve selected the Pololu board, programmer and port. See steps 5-8 of the "Arduino IDE" section.
* If the port doesn’t show up, the USB drivers may be installing, waiting several minutes with the Pololu plugged in may be all it takes before the port becomes available.
* Make sure no other applications are using the serial port (this is unlikely).

### Data isn't showing up on the Phant stream

Make sure you've gone through all steps in the "Setup" section.

Things to check:

* Make sure the public key and private key from your Phant stream match the ones you entered into the Arduino IDE.
* Make sure you’ve entered the correct Wifi network and password, along with the type of encryption (WPA2, NO_SECURITY, etc.).
* To help debug further follow the How To Enter Debug Mode section below.

### How to enter debug mode

1. In the Arduino IDE, open the MonTerra.ino sketch.
2. Find the following line that is commented out using two slashes (//) at the beginning of the line.
3. Remove the two slashes from the beginning of the line to uncomment it.
4. Click the Upload button in the upper left () or under the Sketch menu.
5. Wait for it to say “Done uploading.” at the bottom of the window then click the Serial Monitor button in the upper right corner () or under the Tools menu. If a red error appears near the bottom that says the port is not available, wait a few seconds and then click the Serial Monitor button again.
6. Debugging information will continuously be printed out as the Arduino sends commands to the XBee Wifi module. Things to watch for:
The message “+++ Entering command mode” followed by “NOT OK”

  a. This message indicates the Arduino is unable to communicate with the XBee. The XBee may be asleep. Try disconnecting all power to the Arduino by disconnecting the USB and batteries and then hooking them back up. If this message continues to be printed out, the XBee module may need to be replaced.


  b. The message “Waiting to connect to wifi: FF” repeating over and over.

This message indicates that the XBee is trying to find the specified wifi network. If this message persists it may indicate that you’ve incorrectly input the network name. 

This error can also happen because we are in debug mode. The 3.3V power supply on the Arduino is responsible for regulating messaging over USB. Sometimes there isn’t enough power to be in debug mode and use the XBee. Hooking up the battery pack in addition to the USB cable can help get around this problem.

  c. The message “Waiting to connect to wifi: 24” repeating over and over.


This message indicates that the provided wifi network password is incorrect. Check the WIFI_PSK variable at the top of the program.

  d. The message “Waiting to connect to wifi: 41”

This message usually indicates that the XBee has successfully connected to the wifi network, but is still waiting to be assigned an IP address. This message should not print out more than a few times before successfully sending data to the cloud.

### Other questions?

Contact CMB STEAMlab at 406-522-9087, email steamlab@cmbozeman.org or file an issue on the MonTerra GitHub page: https://github.com/CMBSTEAMlab/MonTerra/issues.

## Circuit Diagrams

These diagrams were generated by EAGLE CAD, the software used to design the MonTerra soil moisture monitoring board.

## Further Resources

The soil moisture monitoring station was designed to be reprogrammable using Arduino and the interchangeable nature of XBee modules allows for different wireless communication techniques to be used. There is a wealth of knowledge online about these technologies. Here are a few places to start:

* To learn more about Arduino:
  * The official Arduino site - https://www.arduino.cc/en/Guide/HomePage
  * SparkFun - https://learn.sparkfun.com/tutorials/what-is-an-arduino      

* To learn more about the Pololu A-Star 32U4 Mini board:
  * Pololu Resources - https://www.pololu.com/product/3103/resources
  * A-Star GitHub repository - https://github.com/pololu/a-star

* To learn more about XBee:
  * Official XBee site - http://www.digi.com/lp/xbee
  * SparkFun datalogging with XBee - https://learn.sparkfun.com/tutorials/internet-datalogging-with-arduino-and-xbee-wifi


* To learn more about the libraries used in the MonTerra Arduino software:
  * CapacitiveSensor - https://github.com/PaulStoffregen/CapacitiveSensor
  * Phant - https://github.com/sparkfun/phant-arduino
  * Narcoleptic - https://code.google.com/p/narcoleptic/


* To learn more about EAGLE CAD, the software the MonTerra Board was designed in:
  * EAGLE CAD home page - http://www.cadsoftusa.com/
  * Tutorials by Jeremy Blum - http://www.jeremyblum.com/category/eagle-tutorials/


