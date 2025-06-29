---
_Source URL: [](https://www.hackster.io/hardikrathod/control-arduino-using-gui-arduino-processing-2c9c6c)._

---

# Control Arduino Using GUI (Arduino + Processing) - Hackster.io


![[826a357955572e984a3b90107755138f.jpg]]

[Hardik Rathod](https://www.hackster.io/hardikrathod)

Published July 21, 2017 © [GPL3+](http://opensource.org/licenses/GPL-3.0)

# Control Arduino Using GUI (Arduino + Processing)

Very easy and interesting project to create GUI (i.e. Buttons, Sliders, Knobs and many more) to control Arduino

[Easy](https://www.hackster.io/projects?difficulty=beginner)Full instructions provided30 minutes9,092
![[b3885c50012673b470c2823f6bc13d40.jpg]]

## [__](https://www.hackster.io/hardikrathod/control-arduino-using-gui-arduino-processing-2c9c6c#things)Things used in this project

### Hardware components

 

|     |
| --- |
| Arduino |
|     |

×1  

|     |
| --- |
| Breadboard |
|     |

×1  

|     |
| --- |
| LED |
|     |

×3  

|     |
| --- |
| 100 Ohm Resistor |
|     |

×1  

|     |
| --- |
| Jumper wires |
|     |

×4 

### Software apps and online services

 

|     |
| --- |
| Arduino IDE |
|     |

   

|     |
| --- |
| Processing |
|     |

  

## [__](https://www.hackster.io/hardikrathod/control-arduino-using-gui-arduino-processing-2c9c6c#story)Story

### [__](https://www.hackster.io/hardikrathod/control-arduino-using-gui-arduino-processing-2c9c6c#toc-introduction-0)Introduction

How interesting if we can control Arduino using some GUI controls (for example Buttons) or represent the sensor results to the screen in graph or slider or text-box or knobs. It would be very nice. Isn't it?

If you have basic idea of Arduino programming then you are totally ready to go. If you don't have, still not a big issue. It is very simple.

In this project you will learn how to create nice GUI to control Arduino and at the end i am sure you will be able to create your own GUIs and i hope you will love it.

### [__](https://www.hackster.io/hardikrathod/control-arduino-using-gui-arduino-processing-2c9c6c#toc-requirements-1)Requirements

As you want to control Arduino, Arduino IDE is first need. And to create GUI all you need is Processing IDE (or you can call it Processing sketchbook). Now let's see what is Processing in short?

**What is Processing?**

Processing is a flexible software sketchbook and a language for learning how to code within the context of the visual arts. Processing is very useful platform for hobbyists, researchers, students for learning and prototyping. Some of the features are:

*   Free and open source

*   For all platforms (GNU/Linux, Mac OS X, Windows, Android, and ARM)

*   Well documented

*   Many libraries

*   Good community

**Arduino IDE**

To download Arduino IDE go here : [Arduino IDE Download page](https://www.arduino.cc/en/Main/Software)

![[c662f5434cf0ef10dc6f27d9c5a931a4.jpg]]

Arduino IDE Download page

**Processing IDE**

To download Processing go here: [Processing Download page](https://processing.org/download/)

![[49aaa16d8513a44164276078f531c89f.jpg]]

Processing IDE Download page

**Running Processing**

When you click on download Processing, it downloads one zip file. Unzip that file and inside the unzipped folder you will find Processing application (see the following image). And to run Processing, double click on that icon.

;

;

__

![[d443789488f3b88bc712209ac0840e59.jpg]]

__

1 / 2 • Processing Application (double click to run)

There are many libraries for different applications. You can also install some extra libraries manually or directly from the menu.

To install new library from menu, go to: Sketch -> Import Library... -> Add Library...

;

;

__

![[a8fefcaba4014e4de0bc3851399193ea.jpg]]

__

1 / 2 • Adding Library

But at the moment we are interested only in GUI design. And there is a very nice library called [ControlP5](http://www.sojamo.de/libraries/controlP5/) is available to create our project. controlP5 is a library written by [Andreas Schlegel](http://www.sojamo.de/) for the programming environment Processing. To add ControlP5 library to Processing just follow the add library process and search for ControlP5 and then click on install. Now you are ready to create your GUI application.

;

;

__

![[ca9f63efb9f0ca4f5bc3ddeddcf3d003.jpg]]

__

1 / 2 • Search for ControlP5

Once you have installed ControlP5, start with creating simple window. See the video down below to get basic idea how to create window and add buttons to the window.

Next step is to write a Arduino sketch. Write a code in such a way that when Arduino receives any character over serial port, it performs some particular task. For example

       if(val == 'r'){           //if r received 
         digitalWrite(11, HIGH); //turn on pin 11 (red led in our case) 
         } 
    

So when Arduino receives char 'r', it sets pin 11 to High. Please check the codes in code section below to get exact idea.

Now comes the Processing part. There is a Serial library in the Processing and we can use that to read and write to the serial port. So what we do now is we assign a function to each of the buttons to send some character to serial port, so when you press any button, it send particular char to the serial port. For example suppose we have a button called red, when you press button red it sends char 'r' to the serial port.

    void red(){ 
     port.write('r'); 
    } 
    

At the other end, Arduino receives that char 'r' and according to the received char it changes state of the pins.

Please check the code, so you can get exact idea how to add buttons and assign functions to the buttons.

Code is in the Code section. There you will find code for both, Arduino and Processing. First compile and upload the Arduino sketch to the arduino and then run Processing sketch.

### [__](https://www.hackster.io/hardikrathod/control-arduino-using-gui-arduino-processing-2c9c6c#toc-components-and-circuit-2)Components and Circuit

;

;

__

![[3d1392952f663b88c6aa1068dbcaa218.jpg]]

__

1 / 2 • Components

Processing window will be look like following if you use code provided below.

![[71435e794c521975fbe34d392ceb26ba.jpg]]

Processing window

Summery of the project is in the following video.

__

Summery of the project

I hope you liked this project and learned something new. Feel free to ask if you have any questions.

Thank

[[#|__Read more]]

## [__](https://www.hackster.io/hardikrathod/control-arduino-using-gui-arduino-processing-2c9c6c#schematics)Schematics

### Circuit

![[b166ed77bbcc8ac379659b61f1ec6111.png]]

## [__](https://www.hackster.io/hardikrathod/control-arduino-using-gui-arduino-processing-2c9c6c#code)Code

*   [[#|Arduino Sketch]]
    
*   [[#|Processing sketch]]
    

### Arduino Sketch

Arduino

**1**void setup() { **2** **3**  pinMode(10, OUTPUT);   //set pin as output , blue led **4**  pinMode(11, OUTPUT);   //set pin as output , red led **5**  pinMode(12, OUTPUT);   //set pin as output , yellow led **6** **7**  Serial.begin(9600);    //start serial communication @9600 bps **8**  } **9** **10**void loop(){ **11** **12**  if(Serial.available()){  //id data is available to read **13** **14**    char val \= Serial.read(); **15** **16**    if(val \== 'r'){       //if r received **17**      digitalWrite(11, HIGH); //turn on red led **18**      } **19**    if(val \== 'b'){       //if b received **20**      digitalWrite(10, HIGH); //turn on blue led **21**      } **22**    if(val \== 'y'){       //if y received **23**      digitalWrite(12, HIGH); //turn on yellow led **24**      } **25**    if(val \== 'f'){       //if f received **26**      digitalWrite(11, LOW); //turn off all led **27**      digitalWrite(12, LOW); **28**      digitalWrite(10, LOW); **29**      } **30**    } **31**  } 

## [__](https://www.hackster.io/hardikrathod/control-arduino-using-gui-arduino-processing-2c9c6c#team)Credits

[![[f586580cb78f2be0bf198ee949dd0eba.jpg]]](https://www.hackster.io/hardikrathod)

### [Hardik Rathod](https://www.hackster.io/hardikrathod)

1 project • 14 followers
[Contact](https://www.hackster.io/users/sign_up?redirect_to=%2Fmessages%2Fnew%3Frecipient_id%3D34063&source=user_contact)

## [__](https://www.hackster.io/hardikrathod/control-arduino-using-gui-arduino-processing-2c9c6c#comments)Comments

Please [log in](https://www.hackster.io/users/sign_in?id=46905&m=base_article&reason=comment&redirect_to=%2Fhardikrathod%2Fcontrol-arduino-using-gui-arduino-processing-2c9c6c%23comments) or [sign up](https://www.hackster.io/users/sign_up?id=46905&m=base_article&reason=comment&redirect_to=%2Fhardikrathod%2Fcontrol-arduino-using-gui-arduino-processing-2c9c6c%23comments&source=comments) to comment.

