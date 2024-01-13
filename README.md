# RP6502 - Enhanced 6502 BASIC

Reference manual and more information archived here:<br>
http://retro.hansotten.nl/6502-sbc/lee-davison-web-site/enhanced-6502-basic/

You must have on your development system:
 * [VSCode](https://code.visualstudio.com/). This has its own installer.
 * A source install of [this CC65](https://github.com/picocomputer/cc65).
 * The following suite of tools for your specific OS.
```
$ sudo apt-get install cmake python3 pip git build-essential
$ pip install pyserial
```

# Initial plotting enhancements for the RP6502 Picocomputer's EhBASIC

Plotting-enhancements work with the 12&13-Jan-2024 EhBASIC+save/load in the master
picocomputer repo (rev: 8583e72).


Four new commands are available using EhBasic's "CALL" keyword. 
CALL addresses supplied are from the mapfile. 
Plotting command is callable from EhBASIC.

Two plotting screen dimensions are supported.


The commands are:

    * HGR,screen_dimension - initializes graphics screen mode
       * CALL HGR,0   - selects 320h x 180v x 8bpp mode (16:9 letterbox);
       * CALL HGR,$FF - selects 320h x 240v x 4bpp mode (4:3 fullscreen)
    * HPLOT,x,y,color - paint a pixel of 'color' at x,y on the screen.
    * TEXTMODE - return VGA-screen back to console/text mode
    * CLS (or HOME) - clear the console/text screen.

Assumptions / Limitations:

    * HPLOT targets (only) the two screen-modes listed above on the rp6502's pico-VGA.
    * The x-coordinate from EhBasic is limited to values <= 255 (8-bits). This is a 
      limitation of parameters following the 'CALL' EhBASIC keyword.
