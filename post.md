# Lab 04: Microcontrollers, Sensors, and Actuators

## What We Did in The Last Lab

In the previous lab, we delved into digital circuit design, starting with the creation of a 2 to 1 mux using fundamental logic gates like AND, OR, and NOT gates. Progressing further, a 74150 mux chip was utilized to construct a 4 to 1 mux, meticulously wiring based on comprehensive diagrams and documentation. Integrating Arduino, it was employed to control and test the mux's functionality, programming it to manage input data and control lines while validating output accuracy through systematic testing. Lastly, a 1-bit adder circuit was designed and implemented, showcasing proficiency in combining logic gates for arithmetic operations. For more in-depth lab details, refer to the previous lab blog post in this [URL](https://github.com/mlcourses/lab-3-blog-post-group5_cs281/blob/main/post.md)

## Overview and Motivation
In this lab, we'll use the arduino microcontroller to communicate and interact with our surrondings. This lab is broken into five different parts. Four of which are exploratory exercises, where we will learn about and use two sensors and two actuators. These include a Buzzer, a Servo, a Ultrasonic Sensor, and a Photoresistor. The Buzzer is an actuator that produces a sound when there are changes in the environment. The Servo is a motor that reacts pulses it gets from the arduino controller. The Ultrasonic Sensor, similar to a sonar radar, uses sonar to measaur distance. The Photoresistor measures how bright a light is. The fifth section of the lab will consists of a design challege. We will choose between a light detector, a distance detector, or a mechanical light follower and design and implement that project. The challenge is developing our own code for the arduino controller, along with devloping our own design to build one of the projects listed above.

## Lab Objectives


## Materials

- PB-503 breadboard prototyping station

- Arduino microcontroller

- Buzzer

- Ultrasonic Sensor

- Wires and connection tools

- Logic Probes

- Arduino IDE software

- USB cable

- Laptop or device for programming and powering the Arduino


## Project Steps

### 1. Buzzer

- In this first part of the lab, we are going to familiarize ourselves with implementing a simple actuator called a buzzer. The buzzer serves to create a tangible change in the surrounding environment by emitting a sound, the intensity of which is regulated by a series of pulses directed to the buzzer.

- The buzzer comprises of two input pins: `+` and `-`. 

- Inside the buzzer is a metallic membrane. In its default state, when no voltage is applied across the input pins, the membrane remains contracted (inward). However, when a 5-volt difference is applied across these pins, the metallic membrane becomes excited, extending outward. This transition from the default state to the excited state, or vice versa, results in an audible click. By rapidly alternating the voltage, we can prompt the buzzer to generate a tone. 

- The frequency of this vibration determines the pitch or frequency of the produced tone.

#### Testing the Buzzer

1.  For the first test of the buzzer, we can start with plugging the buzzer onto the breadboard so that the two pins span two distinct rows with the `+` pin in the higher row and the `-` pin is in the lower row. 

- We will wire the `-` pin to Ground, and plug one end of a test wire to the `+` pin. 

- Using the other end of the test wire, we can touch it and release to any +5V connections throughout the breadboard. We should hear a "click" sound each time we touch and release the wiring pin, see the video below for demo



2.  The second test would be using the breadboard's function generator to power up the buzzer and modify its behavior. 

- We can do it by plugging the other end of the test wire to the input of the function generator (non-TTLs). The video below demonstrates different behaviors of the buzzer corresponding to different settings of the function generator.



3. Automate testing with Arduino

- Plug the other end of the buzzer wire into Arduino pin 13 and wire the Arduino's GND pin to a Ground pin on the breadboard.

- Type and upload the following program to the Arduino:

```C++
#define BUZZER 13
int once = 0;

void setup ()
{
    pinMode(BUZZER,OUTPUT);
    Serial.begin(9600);
    Serial.println("Start");
}
void loop ()
{
    int p = 3;
    int i;
    if ( !once ) {
        Serial.println("Starting buzzer");

        for ( i = 0; i < 500; i++ ) {
            digitalWrite(BUZZER,HIGH);
            delay(p);
            digitalWrite(BUZZER,LOW);
            delay(p);
        }
            once = 1;
            Serial.println("Stopping buzzer");
    }
}
```

- Below is the behavior of the buzzer:

#video

- We can type a new program (as below) to test the buzzer with 2 different frequencies per loop.

```C++
#define BUZZER 13

void setup ()
{
    pinMode(BUZZER,OUTPUT);
    Serial.begin(9600);
    Serial.println("Start");
}
void loop ()
{
    int f1 = 3000;
    int f2 = 1000;
    tone(BUZZER,f1);
    delay(1000);
    tone(BUZZER,f2);
    delay(1000);
}
```


## Testing

## Conclusion




