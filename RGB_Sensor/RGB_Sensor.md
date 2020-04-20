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

In our code, the frequency is set at 20%. You can set the frequency to any other value (you desire), but the output values will change
according to the set frequency and you will have to map the color values relative to the set frequency.

**Components**

* 1 * Arduino Uno Board
* 1 * USB cable
* 1 * TCS230 (RGB color sensor)
* Jumper wires 

### Experimental Procedures

**Step1:-**

Connect your sensor with arduino as shown in following table

TCS230 |	Arduino Uno
-------|-------------
VCC |	5V
GND |	GND
S0 |	Pin 8
S1 |	Pin 9
S2 |	Pin 12
S3 |	Pin 11
OUT	| Pin 10

**Step2:-**

Copy and paste the following code in your arduino console. This code is self explanatory

    int s0_pin =8;

    int s1_pin =9;

    int s2_pin =12;

    int s3_pin =11;

    int out_pin =10;


    void setup() {

    Serial.begin(9600);
    
    // defining pinmodes of different pins

    pinMode(s0_pin, OUTPUT);

    pinMode(s1_pin, OUTPUT);

    pinMode(s2_pin, OUTPUT);

    pinMode(s3_pin, OUTPUT);

    pinMode(out_pin, INPUT);
    
    // Setting frequency-scaling to 20%

    digitalWrite(s0_pin,HIGH);

    digitalWrite(s1_pin,LOW);

    }


    void loop() {
    
    // Setting red filtered photodiodes to be read

    digitalWrite(s2_pin,LOW);

    digitalWrite(s3_pin,LOW);
    
    // Reading the output frequency in red_color

    int red_color = pulseIn(out_pin, LOW);
    
    //Remaping the value of the frequency to 0 to 255

    red_color = map(red_color, 25,72,255,0);

    delay(50);
    
    // Setting Green filtered photodiodes to be read

    digitalWrite(s2_pin,HIGH);

    digitalWrite(s3_pin,HIGH);
    
    // Reading the output frequency in green_color

    int green_color = pulseIn(out_pin, LOW);
    
    //Remaping the value of the frequency to 0 to 255

    green_color = map(green_color, 30,90,255,0);

    delay(50);
    
     // Setting Blue filtered photodiodes to be read

    digitalWrite(s2_pin,LOW);

    digitalWrite(s3_pin,HIGH);
    
    // Reading the output frequency in blue_color

    int blue_color = pulseIn(out_pin, LOW);
    
    //Remaping the value of the frequency to 0 to 255

    blue_color = map(blue_color, 25,70,255,0);

    delay(50);
    
    //printing RED color intensity

    Serial.print("RED: ");

    Serial.print(red_color);

    Serial.print("  ");
    
    //printing GREEN color intensity
 
    Serial.print("GREEN: ");

    Serial.print(green_color);

    Serial.print("  ");
    
    //printing BLUE color intensity

    Serial.print("BLUE: ");

    Serial.print(blue_color);

    Serial.println("  ");

    delay(1000);

    }

**Step3:-**

Now compile the program by clicking on the **Verify** button or by pressing **Ctrl+R**.

**Step4:-**

Now upload the program on your arduino board by clicking on the **upload** button or by pressing **Ctrl+U**

**Step5:-**

Open the **tools-->Serial Monitor** and see the results
