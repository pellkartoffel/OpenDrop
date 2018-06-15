---
title: OD-Measurement
nav: true
---
{% include mathjax.html %}

# General Optical Parameter
{% include figure.html file="optics.png" caption="Comparison of optical parameters" src="https://learn.sparkfun.com/tutorials/temt6000-ambient-light-sensor-hookup-guide?_ga=2.181503214.856477097.1528971890-1685415095.1525085967" height="7cm" %}

Optical quantities can be described in two different systems. Radiometry on the one hand describes electromagnetic radiation including visible light. Photometry on the other hand describes light, in terms of its perceived brightness to the human eye (around 400–700nm). A comparison of the equivalent quantities is given in the following table:

<!--  This table was created with http://tableizer.journalistopia.com -->
<figure>
{% include table_style.html %}
<table class="tableizer-table"  cellspacing="0">
<thead><tr class="tableizer-firstrow"><th>Radiometric Units</th><th>Symbol</th><th>Unit</th><th>Photometric Units</th><th>Symbol</th><th>Unit</th><th>Description</th></tr></thead><tbody>
 <tr><td>Radiant power</td><td>P</td><td>Watts [W]</td><td>Luminous flux</td><td>F</td><td>Lumens [lm]</td><td>total perceived power of light</td></tr>
 <tr><td>Radiant intensity</td><td>I</td><td>Watts per steradian [W/ster]</td><td>Luminous intensity</td><td>I_v</td><td>Candelas [cd = lm/ster]</td><td>perceived power emitted by a light source in a particular direction per unit solid angle</td></tr>
 <tr><td>Irradiance</td><td>E</td><td>Watts per square metre [W/m2]</td><td>Illuminance</td><td>E_v</td><td>Lux [lx = lm/m2]</td><td>total luminous flux incident on a surface, per unit area</td></tr>
</tbody></table>
</figure>
<figcaption>Overview of important optical quantities <a href="">(source)</a></figcaption>

<br>

<figure><center>
<table class="tableizer-table" cellspacing="0">
<thead><tr class="tableizer-firstrow"><th>From</th><th>To</th><th>Given</th><th>Equation</th></tr></thead><tbody>
<tr ><td> Candela (\( I_v \))  </td><td> Lumen (\( \Phi_v \)) </td><td> apex angle &alpha;             </td><td> \( \Phi_v = 2\pi I_v\left( {1 - \cos {\alpha  \over 2}} \right) \) </td></tr>
<tr><td> Lumen (\( \Phi_v \)) </td><td> Candela (\( I_v \))  </td><td> apex angle &alpha;             </td><td> \( I_v = {\Phi_v \over {2\pi \left( {1 - \cos {&frac12; \alpha}} \right)}} \) </td></tr>
<tr ><td> Lumen (\( \Phi_v \)) </td><td> Lux (\( E_v \))      </td><td> surface area A (m<sup>2</sup>) </td><td> \( E_v = {\Phi_v \over A} \) </td></tr>
<tr><td> Lux (\( E_v \))      </td><td> Lumen (\( \Phi_v \)) </td><td> surface area A (m<sup>2</sup>) </td><td> \( \Phi_v = E_v \cdot A \) </td></tr>
<tr ><td> Candela (\( I_v \))  </td><td> Lux (\( E_v \))       </td><td> measuring distance D (m)      </td><td> \( E_v = {I_v \over {D^2}} \) </td></tr>
<tr><td> Lux (\( E_v \))      </td><td> Candela (\( I_v \)) </td><td> measuring distance D (m)        </td><td> \( I_v = E_v \cdot D^2 \) </td></tr>
</tbody></table>
</center></figure>
<figcaption>Conversion table for optical quantities<a href="https://www.compuphase.com/electronics/candela_lumen.htm">(source)</a></figcaption>

A detailed comparison of the different optical quantities can be found here: <a href="https://www.compuphase.com/electronics/candela_lumen.htm">Compuphase.com</a>

# Optical Density Measurement
Description (drawn from <a href="http://www.biotronix.de/Data/EloCheck_Application_Note_1.pdf">Biotronix</a>):

