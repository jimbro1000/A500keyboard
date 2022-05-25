# A500 Keyboard HID Adapter
This is a (prototype) project to develop a simple adapter for the Amiga 500 
keyboard for connection via USB. The project is not particularly revolutionary,
other similar projects exist but require the use of more expensive 
microcontrollers while this solution aims to use the remarkably cheap RP2040
controller (aka Raspberry Pico)

## Components Used
Right now this is being built on a breadboard but the design is mirrored as
a KiCad project.

The initial approach is to utilise a pair of CD4050 hex non-inverting buffers
to manage level shifting between the keyboard (which operates at 5v) and the
RP2040 (operating at 3.3v).

The shift up to 5v is only required to drive LEDs on the keyboard so not actually
mandatory but in order to achieve full brightness the 5v is needed. This could
be achieved with a couple of transistors but the CD4050 chips are cheap enough
and readily available such that it is an equally simply solution.

If you don't care about the brightness of the LEDs then you could simply miss
the second CD4050 out and just jumper between two pairs of pins.

The inclusion of smoothing caps on the board is equally speculative. For the LED
drivers it should be completely unnecessary given the frequencies used. For the
keyboard data lines though it is strongly recommended to make sure the quality 
of transmission is maintained.

All in a single prepared board should cost roughly £14 (being somewhat pessimistic
with component prices). Given the price point on the PCB in batches of 10 and
similar bulk prices on the Pico board that could easily be reduced down to just 
£9 (being optimistic). Deleting the second CD4050 should save another £0.20-0.60
(if you're paying more that for CD4050s something is wrong).
