# Graduator

A bass fuzz for my good friend! Don't tell him, it's a surprise. Starting with a Boss MT-2 (I know, ew, don't tell anybody) because that's allegedly how Arion Salazar got most of his fuzz tone's on Third Eye Blind's self-titled (check out 2:20-2:30 in Graduate, of 4:10 in Thanks a Lot if you like yours with phaser). Hell yeah we want that, don't pretend you don't like that record. 

Adding the popular mods as options, retuning most of the gyrator filters down a bit, adding trim pots for some of the key filters and gains, and doing a non-form-factor layout so I can get all my dumb bugs out of my system before it's annoying to rework.

Form factor by May lol!

Formerly "yellow fuzz" after BRC's "yellow bikes" that happen to be green. Didn't like the sound of it, now it's the Graduator.

## Mods Planned

| Change | Goal | Done |
| ------ | ---- | ---- |
| Make gyrators after clipping stage optional (see C24/C25, C20/C17) | Experiment with pedal character to reduce fizz and deliver more even tone to the eq section so I can hear the difference. | Yes |
| Add bypass option for preboost stage. | Try to reduce fizz. | Yes |
| Add series variable resistors (trim pots) to clipping diodes D3/D4. | Try to reduce fizz. | Yes |
| Add selector switch for 3 different diode options in each direction. | Experiment with higher Vf (LEDs) and give germanium a whirl. | Yes |
| Add trim pot to tune center frequency of preboost filter. Trim R53 from 20k to 220k, chnage C34 from 27n to 68n. | Retune for bass. |  |
| Retune dual bandpass filter after distortion stage. Low peak 50 - 150 Hz, High peak 1k - 3k, both with bypasses. | Retune for bass. |  |

## Parts Needed 

### For Dev Version

* Electromechanical
  * Foot switch, probably no-click momentary pcb mount - FS5700SPMT2B2M2QE
    * FS5700SPMT2B2M1QE for form-factor (panel-mount, solder lugs)
  * Board-mount mini-toggles, the more fun the better.
* Connectors
  * 9V Battery Clip
  * AC Adapter - check barrel sizes from Godlyke adapter I've got.

### For Form-Factor Version
* 1/4" Stereo Jack, Panel Mount with header footprint.
* 1/4" Mono Jack, Panel Mount with header footprint
* Re-evaluate all potentiometer tapers and footprints.

## Issues

### Don't Use KiCad

First and foremost: KiCad's BOM workflow (link symbols to footprints at individual part level -> link to ordering information at footprint level to build BOM from layout) makes no sense to me. Either I'm misunderstanding how this tool works or it's been built to serve the workflow some small community of hobbyists was using. Either way, never again. 

This workflow, plus the look and feel of KiCad's schematic editor, made capturing the design about as smooth and rewarding as swallowing a fork.

### OK Actual Issues

## References

### Other Pedals I'm eyeing
* DOD FX91 Bass Overdrive
* Darkglass - Duality
* Zvex - Wooly Mammoth
* Death by Audio - Fuzz War
* Bass Big Muff
* MXR Bass Fuzz
* Fairfield Barbershop
