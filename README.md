# ZX81_ISSUE_3
ZX81 Computer Replacement concept and PCB design in the same style as the Sinclair ZX81 ISSUE 3 however using a CPLD to replace the original ULA, for example if your ULA is defective.

![A picture of the ZX81 Issue 3 replacement PCB](ZX81_ISSUE_3_CPLD_PCB_REV1_CMP_1.png)  

## Purpose and permitted use, cautions for a potential builder of this design
This project was created for historical purposes out of love for historical computing designs and for the purpose of enabling computing enthousiasts with a sufficient level of building and troubleshooting expertise to be able to experience the technology by building and troubleshooting the hardware described in this project.

Besides the GPL3 license there are a few warnings and usage restrictions applicable:
No guarantees of function or fitness for any particular or useful purpose is given, building and using this design is at the sole responsibility of the builder.

Do not attempt this project unless you have the necessary electronics assembly expertise and experience, and know how to observe all electronics safety guidelines which are applicable.

It is not permitted to use the computer built from this design without the assumption of the possibility of loss of data or malfunction of the connected device. To be used strictly for personal hobby and experimental purposes only. No applications are permitted where failure of the device could result in damage or injury of any kind.

If you plan to use this design or any part of it in new designs, the acknowledgement of the designer and the design sources and inspirations, historical and modern, of all subparts contained within this design should be included and respected in your publication, to accredit the hard work, time and effort dedicated by the people before you who contributed to make your project possible.

No guarantee for any proper operation or suitability for any possible use or purpose is given, using the resulting hardware from this design is purely educational and experimental and not intended for serious applications. Loss of data is likely and to be expected when connecting any storage device or storage media to the resulting system from this design, or when configuring or operating any storage device or media with the system of this design.

When connecting this system to a computer network which contains stored information on it, it is at the sole responsibility and risk of the person making the connection, no guarantee is given against data loss or data corruption, malfunctions or failure of the whole computer network and/or any information contained inside it on other devices and media which are connected to the same network.

When building this project, the builder assumes personal responsibility for troubleshooting it and using the necessary care and expertise to make it function properly as defined by the design. You can email me with questions, but I will reply only if I have time and if I find the question to be valid. Which will probably also lead to an update here. I want to primarily dedicate my time to new project development, I am not able to do any user support, so that's why I provide the elaborate info here which will be expanded if needed.

---------------------------------------------

# Acknowledgements

This project was inspired by:
- Sinclair computers in the 1980s
- Wilf Rigter who helped me with my PCB designs in the 1990s
- the German ZX-Team who inspired me a lot by sending me their Magazin and kind letters and messages. Particularly Peter Liebert Adelt and Kai Fischer with whom I have had very pleasant and memorable contact in the 1990s years.
- Gary Kildall who invented CP/M, the concept of splitting the BIOS from software operation and so much more
- Wayne Warthen who created and manages the ROMWBW CP/M project development which is part of the basis of this project

---------------------------------------------

# Outline of the project
This project has been created in order to repair a defective ZX81 where the original ULA has gone defective, or where the user wants to improve the existing computer with a more modern quality design and solution, where:
- we keep the original look and feel of the Issue 3 PCB by Sinclair
- we want to keep the UM1233 modulator in the computer in order to preserve certain nostalgic aspects and effects such as noise when tuning into the TV channel

Advantages of this design:  
- more modern CPLD is used instead of ULA, more durable and reliable
- manufacturing a new PCB provides a much better modern quality PCB and could be done with ENIG gold plating on expansion connector
- the computer is to a very large degree reconfigurable by reprogramming the ULA which invites experimentation!
- we can use some form of bank switching to increase the RAM size to 128KB because the high address lines to the SRAM are outputs of the CPLD so we can reprogram the functions to do bank switching for example based on IO writes to a certain IO port address banks in certain areas can be swapped to be able to flip data very fast
- we can create a shadow copy mechanism to feature the ROM code in RAM and thus featuring the entire Z80 memory space in RAM
- we would be able to load new ROM code from a tape program, move it in a RAM segment and switch it in place of the ROM area
- CHR$128 UDG is supported
- transistor stages for reliable and convenient line level 2V tape loading using a phone or PC headphone output etc
- transistor amplifier with potmeter level adjustment for the video signal going into the modulator
- free CPLD pins available on solder pads for creating custom circuits using the CPLD for example a joystick, sound output etc
- the memory map is completely reprogrammable
- using the CPLD we can include register bits for enabling operating modes and switching options in software
- some spare inverters are available on the HC04 TTL IC for any purpose

