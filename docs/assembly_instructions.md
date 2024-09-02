# Assembly Instructions

This document attempts to walk through the process of assembling the system with visuals. The hope is that this document can clarify any confusion there may be for where certain screws are placed, as well as offer some tips on how to assemble the structure.

## General Notes

- The economy T square nuts used for the 8020 pieces must be inserted before the channel that is cut into the 8020 profile that holds them in place is closed (i.e. they are not roll-in nuts). Before securing two 8020 profiles together, make sure all of the required T nuts have been placed in the profile. A small allen key can be very useful to move the T nuts within the profile so that they line up with holes in the acrylic or L brackets.
- M5-0.8 8mm screws are used to connect the L brackets with the 20 series beams.
- M5-0.8 10mm screws are used to connect the acrylic panels with the 20 series beams.
- **Do not** overtighten screws and nuts that hold acrylic to the 20 series beams. The acrylic will crack! The acrylic is not a structurally important part of the cover by design, so the bolts do not need to be overtightened. Tighten until snug and that should be fine.
- **Do** tighten the screws and nuts holding the L brackets to the 20 series beams. These are the most structurally important connections; tighten until snug and then give it another quarter-turn or so.

## Step 1: Building the PCBs

For the Main Board, use the reflow oven with normal settings, nothing too special here.

The HV Board and Aux HV Board have four layers of large and thick copper pours across the entire board, making it very difficult to solder. Make sure to reflow these boards for much longer than normal. Consider reflowing them with the banana plugs and Phoenix connectors on the board as well, since it is very difficult to solder them to the board when the board is cold.

The Button Board should be assembled by hand. Ensure that the lever switch is oriented in the correct direction (with the "hinge" of the lever closest to the JST connector) and flat against the PCB.

## Step 2: The Cover

Assemble the section shown in the image below, with annotations indicating the lengths of the 20 series beams (in red), the locations of the 4 L brackets (in blue), and the locations of the M5 bolts that are bolted into the cover top acrylic panel (in green). The purple arrows indicate the locations of the holes where the side panels are to be screwed in. The purple circle indicate the locations of 4 T nuts that need to inserted into the back of the top 100 cm beam which will accomodate the screws for the hinges in a later step.

