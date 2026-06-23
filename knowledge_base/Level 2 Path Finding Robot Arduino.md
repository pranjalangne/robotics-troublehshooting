## JUNIOR ROBOTICS

MANUAL

Path Finding Robot

![](images/f54f717bd52ff6c27418d1218b2c1a12fc89a92ca359d8200bf9fc8f46bcfd75.jpg)

<details>
<summary>natural_image</summary>

Orange robotic device with exposed circuit board and tire, no visible text or symbols
</details>

# Workshop 1

\- Adding Liquid Crystal Display

![](images/7a335a9a788a339de178f878d0f928c5d8775958184f20e21010f2936c515767.jpg)

Hi Andy, welcome to next part of the course which is to make a path finding robot. First, we start with adding an LCD display

![](images/5b3777668efb019101226a0f6bcbb77e51c8b93ab6f18e527b3ef5195660400f.jpg)

That is Exciting, what is an LCD display?

![](images/a9067abad0e7cedc2193a61933804fd8a0a02eb6e4091fc0c8d09f4c1d655136.jpg)

Liquid Crystal Display also known as LCD where you can display letters and number on the screen. LCD is extremely useful when you need to troubleshoot your robot. We are using a 16 x 2 Display, which means it have 16 columns and 2 rows where we can set the cursor at particular position, where we wanted to display the text or numbers

![](images/17d65e31ce112e910490d77db5f65d99630611cb241e458a903edb878b30d40f.jpg)

Okay, what is the first step?

![](images/adbad4d24309b4460706feca592067db4e475860dfe9ca68fea58363038e0864.jpg)

First step is to assemble the display!

Place two golden standoffs in the holes near the batter holder using the screws from the bottom of the robot frame

Refer to figures 1.02 and 1.03  
![](images/6f9168ff4d3dc227421db1c3b30448376dce14c2c6df3ea1ad99b36e15a9cac1.jpg)

![](images/b370ac103399fc18023ea121ab7cd8c54f139651b6e03344b2a1b36381c368d1.jpg)

![](images/38c40f6b4435879d2bf404eff045b7197dabd441983611a4b3e81824a9fb95db.jpg)  
Figure 1.01

![](images/7af40fd92bbe6ae833fd1a0ee84b8d039147cf4e3861442a35c3ca32edeab573.jpg)

<details>
<summary>natural_image</summary>

Close-up of a printed circuit board with visible traces and connectors, no readable text or symbols
</details>

Figure 1.02

![](images/eba6d0f27238bcc027811647c43f8d455c486def8a07a32010de6f39cfacdd2b.jpg)

<details>
<summary>text_image</summary>

Close-up of an electronic circuit board with labeled components and electronic components, including a blue battery and multicolored electronic components.
</details>

Figure 1.03

Follow these images to assemble the LCD display

![](images/3c9e6ca23d334355c92c35334ab2b5c31b4b7f4a3bd8c4ec1eea9a0f1395a78f.jpg)

<details>
<summary>natural_image</summary>

Electronic circuit board with blue display and orange frame, no visible text or symbols on the board or background
</details>

Figure 1.04

![](images/f0a2b6fe0549c28017092e99c8ac5ab4e79d7a475ddddbf44d55258935817afc.jpg)

<details>
<summary>natural_image</summary>

Close-up of an orange robotic vehicle chassis with a blue circuit board and yellow wheels (no visible text or symbols)
</details>

Figure 1.05

## Step 2

Connections:

Connect the LCD to the LCD pins highlighted in the board, make sure pins are connected correctly

i) GND: ground or --  
ii) VCC: +  
iii) SDA - SDA  
iv) SCL - SCL

![](images/c98caeb8227b6ecb94b0dd4215f78f6454bed8039110532fc30aa7c6e4a51adc.jpg)

<details>
<summary>text_image</summary>

GND
VCC
SDA
SCL
AD/AL/2
SS U1
C3
R2
R1
</details>

Figure 1.06

![](images/5f4e83f68677d8c3be40dee91d40a6e9f37ff070f7c1f181e6d6656f5bc05b88.jpg)

<details>
<summary>natural_image</summary>

Close-up of electronic circuit boards and connectors on an orange PCB, with no visible text or symbols on the components themselves.
</details>

![](images/548ca26c6a67621ecea9408bd63322e7645983ddd1dc96627aa99574e468a9b2.jpg)

<details>
<summary>natural_image</summary>

Interior view of an orange toy vehicle chassis with visible circuit boards and wheels (no text or symbols)
</details>

Figure 1.09

![](images/1b5173e8515f72dac1e79d9667ba74179635bf52d42b2d38a616c6bedaa96928.jpg)

<details>
<summary>natural_image</summary>

Top-down view of an orange robotic car with a blue circuit board and wiring, no visible text or symbols
</details>

