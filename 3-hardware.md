---
title: Hardware
nav: true
---

The following picture illustrates the general functions of the OpenDrop v2.1 System:
{% include figure.html file="opendrop_v2.1_label_front.png" alt="OpenDrop Peripherals (front)" height="11cm" %}

On the top there are the following peripherals:
- **12V DC Power Supply Socket**: We used a 12V/2A Power Supply with a 2.5mm DC plug. Higher currents could be necessary at some point because the electrodes need a high amount of power. 
- **Piezo Speaker**: The speaker is used to give an audio feedback. Sounds can be turned on or off in the OpenDrop Library
- **OLED Display**: The display is an Adafruit 128x64 OLED based on the SSD1306 single-chip CMOS display driver. It communicates with the Arduino Micro via a SPI bus.
- **Micro USB Port**: Used to program the Arduino
- **V_GND**: Connect this pin to the top cover ITO glass to implement the feedback feature
- **Fluxl-Matrix**: 16×8 electrodes array, 2.75mm2 in size
- **Button 1**: Free to use for any additional features
- **Button 2**: Start-Button
- **Joystick**: Used for moving around the droplets
- **High Voltage Potentiometer**: The high voltage level that is used to drive the electrode array can be controlled with the potentiometer. Turn clockwise to increase the output voltage
- **High voltage switch**: This switch is a safety feature that provides the possibility to turn the high voltage of if needed

{% include figure.html file="opendrop_v2.1_label_back.png" alt="OpenDrop Peripherals (back)" height="10cm" %}

On the back of the OpenDrop System you can find the following peripherals:
- **Arduino Micro (Socket)**: The heart of the system which controls the functionality of the OpenDrop System.
- **High Voltage Boost Converter**: The power supply unit was originally created for Nixie Tubes and is adopted to the OpenDrop System. It boosts the incoming 12V DC voltage to the high voltage (65-250VDC depending on the potentiometer)
- **HV507PG**: The Serial-to-Parallel Converter has a high voltage output level and is used to address and drive the electrode array
- **Wifi Socket**: The wifi socket can be used to add wifi capability based on the ESP8266 Chip
- **Feedback Amplifier**: The feedback amplifier circuit amplifies the voltage signal from the feedback pin and creates a higher voltage level that can be read by the Arduino
- **Arduino Pin A1**: This pin can be used for adding additional features and is not used by the moment

## HV507PG Serial to Parallel Converter
{% include figure.html file="hv507pg_cascade.png" alt="HV507" height="5cm" %}
According to it’s [datasheet](files/hv507_datasheet.pdf), the HV507PG is “a low-voltage to high-voltage serial-to-parallel converter with 64 push-pull outputs”. As the matrix has got 16x8=128 electrodes, two serial-to-parallel converters are used in series (as a cascade). The DIOA pin of the first chip is configured as the main serial input. The DIOB pin is configured as the output and is connected to the DIOA input of the second chip. In this way it is possible to drive 128 high voltage outputs instead of 64.

Pins: see [here](tables/hv507_pins.htm)

The electrodes can be turned on or off by sending a 128bit code to the DIOA pin of the first HV507PG chip. This data is first send to the static shift register and afterwards stored in the latches. To send the data to the actual electrode matrix - thus activating the high voltage electrodes – the blanking pin must be activated.

{% include figure.html file="hlm507_functional_block_diagram.png" alt="HV507" caption="HV507 Functional Block Diagram" src="files/hv507_datasheet.pdf" height="10cm" %}