![cover-diagram](https://raw.githubusercontent.com/benliao1/HV-Enclosure/master/docs/screenshots/cover.png)

Assemble the two hinge assemblies, connect them with the electronics support bar, and attach the button board assembly as shown in the annotated image below. The 3D-printed button board holder should be connected to the 15 cm beam with 10mm M5 bolts. Use the #3-56 bolts to secure the Button Board to the button board holder into the top and bottom holes of the button board holder (the three middle holes are for the 3 leads of the lever switch). The lengths of the beams are annotated on the diagram, along with the locations of the L brackets. The purple circles indicate the locations of T nuts for connection with the electrical boxes later; four on the front of the beam, and four on the back of the beam. Make sure that you use 4 M5-0.8 10mm **flat-head screws** to attach the hinges to the the 6 cm beams.

![hinge-assembly-diagram](https://raw.githubusercontent.com/benliao1/HV-Enclosure/master/docs/screenshots/hinge_assembly.png)

Connect the hinge assembly to the cover with the remaining M5-0.8 10mm **flat-head screws**. Step 2 is complete when the assembly looks like the image below.

![cover-assembly-complete](https://raw.githubusercontent.com/benliao1/HV-Enclosure/master/docs/screenshots/cover_assembly_complete.png)

## Step 3: The High Voltage Electrical Box

Assemble the two bleeder resistor assemblies. The Aluminum L brackets from McMaster come with screws and nuts; these can be used for the holes that point downwards, but the shorter 1/4"-20 screws bought separately from McMaster must be used for the holes that point horizontally. Similarly, the longer #8-32 screws should be used to attach the bottom resistors to their heat sinks, but the shorter 8-32 screws should be used to attach the side resistors to their heat sinks. This is annotated in the diagram below:

![hv-board-bleeder-resistor-assembly-diagram](https://raw.githubusercontent.com/benliao1/HV-Enclosure/master/docs/screenshots/hv_board_bleeder_resistor_assembly.png)

Attach the bleeder resistor assemblies to the bottom acrylic panel. Ensure that there are nylon spacers between the bottom heat sink and the top of the acrylic panel, and another nylon spacer between the bottom of the acrylic panel and the nut on the end of the screw. Large nylon spacers are used for the 1/4"-20 screws; small nylon spacers are used for the #8-32 screws. When finished with this step, the box should look like this:

![hv-electrical-box-1](https://raw.githubusercontent.com/benliao1/HV-Enclosure/master/docs/screenshots/hv_electrical_box_1.png)

Attach the contactors to the bottom acrylic panel. Use #8-32 screws (no nylon spacers necessary). Note the direction the contactors are placed (the port for the contactor connection accessory should be on the left side, looking from the front of the box). Leave some play in the screws so that the position of the contactors can be adjusted to fit the HV Board PCB. Attach the four #4-40 3" standoffs to the bottom panel as well with #4-40 screws. When finished with this step, the box should look like this:

![hv-electrical-box-2](https://raw.githubusercontent.com/benliao1/HV-Enclosure/master/docs/screenshots/hv_electrical_box_2.png)

Solder the wires connecting the bleeder resistors together on both sides, and that connect the bleed resistors up to the HV Board. These wires are 12 gauge. The wire that connects from the bleed resistor up to the HV board needs to have a ring terminal on one end big enough to accomodate an M6 bolt. The M6 bolt will be screwed through the hole in the HV Board PCB and secured in place by a nut. Afterwards, put the HV Board PCB on top of the four standoffs and secure it in place with #4-40 screws. Insert M6 bolts into the mounting locations for the contactors, screw on a nut onto each bolt, then screw the bolt into the threaded hole in the contactor. When the head of the bolt touches the top surface of HV Board PCB, stop turning the bolt into the contactor (as this would bend the PCB). To secure the bolt, turn the nut that you put on earlier counterclockwise when looking from above up towards the underside of the PCB. Tighten the nut. Finally, lock the contactors in place by tightening down the #8-32 screws holding them to the bottom acrylic panel. When finished with this step, the box should look something like the pictures below, with the wires drawn on as an example:

Right view:
![hv-electrical-box-3-right](https://raw.githubusercontent.com/benliao1/HV-Enclosure/master/docs/screenshots/hv_electrical_box_3_right.png)

Left view:
![hv-electrical-box-3-left](https://raw.githubusercontent.com/benliao1/HV-Enclosure/master/docs/screenshots/hv_electrical_box_3_left.png)

Attach the contactor connector accessories to the Main Board PCB, then attach the Main Board PCB to the acrylic front panel using the two #4-40 1" standoffs and #4-40 screws. Then, insert the contactor connector accessories into the ports on the side of the contactors. When finished with this step, the box should look something like this (of course, the front panel will not stand on its own like in the picture; you can lay it face-down for now):

![hv-electrical-box-4](https://raw.githubusercontent.com/benliao1/HV-Enclosure/master/docs/screenshots/hv_electrical_box_4.png)

Push the head of the barrel jack output of the 120V-12V AC-DC converter through the large hole in the acrylic back panel and pull it through. Attach it to the Main Board PCB. Now, the box should look something like this (again, the front and back panels will not stand on their own like in the picture; you can lay both of the face-down for now):

![hv-electrical-box-5](https://raw.githubusercontent.com/benliao1/HV-Enclosure/master/docs/screenshots/hv_electrical_box_5.png)

Assemble the two side panels. They are mirror images of each other. Remember the 20 series aluminum beams go on the **outside** of the box! There are no L brackets that hold the aluminum beams together; these aluminum beams simply provide a place for all of the different panels to screw into. Below is an annotated diagram of one side panel. Beam lengths are called out in red. Green circles indicate positions of T nuts for accomodating the bolts which secure the acrylic panel to the beams. Purple circles indicate positions of T nuts for accomodating the bolts which secure various other components to the beams (which will be used in later steps).

![hv-electrical-box-side-panel](https://raw.githubusercontent.com/benliao1/HV-Enclosure/master/docs/screenshots/hv_electrical_box_side_panel.png)

Attach the two side panels to the bottom panel, securing them in place with six screws from the bottom. Then, attach the front and back panels, securing them in place with four screws from the front, and four screws from the back. Below is a diagram showing the screws needed to secure the side panels to the bottom panel (in green, should be done first), and the screws to secure the front and back panels to the beams (in purple, should be done second):

![hv-electrical-box-6](https://raw.githubusercontent.com/benliao1/HV-Enclosure/master/docs/screenshots/hv_electrical_box_6.png)

This completes Step 3.

## Step 4: The Auxiliary High Voltage Electrial Box

Assemble the bleeder resistor assembly. Attach the bleeder resistors to the head sink and the heat sink to the bottom panel using #8-32 screws. Ensure that there are nylon spacers between the bottom of the heat sink and the top of the acrylic panel, and between the bottom of the acrylic panel and the #8-32 nut. When completed, the assembly should look like this:

![aux-hv-electrical-box-1](https://raw.githubusercontent.com/benliao1/HV-Enclosure/master/docs/screenshots/aux_hv_electrical_box_1.png)

Attach the four #4-40 2" standoffs to the bottom panel using #4-40 screws. When completed, the assembly should look like this:

![aux-hv-electrical-box-2](https://raw.githubusercontent.com/benliao1/HV-Enclosure/master/docs/screenshots/aux_hv_electrical_box_2.png)

Solder the wires connecting the bleeder resistors together on both sides, and that connect the bleed resistors up to the Aux HV Board. The wire gauge and the method that they are attached to the Aux HV Board is the same as for the HV Board in Step 3. Put the Aux HV Board on top of the standoffs and bolt down the M6 bolts that attach the Aux HV Board to the ring terminal connected to the bleed resistor wires. When finished, the box should look like the pictures below, with wires drawn on as an example:

Right view:
![aux-hv-electrical-box-3-right](https://raw.githubusercontent.com/benliao1/HV-Enclosure/master/docs/screenshots/aux_hv_electrical_box_3_right.png)

Left view:
![aux-hv-electricral-box-3-left](https://raw.githubusercontent.com/benliao1/HV-Enclosure/master/docs/screenshots/aux_hv_electrical_box_3_left.png)

Assemble the two side panels. They are mirror images of each other. Remember the 20 series aluminum beams go on the **outside** of the box! There are no L brackets that hold the aluminum beams together; these aluminum beams simply provide a place for all of the different panels to screw into. Below is an annotated diagram of one side panel. Beam lengths are called out in red. Green circles indicate positions of T nuts for accomodating the bolts which secure the acrylic panel to the beams. Purple circles indicate positions of T nuts for accomodating the bolts which secure various other components to the beams (which will be used in later steps).

![aux-hv-electrical-box-side-panel](https://raw.githubusercontent.com/benliao1/HV-Enclosure/master/docs/screenshots/aux_hv_electrical_box_side_panel.png)

Attach the two side panels to the bottom panel, securing them in place with six screws from the bottom. Then, attach the front and back panels, securing them in place with four screws from the front, and four screws from the back. Below is a diagram showing the screws needed to secure the side panels to the bottom panel (in green, should be done first), and the screws to secure the front and back panels to the beams (in purple, should be done second):

![aux-hv-electrical-box-4](https://raw.githubusercontent.com/benliao1/HV-Enclosure/master/docs/screenshots/aux_hv_electrical_box_4.png)

This completes Step 4.

## Step 5: Connecting the Electrical Box(es) to the Cover

Attach the boxes to the beam on the cover using the gusseted L brackets without guides from 8020.net. Below is an annotated diagram showing where the L brackets go:

![boxes-to-beam-diagram](https://raw.githubusercontent.com/benliao1/HV-Enclosure/master/docs/screenshots/boxes_to_cover_beam.png)

This completes Step 5. The finished cover can now be mounted to the desk, and a gate latch fitted in a suitable place on the top shelf.
