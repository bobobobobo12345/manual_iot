# manual_iot

# Necessities
ESP8266
Ledstrip
Laptop

**#Step 1 : Connecting the cables**
- Connect the +5V wire to the 3V3 pin (in my case the yellow cable)
- Connect the DIN wire to the D5 pin (in my case the green cable)
- Connect the GND wire to the GND pin (in my case the (blue cable)

**#Step 2: installing adafruit**
Arduino has libraries with examples that enable you to get a lot of example code and we will use this to easily connect with our led strip.

If you don't have the arduino program you can download it here: https://www.arduino.cc/en/software

Now open the arduino program and go to Sketch / include library / manage libraries…
Search and install the latest version of "Adafruit Neopixel".


**#Step 3: the code**
when you start up adruino you start with the code:

void setup() {
  // put your setup code here, to run once:

}

void loop() {
  // put your main code here, to run repeatedly:

}



**#Step 4: the code**

Rood groen rood groen rood groen rood groen 
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



**#Step 5: the code**

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



**#Step 6: Finishing it up**
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

Help tools:
![WhatsApp Image 2022-01-31 at 19 45 30](https://user-images.githubusercontent.com/91546248/151876525-27376f17-ad6b-411a-a43f-cb0710be102c.jpeg)



#Errors/mistakes


#Sources
- https://docs.google.com/document/d/1l_9xpU-n7Rhxj-L3wI72Kvc3GQ9q6tFl955J2NTYF9k/edit#
- 


