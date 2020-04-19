# ROTARY ENCODER

**Introduction**

In this tutorial we will learn how rotary encoder works and how to use it with Arduino.
A rotary encoder is a type of position sensor which is used for determining the angular position of a rotating shaft. It generates an electrical signal, either analog or digital, according to the rotational movement.
There are many types of rotary encoders on the basis of output signal and sensing technology.

![types](/rotary_encoder/images/typesrotary.jpg)

What we will use in this tutorial is an incremental rotary encoder and it’s the simplest position sensor to measure rotation.

**Principle**

The encoder has a disk with evenly spaced contact zones that are connected to the common pin C and two other separate contact pins A and B, as illustrated below.When the disk will start rotating step by step, the pins A and B will start making contact with the common pin and the two square wave output signals will be generated accordingly.

![rotaryprinciple](/rotary_encoder/images/Output-Waveform-of-Rotary-Encoder.png)


![waveform](/rotary_encoder/images/rotary-encoder-waveform-v2.webp)

We can notice that the two output signals are displaced at 90 degrees out of phase from each other. If the encoder is rotating clockwise the output A will be ahead of output B.
So if we count the steps each time the signal changes, from High to Low or from Low to High, we can notice at that time the two output
signals have opposite values. Vice versa, if the encoder is rotating counter clockwise, the output signals have equal values. So 
considering this, we can easily program our controller to read the encoder position and the rotation direction.