The PCB is designed much in the same style of the Issue 3 ZX81 PCB. Which means it has all resistors in horizontal orientation, with the same lead length of resistors and diodes.  

The PCB contains the CPLD, Z80A CPU, 27C64 EPROM, 681000 SRAM and a 74HC04 for generating the clock signal.  

The JTAG pins are on the bottom PCB edge, so it will be easy to open the ZX81 case, plug in a programming cable and reprogram the CPLD without needing to unscrew the PCB from the top shell, which spares the membrane keyboard from being unplugged and plugged back in too many times. Theoretically some pin bus strip can be soldered into the back of the PCB to plug the JTAG cable without removing the PCB.

There is no linear regulator on the PCB, instead a modern 5V DC power supply can be used resulting in less heat inside the ZX81 case.

Why this PCB? For people who like the look and style of the original Issue 3 PCB, however want to repair a faulty ULA but at the same time don't want to plug in or wire an adapter PCB, and rather would prefer a more tidy new single PCB design, and yet want to maintain the look and feel of an original Issue 3 PCB as much as possible and reasonable. Some components like CPU, resistors etc can be transferred to the new PCB.

The 27C64 EPROM was chosen because the D2364 has a pinout somewhat different from a 27C64, which would make replacing the ROM more difficult.

The PCB contains a modulator footprint as well. Why a modulator? Because having a modulator, while this decreases the display quality a little, it also has some interesting quirks which some users may enjoy for nostalgic reasons. For example, when tuning into the channel on a TV tuner, it also produces a typical sound/noise in the TV speaker, somewhat corresponding to the pixel patterns seen on the screen. 

Having the modulator and tuning into the channel does provide a more true to original experience. A transistor video output stage and potmeter are included for adjusting output video voltage level, because this may benefit the modulation quality by being able to adjust the signal ideally for the input of the modulator.

Alternatively the composite output cinch bus footprint is included so this also can be soldered in place of the modulator, though it remains highly recommended to try a modulator for the experience if a period TV is available as a monitor.

NB I also found that connecting the video output to a speaker somehow can produce the typical sound heard from tuning into the ZX81 modulator RF channel so that would also be one way to have this experience.

Otherwise, the CPLD ULA offers some simple but interesting features such as complete reprogramming of all the ZX81 circuits, bank switching and/or shadow RAM access to the entire 128KB of the SRAM would be possible, and with a little effort the spare CPLD pins can be wired to some custom device of choice of the builder. With some creative ideas the CPLD could produce sounds and/or interface to a joystick, etc.   

On the EAR and MIC connectors there is the middle pin available to route sound to a speaker when this unused pin is wired to some simple sound or noise circuit inside the ZX81. Or a small speaker could be built into the case for experimenting with beep tones etc using the CPLD.

The 74HC04 has 4 spare gates which have purposely not been routed to anything which normally we wouldn't do but that way the user could make use of those 4 gates for any purpose such as driving LEDs or creating some output signals while protecting the CPLD, etc. and it would not be necessary to cut any connections to be able to use these inverters.

Having a CPLD inside a ZX81 offers a lot of opportunities for further experimentation with the ZX81 display system. Other timing schemes could be created for the pixel display. Also we could use a different crystal to get a different pixel clock frequency, and design some custom hsync timer etc. inside the CPLD. Using a 20MHz Z80 and a really fast EEPROM, or creating an INIT routine for making a ROM shadow copy providing faster memory speeds, this may enable much faster pixel speeds. The clock speed could be dynamically controlled by adding an extra clock signal to a spare pin.

Manufacturing this cost effective PCB would increase the ZX81 PCB quality a lot, having a high quality solder mask, ENIG gold plated edge connector etc. which should improve any interface connection if that also uses gold contacts on the connector.

