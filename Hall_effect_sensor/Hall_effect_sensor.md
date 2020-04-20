# HALL EFFECT SENSOR

**Introduction**

In this tutorial we will look at how to use a hall effect sensor with Arduino. A Hall effect sensor is a transducer that varies its output
voltage in response to a magnetic field.The Hall effect sensor works on the principle of the Hall effect.
The Arduino can detect this voltage change through its interrupt pin and determine whether the magnet is near the sensor or not.
The **KY-003** is a Hall effect sensor. If no magnetic field is present, the signal line of the sensor is HIGH . If a magnetic field is
presented to the sensor, the signal line goes LOW, at the same time the LED on the sensor lights up. This informaton will be used by us in 
our code.

![pinout](/Hall_effect_sensor/images/hallsensor.jpg)

**Components**

* 1 * Arduino Uno Board
* 1 * USB cable
* 1 * Hall effect sensor
* Jumper wires

**Experimental Procedures**

**Step1:-**

Connect your sensor with arduino as shown in following diagram

![connection](/Hall_effect_sensor/images/Hall-effect-sensor-interfacing-with-arduino.jpg)

* Pin – is GND, connect to GND of the Arduino
* Middle pin is +5 v, connect to Arduino +5
* Pin S signal, connect to Arduino pin 2

**Step2:-**

**Code** is fairly simple and self explanatory

    int Led = 13 ; // Arduino built in LED
    int SENSOR = 2 ; // define the Hall magnetic sensor
    int val ; // define numeric variables 
 
    void setup ()
    {
      Serial.begin(9600);
      pinMode (Led, OUTPUT) ;    // define LED as output
      pinMode (SENSOR, INPUT) ;  // define the Hall magnetic sensor line as input
    }
 
    void loop ()
    {
      val = digitalRead (SENSOR) ; // read sensor line
      if (val == LOW) // when the Hall sensor detects a magnetic field, Arduino LED lights up
      {
        digitalWrite (Led, HIGH);
        Serial.println("Magnetic field detected");
      }
      else
      {
        digitalWrite (Led, LOW);
        Serial.println("No magnetic field detected");
      }
      delay(1000);
    }
    
Copy and paste this code on your console.

**Step3:-**

Now compile the program by clicking on the **Verify** button or by pressing **Ctrl+R**.

**Step4:-**

Now upload the program on your arduino board by clicking on the **upload** button or by pressing **Ctrl+U**

**Step5:-**

Open the **tools-->Serial Monitor** and see the results by bringing the magnet near the sensor.
