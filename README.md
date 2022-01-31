# manual_iot

# Necessities
ESP8266
Ledstrip
Laptop

#Step 1 : Connecting the cables
- Connect the +5V wire to the 3V3 pin (in my case the yellow cable)
- Connect the DIN wire to the D5 pin (in my case the green cable)
- Connect the GND wire to the GND pin (in my case the (blue cable)

#Step 2: installing adafruit
Arduino has libraries with examples that enable you to get a lot of example code and we will use this to easily connect with our led strip.

If you don't have the arduino program you can download it here: https://www.arduino.cc/en/software

Now open the arduino program and go to Sketch / include library / manage libraries…
Search and install the latest version of "Adafruit Neopixel".

#Step 3: the code
when you start up adruino you start with the code:

void setup() {
  // put your setup code here, to run once:

}

void loop() {
  // put your main code here, to run repeatedly:

}


#Step 4: Finishing it up
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


