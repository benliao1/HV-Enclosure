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

## Connecting to the HV Board/Aux HV Board Phoenix Connectors

The Phoenix connectors that will connect to the ones used on the HV Board and Aux HV Board is the one at [this Digikey link](https://www.digikey.com/en/products/detail/phoenix-contact/1969373/2526720).

## Connecting Additional Current

The current rating of the contactors is 150 A. The banana blugs are rated for 25 A each, and the Phoenix connector is rated for 76 A. Here are the different ways to connect to the board for different current regimes:

- 0 A - 25 A: One set of banana plugs OR the Phoenix connector
- 25 A - 50 A: Both sets of banana blugs OR the Phoenix connector
- 50 A - 76 A: Phoenix connector
- 76 A - 101 A: One set of banana plugs AND the Phoenix connector
- 101 A - 126 A: Both sets of banana plugs AND the Phoenix connector
- 126 A - 150 A: Both sets of banana plugs AND the Phoenix connector AND a thick wire screwed directly to the M6 bolt connected to the contactor terminals

For current greater than 150 A, you will need to replace the contactor with one that can break higher current. Luckily, the manufacturer of the contactor used in the prototype makes contactors with higher rated currents in the same form factor, so that should be a quick swap-in if desired. However, the PCBs were only designed to handle 150 A, so pushing the PCBs past 150 A could result in some overheating in the copper pours.

## Contactors vs. Solid State Breakers

When designing the enclosure, there was a long discussion about whether to use contactors or solid state breakers to break the current between the supply and the converter under test. Solid state breakers are, in theory, better than contactors since they can turn on and off much faster and are cheaper / less bulky than contactors. But, in reality, there are no solid state breakers than can simultaneously block 1 kV and pass 150 A of current; you can only get one or the other. As such, there would need to be two different versions of the enclosure: one for high voltage, low current; and another for low(er) voltage, high current. This has the potential to cause a lot of confusion for the user. Additionally, the on-state resistance of solid-state breakers is typically greater than contactors, and at sufficiently high currents, would need heat sinks and a cooling apparatus to maintain safe operation. These would add a lot of bulk to the high voltage electrical box (comparable to the contactor) and a lot of additional complexity. The final reason that contactors were chosen over solid state breakers was that there was a concern that the contactors would wear out quickly because contactors have a relatively low life if they are constantly breaking high current (i.e. turning off at high current). This is true, but the only time that the contactors in the high voltage enclosure need to turn off at high current is if the user lifts the cover while a test is running (and thus, current is flowing through the contactor from the supply to the converter under test). Presumably, this should happen exceedingly rarely; under normal operation, the contactor stays closed for the entire duration that the system is energized. Thus, the relatively low life of the contactors when subjected to repeated high-curent breaks is of little concern to us.
