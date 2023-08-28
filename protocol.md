## neotrellis wire protocol
The neo trellis wire protocol is implemented over UART to update newtrellis LEDs or read the button states when a key is pressed


## STRUCTURE
<CODE><array><\n>

## LED Update frame
The update frame is used update the neopixels color and brightness
L,1,255,255,255,150,.....\n
L = LED
1 = LED number
255 = RED Value uint8
255 = GREEN Value uint8
255 = BLUE Value uint8
150 = Brightness uint8

The frame can have upto 64 LEDs. LED 0 is not used. The command processor will only update the LEDs that are in the frame, if you want to clear an LED you have to set the LED to 0,0,0,0. The procesor will not maintain states over a power cycle.

## Button status frame
This frame will be the default frame that will be sent out by the new trellis board.
B,1,0,....\n
B= Button fram
1= LED 1 is pressed
0= LED 0 is not pressed

Button frames are fixed lenght starts with 'B' and end with '\n' with 64 uint8 (bool) values 1 = button pressed, 0 = button released. The fram is sent out every 100ms and an additional frame is sent out when a button is pressed.

## LED MAP
![LED MAP](led_map.jpg?raw=true "LED MAP")

## Demo code
a long press of LED 1 will put the neo trellis board in a demo mode. This will cycle through a few fun patterns

## MIDI mode
TBD
