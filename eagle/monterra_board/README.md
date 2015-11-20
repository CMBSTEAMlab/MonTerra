# MonTerra Board

These EAGLE files represent the MonTerra soil moisture monitoring station PCB. 
The design is meant to be modular so different parts can be swapped out, such
as the XBee Wifi Module for other XBees or the 3 different Pololu A-Star Minis.

# Future development

## Added capacitors to the board to help reduce noise for the XBee. 

From the XBee manual:

"Poor power supply can lead to poor radio performance, especially if the supply voltage is not kept
within tolerance or is excessively noisy. To help reduce noise, 1μF and 8.2pF capacitors are
recommended to be placed as near to pin 1 on the PCB as possible. If using a switching regulator for
your power supply, switching frequencies above 500 kHz are preferred. Power supply ripple should
be limited to a maximum 50mV peak to peak."

## Change the power source for the XBee

The XBee is currently being powered from the Pololu's 3V3 pin, which can't
supply enough current for the maximum XBee ratings and can result in unexpected
behavior from the XBee. Consider using this power regulator from Pololu: https://www.pololu.com/product/2122

## Add solar charging circuit

When trickle charging NiMH batteries (at or below C10), a charge controller
circuit can be avoided and a diode and solar panel is all that is needed. Otherwise,
a charge controller is necessary. 

## Add more sensors

Information such as temperature, CO2 levels, light levels would be of interest along
with soil moisture levels.
