# JUNIOR ROBOTICS

MANUAL

## Soccer Bot

## Workshop 1

![](images/f42c2511ec48815949c8046bfd361f5420e7561b52a2e65c94693b6ce982caf6.jpg)

Hi Andy, welcome to the next part of our course which is to make a SoccerBot

First, we start revising what we learned in Level 2 course

![](images/947d1efe7acea944274260e0549f345596947627d9248005ed0e4d01f6c77729.jpg)

Do you remember what you learned in Level 2 ?

![](images/2ff82681758fd709814274860790b779fc938b098844be08d268e15c54734789.jpg)

![](images/7e607fbcbf465cb0544a436bbf4300a6223c1736a0060e10d343e2b33e571f07.jpg)

Okay, I remember we learned how to make a Path Finding Robot and a Social Distancing Robot

Great!!! Let’s revise then with another basic LED program, we will play with the brightness of LED light

![](images/6a7e6f054b8fa865c852d95a5a1c5a22402c6256e1e0d980a42ac89af7b9b8ad.jpg)

![](images/cd952de3f8e1f74c47f745cf546c5a6be77a074948d42a575883b160010dd490.jpg)

Interesting, I’m ready to start

Let’s write a code for increasing the LED brightness from dark to bright

To control the brightness of the LED we will be using PWM signal, this signal can go from 0 to 255, we can assign this to the longer pin(positive) of the LED so that it’s brightness can be controlled

```cpp
int Led_brightness = 0;
void setup() {
    // put your setup code here, to run once:
    pinMode(5,OUTPUT);
    pinMode(6,OUTPUT);
}

void loop() {
    // put your main code here, to run repeatedly:
    digitalWrite(5,LOW);
    for(int i=0; i<256; i++)
    {
        Led_brightness = i;
        analogWrite(6, Led_brightness);
        delay(1000);
    }
}
```  
Figure 1.01

## Challenge 1

Decrease the brightness of the LED from bright to dark

## Workshop 2


The Analog Joystick is similar to two potentiometers connected together, one for the vertical movement (Y-axis) and other for the horizontal movement (X-axis). The joystick also comes with a Select switch, when the gear is pressed the switch changes its position and when released, it will go back to alternative position, the joystick has 5 pins as shown in the figure

VCC - Power supply

GND – Ground

VRx – Horizontal control

VRy – Vertical control

SW - Switch

![](images/1d51256417d55bf913d22e59f7808ce12bc8f37d2355a94789cff6c5807ae520.jpg)

<details>
<summary>natural_image</summary>

Close-up of a black industrial motor with a spherical body and external components (no visible text or symbols)
</details>

Figure 1.02

The four positions of the gear can be used to control the Forward, Backward, Left and Right directions of the Aebo. Initially when the gear is in idle position the X and Y values are 512,512 which means neutral position and when you move the Joystick gear completely forward, the y axis value goes towards 1023(max value) and if pushed in opposite direction its value goes towards zero, similarly for X-axis, complete Left will go to 1023 and if pushed to complete right will go towards zero

![](images/5e3ef52059c527be9437786b9da096db6d80f838d0d733e8a7dd6880eab3399d.jpg)

<details>
<summary>text_image</summary>

X = 512
Y = 1023
X = 0
Y = 1023
X = 1023
Y = 1023
X = 0
Y = 512
X = 512
Y = 512
X = 0
Y = 0
X = 512
Y = 0
GND
+5V
VRx
VRy
SW
</details>

Figure 1.03

will connect the Joystick to the Robot as shown in the figures 1.04 And 1.05

![](images/1855f76a5ad4beb14e057a344708203dcb22459328e830796490d33ed4bacfa2.jpg)


Figure 1.04

![](images/5a627724213e12de46cf001630488ad2cb265966949f8a4cbda2bcfc23edb9a2.jpg)

<details>
<summary>natural_image</summary>

Close-up of a black handheld device with a spherical component mounted on a circuit board, no visible text or symbols.
</details>

![](images/9aa2fa577484c8a54d974eb0370854d5bd0d7756416586130d5ee19e2c973e2e.jpg)

<details>
<summary>natural_image</summary>

Close-up of electronic components including a blue circuit board, orange electronic device, and a black sensor module (no visible text or symbols)
</details>

Figure 1.05

Let’s write a code for displaying VRx and VRy values on our LCD display to understand how the joystick works