Figure 1.08

## Step 3

After installation, we are ready to program the LCD

Before programming we need to add the Liquid Crystal Display zip file to our library, go to sketch and click on Include library and select add zip library and select our LCD file as shown in the below figure

![](images/79c8f2433239db80416fbb139780d58ee1d166026cc6e734ca9e8d8f0e7ffa7e.jpg)


Figure 1.10

Address – The address represents the address of the LCD, we need this as we are using I2C protocol. There are two options available, we will use hit and try method, try both the address and one of them will work.

Let’s make a program for our LCD to print “Hello World”

![](images/6bc2257a845b0a3827fbd290e0501f2278f35acde9da8f2171abe2881bafb8f5.jpg)

<details>
<summary>text_image</summary>

#include <LiquidCrystal_I2C.h>
// Including the LCD Display Library

LiquidCrystal_I2C lcd = LiquidCrystal_I2C(0x27,16,2);
//Assigning the LCD address, rows and columns
void setup() {
    // put your setup code here, to run once:
lcd.begin();
lcd.backlight();
}

void loop() {
    // put your main code here, to run repeatedly:
lcd.setCursor(0,0);
lcd.print("Hello world");
}
</details>

Figure 1.11

## Challenge 1

Display your first name in the first row and last name in the second row

# Workshop 2

Let us make a counter to count from 1 to 100 on LCD and display the same. We need to create a variable for this. Variable is like an empty container in which we can store different letters or numbers.

Hello\_world | Arduino 1.8.15 (Windows Store 1.8.49.0) File Edit Sketch Tools Help  
![](images/84ff4507a5c4113e6df52fbf147de5ee2886ac432aa5297700e1531a42c8ab1c.jpg)

Hello\_world §  
```cpp
#include <LiquidCrystal_I2C.h>
// Including the LCD Display Library

LiquidCrystal_I2C lcd = LiquidCrystal_I2C(0x27,16,2);
//Assigning the LCD address, rows and columns
void setup() {
    // put your setup code here, to run once:
lcd.begin();
lcd.backlight();
}

void loop() {
    // put your main code here, to run repeatedly:
lcd.setCursor(0,0);
int Variable_count,i;
for(i=1;i<= 100; i++)
{
    Variable_count = i;
    lcd.print(Variable_count);
    delay(1000);
    lcd.clear();
}
}
```  
Figure 1.12

## Workshop 3

\- Adding Servo Motor

Hi Aebo, what are we doing today?


Andy, we are learning about how to use our servo motor


What is a servo motor?


A servomotor is a linear actuator that allows for precise control of angular or linear position which uses position feedback to control our robot’s motion and final position


Are we adding the servo motor to our robot today?


Yes, let’s start today’s workshop

![](images/5724edd8bc9f3c66f921aa50f2d37aa2fb60654f99b74bf0c86af370d36da2a6.jpg)

<details>
<summary>natural_image</summary>

Close-up of a blue electronic device with orange and black wires, no visible text or symbols
</details>

## Step 1

First, take a servo motor and a servo horn. The servo has three cables:

i) Brown  GND  
ii) Red Vcc  
iii) OrangeOut

## Step 2

Insert the servo horn with four sides on top of the motor and insert the motor into the board with wire going in first and connect it to the Servo (pin 8) port as shown in the figures. The side with the brown cable goes into the positive side of the servo motor pin located in the board

Refer to the following images for assembling the servo motor

![](images/5890372eec389f28a5c35f519f34fc4a2aa296f8c07ee84fdac0e54a20ec4b2a.jpg)

<details>
<summary>natural_image</summary>

Close-up of an electronic circuit board with electronic components and a red circle highlighting a specific component (no readable text or symbols)
</details>

Figure 1.15

![](images/6acb2e138a887c07886c9e7a063d0e6071dc9eef0cb37159852e189b01486ddc.jpg)

<details>
<summary>natural_image</summary>

Close-up of an orange industrial component with a blue plastic housing and white components, no visible text or symbols.
</details>

Figure 1.16

![](images/4b0f678ad67ca9a8de45807641dfaa7dfefefcabbbcdbb90e1ed560b96506dc3.jpg)

<details>
<summary>natural_image</summary>

Close-up of a blue electronic device with visible wiring and a white connector, mounted on an orange base (no text or symbols visible)
</details>

Figure 1.17

![](images/b6fba14d14a0df2fddfe93066037564200268a3641e8ab2e13dc621e14b5673b.jpg)

<details>
<summary>natural_image</summary>

Close-up of an electronic circuit board with embedded components and wiring, no visible text or symbols on the main body
</details>

Figure 1.18

## Step 3

To move the servo, first, upload the code in the following Figure into the Arduino. This code makes the servo move between angle 0 degrees and 180 degrees in the interval of 1 second To move the servo, first, upload the code in the figure 1.19 to the Arduino. This code makes the servo move between angle o degrees and 180 degrees in the interval of 1 degree

