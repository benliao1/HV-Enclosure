# High Voltage Enclosure

This Github repo contains all of the design files (both mechanical and electrical) as well as extensive documentation for the high voltage safety enclosure. It is meant to be living and not used simply as a reference. Any updates to the design should be uploaded to the Github, along with any necessary updates to the documentation files. Keeping these files up-to-date is important, especially since new high voltage enclosures or maintenance / part replacement on existing enclosures may require the files to be used again at any given time (unlike former research projects, which will be used as references but more likely than not will never be built again).

## Overview

The high voltage safety enclosure is an assembly designed to protect someone in the event of a catastrophic mechanical failure of a converter under test or improper use of electrical equipment during a test which would otherwise result in the possibility of the person touching something at high voltage. Thus, the enclosure consists of the following parts:

- A **cover** which can be lowered to cover a portion of the lab bench and raised to allow access to the test setup
- A **latching mechanism** which holds the cover in the raised position
- A **button assembly** which detects when the cover is open or closed and which drives the electrical components of the enclosure
- An **HV Electrical Box** which contains electronics to operate the high voltage contactors and bleeder resistors on the input side of the converter under test
- An **Auxiliary HV Electrical Box** which is an __optional__ assembly containing electronics to operate bleeder resistors on the output side of the converter under test

The cover protects against catastraphic mechanical failure and against unintentional contact between a foreign object and the converter under test. The electrical boxes and button assembly ensure that the converter under test can only be energized (i.e. connected to the power supply) when the cover is down; when the cover is up, bleeder resistors are automatically connected across the input to bleed any large input capacitors that may be energized (and, if the auxiliary HV Electrical Box is used, bleeder resistors are automatically connected across the output to bleed any large output capacitors as well).

## Repository Structure

The following is a brief overview of where to find various files and components in this repository.

- The **mechanical** folder contains all of the CAD models of nearly every component used in the mechanical portion of the HV enclosure. Since the enclosure was designed in Solidworks, all CAD files are `.sldprt`, `.sldasm`, or `.step` files. Notably, this folder does **not include** any bolts, nuts, or L brackets used in the cover, and does **not include** the gate latch used in the latching mechanism. Below is a list of the kinds of files that can be found here:
	- All 8020 beams used in the cover and electrical boxes
	- All acrylic pieces used in the cover and electrical boxes
	- 3D exported renderings of the various PCBs in the design
- The **electrical** folder contains all of the Altium component libraries, schematics, and layouts for the various PCBs designed for the HV enclosure. Below is a list of the PCBs used in the design:
	- **Main Board**: this board connects to the incoming 12 V DC supply from the wall, sends power to the other boards, operates the contactors, sends signals to operate the bleeder resistors, receives the signal from the button detecting when the cover is closed or not, and displays the state of the system to the user.
	- **HV Board**: this board connects the power supply and the converter under test. It contains the high-voltage JFETs that connect/disconnect the bleeder resistors across the input of the converter, as well as mounting holes for the contactors which electrically connect/disconnet the power supply from the converter under test.
	- **Auxiliary HV Board**: this board connects the converter under test with the load. It contains high-voltage JFETs that connect/disconnect the bleeder resistors across the output of the converter.
	- **Button Board**: this board houses the lever switch which detects when the cover is closed, which is sent to the Main Board.
- The **docs** folder contains more documentation and useful reference material:
	- BOMs for the mechanical and electrical components used in the HV enclosure (as well as suppliers of these components)
	- Assembly instructions for the HV enclosure
	- Documents describing what needed to be considered and what principles were followed throughout the design process
	- All photos and screenshots used in the repository

## Quick Specifications

The following is a list of the most important specifications of the system as designed in the first prototype:

- Rated voltage: 1000 V
- Rated current (banana plugs): 25 A per plug
- Rated current (Phoenix connector): 75 A per pin
- Bleeder resistor value: 4x 390 Ohms in parallel (total 97.5 Ohms)
- Bleeder resistor power ratings: 100 W per resistor (continuous, with heat sink); 12.5x overload for 2 seconds
	- Maximum power dissipation is 5 kW for 2 seconds across entire resistor bank - appoximately enough to discharge 10 mF of input capacitance at 1000 V, reducing the voltage on the input bus below 100 V in a little over 2 seconds (see [datasheet](https://www.te.com/commerce/DocumentDelivery/DDEController?Action=srchrtrv&DocNm=1773035&DocType=DS&DocLang=English), page 3 "Power Overload" graph for details)

## Credits

First prototype designed and assembled by Ben Liao in late 2023 to mid-2024 (completed August 2024). Contributors to the this first iteration included Logan Horowitz, Nathan Biesterfeld, Nathan Miles Ellis, and Robert Pilawa.
