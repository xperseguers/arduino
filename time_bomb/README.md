# Time Bomb

This project uses a 1.3 inch SH1106 SPI OLED display to simulate a time bomb.

The initial state will show a warning that you never should press the little switch:

![Initial state][preview1]

If you press the switch anyway, the green light (see schematics below) will start
blinking, before going off and showing the red light instead. At that point a countdown
timer is displayed, starting at 20 seconds:

![Countdown timer][preview2]

If you just wait, it finally explodes:

![Bang!][preview3]

The two orange/blue wires are used to try to defuse the time bomb. Removing ("cutting")
the blue will stop the countdown timer while the orange will speed up the timer.

## Required Components

The following components are required to build this project:

1. An Arduino UNO board
2. 1.3" (128x64) OLED display
3. 1 push switch
4. LEDs (green/red)
3. 10㏀ resistors for the switch and the blue/orange wires
4. 220Ω resistors for the LEDs
5. A breadboard
6. Jumper wires

The SPI OLED SH1106 display may be bought from https://www.chipandlove.ch/ (ref `OLEDWHITE13`).

## Schematics

Connect the components as shown in the schematics below:

![Schematics][schematics]

### OLED - Arduino

The pin to pin description of the connection between the Arduino and the OLED display is
illustrated below.

```
GND - GND
VDD - 5V
SCK - D10  (SCK may be referenced as D0 or CLK)
SDA - D9   (SDA may be referenced as D1 or MOSI)
RES - D12
DC  - D11
CS  - D13
```

Go over the connections once again to ensure everything is as it should be.

## Code

With the schematics complete we can now write the code for the project. Please see
[complete source code](TimeBomb.ino).

## Tools

Since this is my first documented Arduino project, here are some useful resources.

### Fritzing

The Fritzing application lets you create beautiful breadboard just like for this project.

Link: https://fritzing.org/download/

- Hint 1: You may use an official release from the corresponding GitHub project if you want
  to try before making the suggested small donation).
- Hint 2: Be sure to check [this video](https://www.youtube.com/watch?v=X4tTF6WQHZk&fbclid=IwAR0S4Fhb5g93k9-ZtyVsuLfrtjdGo2LeXwhxxmZ6jhs-Uq6hJDegnFAlypA)
  to create bended wires.
- Hint 3: I found the OLED display part for Fritzing [here](https://github.com/adafruit/Fritzing-Library/blob/master/parts/Adafruit%20OLED%20Monochrome%20128x64%201.3%20inch.fzpz).

### Img2Code

The Adafruit GFX library makes it easy to draw an image as a byte array to the OLED
display. In order to quickly convert any image to a byte array, you may use the Java
tool Img2Code available in the [Adafruit GFX library repository](https://github.com/ehubin/Adafruit-GFX-Library.git).

Running macOS Catalina (10.15), the default Java version I had is 11, which is not compatible
with the tool. You may use `brew` to install a compatible version of Java to create the
executable:

```
brew tap adoptopenjdk/openjdk
brew cask install adoptopenjdk10
/usr/libexec/java_home -V
export JAVA_HOME=`/usr/libexec/java_home -v10`
./gradlew
```

To run the Img2Code tool:

```
export JAVA_HOME=`/usr/libexec/java_home -v10`
./gradlew run
```

### Font Converter

Not yet used, but found while looking for other resources: http://oleddisplay.squix.ch/#/home


[preview1]: images/preview_1.png

[preview2]: images/preview_2.png

[preview3]: images/preview_3.png

[schematics]: images/schematics.png