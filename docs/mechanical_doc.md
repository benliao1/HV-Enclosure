# Mechanical Design Documentation

This document contains information on the design process for the mechanical portion of the enclosure, notes on working on and editing the files/design, and the parameters that can be changed (for example, to make the box wider or narrower).

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
		- `miscellaneous`: Solidworks part models of miscellaneous components mainly used to connect other components together:
			- Standoffs for holding the PCBs inside the high voltage electrical boxes
			- The handle on the cover
			- The bar attached to the cover which engages with the gate latch on the top shelf (the gate latch is not modeled here, only the bar)
			- The 3D-printed holder for the button board which allows the button board to be precisely placed to detect when the cover is closed

## Design Considerations

This section describes the functional considerations that were taken into account throughout the design process.

- **Weight**: the cover and high voltage electrical boxes cannot be too heavy, since that would put undue stress on the mounting screws attached to the hinge attachment assemblies, especially when the cover is in the raised position
- **Cost**: highly specialized parts were mostly avoided, and the amount of structural material kept to a minimum in an effort to reduce cost
- **Ease of Use**: Spaces were left between the top of the cover and the front of the first shelf above the lab bench, as well as between the side panels of the cover and the lab bench, so that the user can route oscilloscope probes and control wires easily. The high voltage electrical boxes were also fitted with a simple connection to the 120 V AC grid for power, which eliminates the need for attaching a separate power supply to the enclosure.
- **Stability**: The cover is designed to be stable in the raised position; i.e. the cover will stay in the raised position by resting against the top shelf. The gate latch is not needed to keep it in the top position, but for greater safety and insurance that the cover won't fall down unexpetedly, it's still advised to latch the cover whenever it is in the raised position
- **Electrical Insulation**: Since there will be high voltage and current flowing through the high voltage electrical boxes, is is undesirable to openly expose the conducting surfaces of the high voltage boards and bleed resistors. The electrical boxes were designed to enclose the high voltage boards on five sides (with the underside of the first shelf forming the sixth side), protecting them from foreign objects as well as confining the high voltage to that small volume. In the event that a wire inside the box somehow breaks loose, the wire will not touch a piece of metal and energize the cover itself (unless it accidentally touches the tips of one of the bolts holding the acrylic to the metal box structure).

## Creating New 20 Series Profile Lengths

To makes a new 20 series beam length in Solidworks, go to `mechanical/parts/2020` and open `2020_base.SLDPRT`. Click on the Boss Extrude feature and edit the extrusion length as desired. Save the edited part as a new file and name it following the naming convention: `2020_<length>` where the length is in cm. For example, `2020_100` is 100 cm long. Lengths with decimals have dashes in replace of the period, e.g. `2020_25-4` for a beam 25.4 cm long.

## Nylon Spacers

Nylon spacers were used to separate the heat sinks and the acrylic panels because nylon has a higher melting temperature than acrylic and also resists thermal deformation below the melting temperature. Thus, in the event the bleed resistors and their heat sinks get extremely hot in an extreme use case, the nylon spacers will hopefully prevent the heat sinks from heating up the acrylic panels so much that they deform or otherwise cause structural damage to the high voltage electrical boxes.

## Allowable Dimension Adjustments

The height of the enclosure cannot be easily changed as the angle the cover makes with the lab bench is set; changing the height of the enclosure (i.e. the distance between the first shelf and the lab bench) would require changes to both the height and width of the cover as well as the non-right angle in the acrylic cover side panel.

### Enclosure Width

To change the width of the enclosure, the following items need to be edited:

- The length of the 20 series beams at the top and bottom of the cover
- The width of the acrylic top panel of the cover
- The length of the 20 series beam holding up the high voltage electrical boxes

All of these should be modified by the same length.

### Length Enclosure Extends Underneath First Shelf

If the supports for the enclosure interfere with the placement of lights underneath the first shelf, the following can be shortened to make room:

- The length of the 20 series beam in the hinge assemblies holding the enclosure to the bottom of the shelf

It is probably best to leave this beam to be as long as possible, as a longer beam provides better support. To make this distance even shorter, it may be necessary to modify the dimensions of the high voltage electrical boxes or turn them 90 degrees to mount them lengthwise along the aluminum bar.
