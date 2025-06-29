# Programming a HTTP Server on ESP-8266-12E
#programming/project/esp-8266
*Source URL: [](https://www.instructables.com/id/Programming-a-HTTP-Server-on-ESP-8266-12E/).*
- - - -


Published Oct 15th, 2015

## Introduction: Programming a HTTP Server on ESP-8266-12E
[![[FE89EJOIFR67VAC.jpg]]](https://cdn.instructables.com/FE8/9EJO/IFR67VAC/FE89EJOIFR67VAC.LARGE.jpg)

[![[F27TW9TIFPONC7F.jpg]]](https://www.instructables.com/member/jainrk/)By [jainrk](https://www.instructables.com/member/jainrk/)[More by
the author:](https://www.instructables.com/member/jainrk/)

[![[F4QMO9CJ98RBLPR.jpg]]](https://www.instructables.com/id/DIY-Fold-Letter-Envelopes-From-an-8-X-11-Sheet-of-/)

[![[FTT4454J0COV25W.jpg]]](https://www.instructables.com/id/ESP8266-I2C-PORT-and-Address-Scanner/)

[![[FTG09PPIZ6CPRGX.jpg]]](https://www.instructables.com/id/1-USB-to-UART-serial-Flashing-Device-dongle-With-3/)

In this Instructable, together we will undertake the journey of programming the [ESP8266-12E WIFI Development Board](http://goo.gl/15aaWl) as an HTTP server. Using a web browser we will send instructions to the ESP8266-E12 to change it's behavior. Throughout the process, at each step we will also look under the hood to see what is going on inside. While doing this we will control the on board LED to turn ON and OFF with commands issued via a web browser.

In my previous Instructable [Programming the ESP8266-12E using Arduino software/IDE](http://goo.gl/IZch2B) I have described how to add the ESP8266-E12 board to the Arduino software/IDE and write your first sketch to blink the on board LED. The code is hardwired, hence on power up the ESP-8266-12E does what it is suppose to do - blink the LEDs. One cannot change the behavior of the board without reprogramming it.

In an ideal world of IoT the ESP8266-E12 should communicate with us over WiFi and over the the internet. We should be able to control the ESP-8266-E12 over Wifi using protocols specific to the internet. We should be able to instruct the ESP-8266-12E to do "Things" without having to reprogram.

## Step 1: Opening the "Connect to a Network" Window
[![[FBC20XYIFR67ZEL.jpg]]](https://cdn.instructables.com/FBC/20XY/IFR67ZEL/FBC20XYIFR67ZEL.LARGE.jpg)

[![[FXQF4LUIFR67ZMP.jpg]]](https://cdn.instructables.com/FXQ/F4LU/IFR67ZMP/FXQF4LUIFR67ZMP.LARGE.jpg)

In your Windows environment open the ***Network and Sharing Center***. You get to the *Network and Sharing Center* via the *Control Panel*.

Click on *Connect to a network* to open the_**Connect to a network***window*. Leave it open, w_e will be referring to this window often. You may shut the ***Network and Sharing Center***.

## Step 2: Writing the SimpleWebServer Sketch
[![[FHD7TS4IFR681VD.jpg]]](https://cdn.instructables.com/FHD/7TS4/IFR681VD/FHD7TS4IFR681VD.LARGE.jpg)

Connect your ESP8266-12E to your computer.

Open your Arduino program/IDE and paste the following code:

*#include <ESP8266WiFi.h>*

_**WiFiServer** server(****80****); //Initialize the server on Port 80_

*void setup() {*

*WiFi.mode(**WIFI_AP**); //Our ESP8266-12E is an AccessPoint
WiFi.softAP("**Hello_IoT**", "**12345678**"); // Provide the (SSID, password); .
server.**begin()**; // Start the HTTP Server*

*}*

*void loop() { }*

This boiler plate code will be a part of every ESP8266 sketch we write. This code does the following:

- Includes the ESP8266 library ***ESP8266WiFi.h***.
- Creates the instance "***server***" of the class "***WiFiServer***" listening on port ***80***. Notice "***server***" is a global instance.
- Set the mode of our ESP8266 to be an Access Point (AP).
- Provide the SSID and password. The password / passphrase has to be at least 8 characters long.

- Fire-up our server by calling the ***begin()*** method.

Save as ***SimpleWebServer*** sketch. Compile and upload the sketch *to your* ESP8266-12E.

## Step 3: Checking Our Server
[![[FNLNL4NIFR681EP.jpg]]](https://cdn.instructables.com/FNL/NL4N/IFR681EP/FNLNL4NIFR681EP.LARGE.jpg)

Open the "***Connect to network***" window. You should see our server with SSID "***Hello_IoT***" in the list. Select the **Hello_IoT** network, provide the *password/passphrase* and save it.

**Hurrah our ESP8266-12E is operating as a HTTP server listening on port 80.**

## Step 4: Looking Under the Hood
[![[FNMZOYPIFR6820H.jpg]]](https://cdn.instructables.com/FNM/ZOYP/IFR6820H/FNMZOYPIFR6820H.LARGE.jpg)

Launch the **Serial Monitor***Tools |* *Serial Monitor* or with the shortcut keys *Crtl-Shift-M*.

## Step 5: Get HTTP Server Information From the ESP8266-12E
[![[F3205KCIFR686SW.jpg]]](https://cdn.instructables.com/F32/05KC/IFR686SW/F3205KCIFR686SW.LARGE.jpg)

[![[FZ2WNOIIFR68994.jpg]]](https://cdn.instructables.com/FZ2/WNOI/IFR68994/FZ2WNOIIFR68994.LARGE.jpg)

Add the following piece of code in the end of the setup() function:

***//Looking under the hood**
Serial.begin(115200); //Start communication between the ESP8266-12E and the monitor window
IPAddress* *HTTPS_ServerIP*_= WiFi.softAPIP(); // Obtain the IP of the Server
__Serial.print("Server IP is: "); // Print the IP to the monitor window
_*Serial.println(**HTTPS_ServerIP**);*

Compile and load the sketch and watch the Monitor Window. You should see the default IP address of the ESP8266-12E as *192.168.4*.*1*.

## Step 6: Web Browser Connects/Talks to Server
[![[FDMF0AHIFR6883W.jpg]]](https://cdn.instructables.com/FDM/F0AH/IFR6883W/FDMF0AHIFR6883W.LARGE.jpg)

[![[FUS23JNIFR6898C.jpg]]](https://cdn.instructables.com/FUS/23JN/IFR6898C/FUS23JNIFR6898C.LARGE.jpg)

It is time for a web browser to connect to our HTTP server.

Enter the following code within the loop() function:

*WiFiClient client = server.available();
if (!client) {
return;
}
//Looking under the hood
Serial.println("Somebody has connected :)");*

Compile and load to the ESP8266-E12.

Open a browser window and enter [http://192.168.4.1](http://192.168.4.1/) and and hit enter.

Observe your Monitor window to check for a connection.

## Step 7: Listen to What the Browser Is Sending to the HTTP Server
[![[FR860V9IFR68BIS.jpg]]](https://cdn.instructables.com/FR8/60V9/IFR68BIS/FR860V9IFR68BIS.LARGE.jpg)

[![[F4JPV5LIFR68ACU.jpg]]](https://cdn.instructables.com/F4J/PV5L/IFR68ACU/F4JPV5LIFR68ACU.LARGE.jpg)

The web browser connects to the HTTP server and sends the request. The server receives the request and does something with it. Rather it can do a lot of different things.

Enter the following code in the loop() function.

*//Read what the browser has sent into a String class and print the request to the monitor
String request = client.readString();
//Looking under the hood
Serial.println(request);*

Compile and upload to the ESP8266-E12. Enter the following in the address field of your browser *[http://192.168.4.1/PARAM](http://192.168.4.1/PARAM)*.

The browser sends a GET request to the server. Notice "/PARAM" following the GET request. Off all the text sent we are only interested in the first line of the request. Thus we replace the code
***String request = client.readString();***
with
***String request = client.readStringUntil('\r');***

## Step 8: Turning the LED ON/OFF Through the Web Browser
[![[FJ11G2MIFR46BEN.jpg]]](https://cdn.instructables.com/FJ1/1G2M/IFR46BEN/FJ11G2MIFR46BEN.LARGE.jpg)

[![[FSCZDANIFR46BFI.jpg]]](https://cdn.instructables.com/FSC/ZDAN/IFR46BFI/FSCZDANIFR46BFI.LARGE.jpg)

We are ready to turn the LED on GPIO16 ON/OFF through commands given via the web browser.

Firstly initialize the digital port GPIO16 as an output port and keep the initial state of the LED ON.
At the bottom of *setup()* function add the following lines of code:

*pinMode(LED_PIN, OUTPUT); //GPIO16 is an OUTPUT pin;
digitalWrite(LED_PIN, LOW); //Initial state is ON*

At the bottom of *loop()* function add the following lines of code:

*// Handle the Request*

*if (request.indexOf("/OFF") != -1){
digitalWrite(LED_PIN, HIGH); }
else if (request.indexOf("/ON") != -1){
digitalWrite(LED_PIN, LOW);
}*

In the address bar of your browse type the following URL:
[*http://192.168.4.1/OFF*](http://192.168.4.1/OFF)

The LED on the ESP8266-E12 will turn OFF.

Then type the following URL:
[*http://192.168.4.1/ON*](http://192.168.4.1/ON)

The LED on the ESP8266-E12 will turn ON.

## Step 9: Let Us Get a Little Fancy
[![[FXZLQEJIFSLMKJX.jpg]]](https://cdn.instructables.com/FXZ/LQEJ/IFSLMKJX/FXZLQEJIFSLMKJX.LARGE.jpg)

[![[FC0XR9WIFSLMQ79.jpg]]](https://cdn.instructables.com/FC0/XR9W/IFSLMQ79/FC0XR9WIFSLMQ79.LARGE.jpg)

It is cumbersome to change the URL each time we need to turn the LED ON or OFF. Let us add some HTML code and some buttons.

Copy this code and add it at the bottom of the Loop() function:

**// Prepare the HTML document to respond and add buttons:**

**INSTRUCTABLES MANGLES THE HTML CODE**

***//Serve the HTML document to the browser.***

*client.flush(); //clear previous info in the stream
client.print(s); // Send the response to the client
delay(1);
Serial.println("Client disonnected"); //Looking under the hood*

**Compile and load.**

**HAPPY IoTing!!!**

## Step 10: ​List of Other Instructables I Have Written
[Programming the ESP8266 WeMos-D1R2 using Arduino software/IDE](https://www.instructables.com/id/Programming-the-WeMos-Using-Arduino-SoftwareIDE/)

[Programming a HTTP Server on ESP-8266-12E](https://www.instructables.com/id/Programming-a-HTTP-Server-on-ESP-8266-12E/)

[Programming the ESP8266-12E using Arduino software/IDE](https://www.instructables.com/id/Programming-the-ESP8266-12E-using-Arduino-software/)

[Programming the ESP8266MOD ESP-12 module using the Witty Board and Arduino IDE](https://www.instructables.com/id/Programming-the-ESP8266MOD-ESP-12-Module-Using-the/)

[DIY Dual Cup Suction Lifter Temporary Car Roof Rack](https://www.instructables.com/id/DIY-Dual-Cup-Suction-Lifter-Temporary-Car-Roof-Rac/)

## 8 People Made This Project!

* 
![[F9DN2U3IJWWR96J.jpg]]
### [edmondkreuk](https://www.instructables.com/member/edmondkreuk/) made it!

* 
![[FUWXGKHJ8AGRYPC.jpg]]
### [AlfaS4](https://www.instructables.com/member/AlfaS4/) made it!

* 
![[F4KHKZKIZT6PMPH.jpg]]
### [IzzanD](https://www.instructables.com/member/IzzanD/) made it!

* 
![[F1HWH86IUOHRYPD.jpg]]
### [flyingsparkie](https://www.instructables.com/member/flyingsparkie/) made it!

* 
See 4 more that made it


Did you make this project? Share it with us!

## Recommendations

* 
[![[images/_resources/Programming_a_HTTP_Server_on_ESP-8266-12E.resources/unknown_filename.png]]](https://www.instructables.com/id/All-in-One-Arcade-System/)
### [All in One Arcade System](https://www.instructables.com/id/All-in-One-Arcade-System/)
by [pjnovas](https://www.instructables.com/member/pjnovas/) in [Technology](https://www.instructables.com/technology/)

* 
[![[images/_resources/Programming_a_HTTP_Server_on_ESP-8266-12E.resources/unknown_filename.png]]](https://www.instructables.com/id/IoT-Split-flap-Weather-Forecast-Powered-by-XOD/)
### [IoT Split-flap Weather Forecast Powered by XOD](https://www.instructables.com/id/IoT-Split-flap-Weather-Forecast-Powered-by-XOD/)
by [gabbapeople](https://www.instructables.com/member/gabbapeople%20/) in [Arduino](https://www.instructables.com/technology/arduino/)

* 
[![[images/_resources/Programming_a_HTTP_Server_on_ESP-8266-12E.resources/unknown_filename.png]]](https://www.instructables.com/id/ACRYLIC-RAINBOW-LAMP-WITH-ENGRAVED-BUTTERFLIES-AND/)
### [DIY ACRYLIC INDIGO BUTTERFLY LAMP.](https://www.instructables.com/id/ACRYLIC-RAINBOW-LAMP-WITH-ENGRAVED-BUTTERFLIES-AND/)
by [Maggie Shah](https://www.instructables.com/member/Maggie%20Shah/) in [Arduino](https://www.instructables.com/technology/arduino/)

* 
[![[images/_resources/Programming_a_HTTP_Server_on_ESP-8266-12E.resources/unknown_filename.png]]](https://www.instructables.com/class/Arduino-Class/)
![[images/_resources/Programming_a_HTTP_Server_on_ESP-8266-12E.resources/unknown_filename.3.png]]
### [Arduino Class](https://www.instructables.com/id/Arduino-Class/)
71,851 Enrolled


* ### Creative Misuse Contest
[![[images/_resources/Programming_a_HTTP_Server_on_ESP-8266-12E.resources/unknown_filename.2.png]]](https://www.instructables.com/contest/misuse/)

* ### Tiny Home Contest
[![[images/_resources/Programming_a_HTTP_Server_on_ESP-8266-12E.resources/unknown_filename.2.png]]](https://www.instructables.com/contest/tinyhomes/)

* ### Fix It! Contest
[![[images/_resources/Programming_a_HTTP_Server_on_ESP-8266-12E.resources/unknown_filename.2.png]]](https://www.instructables.com/contest/fixit/)


![[user.gif]]

We have a **be nice** policy.
Please be positive and constructive.

## 97 Discussions
[![[F8MEU11ID4CRG5O.jpg]]](https://www.instructables.com/member/iamashwin99/)
[iamashwin99](https://www.instructables.com/member/iamashwin99/)

Tip 6 weeks ago

[**](https://www.instructables.com/id/Programming-a-HTTP-Server-on-ESP-8266-12E/#)

Great tutorial!

I used

int LED_PIN = LED_BUILTIN;

at the very beginning and at the very end of loop() i added:

// Prepare the HTML document to respond and add buttons:

String s = "HTTP/1.1 200 OK\r\n";

s += "Content-Type: text/html\r\n\r\n";

s += "\r\n\r\n";

s += "<input type=\"button\" name=\"b1\" value=\"Turn LED ON\" onclick=\"location.href='/ON'\">";

s += "";

s += "<input type=\"button\" name=\"bi\" value=\"Turn LED OFF\" onclick=\"location.href='/OFF'\">";

s += "\n";

[//Serve](https://serve/) the HTML document to the browser.

client.flush ();

[//clear](https://clear/) previous info in the stream

client.print (s); // Send the response to the client

delay(1);

Serial.println("Client disonnected" );

[//Looking](https://looking/) under the hood)

[![[FN80W7VJFUABR4S.jpg]]](https://www.instructables.com/member/stipser1./)
[stipser1.](https://www.instructables.com/member/stipser1./)

Question 5 months ago

[**](https://www.instructables.com/id/Programming-a-HTTP-Server-on-ESP-8266-12E/#)

It seems like server.available never returns anything.
I never get past the if(!client) condition

[![[FGFYHILIDZSEVXL.jpg]]](https://www.instructables.com/member/TommasoM1/)
[TommasoM1](https://www.instructables.com/member/TommasoM1/)

Question 6 months ago

[**](https://www.instructables.com/id/Programming-a-HTTP-Server-on-ESP-8266-12E/#)

please have you any information about server.on class? i use it in my project because is very useful but i am not able to understand if there is the possibility to exchange parameters from the cliet to the server . I was not able to find any doc out of the standard arduino server doc where server.on is not listed at all.

[![[images/_resources/Programming_a_HTTP_Server_on_ESP-8266-12E.resources/unknown_filename.1.png]]](https://www.instructables.com/member/llancaster3/)
[llancaster3](https://www.instructables.com/member/llancaster3/)

7 months ago

[**](https://www.instructables.com/id/Programming-a-HTTP-Server-on-ESP-8266-12E/#)

I have the same issue as PeterJ155.

It failed when I added the line

WiFiClient client = server.available();

error : 'class ESP8266WebServer' has no member named 'available'

What other changes did you make to get it to work ????

[![[images/_resources/Programming_a_HTTP_Server_on_ESP-8266-12E.resources/unknown_filename.1.png]]](https://www.instructables.com/member/mazzoESP8266/)
[mazzoESP8266](https://www.instructables.com/member/mazzoESP8266/)

7 months ago

[**](https://www.instructables.com/id/Programming-a-HTTP-Server-on-ESP-8266-12E/#)

Everything worked except that in my case I had to add the following line before the void setup()

LED_PIN D4.

Thanks.

[![[images/_resources/Programming_a_HTTP_Server_on_ESP-8266-12E.resources/unknown_filename.1.png]]](https://www.instructables.com/member/VivekA36/)
[VivekA36](https://www.instructables.com/member/VivekA36/)

10 months ago

[**](https://www.instructables.com/id/Programming-a-HTTP-Server-on-ESP-8266-12E/#)

Thanks a lot. Very useful introductory tutorial.

[![[FI6DTEKJ8QGF0LC.jpg]]](https://www.instructables.com/member/ColinMarsh/)
[ColinMarsh](https://www.instructables.com/member/ColinMarsh/)

a year ago

[**](https://www.instructables.com/id/Programming-a-HTTP-Server-on-ESP-8266-12E/#)

Hi. I love the sketch and any other of your works that I have seen, well
done. This is exactly what I was looking for to set up a VPN using a
couple of Wemos D1's. Everything compiles/uploads until I get the IDE
error message that 'LED_PIN' was not declared in this scope. I have
followed the tute several times and get the same error. I am a bube,
looking to learn, but it looks like it was previously declared in the
setup loop. Thanks again, great work.

[![[images/_resources/Programming_a_HTTP_Server_on_ESP-8266-12E.resources/unknown_filename.1.png]]](https://www.instructables.com/member/hon20002000/)
[hon20002000](https://www.instructables.com/member/hon20002000/)

a year ago

[**](https://www.instructables.com/id/Programming-a-HTTP-Server-on-ESP-8266-12E/#)

thank for a great but i get some problem.

the function is okay but no words show on the button.

[![[images/_resources/Programming_a_HTTP_Server_on_ESP-8266-12E.resources/unknown_filename.1.png]]](https://www.instructables.com/member/GustavG3/)
[GustavG3](https://www.instructables.com/member/GustavG3/)

a year ago

[**](https://www.instructables.com/id/Programming-a-HTTP-Server-on-ESP-8266-12E/#)

Thanks for a great and well written tutorial!

[![[images/_resources/Programming_a_HTTP_Server_on_ESP-8266-12E.resources/unknown_filename.1.png]]](https://www.instructables.com/member/Dee741/)
[Dee741](https://www.instructables.com/member/Dee741/)

a year ago

[**](https://www.instructables.com/id/Programming-a-HTTP-Server-on-ESP-8266-12E/#)

Hi,

Great tutorial!! I have the ESP8266-12E onboard LED switching ON/OFF using the URL ON/OFF method.....BUT.... the HTML buttons don't work at all on the webpage from my phone. The code is exactly as you have written it. An ideas as to what I am doing wrong??

Thanks

Darren

[![[images/_resources/Programming_a_HTTP_Server_on_ESP-8266-12E.resources/unknown_filename.1.png]]](https://www.instructables.com/member/PetitBiscuit/)
[PetitBiscuit](https://www.instructables.com/member/PetitBiscuit/)

a year ago

[**](https://www.instructables.com/id/Programming-a-HTTP-Server-on-ESP-8266-12E/#)

Hey ! I'm new and I would like to know if it's possible to turn my nodemcu esp8266-12e as an acces point to internet ? Or juste to grap internet with it. My computer didn't have a wifi chip, i need an ethernet cable and I want to use the wifi chip of my nodemcu to get acces to internet with the wifi of my router on my computer. Possible ?

[![[F015TKFIL2624R2.jpg]]](https://www.instructables.com/member/ItsGraGra/)
[ItsGraGra](https://www.instructables.com/member/ItsGraGra/)

a year ago

[**](https://www.instructables.com/id/Programming-a-HTTP-Server-on-ESP-8266-12E/#)

Great tutorial, thanks.

I just had to change the LED pin numbers, int LED_PIN = 15; and swap HIGH for LOW and vice-versa.

Worked first time as AP, all I need now is learn how to connect it to my router instead and get out on the internet.

[![[images/_resources/Programming_a_HTTP_Server_on_ESP-8266-12E.resources/unknown_filename.1.png]]](https://www.instructables.com/member/Babar%20Latif/)
[Babar Latif](https://www.instructables.com/member/Babar%20Latif/)

a year ago

[**](https://www.instructables.com/id/Programming-a-HTTP-Server-on-ESP-8266-12E/#)

Hi,

Do you have a tutorial for making ESP8266 connect to the network without adding SSID and Password to the program ??

.

I want to learn to code that can allow giving new SSID and Password without re-programming.

[![[F6MLPVOIT22SGZ9.jpg]]](https://www.instructables.com/member/AjinkyaW1/)
[AjinkyaW1](https://www.instructables.com/member/AjinkyaW1/)

2 years ago

[**](https://www.instructables.com/id/Programming-a-HTTP-Server-on-ESP-8266-12E/#)

hellow .

i tried the instructions and program you have given. my practical was successful ,

but the thing where i am getting the problem is ,

when i power off the esp8266 device and when the power comes back , it doesnt start the program i have uploaded , i need to reprogram it to make it work again.

my pin connections are :

ESP8266-12E : TTL

while programming the esp8266 via ttl.

gnd - gnd

vcc - vcc (3.3v)

en - (3.3v)

rx - tx

tx -rx

GPIO 0 - GND

GPIO 15 - GND

AFTER PROGRAMMING I REMOVE GPIO 0 AND GPIO 15 FROM the ground.

the program i have uploaded only works once when the upload is complete but not after the power goes and comes again.

please help i have read a lot of things on internet. and have failed solving the issue.

thanks in advance

[![[images/_resources/Programming_a_HTTP_Server_on_ESP-8266-12E.resources/unknown_filename.1.png]]](https://www.instructables.com/member/TrucV/)
[TrucV](https://www.instructables.com/member/TrucV/)

a year ago

[**](https://www.instructables.com/id/Programming-a-HTTP-Server-on-ESP-8266-12E/#)

this is so helpfu, bro !!
thank you so much !!!

[![[FIB4GL1IVA4Z3OS.jpg]]](https://www.instructables.com/member/JonnyF4/)
[JonnyF4](https://www.instructables.com/member/JonnyF4/)

2 years ago

[**](https://www.instructables.com/id/Programming-a-HTTP-Server-on-ESP-8266-12E/#)

I have other scripting exp but an absolute Noob here. All went well till i tried connect to device with Chrome via [http://192.168.4.1/](http://192.168.4.1/) and got no response via Serial Monitor. Got "Server IP is: 192.168.4.1" tried to connect and nothing ? Nor did the next step work with [http://192.168.4.1/PARAM...](http://192.168.4.1/PARAM...)

Please help...

[![[FI6DTEKJ8QGF0LC.jpg]]](https://www.instructables.com/member/ColinMarsh/)
[ColinMarsh](https://www.instructables.com/member/ColinMarsh/)

a year ago

[**](https://www.instructables.com/id/Programming-a-HTTP-Server-on-ESP-8266-12E/#)

HI. All good now, thanks heaps

[![[F27TW9TIFPONC7F.1.jpg]]](https://www.instructables.com/member/jainrk/)
[jainrk (author)](https://www.instructables.com/member/jainrk/)

a year ago

[**](https://www.instructables.com/id/Programming-a-HTTP-Server-on-ESP-8266-12E/#)

I will duplicate it on my board and let you know.

[![[F4JNLXTIYB2HF9Q.jpg]]](https://www.instructables.com/member/PierreV16/)
[PierreV16](https://www.instructables.com/member/PierreV16/)

a year ago

[**](https://www.instructables.com/id/Programming-a-HTTP-Server-on-ESP-8266-12E/#)

Am a novice, Fleming from Belgium, 72 years young.

Am the ESP5266-12th started under the Boardname: "WeMos-D1R2 & mini" At step 5, here I get 1 line, the Server IP.

Step 6. Data at the void Loop (). Just get the Server Ip, not more.

Did not work with this Board, so chosen other Board "NodeMCU 1.0 (ESP-12th Module)" here I could places the data on the Board , but get back only Server IP.

Have tried to access Hello_IoT by the password of the Wifi connection, but don't get any connection.

Then tried the code from the Board, "VID and PID" behind each other as "1A867523" that do not work.

Can of course be that linking too early.

Can someone help me there. Mail may also, "p.vanovermeire@gmail.com" Skype name "lappierre"

[![[FYXLVEJIZ6D2JAW.jpg]]](https://www.instructables.com/member/TheerapongSanthaveesuk/)
[TheerapongSanthaveesuk](https://www.instructables.com/member/TheerapongSanthaveesuk/)

a year ago

[**](https://www.instructables.com/id/Programming-a-HTTP-Server-on-ESP-8266-12E/#)

Very nice tutorial.

[![[images/_resources/Programming_a_HTTP_Server_on_ESP-8266-12E.resources/unknown_filename.1.png]]](https://www.instructables.com/member/Damiend43/)
[Damiend43](https://www.instructables.com/member/Damiend43/)

2 years ago

[**](https://www.instructables.com/id/Programming-a-HTTP-Server-on-ESP-8266-12E/#)

When listening on the com port I get very strange/obscurs reading like "len 138L€" or "00, leuÿôºÿLæ".

[![[F39ER99I1FQ0790.jpg]]](https://www.instructables.com/member/JohnN3/)
[JohnN3](https://www.instructables.com/member/JohnN3/)

2 years ago

[**](https://www.instructables.com/id/Programming-a-HTTP-Server-on-ESP-8266-12E/#)

Didn't work for me so far. I got to step 8 and didn't see where the gpio pin "LED_PIN" was declared. Since I'm using a ESP12E I changed to gpio-4 by adding a declaration prior to setup of "int LED_PIN = 4;". Then added the next part to handle the request. Uploaded that and nothing happened. The serial monitor shows "Somebody has connected" and "Get /off HTTP/1.1" or "Get /on HTTP/1.1" depending on what I put in the address. The browser ( Chrome, on my smart phone) indicated "... the page was not working 192.168.4.1 didn't send any data...ERROR_EMPTY_RESPONSE". The gpio never changed states either. I've built servers using Nodemcu/lua in the past modeling from other examples. I wanted to move to the arduino IDE due to the slow development of the Nodemcu IDE platform. I must admit I'm just learning the intrices of Arduino IDE. It seemed easier using Nodemcu at least for me.

[![[FB669M6IKFS133V.jpg]]](https://www.instructables.com/member/rwittoz/)
[rwittoz](https://www.instructables.com/member/rwittoz/)

2 years ago

[**](https://www.instructables.com/id/Programming-a-HTTP-Server-on-ESP-8266-12E/#)

Hello , how to switch off AP module ? Thank

[![[images/_resources/Programming_a_HTTP_Server_on_ESP-8266-12E.resources/unknown_filename.1.png]]](https://www.instructables.com/member/pbaker-1/)
[pbaker-1](https://www.instructables.com/member/pbaker-1/)

2 years ago

[**](https://www.instructables.com/id/Programming-a-HTTP-Server-on-ESP-8266-12E/#)

oh, wow, BRILLIANT. Worked first time!

[![[FOLD9SIIZ6COZWA.jpg]]](https://www.instructables.com/member/flyingsparkie/)
[flyingsparkie](https://www.instructables.com/member/flyingsparkie/)

2 years ago

[**](https://www.instructables.com/id/Programming-a-HTTP-Server-on-ESP-8266-12E/#)

brill one again! Went straight through ok. Only had to change board to wemos and not the nodemcu. Oh and for mine LED_BUILTIN used instead of LED_PIN. Created another line to make the led blink too..

else if (request.indexOf("/BLINK") !=-1){
for(int t=0;t<10;++t){
digitalWrite(LED_BUILTIN, LOW);
delay(1000);
digitalWrite(LED_BUILTIN, HIGH);
delay(500);
}

and the little buttons on the page are really cool for a start. I didn't know you could do that within the arduino sketch!

Thanks agin :-D

[![[images/_resources/Programming_a_HTTP_Server_on_ESP-8266-12E.resources/unknown_filename.1.png]]](https://www.instructables.com/member/Amatthew1/)
[Amatthew1](https://www.instructables.com/member/Amatthew1/)

2 years ago

[**](https://www.instructables.com/id/Programming-a-HTTP-Server-on-ESP-8266-12E/#)

Nice intro. Where should I look to go further?

Programming a HTTP Server on ESP-8266-12E by [jainrk](https://www.instructables.com/member/jainrk/)