Creating some I/O port inside the CPLD and allowing this to do bank switching of the 8 16KB SRAM banks, and offering shadow copy features to load custom programs instead of the original ROM are also features which could be created to make a lot of new ideas possible in dynamic memory configuration. For example loading an alternative ROM image from a tape file and enabling it in SRAM. 
The A6 to /INT connection is now configurable inside the CPLD and could be made dependent on some I/O bit value which allows it to be turned on or off, for example for running software routines which are not compatible with this mechanism. An external interface could drive INT on the CPU instead of A6 in order to be able to use interrupts for other purposes.

---------------------------------------------

# Status of the project
The PCB design and initial CPLD project are finished.  

![Front picture of the PCB](ZX81_ISSUE_3_CPLD_PCB_REV1_1.png)  

---------------------------------------------

![Back picture of the PCB](ZX81_ISSUE_3_CPLD_PCB_REV1_BACK_1.png)  

---------------------------------------------

Explanation of optional components for different functions:  

C11	47nF  
R27	1k  
optional tape input filter, don't populate and first test tape loading  
if tapes load fine, don't populate this filter  

D9	1N4148  
R31	390 ohm  
R32	560 ohm  
optional for USA TV output using RF modulator  

J12  
short when using cinch video output instead of a modulator  

R30	4k7  
populate for NTSC standard video output  

R56	10k  
populate for PAL standard video output  
  

Status: PCB has been received and will be built and tested.  

The CPLD project zip file in the directory is only an initial version, possibly more functions will be added or modified.
If so, I will share the updated CPLD project here.

# Building advice  
Soldering this board should start by soldering the CPLD first.  
So the first step is adding no clean flux on the SMD pads.  
After that solder can be loaded onto the pads using a bigger wedge shaped solder tip.  
Wiping along the length of the pads, adding sufficient solder, all pads can be loaded with solder as much as they will take to make sure that when soldering the PLCC J lead chip onto the pads, the pads will quickly take more solder and attach with each pin of the PLCC IC.  
Position the IC very carefully to make sure it's really straight, make sure pin 1 is aligned, and then add some solder onto a smaller soldering tip, and apply some solder to the corner pins, fixing the PLCC in the correct place. After doing opposing corners and adjusting again to make sure it's absolutely straight, take your time, then you can solder all the pins with strong light and magnification making sure you have a really good view on the work.   
After doing this, first use a strong magnification and light to visually inspect all the pins. After that you can beep out all adjacent pins to make sure there are no shorts. If there is a connection, use braid solder wick and no clean flux to remove the short, and solder again after applying some new flux.

After soldering the CPLD, all the other components can be soldered in. Check the text above which of the optional components you will want to add.

The CPLD has various pins available to solder pads on the board, most of which can be reached from the bottom, make sure not to insert any wires to far, only barely solder them into the holes so they don't touch anything they shouldn't. I suggest if you are sure that the ICs are fine, you can solder them directly into the board. This will make the computer really solid and reliable. The ROM would be left removable using a socket.

If you want to add any expansions, you could consider soldering a boxheader to the edge pads so you can use a flatcable to avoid loose contacts.

/ROMCS and /RAMCS use separation resistors and are connected to the expansion connector so the control can be overridden by expansions by holding them high or selectively driving them in some way.

It's an interesting idea to make some kind of bank switching RAM system. We have 128KB of SRAM in the computer which has 3 address inputs which can be manipulated using logic. So we can potentially move around 8 pages of 16KB RAM by changing the output address lines from the inputs by the Z80. This could potentially be used for animation, alternate screen data and other purposes like loading very large programs.  
I may look into swapping some areas around in some way in order to add different ROM code. For example, CP/M code could possibly be loaded into the low memory area and calling the reset start address from outside of the area after swapping the CP/M code into place. However without display and keyboard drivers or a serial console you cannot operate CP/M.  
A possible simple method for exchanging the Z80 memory contents would be to invert the A15 output, initialize the computer, then load everything in place in the top half of RAM, then inverting the A15 and disabling the ROM. This could load alternate software into the system and a next step can be to overwrite the second half of RAM as well. Of course, some form of keyboard and display control would make sense in the new "ROM" code so the computer will keep a console going with the user.

Kind regards,

Rodney
