# Mechanical Design Documentation

This document contains information on the design process for the mechanical portion of the enclosure, notes on working on and editing the files, and the parameters that can be changed (for example, to make the box wider or narrower).

## Structure of `mechanical` Folder

To access the assembly, it is recommended to start by opening the `mechanical/full_model.SLDASM` file. Right clicking on indivisual components and selecting "Open Part" or "Open Subassembly" allows you to open additional components in the assembly. If you want to open individual components directly, the structure of the `mechanical` folder is as follows:

- `mechanical`: root directory
	- `full_model.SLDASM`: complete model of the enclosure along with desk and instruments for comparison. The cover can be moved up and down in this model by clicking and dragging it up and down.
	- `desk_and_instrument_models`: models of the desk, shelves, large DC power supply, large electronic load, and typical oscilloscope used in the full model.
	- `subassemblies`: various subassembly files that together make up the full model. This includes the cover and the electronics (which itself is made up of multiple subassemblies)
	- `parts`: all of the `.SLDPRT` files that makes up the enclosure.
		- `2020`: Solidworks part models of 20 series aluminum profile beams from [8020.net](8020.net) of various sizes, along with a drawing of the cross section and a base model (which can be copied and modified to create additional beam lengths should they be needed).
		- `acrylic`: Solidworks part models of all the acrylic pieces used in the cover and both the HV Electrical Box and the Auxiliary HV Electrical Box.
		- `bleed_resistor_parts`: Solidworks part models of the various components used to hold the bleed resistors and their aluminum heat sinks to the electrical boxes. This includes the nylon spacers and large L brackets.
		- `contactor_parts`: Solidworks part models of the contactor and the electrical connector used to operate the contactor coil
		- `miscellaneous`: Solidworks part models of miscellaneous components mainly used to connect other components together. These include:
			- Standoffs for holding the PCBs inside the high voltage electrical boxes
			- The handle on the cover
			- The bar attached to the cover which engages with the gate latch on the top shelf (the gate latch is not modeled here, only the bar)
			- The 3D-printed holder for the button board which allows the button board to be precisely placed to detect when the cover is closed

## 