servo\_1 | Arduino 1.8.15 (Windows Store 1.8.49.0) File Edit Sketch Tools Help  
```cpp
#include <Servo.h>
// Including servo motor library
Servo myServo;
void setup() {
    // put your setup code here, to run once:
myServo.attach(8);
//Attaching pin 8 to our servo motor
}

void loop() {
    // put your main code here, to run repeatedly:
myServo.write(0);
delay(1000);
myServo.write(180);
delay(1000);
}
```  
Figure 1.19


## Challenge 2

Make servo move in 10 degrees interval from 0 to 180 and 180 to 0

```cpp
#include <Servo.h>
// Including servo motor library
Servo myServo;
void setup() {
    // put your setup code here, to run once:
myServo.attach(8);
//Attaching pin 8 to our servo motor
}

void loop() {
    // put your main code here, to run repeatedly:
int counter =0, i;
myServo.write(0); // setting up the basic position to 0 degrees
for(i=1; i<=180; i++)
{
myServo.write(counter =i);
delay(300);
}
for(i = counter; i>0; i--)
{
myServo.write(counter=i);
delay(300);
}
}
```  
Figure 1.21

## Workshop 4

\- Adding Ultrasonic sensor


Hi Aebo, what are we doing today?


Andy, we are learning how to use our ultrasonic sensor


What is an ultrasonic sensor?

Ultrasonic sensors are devices that generate or sense ultrasound energy, it measures the distance of a target object by emitting ultrasonic sound waves, and converts the reflected sound into an electrical signal

Are we connecting the sensor to our Aebo?

Yes, let’s start

## Step 1

Insert the ultrasonic sensor into the casing

The next step is to connect the ultrasonic sensor with the mounting. Before doing this, upload the servo calibration program into your Arduino. This to make sure the servo motor is calibrated to face forward when the servo angle is 90

![](images/954d60107407319f480d42e451f881b5b856d5afec3d8d1641c938e064717c4b.jpg)

<details>
<summary>text_image</summary>

#include <Servo.h>
// Including servo motor library
Servo myServo;
void setup() {
    // put your setup code here, to run once:
myServo.attach(8);
//Attaching pin 8 to our servo motor
}

void loop() {
    // put your main code here, to run repeatedly:

myServo.write(90); // setting up the basic position to 90 degrees
}
</details>

Figure 1.22

![](images/41559d32f496900023ce6766a86c05bcd1210212fc45122b54f02ce964681f4c.jpg)

<details>
<summary>natural_image</summary>

Close-up of a blue electronic device with two circular ports and three antennas (no visible text or symbols)
</details>

Figure 1.23

![](images/8c94f67ade9f8d3800a5f956343f85db5488e9deb3090df3f2e7c5f4ce98e7b1.jpg)

<details>
<summary>natural_image</summary>

Orange 3D model with two circular speakers mounted on a base (no text or symbols visible)
</details>

Figure 1.24

![](images/11e577351c6bdeed8eef45efc2f97fee11c64d8b930ed3de381525ff5ee147e6.jpg)

As shown in the figure, connect the ultrasonic sensor to the sensor mount and secure it using the screws given in the servo motor packet and connect the pins of ultrasonic sensor to the pins on the board using the jumper cables

![](images/fd4f03f18ba75cd69cf66e9f7f95ce5d6b767ea45eb3c3b4e4001304a38b16e9.jpg)

<details>
<summary>natural_image</summary>

Close-up of an orange electronic circuit board with soldering iron and a multi-colored electronic component (no visible text or symbols)
</details>


Figure 1.27

To get the value of the distance in front of the robot use the code below. The distance is displayed in cms


```cpp
#include <LiquidCrystal_I2C.h>
// Including the LCD Display Library
LiquidCrystal_I2C lcd = LiquidCrystal_I2C(0x27,16,2);
float calc_distance()
{
    digitalWrite(A1,LOW);
    delayMicroseconds(2);
    digitalWrite(A1, HIGH);
    delayMicroseconds(10);
    digitalWrite(A1,LOW);
    long int duration = pulseIn(A0, HIGH);
    float distance = duration * (0.034/2);
    return distance;
}
void setup() {
    // put your setup code here, to run once:
lcd.begin();
lcd.backlight();
pinMode (A1, OUTPUT);
pinMode(A2, INPUT);
}

void loop() {
    // put your main code here, to run repeatedly:
    lcd.setCursor(0,0);
float distance = calc_distance();
    lcd.print(distance);
    delay(100);
    lcd.clear();
}
```  
Figure 1.29

To complete this program, we have used basic mathematics principles like Speed = Distance/Time and speed of light is 343m/s or 0.034 cm/s

## Workshop 5 & 6