```cpp
#include <LiquidCrystal_I2C.h>

int Vrx = 0;
int Vry = 0;

LiquidCrystal_I2C lcd(0x27,16,2);

void setup() {
  // put your setup code here, to run once:
  lcd.begin();
  lcd.backlight();
  pinMode(A2,INPUT);
  pinMode(A3,INPUT);
}

void loop() {
  // put your main code here, to run repeatedly:
  Vrx = analogRead(A2);
  Vry = analogRead(A3);
  lcd.setCursor(0,0);
  lcd.print("Vrx value is");
  lcd.print(Vrx);
  lcd.setCursor(0,1);
  lcd.print("Vry value is");
  lcd.print(Vry);
  delay(100);
  lcd.clear();
}
```  
Figure 1.06

## Workshop 3


We can use earlier defined blocks of Forward, Backward, Left, Right and Stop\_robot in our program to control the Aebo using the Joystick

```txt
int Vrx = 0;
int Vry = 0;
void Left();
void Right();
void Forward();
void Backward();
void Stop_robot();
void setup() {
    // put your setup code here, to run once:
pinMode(A2,INPUT);
pinMode(A3,INPUT);
pinMode(3,OUTPUT);
pinMode(11,OUTPUT);
pinMode(12,OUTPUT);
pinMode(13,OUTPUT);
}
void loop() {
    // put your main code here, to run repeatedly:
Vrx = analogRead(A2);
Vry = analogRead(A3);
if (Vry<200)
{
    Forward();
    }
    if (Vry>800)
{
    Backward();
    }
    if (Vrx<200)
{
    Left();
    }
    if (Vrx>800)
{
    Right();
    }
    if (((Vrx>200) && (Vrx<800)) && ((Vry>200) && (Vry<800)))
{
    Stop_robot();
    }
}
```  
Figure 1.07

## Workshop 4


## Bluetooth Module

The Bluetooth module is designed for serial communication which Transmits and Receives data in a pipeline within a range of 30ft or 10 meters

We use two modules for our Aebo communication, one is connected to Joystick for transmitting commands and the other is connected to the Aebo board for Receiving commands

Before communication, both the Bluetooth modules need to be paired, which is already done before hand

Now when both the Bluetooth modules were turned on, the red light will blink continuously which means it is searching for its pair, if we bring both of them within range then they will communicate and get paired, after that both Bluetooth lights will blink at heartbeat rate

![](images/ba0929f4f688b217f187d0ce8ae626e77050ead9f61d214cd3851f848ee30747.jpg)

<details>
<summary>natural_image</summary>

Close-up of a transparent electronic circuit board with visible traces and components (no readable text or symbols)
</details>

Figure 1.13

![](images/5f052969d46b2b196f876c19b5fe29fd33a54a047e8561f9b44d867c50b8fbf7.jpg)


Figure 1.14

Connect the two joysticks to the Aebo controller as shown in figures 1.16 and insert the Bluetooth transmitter which has T written on its back side as shown in figure 1.17

![](images/9afffd6d18142a2d1c52da32a4ef2981817850ad2ebf9b209d770f803a2640ae.jpg)

<details>
<summary>natural_image</summary>

Purple electronic circuit board with various connectors and connectors (no visible text or symbols)
</details>

Figure 1.15

![](images/8fd6aef1ae353841aac431de2b24020752567d5c3552f0eff85e9d880779d86a.jpg)

<details>
<summary>natural_image</summary>

Purple circuit board with two black controllers and a printed circuit board (no visible text or symbols)
</details>

Figure 1.16

![](images/c54392e2da98b679dafbd8964198c1cebb135b0e79a790e72539a9cca755861f.jpg)

<details>
<summary>natural_image</summary>

Purple circuit board with two black controllers and a display module (no visible text or symbols)
</details>

Figure 1.17

![](images/94d5dbe58df49c6fb44ee22ff7955593fb922c07643e5820ecae852f8b11b312.jpg)


Figure 1.18

Insert the Bluetooth receiver module which has R written on its back side into the robot as shown in figures 1.18 and 1.20

![](images/ebd01d92742d60dd8d91b020444e51c5603c1f94afb32e155224cbcccfab897d.jpg)

<details>
<summary>natural_image</summary>

Close-up of a small electronic circuit board with visible traces and components, mounted on an orange base (no readable text or symbols)
</details>

Figure 1.19

![](images/5c99eed75ccaf36f36155a1f075a572a029406b9e9455ad57339bb91d94e85f5.jpg)

<details>
<summary>natural_image</summary>

Close-up of a small electronic device with a black power source, orange circuit board, and blue display panel (no visible text or symbols)
</details>

Figure 1.20

