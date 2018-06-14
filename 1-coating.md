---
title: Coating
nav: true
---

# Hydrophobic Surface Coating

Description (drawn from the [Official OpenDrop Website](gaudi.ch/OpenDrop/)):

Key to using the electro-wetting effect for moving droplets is a super hydrophobic and well gliding surface. There are different coating materials on the market for electro-wetting such as Fluoropel, Teflon AF or Cytop. These are amorphousfluoropolymer that can be deposited by spin coating or by dipcoating. 
Several different materials have been tested with the OpenDrop System. The easiest way is to use Polyethylen (PE) kitchen foil (saran wrap) coated with Rain-X - a commercially available rain repellent for wind shields. This coating lasts for about 2h. A better solution for creating a hydrophobic surface is parafilm and a high viscous (5cSt) silicon oil. It can last up to 3 days and is the combination used in the following experiments.
More advanced solutions for devices with top cover are using PTFE foil and Fluoropel. Also see the notes on the GaudiLabs website for different materials that were tested. 

## Topless Configuration
To hook up the topless configuration with Parafilm and silicon oil, follow these steps:
- Unscrew the PCB (“Cartridge 1”) from the OpenDrop System
{% include figure.html file="topless_configuration/topless_step_1.jpg" file2="topless_configuration/topless_step_2.jpg" height="6.5cm" %}
- Clean the table, gloves, PCB and the electrodes with pure alcohol
{% include figure.html file="topless_configuration/topless_step_3.jpg" file2="topless_configuration/topless_step_4.jpg" height="5.4cm" %}
- Cut out a piece of Parafilm foil and attach it to the table with Scotch tape
{% include figure.html file="topless_configuration/topless_step_5.jpg" file2="topless_configuration/topless_step_6.jpg" height="6.5cm" %}
- Stretch the Parafilm to get a thin layer
{% include figure.html file="topless_configuration/topless_step_7.jpg" height="6.5cm" %}
- Now turn the foil sideways and attach it to the table as before. Wrap one end around the PCB and stretch the Parafilm again
{% include figure.html file="topless_configuration/topless_step_8.jpg" file2="topless_configuration/topless_step_9.jpg" height="5.9cm" %}
- Cut off the redundant pieces of Parafilm and turn down the foil at the edges of the PCB. Make sure the grounding around the screw holes is not covered by the foil.
{% include figure.html file="topless_configuration/topless_step_10.jpg" file2="topless_configuration/topless_step_11.jpg" height="5.9cm" %}
- Apply some silicon oil on top of the electrodes to avoid air. Be careful to uses as little oil as possible as this will add to the dielectric gap.
- Apply the silicon oil to the foil
{% include figure.html file="topless_configuration/topless_step_14.jpg" file2="topless_configuration/topless_step_15.jpg" height="5.9cm" %}
- Add a droplet of water on the device. A droplet size of around 6-10uL should do the job.
{% include figure.html file="topless_configuration/topless_step_16.jpg" height="6.5cm" %}
- Remove all static charge from the droplet by touching them with the grounded wire. 

**ATTENTION**: Do not get too close to the electrode. This can cause a short circuit between GND and high voltage that will damage the flash registers as well as the Arduino
{% include figure.html file="topless_configuration/topless_step_17.jpg" height="6.5cm" %}
&nbsp;

## Top-Cover Configuration
A more advanced setup is the top cover configuration. It can be used to do experiments including feedback reading, smaller volumes and droplet splitting. Therefore, a conductive ITO-glass is used on top of the droplets. This will end up in a closed circuit between the high voltage power source and the grounding of the feedback pin so that it is possible to read the current positions of the droplets on the electrode matrix.
{% include figure.html file="top_cover_configuration.png" caption="Top-Cover Configuration" height="5cm" %}

During first experiments with a spin-coated ITO-glass there occurred some problems with the droplet movement. The droplets stuck to the glass surface and could not be moved.