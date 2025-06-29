---
_Source URL: [](http://www.openhomeautomation.net/wireless-co2-sensor-arduino/)._

tags: 
- '#co2 #tutorial #project'

---

# Build a Wireless CO2 Sensor with Arduino - Open Home Automation


# Build a Wireless CO2 Sensor with Arduino

Indoor Air Quality (IAQ) monitoring is growing trend in the home automation space. And one way to measure air quality is to measure the carbon dioxide (CO2) that is present in your home. Indeed, high levels of CO2 in your home can lead to getting drowsy, having headaches, and functioning at lower activity levels. There are not that many sensors out there that you can buy and easily interface with open-source platforms like Arduino. Luckily, the people at [CO2Meter.com](http://www.co2meter.com/) offered to send us a K30 CO2 sensor to independently test their Arduino code. In this article, I will show you how to use this sensor with Arduino and how to interface it with the CC3000 WiFi chip to build a wireless CO2 sensor. Let’s dive in!

### Hardware requirements

The whole project is based on the Arduino platform, so of course you will need an Arduino board. I really recommend using the [Arduino Uno](http://buy.geni.us/Proxy.ashx?TSID=5094&GR_URL=http%3A%2F%2Fwww.amazon.com%2Fgp%2Fproduct%2FB00F6JCV20%2Fref%3Das_li_qf_sp_asin_il_tl%3Fie%3DUTF8%26camp%3D1789%26creative%3D9325%26creativeASIN%3DB00F6JCV20%26linkCode%3Das2%26tag%3Dopenhomeautomation-20) board for this project, as it is the only board that is currently compatible with the CC3000 library at the time this article was written.

You will also need the K30 sensor to measure the CO2 levels in your home, which can be found directly on the [CO2Meter.com](http://www.co2meter.com/products/k-30-co2-sensor-module) website.

Then, you need the CC3000 chip. I recommend is using the [Adafruit CC3000 breakout board](http://buy.geni.us/Proxy.ashx?TSID=5094&GR_URL=http%3A%2F%2Fwww.amazon.com%2Fgp%2Fproduct%2FB00H232MUE%2Fref%3Das_li_qf_sp_asin_il_tl%3Fie%3DUTF8%26camp%3D1789%26creative%3D9325%26creativeASIN%3DB00H232MUE%26linkCode%3Das2%26tag%3Dopenhomeautomation-20), which is the only one I tested that worked without problem. It is nice and compact, has voltage regulators onboard, as well as an onboard antenna.

Finally, you need a [breadboard and some jumper wires](http://buy.geni.us/Proxy.ashx?TSID=5094&GR_URL=http%3A%2F%2Fwww.amazon.com%2Fgp%2Fproduct%2FB004RXKWDQ%2Fref%3Das_li_qf_sp_asin_il_tl%3Fie%3DUTF8%26camp%3D1789%26creative%3D9325%26creativeASIN%3DB004RXKWDQ%26linkCode%3Das2%26tag%3Dnevjusfin-20) to make the connections between the different parts.

### Software requirements

For this project, you need the usual [Arduino IDE](http://arduino.cc/en/main/software). You will also need the [Adafruit’s CC3000 library](https://github.com/adafruit/Adafruit_CC3000_Library), as well as the library for the K30 sensor. [Download the K30 CO2 sensor library (zip) here](http://www.co2meters.com/Documentation/AppNotes/AN126-K3x-sensor-arduino-uart.zip). To install a library, just download the folders, and put them into your /Arduino/libraries/ folder.

You will also need a web server running on your computer. There are thousands of tutorial for that, but I recommend using [MAMP](http://www.mamp.info/en/index.html) if you are on OS X.

The complete code for this project can be found on [our GitHub repository](https://github.com/openhomeautomation/arduino-k30-wifi).

### Hardware configuration

The hardware configuration for this project is actually not that complicated, thanks to the good information that you will find about the CC3000 breakout board. Connect the IRQ pin of the CC3000 board to pin number 3 of the Arduino board, VBAT to pin 5, and CS to pin 10. Then, you need to connect the SPI pins to the Arduino board: MOSI, MISO, and CLK go to pins 11,12, and 13, respectively. Finally, take care of the power supply: Vin goes to the Arduino 5V, and GND to GND.

The K30 sensor is qui easy to connect: you need to connect two power pins (5V and GND) and two pins for the serial connection. The following picture summarises the hardware connections for the K30 sensor:

<https://www.openhomeautomation.net/wp-content/uploads/2013/11/IMG_7738_edit1.jpg>

[![[unknown_filename.1.jpeg]]](https://www.openhomeautomation.net/wp-content/uploads/2013/11/IMG_7738_edit1.jpg)

### Testing the K30 sensor

We will now test the K30 sensor individually, just to be sure that your hardware connections are correct and that the sensor is functioning correctly. The kSeries library that you installed at the beginning of this tutorial handles most of the hard work to interface with the sensor. You first have to include the library:

#include "kSeries.h"

1.  #include "kSeries.h"

#include "kSeries.h"

You then need to create an instance of the sensor. It uses the software serial library internally, so you also need to specify which pins you used for the serial connection:

kSeries K\_30(6,7);

1.  kSeries

kSeries K\_30(6,7);

Then, reading the CO2 value from the sensor is actually easy:

double co2 = K\_30.getCO2('p');

1.  double co2 = K\_30.getCO2

double co2 = K\_30.getCO2('p');

The rest of the sketch simply consists in printing out the value to the serial monitor. This is the complete sketch to test the K30 sensor:

#include "kSeries.h"

// Create K30 instance on pin 6 & 7
kSeries K\_30(6,7);

void setup()
{
  Serial.begin(9600);
}

void loop()
{
  // Get CO2 value from sensor
  double co2 = K\_30.getCO2('p');

  // Print the value on Serial
  Serial.print("Co2 ppm = ");
  Serial.println(co2);

  // Wait 2 seconds
  delay(2000);
}

1.  #include "kSeries.h"
2.  // Create K30 instance on pin 6 & 7
3.  kSeries
4.  setup
5.  Serial.begin
6.  // Get CO2 value from sensor
7.  double co2 = K\_30.getCO2
8.  // Print the value on Serial
9.  Serial.print"Co2 ppm = "
10.  Serial.println
11.  // Wait 2 seconds
12.  delay

#include "kSeries.h"

// Create K30 instance on pin 6 & 7
kSeries K\_30(6,7);

void setup()
{
  Serial.begin(9600);
}

void loop()
{
  // Get CO2 value from sensor
  double co2 = K\_30.getCO2('p');

  // Print the value on Serial
  Serial.print("Co2 ppm = ");
  Serial.println(co2);

  // Wait 2 seconds
  delay(2000);
}

You can then upload the sketch to your Arduino board, and open the serial monitor. You should see the CO2 reading being printed every 2 seconds. The value should be between 500 ppm and 700 ppm if you are indoors.

### Putting it all together

We can now dive into the core of this article, and connect the K30 wirelessly to a remote server. This is quite similar to what you can see in our article about the [WiFi-connected weather station](http://www.openhomeautomation.net/?p=790).

First, the Arduino sketch. Of course, you need to import the right libraries:

#include <Adafruit\_CC3000.h>
#include <ccspi.h>
#include <SPI.h>
#include <string.h>
#include "utility/debug.h"
#include "kSeries.h"
#include<stdlib.h>

1.  #include <Adafruit\_CC3000.h>
2.  #include <ccspi.h>
3.  #include <SPI.h>
4.  #include <string.h>
5.  #include "utility/debug.h"
6.  #include "kSeries.h"
7.  #include<stdlib.h>

#include <Adafruit\_CC3000.h>
#include <ccspi.h>
#include <SPI.h>
#include <string.h>
#include "utility/debug.h"
#include "kSeries.h"
#include<stdlib.h>

Then, you need to define inside the code what is specific to your configuration: WiFi name & password, IP address of your computer, port of your server (usually 80), and the repository you put your server code in:

#define WLAN\_SSID "yourNetwork"
#define WLAN\_PASS "yourPassword"

uint32\_t ip = cc3000.IP2U32(192,168,0,1);
int port = 80;
String repository = "/arduino-k30-wifi/";

1.  #define WLAN\_SSID "yourNetwork"
2.  #define WLAN\_PASS "yourPassword"
3.  uint32\_t ip = cc3000.IP2U32
4.  port =
5.  String repository = "/arduino-k30-wifi/"

#define WLAN\_SSID "yourNetwork"
#define WLAN\_PASS "yourPassword"

uint32\_t ip = cc3000.IP2U32(192,168,0,1);
int port = 80;
String repository = "/arduino-k30-wifi/";

We can then create the CC3000 instance:

Adafruit\_CC3000 cc3000 = Adafruit\_CC3000(ADAFRUIT\_CC3000\_CS, ADAFRUIT\_CC3000\_IRQ, ADAFRUIT\_CC3000\_VBAT,
SPI\_CLOCK\_DIV2);

1.  Adafruit\_CC3000 cc3000 = Adafruit\_CC3000ADAFRUIT\_CC3000\_CS, ADAFRUIT\_CC3000\_IRQ, ADAFRUIT\_CC3000\_VBAT,
2.  SPI\_CLOCK\_DIV2

Adafruit\_CC3000 cc3000 = Adafruit\_CC3000(ADAFRUIT\_CC3000\_CS, ADAFRUIT\_CC3000\_IRQ, ADAFRUIT\_CC3000\_VBAT,
SPI\_CLOCK\_DIV2);

And let’s not forget to create the instance for the K30 sensor:

kSeries K\_30(6,7);

1.  kSeries

kSeries K\_30(6,7);

In the setup() part of the sketch, we need to connect the CC3000 to the network:

cc3000.connectToAP(WLAN\_SSID, WLAN\_PASS, WLAN\_SECURITY);

1.  cc3000.connectToAPWLAN\_SSID, WLAN\_PASS, WLAN\_SECURITY

cc3000.connectToAP(WLAN\_SSID, WLAN\_PASS, WLAN\_SECURITY);

In the loop() part, we need to get data from the sensor, and to send it to the server by doing a GET request. The first part is really simple:

double co2 = K\_30.getCO2('p');

1.  double co2 = K\_30.getCO2

double co2 = K\_30.getCO2('p');

And transform this into a string:

String co2\_ppm = String((int) co2);

1.  String co2\_ppm = String

String co2\_ppm = String((int) co2);

Establishing the connection to the remote server can be tricky. That’s why the sketch is including a function called send\_request to handle that part. This is the code to send the request:

String request = "GET "+ repository + "sensor.php?data=" + co2\_ppm + " HTTP/1.0";
send\_request(request);

1.  String request = "GET "+ repository + "sensor.php?data=" + co2\_ppm + " HTTP/1.0"
2.  send\_requestrequest

String request = "GET "+ repository + "sensor.php?data=" + co2\_ppm + " HTTP/1.0";
send\_request(request);

We can see that this code is calling a file named sensor.php on the server side. The server.php file will basically get the variable containing the data, and save it into a file:

<?php

  // Store data
  if ($\_GET\["data"\]) {

    $myFile = "data.txt";
    $fh = fopen($myFile, 'w');
    fwrite($fh, $\_GET\["data"\]);
    fclose($fh);

  }

?>

1.  <?php
2.  // Store data
3.  $\_GET"data"
4.  $myFile"data.txt"
5.  fopen$myFile
6.  fwrite$\_GET"data"
7.  fclose
8.  ?>

<?php

  // Store data
  if ($\_GET\["data"\]) {

    $myFile = "data.txt";
    $fh = fopen($myFile, 'w');
    fwrite($fh, $\_GET\["data"\]);
    fclose($fh);

  }

?>

Then, another file called data\_display.php reads the content of the files and displays it:

<?php

  $myFile = "data.txt";
  $fh = fopen($myFile, 'r');
  $line = fgets($fh);
  fclose($fh);

  echo $line;

?>

1.  <?php
2.  $myFile = "data.txt"
3.  fopen$myFile,
4.  $line = fgets
5.  fclose
6.  echo $line;
7.  ?>

<?php

  $myFile = "data.txt";
  $fh = fopen($myFile, 'r');
  $line = fgets($fh);
  fclose($fh);

  echo $line;

?>

Finally, the file sensor.html is in charge of displaying the data in the browser. The data is automatically updated with this JavaScript code:

<script type="text/javascript">

setInterval(function()
{
  $("#dataDisplay").load('data\_display.php');
}, 1000);

</script>

1.  <script type="text/javascript">
2.  setIntervalfunction
3.  "#dataDisplay"'data\_display.php'
4.  </script>

<script type="text/javascript">

setInterval(function()
{
  $("#dataDisplay").load('data\_display.php');
}, 1000);

</script>

As usual, all the files are available on [our GitHub repository](https://github.com/openhomeautomation/arduino-k30-wifi). You can now put all the server files into your server repository, and upload the Arduino sketch to your board. If you open the serial monitor, this is what you should see (don’t forget to start your web server !):

<https://www.openhomeautomation.net/wp-content/uploads/2013/11/sketch+monitor.png>

[![[images/_resources/Build_a_Wireless_CO2_Sensor_with_Arduino_-_Open_Home_Automation.resources/unknown_filename.png]]](https://www.openhomeautomation.net/wp-content/uploads/2013/11/sketch+monitor.png)

This is the final result when you access the server from your computer:

<https://www.openhomeautomation.net/wp-content/uploads/2013/11/server.png>

[![[images/_resources/Build_a_Wireless_CO2_Sensor_with_Arduino_-_Open_Home_Automation.resources/unknown_filename.2.png]]](https://www.openhomeautomation.net/wp-content/uploads/2013/11/server.png)

Of course, this interface can be accessed in the browser of any device connected to your local WiFi network, like your phone or your tablet.

As always, please comment below if you have any question, a suggestion on how to improve the article, or if you find some nasty bugs in the code! If you liked this article, please share it around! Finally, this is the list of the parts that were used in this project:

You can also find most of the required parts for this tutorial in our [Arduino WiFi kit](http://openhomeautomation.net/product/arduino-wifi-kit/).

