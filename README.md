# Custom-Light-Automation

I used the Adafruit Feather HUZZAH ESP8266 (MCU) board. This board specifically because it is 3.3V logic so I can talk to the Pi, which is also 3.3V. 
I programmed this MCU to control a strip of Neopixels (individually addressable RGB LEDs in a string) and accept custom commands (set color, affect, etc.) over SoftSerial. SoftSerial allows you to use nearly any GPIO as a TX and RX connection (the 2 basic pins needed for serial communication). 
The reason I used SoftSerial instead of the hardware one was, so I could debug and flash the MCU over USB to my computer while the MCU communicates over SoftSerial to the Pi.
To program the Pi's GPIO and to communicate with my Google Home I used an IDE called Particle. I installed Particle on my Pi and now I can program the GPIO from the particle build website (build.particle.io/build). Now I can program the Pi's hardware serial to send my color/ affect commands. 
Particle can also react to triggers from IFTTT. In the Particle code I "subscribe" to events in my code. When an event is published, a function in my code will be called. 
I created an account on IFTTT and created my own applet. This applet's "IF" is a Google assistant command, it's "THAT" is Particle. Whenever I say, "Hey Google Set String $" it will post an event called "Static_String" which will in turn call the particle function "setStatic". The "$" is whatever word(s) I say after the initial "Hey Google Set String", in this case it’s a color or an affect (Ex. "Hey Google Set String Red").
