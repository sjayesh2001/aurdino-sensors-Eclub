# RGB COLOR SENSOR (TCS230)

### Introduction

In this tutorial we are going to read the colors using the RGB color sensor (TCS230 Sensor) and Arduino Uno.
The RGB color sensor senses the color light by using the photodiodes.
The sensor converts the readings from the photodiode into a square wave by using the light to frequency converter. The frequency of these
waves is directly proportional to the light intensity. Then the Arduino reads these square waves and gives us the values of the RGB
colors.

**Pins**

The sensor has 8 pins; S0, S1 are for setting the frequency and S2, S3 are for reading the color values. The out pin is supposed to give 
the output to  Arduino in the form of a square wave. The other pins are for powering the sensor.

![pin](/RGB_Sensor/images/tcs3200-tcs230-color-sensor-500x500.jpg)

To read colors from sensors, we will be using the S2 and S3 pins. The pin combination for reading the RGB colors is as follows

S2 |	S3 |	Color
---|-----|-------
LOW |	LOW |	Red
LOW |	HIGH |	Blue
HIGH |	LOW |	Clear
HIGH |	HIGH |	Green

So with the help of pin combinations provided in the above table, we can read values of each color.
After that, we will map these values to 0-255 (standard notation)

The sensor also has two more pins which are S0 and S1. These pins are used to set the frequency to 0%, 2%, 20% or 100%. The pin 
combination for setting the frequency using these pins is as follows

S0 |	S1 |	Output Frequency
---|-----|------------------
LOW |	LOW |	0%
LOW |	HIGH |	2%
HIGH | LOW	| 20%
HIGH |	HIGH |	100%