\- Social Distancing Robot

Hi Aebo, what are we doing today?

Andy, we are making our Aebo a social distancing Robot

What is a social distancing robot?

A social distancing robot will maintain safe distance from any obstacle, if an object appears in its path, it will stop and move backwards and after moving away from the obstacle, it goes forward and if the object maintains safe distance then the robot stays still


Sounds good, let’s start coding then

We can use earlier defined blocks of forward, backward and stop Robot in our social distancing Robot

## Final code for social distancing Robot

Social\_Distancing | Arduino 1.8.15 (Windows Store 1.8.49.0)

Social\_Distancing §  
```txt
#include<Servo.h>
#include<LiquidCrystal_I2C.h>
Servo myservo;
LiquidCrystal_I2C lcd(0x27,16,2);
int distance;
int duration;

void setup() {
lcd.begin();
pinMode(A0,INPUT);
pinMode(A1,OUTPUT);
pinMode(12,OUTPUT);
pinMode(13,OUTPUT);
pinMode(11,OUTPUT);
pinMode(3,OUTPUT);
myservo.attach(5);
myservo.write(90);
}

void loop() {
myservo.write(90);
delay(100);
lcd.setCursor(10,0);
lcd.print("      ");
calc_distance();
lcd.setCursor(0,0);
lcd.print("Distance");
lcd.setCursor(10,0);
lcd.print(distance);
if (distance < 20)
{
backward();
}
if (distance > 20 and distance <35)
{
stopRobot();
}
if (distance > 35){
forward();
}
}
```

```cpp
void calc_distance()
{
digitalWrite(A1,LOW);
delayMicroseconds(2);
digitalWrite(A1,HIGH);
delayMicroseconds(10);
digitalWrite(A1,LOW);
duration = pulseIn(A0,HIGH);
distance = 0.034*duration/2;
}
void forward()
{
digitalWrite(12,HIGH);
digitalWrite(13,HIGH);
analogWrite(3,100);
analogWrite(11,100);
}

void backward()
{
digitalWrite(12,LOW);
digitalWrite(13,LOW);
analogWrite(3,100);
analogWrite(11,100);
}

void stopRobot()
{
analogWrite(3,0);
analogWrite(11,0);
}
```  
Figure 1.30

## Workshop 7 & 8

## - Path finding Robot


Hi Aebo, what are we doing today?

Andy, we are making a path finding robot

What is a path finding robot?

A path finding robot travels through an obstacle course where humans cannot enter, for example robots used in mining, rescue robots used in underground caves

What are the steps to be followed?

We will learn the steps in detail along the way let’s start

## Follow the below steps to complete the path finding robot

We need to program our robot so it moves forward when the distance in front of the robot is more than 20cms.  
If distance is less than 20cms, robot looks left and right.  
 Gets the distance of each side.

Compares the distance and travel towards the direction which has greater distance

## Final code for Path Finding Robot

```cpp
#include <LiquidCrystal_I2C.h>
#include <Servo.h>
float distance = 0;
float leftdistance = 0;
float rightdistance = 0;

Servo servo_8;

void seeleft () {
    servo_8.write(135);

}

void seeright () {
    servo_8.write(45);

}
void seestraight () {
    servo_8.write(90);

}

LiquidCrystal_I2C lcd = LiquidCrystal_I2C (0x27, 16,2);

int calc_distance(int trig, int echo) {
    digitalWrite(trig,LOW);
    delayMicroseconds(2);
    digitalWrite(trig,HIGH);
    delayMicroseconds(10);
    digitalWrite(trig,LOW);
    float duration = pulseIn(echo,HIGH);
    int distanceValue = duration*0.034/2;
    return distanceValue;
}

void Forward () {
    digitalWrite(12,1);
    digitalWrite(13,1);
    analogWrite(11,100);
    analogWrite(3,100);
}
```  
Figure 1.31

```cpp
void left () {
    digitalWrite(12,1);
    digitalWrite(13,0);
    analogWrite(11,100);
    analogWrite(3,100);
}
void Backward () {
    digitalWrite(12,0);
    digitalWrite(13,0);
    analogWrite(11,100);
    analogWrite(3,100);
}
void right () {
    digitalWrite(12,0);
    digitalWrite(13,1);
    analogWrite(11,100);
    analogWrite(3,100);
}
void StopRobot () {
    digitalWrite(12,0);
    digitalWrite(13,0);
    analogWrite(11,0);
    analogWrite(3,0);
}
void setup() {
    servo_8.attach(8);
    lcd.begin();
    pinMode(A0,INPUT);
    pinMode(A1,OUTPUT);
    pinMode(12,OUTPUT);
    pinMode(13,OUTPUT);
    pinMode(11,OUTPUT);
    pinMode(3,OUTPUT);
}
```  
Figure 1.32