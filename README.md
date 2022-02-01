# manual_iot
In this manual I will explain how to control a ledstrip with a laptop and a ESP8266.


# Necessities
Make sure you have the following equipment before you start this manual. 
 
- ESP8266
- Ledstrip
- Laptop or computer
- USB C cable

**#Step 1 : Connecting the cables**
- Connect the +5V wire to the 3V3 pin (in my case the yellow cable)
- Connect the DIN wire to the D5 pin (in my case the green cable)
- Connect the GND wire to the GND pin (in my case the (blue cable)
- Connect the usb c to the ESP8266 and your laptop or computer (in my case laptop)

![IMG_1384](https://user-images.githubusercontent.com/91546248/151878379-815c3b14-fdf0-4929-86eb-076112d23ea0.jpg)
![IMG_1386](https://user-images.githubusercontent.com/91546248/151879057-ae8aa8bb-2fd4-4ffc-9bff-c8d90b9def9e.jpg)
![IMG_1387](https://user-images.githubusercontent.com/91546248/151879118-6c20f13a-0b0c-42e6-8701-7a63b385145e.jpg)
![IMG_1388](https://user-images.githubusercontent.com/91546248/151879155-198b1e7d-6e6b-4057-86a6-0e420cc18b08.jpg)

**#Step 2: installing adafruit**
Arduino has libraries with examples that enable you to get a lot of example code and we will use this to easily connect with our led strip.

If you don't have the arduino program you can download it here: https://www.arduino.cc/en/software

Now open the arduino program and go to Sketch / include library / manage libraries…
Search and install the latest version of "Adafruit Neopixel".


**#Step 3: the code**
when you start up adruino you start with the code:

```
void setup() {
  // put your setup code here, to run once:

}

void loop() {
  // put your main code here, to run repeatedly:

}
```

Delete the code and change the code into the following...


**#Step 4: the code**
```
#include <Adafruit_NeoPixel.h>

#define PIN        5

#define NUMPIXELS 12

Adafruit_NeoPixel pixels(NUMPIXELS, PIN, NEO_GRB + NEO_KHZ800);

#define DELAYVAL 4000
  void setup() {
  pixels.begin();
}

void loop() {
  pixels.clear();
  for(int i=0; i<NUMPIXELS; i++) {

    pixels.setPixelColor(i, pixels.Color(0, 150, 0));

    pixels.show();

    }     delay(DELAYVAL);
    pixels.clear(); 
  for(int i=0; i<NUMPIXELS; i++) {

    pixels.setPixelColor(i, pixels.Color(150, 0, 0));

    pixels.show();  
  } delay(DELAYVAL);
  for(int j=0; j<50; j++){ 
  for(int i=0; i<NUMPIXELS; i++) {
      if(j%2)
        pixels.setPixelColor(i, pixels.Color(100, 100, 100));
      else
        pixels.setPixelColor(i, pixels.Color (0, 0, 0));
      pixels.show();
  }   delay(50);
}
}
```

**#Step 5: upload the code**

The result:
![IMG_1395](https://user-images.githubusercontent.com/91546248/151879448-b6ecd675-0264-4405-8519-ff7c7ca8cc47.jpg)
![IMG_1393](https://user-images.githubusercontent.com/91546248/151879458-b4125f77-303e-45e5-9a18-cd05beb47732.jpg)
![IMG_1394](https://user-images.githubusercontent.com/91546248/151879463-a95777f6-3f6b-43e9-b7b6-fb6f0109defb.jpg)


Help tools:
![WhatsApp Image 2022-01-31 at 19 45 30](https://user-images.githubusercontent.com/91546248/151876525-27376f17-ad6b-411a-a43f-cb0710be102c.jpeg)




#Errors/mistakes
**#This code makes the lights go red green red green red green**

This wil make the lights go red green red green etc.

```
void loop() {
  pixels.clear(); // Set all pixel colors to 'off'
  for(int i=0; i<NUMPIXELS; i++) {
    if (I%2) //als je I zou delen door 2 dan is het 1 rest 1. Als i 3 is is het 1
      pixels.setPixelColor(i, pixels.Color(0, 150, 0));
    else
      pixels.setPixelColor(i, pixels.Color(150, 0, 0));
    pixels.show();
    delay(DELAYVAL);
  }
}
```

**#Here i forgot that the J should be a j**
Make sure you use CAPITAL and non capital letters the right way in your code. Otherwise you will get an error message and you won't be able to upload to code.

<img width="503" alt="Screenshot 2022-01-31 at 20 30 11" src="https://user-images.githubusercontent.com/91546248/151982926-5437a18b-759b-4116-8609-840b0f57cc75.png">

<img width="499" alt="Screenshot 2022-01-31 at 20 30 22" src="https://user-images.githubusercontent.com/91546248/151982714-a8a67a35-e580-46b6-a58b-f8ea94b012c9.png">



**#the code**
```
// NeoPixel Ring simple sketch (c) 2013 Shae Erisson
// Released under the GPLv3 license to match the rest of the
// Adafruit NeoPixel library

#include <Adafruit_NeoPixel.h>
#ifdef __AVR__
 #include <avr/power.h> // Required for 16 MHz Adafruit Trinket
#endif

// Which pin on the Arduino is connected to the NeoPixels?
#define PIN        5 // On Trinket or Gemma, suggest changing this to 1

// How many NeoPixels are attached to the Arduino?
#define NUMPIXELS 12 // Popular NeoPixel ring size

// When setting up the NeoPixel library, we tell it how many pixels,
// and which pin to use to send signals. Note that for older NeoPixel
// strips you might need to change the third parameter -- see the
// strandtest example for more information on possible values.
Adafruit_NeoPixel pixels(NUMPIXELS, PIN, NEO_GRB + NEO_KHZ800);

#define DELAYVAL 4000 // Time (in milliseconds) to pause between pixels

void setup() {
  // These lines are specifically to support the Adafruit Trinket 5V 16 MHz.
  // Any other board, you can remove this part (but no harm leaving it):
#if defined(__AVR_ATtiny85__) && (F_CPU == 16000000)
  clock_prescale_set(clock_div_1);
#endif
  // END of Trinket-specific code.

  pixels.begin(); // INITIALIZE NeoPixel strip object (REQUIRED)
}

void loop() {
  pixels.clear(); // Set all pixel colors to 'off'

  for(int i=0; i<NUMPIXELS; i++) {

    pixels.setPixelColor(i, pixels.Color(0, 150, 0));

    pixels.show();   // Send the updated pixel colors to the hardware.

    }     delay(DELAYVAL);
    pixels.clear(); // Set all pixel colors to 'off

  for(int i=0; i<NUMPIXELS; i++) {

    pixels.setPixelColor(i, pixels.Color(150, 0, 0));

    pixels.show();   // Send the updated pixel colors to the hardware.
    // Pause before next pass through loop
  } delay(DELAYVAL);
}
```
#Sources
- https://docs.google.com/document/d/1l_9xpU-n7Rhxj-L3wI72Kvc3GQ9q6tFl955J2NTYF9k/edit#
- https://www.arduino.cc/reference/en/


