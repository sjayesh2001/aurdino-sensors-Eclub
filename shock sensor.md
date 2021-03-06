## SHOCK SENSOR

**Introduction** 

This shock sensor uses a SW-18015P switch to detect shocks, vibrations and impacts. There is no special library 
for this sensor as it is a simple sensor which consist of a switch which primarily consists of a terminal that forms a center 
post and a second terminal that is a spring that surrounds the center post. When a sufficient force is transferred to the switch,
the terminal consisting of the spring moves and shorts both terminals together momentarily. So, therefore output from this sensor
is either 0 or 1.

![pin diagram](/images/shocksensor.jpg)

**Components**

* 1 * Arduino Uno board
* 1 * USB cable
* 1 * breadboard
* 1 * shock sensor
* DuPont Wires(Female to Male)

**Example**

Let us a build a simple circuit using shock sensor. In this circuit the builtin led of arduino will light up whenever sensor will
detect a shock.

**Connections**

* +ve terminal to +5v 
* -ve terminal to gnd
* signal(s) to digital pin 3 of arduino

![connection](/images/Arduino_KY-002_Keyes_Vibration_switch_module_connection-diagram.png)

**Code**:-

    int val; // define a numeric variable val 

    void setup () {
	pinMode (13, OUTPUT); // LED pin as output  
	pinMode (3, INPUT); // input from KY-002 sensor
     } 

    void loop () {
	val = digitalRead (3); // read the value from KY-002
	if (val == HIGH ) {// when sensor detects shock, LED flashes  
		digitalWrite(13, LOW);
	} else {
		digitalWrite (13, HIGH);
	}
    }
    
* Now compile the program by clicking on the **Verify** button or by pressing **Ctrl+R**.
* Now upload the program on your arduino board by clicking on the **upload** button or  by pressing **Ctrl+U**.
* Either you can use **Built-in led** or you can connect an external led to a digital pin of arduino and changing the code
accordingly.

