# Module8_Project

Arduino Group 7

Thomas Brants s2920352

Razvan Stefan s2957868

Alex Zambori s3009076

Dirk Weersink s2606720

## Required Libraries

In order for this project to run, we need multiple libraries, which are available to install using the Arduino IDE. Here is the list of required libraries:

-   AES
-   ArduinoBLE
-   Arduino Cryptographic Library (<https://rweather.github.io/arduinolibs/classCurve25519.html>)
-   Arduino_APDS9960
-   CRC16 by Rob Tillart
-   PDM
-   Porcupine_EN
-   Logger by Christopher Baker

## Setting up

To run this project, 2 Arduino Nano 33 BLE are required, one of them will have the role of controller(the arduino folder), and the other one will be the peripheral (receiver folder).

In order for the microphone component to work it is very important to use the exact same Arduino board as we did. This is because the library we have for detecting pass phrases requires a specific Arduino id, which we provided when training the model. The Arduino that should be the controller is "IES-IC-120".

Additionally, we have experienced a weird bug regarding uploading the C++ code to the Arduino. For some reason, the IDE does not do it properly. Our fix for this issue has been hitting the reset button on the Arduino while the IDE is still compiling or uploading while in boot mode (make sure to select the correct com port).

Because of how the Arduino BLE library is implemented, the connection between the two Arduino has a reliability of around 50%. If it seems that the two Arduino are not ever going to connect, resetting both of them at the same time is a good idea.

## Using the sensors

The sensors are required to do the credentials check in this system.

Firstly, the gesture sensor. We recommend holding the Arduino flat and well lighten. The gesture should be performed at a medium to low speed. Also, the gesture sensor is not very reliable, usually reading the wrong gesture. The best way we found was placing the Arduino perpendicular to the table edge. The current correct sequence is a up followed by a down, but it can always be changed from the credentials file.

Secondly, the microphone. For the best chances of the microphone picking the sound up, it is important to speak very close to it and as clear as possible. The current correct pass phrase is "unlock". This can also be changed from the credentials file to another word that the model is trained on, which are "hey computer" and "password".

Additionally, we recommend, that when running the program, to have as little interference as possible to increase the chance of Bluetooth connection.
