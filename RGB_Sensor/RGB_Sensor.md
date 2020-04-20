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

To read colors from sensors, we will be using the S2 and S3 pins. The pin combination for reading the RGB colors is as follows

S2 |	S3 |	Color
---|-----|-------
LOW |	LOW |	Red
LOW |	HIGH |	Blue
HIGH |	LOW |	Clear
HIGH |	HIGH |	Green