For each time the Joystick is moved from one direction to another, forward , backward, left, or right, the Vrx, Vry and switch values will change and update continuously which makes it difficult to send values through a wireless connection.

Due to this reason we will send a simple character instruction of ‘F’ for forward and ‘S’ for stop and similarly for all other directions. To program the joystick module, we need to follow the following steps.

## Step 1 :

Now we are ready to program and upload to our joystick

You can use the code from the fig 1.21.7 and upload it to the board by selecting the AEBO joystick board as shown in fig 1.21.8.

```txt
void setup() {
    // put your setup code here, to run once:

    //Joystick2
    pinMode(8,INPUT); //Xaxis
    pinMode(9,INPUT); //Y axis

    Serial1.begin(115200);

}

void loop() {
    // put your main code here, to run repeatedly:

    VRX2 = analogRead(8);
    VRY2 = analogRead(9);

    if (VRX2 <200){
        Serial1.println('L');
    }

    if (VRX2 >700){
        Serial1.println('R');
    }

    if (VRY2 <200){
        Serial1.println('B');
    }

    if (VRY2 >700){
        Serial1.println('F');
    }

    if (VRX2>200&&VRX2<700&&VRY2>200&&VRY2<700){
        Serial1.println('S');|
```

Figure 1.21.7  
![](images/de7e911f85191dd4112fd2267199b0777b85175871e665383cb1221fc2c2a087.jpg)

<details>
<summary>text_image</summary>

sketch_aug05a | Arduino 1.8.15 (Windows Store 1.8.49.0)
File Edit Sketch Tools Help
Auto Format Ctrl+T
Archive Sketch
Fix Encoding & Reload
Manage Libraries... Ctrl+Shift+I
Serial Monitor Ctrl+Shift+M
Serial Plotter Ctrl+Shift+L
// Joystick
pinMode (8, 9)
pinMode (9)
WiFi101 / WiFiNINA Firmware Updater
Board: "Arduino Uno" > Boards Manager...
Serial1.b
Port > AEBO Boards > AEBO Joystick
Get Board Info > Arduino AVR Boards >
}
void loop()
// put your main code here, or text export/return;
VRX2 = analogRead(8);
VRY2 = analogRead(9);
if (VRX2 <200) {
Serial1.println('L');
}
if (VRX2 >700) {
Serial1.println('R');
}
if (VRY2 <200) {
Serial1.println('B');
}
if (VRY2 >700) {
Serial1.println('F');
}
if (VRX2>200&&VRX2<700&&VRY2>200&&VRY2<700) {
Serial1.println('S');
}
</details>

Figure 1.21.8

## Workshop 5



## Step 1

First, take two servo motors and insert them into the servo ports with wire going in first and fix them as shown in the figures 1.08 and 1.09

![](images/e11c1d880f0432e9f1b04d15d0f51cd5b05a90f6e52fb8b8cde8d619053716f4.jpg)

<details>
<summary>natural_image</summary>

Close-up of an electronic circuit board with components like a blue LED and battery, no visible text or symbols.
</details>

Figure 1.08

![](images/c2756cd6cf469ce7c7a115430df94cd0ecb4aadf3a95550c83519ab6fcfcc6d0.jpg)

<details>
<summary>natural_image</summary>

Close-up of a blue electronic circuit board with wires and connectors, mounted on an orange surface (no visible text or symbols)
</details>

Figure 1.09

![](images/6c4782e85a5795e5d1acad857b8e1e5c680d5bb9d467ec4ddf08a55f92337e3b.jpg)

<details>
<summary>natural_image</summary>

Orange robotic vehicle with orange sensor and blue actuators on a track, no visible text or symbols on the device itself.
</details>

Figure 1.10

Connect the servo motors to the P9 and P10 pins with brown wire going to negative as shown in figures 1.11 and 1.12

![](images/851c653b8daa27b86a820c6745f5566b9c8688df1e32452d9a1d5fe4699402c1.jpg)


Figure 1.11

![](images/341e2c3f2ac1e4b6b795eca1ed9be557e14ea5286ba631c798ddeff50b3b01d0.jpg)

<details>
<summary>natural_image</summary>

Orange robotic vehicle chassis with visible circuit board, wheels, and wiring (no readable text or symbols)
</details>

![](images/6890687d80825d2807927879120ffd66f750c4899b4145da344977e956dfb4df.jpg)

<details>
<summary>natural_image</summary>

Close-up of an electronic circuit board with labeled components and connectors (no readable text or symbols)
</details>

Figure 1.12

## Workshop 6

## Step 1

Insert the servo horns into the flaps and place them on top of the servo motors as shown in figure 1.22

