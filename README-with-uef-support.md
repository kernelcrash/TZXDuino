```
TZXDuino with UEF support
=========================
Based on TZXDuino 1.8

Adds in UEF playback, and a sort of turbo mode 
playback for UEF files.

The UEF files you put on the SD card must be gunzip'd first. eg. in linux or Mac

  gunzip -c game.uef >game.uef.tmp && mv game.uef.tmp game.uef

Playback is a square wave, rather than a sine wave. My Electron seems fine with
that.

Normal UEF playback is at 1200 baud. If you hold down the ROOT key
as you turn on (or if you hit reset on the Arduino), then you should see
'Turbo UEF mode' flash up on the LCD. Now playback is at 1550 baud with
shorter carrier tone sequences. This works fine for a lot of UEF's, but there
are some that will require you to use the normal 1200 baud mode (eg. Imogen)

If you want it to default turbo mode, change the uefTurboMode setting in the 
TZXDuino.h file:

  byte uefTurboMode=1;

Now it should say 'Turbo UEF mode' at power on unless you hold down ROOT.

I just run the audio out (D9) via a a few resistor/caps instead of via an amp;



   D9 ----/\/\/\/-------+
           100R         |
                        |
                        /         10uF electrolytic
                        \       +| |
                 200R   /<-------| |--------> to 3.5mm jack
                trimpot \        | |
                        /
                        \
                        |
                        |
                    ---------
                      -----
                       ---
                        .

```
kernelcrash.com
