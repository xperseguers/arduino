# Time Bomb

This project uses a 1.3 inch SH1106 SPI OLED display to simulate a time bomb.

The initial state will show a warning that you never should press the little switch:

![Initial state][preview1]

If you press the switch anyway, the green light (see full breadboard below) will start
blinking, before going off and showing the red light instead. At that point a countdown
timer is displayed, starting at 20 seconds:

![Countdown timer][preview2]

If you just wait, it finally explodes:

![Bang!][preview3]


[preview1]: images/preview_1.png

[preview2]: images/preview_2.png

[preview3]: images/preview_3.png