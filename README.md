# MonTerra Soil Moisture Monitoring Station

## Where did the MonTerra Soil Moisture Monitoring Station come from?
The Children’s Museum of Bozeman’s STEAMlab is a hands-on, mentor-led learning environment where children from a wide variety of backgrounds and skill levels combine digital design, high-tech fabrication and simple electronics to construct meaningful projects, build skills, and unlock understanding.

In partnership with Montana State University’s Extended University and the Institute on Ecosystems, students in the STEAMlab engaged in a year-long project to design, prototype and test a variety of tools for measuring soil moisture. Each component of the MonTerra Soil Moisture Monitoring Station - from the 3D printed enclosure to the interior circuitry to the code that uploads moisture data to the web - was designed by high school kids in Bozeman for use by schoolchildren all around Montana.

## Measuring soil moisture with your MonTerra Soil Moisture Monitoring Station
### What is soil moisture?
Soil moisture is the water that is held in the spaces between soil particles. This moisture can enter the soil through surface precipitation - like rain and snow - and can also be absorbed from the surrounding soil, as water travels to fill the empty spaces between soil particles. Water can leave the soil through evaporation, as well as through drainage. Different types of soil absorb and retain moisture at different rates.

Many valuable nutrients are dissolved in this water, and are carried from one portion of the soil to another. Water makes chemical reactions in the soil possible, and supplies microorganisms with the water necessary for life.

### Why is measuring soil moisture important?
Measuring the amount of water contained in soil can yield valuable information that can be used to identify trends in plant health, local crop conditions, long-term weather patterns, and even global climate. Farmers, scientists, engineers, government agencies and private companies are all interested in data about soil moisture.

### How does the MonTerra Soil Moisture Monitoring Station work?
The MonTerra uses a “capacitive” sensor, which measures the ability of a material (in this case, soil) to hold an electrical charge when a voltage is applied to it. The sensor in the MonTerra is the tiny purple circuit board at the end of the long wire that is attached to the Arduino controller inside the 3D printed housing. It will need to be carefully buried in the soil at a depth of TKTK inches in order to function properly. The MonTerra is powered by six NiMH rechargeable batteries.

The Arduino controller acts as the “brain” of the MonTerra. The Arduino contains a tiny computer chip that can be programmed using the Arduino Integrated Development Environment (or IDE) to perform a wide variety of tasks. We’ve programmed the MonTerra’s Arduino to send an electrical current through the sensor that you’ve buried in the ground. The sensor contains two copper plates that work together to measure the amount of electrical charge that is held in the soil. The Arduino determines this charge by measuring how long it takes for voltage to travel from its “send” pin, through the sensor, and back to its “receive” pin. This measurement is directly related to the amount of water contained in the soil. If you hold the capacitor in the air, it returns a number to the Arduino between 8,000 and 9,000. If you place the capacitor in a glass or water, the number is closer to 100,000. So the higher the number, the more moisture is contained in the soil.

Touchscreens on iPads and smartphones use this exact same system to record the movements of your finger. Human skin is about 70% water. When your finger comes into contact with the touch screen, the screen measures the change in capacitance from low (air) to high (finger), and uses that data to record your finger’s location.

The Arduino “brain” also uploads the sensor data to the wifi chip, and controls the sensor’s cycle of sleep/wakefulness. All of these activities are determined by the code - the computer program - that we’ve written for the Arduino. In order to get your MonTerra up and running, you’ll need to modify the code to connect it to your school’s wifi account. (See below for instructions.)

You can also modify the code to make other changes to the MonTerra, for example, to increase the number of measurements that the sensor records, add additional sensors, connect it to external devices, etc. You could code the MonTerra to run an automatic watering system for a houseplant or greenhouse; you could program it to communicate with other sensors to irrigate an entire farm.

