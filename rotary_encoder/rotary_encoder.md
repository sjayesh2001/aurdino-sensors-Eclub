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

**Example**

Here we are going to see an example that how we can use rotary encoder to count the position at any instant of time.

**Components**

* 1 * Arduino Uno Board
* 1 * USB cable
* 1 * Rotary Encoder
* Jumper wires 

**Step1:-**

![pinout](/rotary_encoder/images/Rotary-Encoder-Pinout.jpg)

*Connections*

* gnd and +ve terminal to GND and +5v respectively
* CLK (output A) to D-6
* DT (output B) to D-7

We are not using switch pin here.

**Step2:-**

Type the following code in your arduino

**Source Code**

    #define outputA 6
    #define outputB 7
    int counter = 0; 
    int aState;
    int aLastState;  
    void setup() { 
     pinMode (outputA,INPUT);
     pinMode (outputB,INPUT);
   
     Serial.begin (9600);
     // Reads the initial state of the outputA
     aLastState = digitalRead(outputA);   
     } 
    void loop() { 
      aState = digitalRead(outputA); // Reads the "current" state of the outputA
      // If the previous and the current state of the outputA are different, that means a Pulse has occured
      if (aState != aLastState){     
        // If the outputB state is different to the outputA state, that means the encoder is rotating clockwise
        if (digitalRead(outputB) != aState) { 
       counter ++;
     } else {
       counter --;
     }
     Serial.print("Position: ");
     Serial.println(counter);
    } 
    aLastState = aState; // Updates the previous state of the outputA with the current state
    }