Measuring the optical density of growing cultures is a common method to quantify various important culture parameters like cell concentration, biomass production or changes in the cell morphology. In general, measuring the optical density (OD) is a common method to quantify the concentration of substances (Beer-Lambert-Law), since the absorbance is proportional to the concentration of the absorbing species in the sample. Photometers quantify the optical density of liquid samples by comparing the intensity of light that has passed through and the intensity of the light before it enters the sample.

## Derivation
According to the Beer–Lambert law, the absorbance $$A_\lambda$$ of a material for a specific wave length $$\lambda$$ is given by: 

$$A_\lambda=\log_{10}⁡\left(\frac{I_{v0}}{I_{v1}}\right)=\epsilon_\lambda\cdot c \cdot d$$

where $$I_{v0}$$ in $$Wm^{-2}$$ is the intensity of the incident light, $$I_{v1}$$ in $$Wm^{-2}$$ is the intensity of the transmitted light, $$\epsilon_\lambda$$ in e.g. $$m^2 mol^{-1}$$ is the molar absorption coefficient that is dependent on the specific substance, $$c$$ in $$mol \cdot l^{-1}$$ is the concentration of the substance and $$d$$ is the pathlength of the sample.

*Drawn from <a href="http://www.rsc.org/images/EiC-05_2007-spectrophotometer_tcm18-214788.pdf">RSC.org</a>:*

As well as absorption by the compound, other processes reduce the intensity of light that passes through the sample, so it is essential to take a ‘background’ reading for the solvent and the cell, which corresponds to $$I_{v1}$$.
It is assumed that the relationship between the incident light and the measurement values received from the light sensor is linear. In that case, the ratio $$I_{v0}/I_{v1}$$  can be expressed as:

$$\frac{I_{v0}}{I_{v1}} = \frac{I_{sample}}{I_{solvent}} = \frac{V_{sample}-V_{zero}}{V_{solvent}-V_{zero}}$$

where $$V_{sample}$$ and $$V_{solvent}$$ are the readings of the light sensor for the sample cell and the solvent. $$V_{zero}$$ is the measurement value that is received from the sensor when no light is falling on the photodiode. In our case, this offset is $$V_{zero}=0$$. Hence, the absorbance can be calculated by

$$A_\lambda=\log_{10⁡}\left(\frac{V_{sample}}{V_{solvent}}\right)=\epsilon_\lambda \cdot c \cdot d$$

and the concentration we are looking for can be expressed as:

$$c=\frac{1}{\epsilon_\lambda d} \log_{10⁡}\left(\frac{V_{sample}}{V_{solvent}} \right)$$

## Setup
To measure the absorbance of a substance, a light ray is sent through the substance and is detected by a luminosity sensor. By comparing the values of a blank material with the results of the substance to be measured, the absorbance of a specific material can be determined. 

The light emitting source is a 600nm orange LED (HLMP-C423) that is applied above the electrode at position (0,0) (top left). The light is then detected by an ambient light sensor breakout board (Sparkfun TEMPT6000) that measures the illuminance (in lux) of the incident light in a range of 390nm to 700nm. 

{% include figure.html file="sparkfun_lux_sensor_tempt6000.jpg" caption="TEMT6000 Ambient Light Sensor Breakout Board" src="https://www.sparkfun.com/products/8688" height="4cm" %}

The analogue output is received by the Arduino (Pin A0) and is used for further calculations. 
{% include figure.html file="light_sensor_schematic.png" caption="Light sensor schematic" height="12cm" %}

On the OpenDrop Device, the Pin A0 can be accessed through the Pad P2 on the backside of the PCB. The pads P3 (5V) and P12 (GND) can be used for powering the LED and the sensor.

{% include figure.html file="OD_measurement_wiring-2.jpg" caption="Wiring the light sensor on the OpenDrop System" height="12cm" %}

A current limiting resistor of 150 Ohm is used to limit the current through the LED. The HLMP-C423 LED has got a voltage drop of 1.9V which results in a forward current of around 20mA. According to Ohm’s law the resistor should be around

$$R = \frac{5V - 1.9V}{20mA} = 155\Omega$$

For first tests a 3D-printed setup is used to configure the basic measurement. The liquid is put into a standard 1x1cm cuvette normally used for a professional spectrophometer.