Before connecting them make sure left and right flaps are placed correctly and fit them Properly as shown in figures 1.23 and 1.24

![](images/3e22d89408cc24a8aff6e1618cd4ecd07bc7f7b31f49c81f217948d6ca438a52.jpg)  
Figure 1.22

![](images/ecf436c2e5f9d2b14e7c12f9164a17543045c4f84c9e5ea492ffef7f4e81e06a.jpg)

<details>
<summary>natural_image</summary>

Orange robotic vehicle with orange base, black sensor, and yellow screwdriver (no visible text or symbols)
</details>

Figure 1.23

![](images/c48dac55e1b5e9f3ecb3d6f8c7fb97f97d0f876862395a2a174e73b25020c524.jpg)

<details>
<summary>natural_image</summary>

Robotic vehicle with orange safety enclosure and yellow screwdriver, no visible text or symbols
</details>

Figure 1.24

Now for controlling the flaps, we use the switch button of the joystick, When the button is pressed both the flaps will be opened and when released they will close

For Bluetooth we send ‘O’ to open the flaps with 90 degrees and ‘C’ to close the flaps Now make sure for closing the flaps, the one connected on the Bluetooth side is set to 180 degrees because the servo horn is designed to the shorter side and for the other side flap set it to zero degrees

Add the code shown in figure 1.25 to control the flops

```cpp
void Flaps_open()
{
    servo_9.write(180);
    servo_10.write(0);
}

void Flaps_closed()
{
    servo_9.write(90);
    servo_10.write(90);
}
```  
Figure 1.25

## Workshop 7
et’s wrap it up then

# Upload the final code for soccerbot as shown in figure 1.26 and 1.27

```cpp
#include <SoftwareSerial.h>
#include <Servo.h>
int bluetooth;
Servo servo_9;
Servo servo_10;
void Left();
void Right();
void Forward();
void Backward();
void Stop_robot();
void Flaps_open();
void Flaps_closed();
void setup() {
    // put your setup code here, to run once:
pinMode(3,OUTPUT);
    pinMode(11,OUTPUT);
    pinMode(12,OUTPUT);
    pinMode(13,OUTPUT);
    Serial.begin(115200);
    servo_9.attach(9);
    servo_10.attach(10);
}

void loop() {
    // put your main code here, to run repeatedly:
        if(Serial.available() > 0){
            bluetooth = Serial.read();
            if(String(char(bluetooth)) == "F") {
                Forward();
            }
            if(String(char(bluetooth)) == "B") {
                Backward();
            }
            if(String(char(bluetooth)) == "L") {
                Left();
            }
            if(String(char(bluetooth)) == "R") {
                Right();
```  
Figure 1.26

```cpp
void Backward () {
    digitalWrite(12,LOW);
    digitalWrite(13,LOW);
    analogWrite(3,100);
    analogWrite(11,100);
}

void Stop_robot () {
    analogWrite(3,0);
    analogWrite(11,0);
}

void Flaps_open()
{
    servo_9.write(180);
    servo_10.write(0);
}

void Flaps_closed()
{
    servo_9.write(90);
    servo_10.write(90);
}
```  
Figure 1.27

Upload the final code for the joystick as shown in figure 1.28  
```aidl
// X axis reading
int VRX2 = 0;
// Y axis reading
int VRY2 =0;
// Switch reading
int SW2 =0;
void setup() {
    // put your setup code here, to run once:
    pinMode(13,OUTPUT);
    // Joystick 2
    pinMode(8,INPUT); // X axis pin
    pinMode(9,INPUT); // Y axis pin
    pinMode(4,INPUT); // switch pin
    Serial1.begin(115200);
    digitalWrite(4,HIGH);
}

void loop() {
    // put your main code here, to run repeatedly:
        // Reading the values
    VRX2 = analogRead(8);
    int    x_value2 = VRX2;
    VRY2 = analogRead(9);
    int    y_value2 = VRY2;
    SW2 = digitalWrite(4);
    delay(10);

    if(x_value2<100){
        Serial1.println('R');
    }
    if(x_value2>800){
        Serial1.println('L');
    }
    if(y_value2<100){
        Serial1.println('B');
    }
    if(y_value2>800){
        Serial1.println('F');
    }
    if(x_value2>200&&x_value2<800&&y_value2>200&&y_value2<800){
        Serial1.println('S');
}

    if(SW2 == 0){
        Serial1.println('O');
    }
    if(SW2 == 1){
        Serial1.println('C');
    }
}
```  
Figure 1.28

