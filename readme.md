# Graduator

## What?

A bass fuzz for my good friend! Don't tell him, it's a surprise. Starting with a Boss MT-2 (I know, ew, don't tell anybody) because that's allegedly how Arion Salazar got most of his fuzz tone's on Third Eye Blind's self-titled (check out 2:20-2:30 in Graduate, of 4:10 in Thanks a Lot if you like yours with phaser). Hell yeah we want that, don't pretend you don't like that record. 

Formerly "yellow fuzz" after BRC's "yellow bikes" that happen to be green. Didn't like the sound of it, now it's the Graduator.

### Rev 01

Rev01 (non form-factor) has been built, brought up, and play tested. 

![SN00](/images/Rev01/SN00_cropped.jpg)

## Rev01 User Guide

[Electric Druid](https://electricdruid.net/boss-mt-2-metal-zone-pedal-analysis/) has an awesome write-up on the key circuit blocks in the original MT-2 design that's worth a read. If you want a comprehensive survey of the guts of this pedal, read that, then the mods section below, and you're done. 

### Controls

Controls are described by order in the signal chain, rather than physical layout. 

![Rev01 Controls Labeled](/images/Rev01/user_guide/controls_labeled.png)

| Control | Original MT-2 Control, or Experiment | Circuit Block | What's it Do? |
| ------- | ------------------------------------ | ------------- | ------------- |
| Gain | Experiment | Distortion Block - First Op-Amp Stage Gain, P1. ![Gain](/images/Rev01/user_guide/pre_dist_gain_sch.PNG) | The "pre-distortion" gain block does two things: <ul><li> Applies a band-pass-filtered boost (the center frequency of this boost has a mod described separately). </li><li> Demands enough gain from op amp U1A to cause some distortion when at high gain setttings. </li></ul> In the original MT-2, the gain of this stage is fixed. In the graduator, the feedback resistance here can be reduced, which reduces the gain. If the pre-boost filter is ignored (or the pre-boost filter select switch is used to skip the pre-boost filter), this control doesn't really do much at all; the end result of reducing the gain here is audibly identical to reducing the "Distortion" control. But with a filter selected, this control lets you choose how much that initial band-pass boosts, which can be kind of interesting. Definitely won't be included in the form factor design, but merits playing around with while you're playing the the pre-boost filter select. |
| Pre-Boost Filter Select | Experiment | Distortion Block - First Op-Amp Stage Gyrator Select, SW1. ![Pre-Boost Filter Select](/images/Rev01/user_guide/pre_dist_filter_select.PNG) | As you can read about [here](https://sound-au.com/articles/gyrator-filters.htm), "gyrators" are nifty little active circuit blocks that let you make a thing that acts like an inductor out of a capacitor and a transistor or op-amp. Why not just use an inductor is a good question and is covered in that guide in good detail. For our purposes here, this control lets you pick between two filters, or a third disable setting: <ul><li> A stock filter which is described in the electric druid guide; it's a 36dB boost centered at 1 kHz with a "Q" of 2.8 ("Q", or "Quality Factor" describes how narrow and pointy that bandpass's frequency response is; a filter with high "Q" will be super pointy and really impact just its center frequency, while a filter with lower "Q" will be more gradual and wide and impact frequencies up and down the band around its center.).</li><li> A modified filter: 36 dB boost centered at 224 kHz, with a Q of 3.2. I made this mod to push the boost down into a range I thought might be better for a bass fuzz. </li><li> The disable setting just floats the switch terminal, which is kinda a bug because it takes the feedback (the "gain" control) out of the mix. You'll notice some volume variation going to and from this setting depending on where the "gain" is set. I may fix it. I may not. </li></ul>A bonus feature of this section is that one or both of these filter blocks could be retuned by changing a few parts, letting you do A/B comparison between a setting you like and a new setting you're considering. |
| Distortion | Original | Distortion Block - Second Op-Amp Stage Gain, P2A/B. ![Distortion](/images/Rev01/user_guide/dist_control.PNG) | Controls the gain of the second op-amp stage before the diode limiter that really clips the signal. Running this op-amp at high gain will boost the signal to the "rails", and you'll get very hard, square peaks, before you even hit the diode limiter. There are many different sources of distortion in this pedal, it's definitely not all up to just one circuit block to hammer your signal into a mess. |
| Diode Select Switches | Experiment | Distortion Block - Diode Limiting Stage, SW2 / SW3 ![Diode Select](/images/Rev01/user_guide/diode_select.PNG) | The core of this pedal, as with many distortion pedals, is the diode limiter. This stage takes your nice sine-shaped waveform and clips the peaks off of it when they exceed the forward voltage of the diodes. Different diodes have different forward voltages, and different response "shapes" as they effectively turn on and off. The internet is full of forums where people will swear that this diode does this or that and sounds this way or that way, and many of them are subjectively right but nearly all of them are oversimplifying the test case they're talking about. Since there are so many sources of distortion in this (and every) circuit, you're hearing them all. The diode is just part of it. Anyway, this mod lets you pick between three different kinds of diode for your limiter. Even weirder, it lets you choose the diode for the top and bottom half of your waveform separately, so you can produce very "asymmetric" distortion. Right now, you have: <ul><li> A Silicon diode, the generic [1N4148](https://www.diodes.com/assets/Datasheets/ds12019.pdf), with a forward voltage around 1V. </li><li> A Germanium diode, the generic [1N34A](https://www.nteinc.com/specs/original/1N34A.pdf), with a forward voltage around 1V. </li><li> An LED, [Kingbright WP7113QBC/D](https://www.mouser.com/datasheet/2/216/WP7113QBC-D-58299.pdf). This is a blue LED, and has a forward voltage of not less than 2.4V. This is really a bug; I should have used a red or yellow LED with a forward voltage closer to the other two, so that you could compare tone without comparing volume - you'll notice right away that the blue LED is louder than the other diodes. I like how it sounds, though, so I'm considering that a future experiment and letting it ride. </li></ul> Just like the pre-distortion boost section, this section is a great place to swap out components you're curious about and A/B test stuff. |
| Diode Series Resistance Control | Experiment | Distortion Block - Diode Limiting Stage, P3 / P4. ![Diode Resistance Control](/images/Rev01/user_guide/diode_R_control.PNG) | Diode clipping can be very harsh and introduce harmonics that you wouldn't get from, say, output stage distortion in a tube amplifier, which can sound really buzzy and cheap and not great. In an attempt to prevent this, I added 1k potentiometers - variable resistors - in series with the diodes, to soften the "knee" when they turn on and off and try and reduce that fuzz. In practice, the EQ section of this pedal has way, way more impact on the harmonic content that makes it out of the pedal, and I find this control completely inaudible. |
| Post-Boost Filter Enables | Experiment | Distortion Block - after Diode Limiting Stage, SW4 / SW5. ![Post Boost Filter Control](/images/Rev01/user_guide/post_dist_boost_filters.PNG) | The original MT-2 includes this stage with both Gyrator sections included, which provides a "double-humped" bandpass boost. In the original, the two sections are: <ul><li> A ~5dB boost at 105 Hz with Q=14.6. </li><li> A ~10dB boost at 4.9 kHz with Q=2.2. </li></ul>In the graduator, the two sections are: <ul><li> A ~5dB boost at 333 Hz with Q=4.6. </li><li> The original ~10dB boost at 4.9 kHz with Q=2.2. </li></ul>There are really two mods here: <ul><li> I've moved the lower peak up the frequency spectrum and fattened it up a bit. </li><li> Both peaks can be enabled or disabled with the respective switches. </li></ul> This is a little more subtle to play with than I expected, and I like that. Try it out. |
| EQ - Low | Original | Tone Block | The original "low shelf" control, a band-pass filter centered at 105 Hz with a Q of 3.1, which can provide up to 20dB of cut or boost. The whole EQ section is covered very nicely with plots in the Electric Druid guide, highly recommend. |
| EQ - Mid Frequency | Original | Tone Block | The original "mid frequency" control, which controls the center of the mid band-pass filter. Filter center frequency can be swept from about 200 Hz to about 7 kHz. This control would be a lot better as a log taper pot, to spread the frequencies of interest logarithmically along the range of the pot, but a dual-ganged log-taper 50kΩ pot is not an easy thing to find. As a result, you'll hear this control really come to life between about 1 o-clock and 5 o-clock. |
| EQ - Mid | Original | Tone Block | Cut or boost up to 15 dB with the mid-band filter centered wherever you put it with the Mid Frequency knob. |
| EQ - High | Original | Tone Block | High Shelf EQ, begins to kick in around 1kHz, where it offers around 6 dB of cut or boost, and flattens around 10 kHz, where it offers around 20 kHz of cut or boost. | 
| Level | Original | Tone Block | You know what this does. | 
| Enable / Bypass | Original | Switching Section | You know what this does too. |


## Mods

| Change | Goal | Done |
| ------ | ---- | ---- |
| Make gyrators after clipping stage optional (see C24/C25, C20/C17) | Experiment with pedal character to reduce fizz and deliver more even tone to the eq section so I can hear the difference. | Yes |
| Add bypass option for preboost stage. | Try to reduce fizz. | Yes |
| Add series variable resistors (trim pots) to clipping diodes D3/D4. | Try to reduce fizz. | Yes |
| Add selector switch for 3 different diode options in each direction. | Experiment with higher Vf (LEDs) and give germanium a whirl. | Yes |

## Issues

### Rev01 (Non-Form-Factor)

| Issue | Workaround | Fix | Fixed in Master |
| ----- | ---------- | --- | --------------- |
| C2 and R6 ref designators are swapped. HTML BOM shows correct outlines. | Install per HTML BOM. | Swap ref des back. | |
| R4, R6-7, R12, R14-15, R17-18, R24-26, R33, R51 MPN is for 1k part, should be 10k (part description on BOM is correct, but MPN is wrong). | Install 10k part. | Update component in lib. | | 
| R14 and R15 ref des are colliding. | N/A | Fix in layout. | |
| NSVJ3910SB3T1G was replaced in order with J113, which is a through-hole part and won't fit. | Order correct part. | Make sure MPN in design is correct and orderable. | |
| PTV111-4420-A104 was missing from kit, got extra PTV112-4420-A104 instead. | Cut leads 1 and 2, bend 3-6 down to fit into pads 1-4 to use just one pot of the two in the package. | Order the right thing. | |
| PTV111-4420-A503 was missing from kit, got extra PTV112-4420-A503 instead. | Cut leads 1 and 2, bend 3-6 down to fit into pads 1-4 to use just one pot of the two in the package. | Order the right thing. | |
| Nichicon UST1H010MDD1TE footprint is wrong (C1, C19, C26, C36, C43, C46): lead spacing is nto correct, part leads are flared for wider spacing than footprint. | Bend leads back. | Correct footprint. | | 
| D6 missing MPN info. | N/A | Correct part library ref. | |
| No test points, doh. | N/A | Add some ground test points and stage-to-stage test points and jumpers. | |
| 22 Ohm series-R on power rail, why even would you do that? | Short that. | Remove that. | |
| Polarity marks on op-amps are not visible enough, and are obscured when sockets are installed (U1 was installed rotated 180 degrees in first build). | Note polarity carefully during build. | Improve op amp polarity marks. | |
| Pre-distortion boost gain pot P1 is backwards (CCW for more) | Turn it the other way, or snip top-side trace between pins 1-2, short pins 1-3. ![Sch](/images/Rev01/P1_fix_sch.PNG) ![Layout](/images/Rev01/P1_fix_pcb.PNG) | Correct in schematic. | |
| Dual pots installed in P5, P6, P7, and P9 with pins 3-6 slid over into pads 1-4 don't match design correctly. | Double-check pinout of these parts and revise rework used to place dual pots in single-pot footprints. | Use the parts on the BOM, duh. | |
| Duplicate TONE_OUT net names caused short across level pot. ![Tone Out Issue](/images/Rev01/tone_out_short.PNG) | Cut extra trace on top layer. ![Tone Out Workaround](/images/Rev01/tone_out_short_fix.PNG) | Remove duplicate net label. | |
| Incorrectly routed jack as center-positive, which makes the battery not work at all. | Cut and swap traces to make center-negative. ![Jack Rework](/images/Rev01/power_jack_rework_pcb.PNG) | Permanentify rework. | |
| Mid frequency control only does much between about 1-o-clock and 5-o-clock. | Use as is. | Try once more to find a log pot... good luck. | |
| Pre-boost filter select switch SW1 should probably have a resistor on its unused pole, rather than having fixed gain and taking the "gain" control out of the mix. |  |  |  |

## Parts Needed

### For Rev02 (Form-Factor)
* 1/4" Stereo Jack, Panel Mount with header footprint.
* 1/4" Mono Jack, Panel Mount with header footprint
* Re-evaluate all potentiometer tapers and footprints.

## Play testing notes

* It sounds... like an MT-2 with some stuff changed. 
* The pre-filter change is the most interesting, as swapping diode types. 
* Post-filters are also interesting, but a bit less so. 
* Still many settings that produce lots of unpleasant fizz. Tonally I'd still say it's "mostly bad with the ability to do some good things."
* Series-R on the dioes does exactly nothing. On the scope, it does visibly soften the knees a little, but by the time this has been through the tone section, that does the same thing. 
* Secondary control on the initial boost gain does exactly the same thing as the drive control. Might try playing with it a bit more with the pre-filter set to off, but for the most part just set it to 10 and leave it. 


## References

### Other Pedals I'm eyeing
* DOD FX91 Bass Overdrive
* Darkglass - Duality
* Zvex - Wooly Mammoth
* Death by Audio - Fuzz War
* Bass Big Muff
* MXR Bass Fuzz
* Fairfield Barbershop
