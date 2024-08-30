# Electrical Design Documentation

This document contains information on the design process for the electrical portion of the enclosure, notes on working on and editing the files/design, and the parameters that can be changed.

**It should be noted that much of the electronics is actually explained in the Altium schematics. Please read those for very detailed explanations of how the electrical circuitry actually works.** Thus, there will not be any documentation in this document explaining how the boards works.

## Structure of `electrical` Folder

The structure of this folder should be relatively self-exlanatory. Each of the four PCBs has its own Altium PCB Project, containing a schematic file, a layout file, and (with the exception of the Button Board) a populated smart BOM file for convenience. The two integrated libraries `HV_Box_IntLib.IntLib` and `Load_Bank_New_IntLib.IntLib` need to both be installed into your Altium workspace to properly open the files. Apologies for the fact that there's two integrated libraries -- I (Ben) didn't really know how they worked when I started this project so I used both a new integrated library created just for this project as well as components from a previous project I did.

## Schematic Rules and Net Classes

The schematics were made very carefully with a mind towards ease of understanding, good organization, and self-documentation. Generally, logic and power flow from left to right, top to bottom. Each section is demarcated with thick dark red boxes, and with a comment explaining the purpose and various quirks (if any) of that particular section.

Since all the PCBs (except the Button Board) have sections which handle different power regimes that require different clearances in the layout, each net on the boards is assigned a net class:

- "Low Voltage": this net class contains all logic signals and power rails that are referenced to the ground of the 120V-12V AC/DC converter plugged into the wall. The maximum voltage on any of these traces is 12 V.
- "Isolated": this net class contains all logic signals and power rails that have passed through either isolated gate drivers or the isolated power converts, but **do not** directly handle the high voltages and currents associated with the converter under test. The ground reference of these traces is the `JFET_SOURCE` net, i.e. the voltage attached to the source of the JFETs which connect/disconnect the bleeder resistors. The maximum voltage of any of these traces relative to that reference is 12 V, but the isolation barrier can see up to the voltage rating of the enclosure (1 kV), requiring large clearances between this net class and the Low Voltage net class.
- "High Voltage": this net class contains all of the mounting points, copper pours, and jacks which handle the high voltage and current associated with the converter under test. Every net in this net class can see a voltage difference of up to the voltage rating of the enclosure with every other net in the class, so all nets in this class requires large clearances with other members of the High Voltage class, as well as all members of the Isolated and Low Voltage classes

The three net classes are also assigned colors to make them easy to identify in both the schematic and the layout:

- "Low Voltage" class nets and blankets are colored yellow ![yellow](https://placehold.co/15x15/fffe01/fffe01.png)
- "Isolated" class nets and blankets are colored blue ![blue](https://placehold.co/15x15/6e6eff/6e6eff.png)
- "High Voltage" class nets and blankets are colored red ![red](https://placehold.co/15x15/ff6f6f/ff6f6f.png)

## Design Considerations
