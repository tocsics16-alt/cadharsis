# cadharsis
A tool that can generate KiCad compatible footprints and symbols from .cad boardview files. 

Hey! 

I made a tool, which can be used to generate KiCad compatible footprints and symbols from .cad boardview files, mainly with BGA chips in focus.
_I have NOT found anything similiar to this on the internet._
**It could save you weeks and months.**

Footprints and symbols can be used to make your own schematics, PCBs, stencils, and whatever else pops in your mind.

The initial idea came when I saw [this guy build his own Ryzen based SBC](https://www.youtube.com/watch?v=9TmLN8_jEKs) from scratch, then I saw [this guy make his own BGA stencil](https://www.youtube.com/watch?v=GkDnh_v5iBM) from some pictures and measurements and realized how useful a tool like this could be for people in this field.

---

### How it works to generate a symbol

_For this example I'm going to use an intel 8th gen SoC chip._

Open the .cad boardview file containing the component you want to export as a KiCad symbol.

Enter the component reference (for example, in the boardview I used, the CPU reference is UC1) into the Component Marking field, then click Analyze. The program will automatically read all pins belonging to the selected component, including their pin numbers and pin names.

<img width="401" height="367" alt="151950_1775143189927_cad1 png" src="https://github.com/user-attachments/assets/82ecddf2-0afc-459d-b6ec-69234e5a24a3" />

- The Component Netlist section displays every pin detected for the selected component.
- Under Grouping by Prefixes, you can choose whether pins sharing the same prefix should be grouped into separate symbol units. This results in a much cleaner schematic. For example, all pins starting with PCH_ can be placed into their own dedicated unit, separated from the remaining pins.
- The Pins per Misc Unit option determines the maximum number of pins placed into each miscellaneous unit (pins that are not grouped by a prefix). Lower values create more units with fewer pins each.
- You can also specify the desired symbol width.
- Once everything is configured, simply generate and save the symbol file.
- The generated symbol can then be imported directly into KiCad.

Below is an example of a PCH_ grouped unit containing all pins whose names begin with PCH_:


<img width="960" height="510" alt="153205_1775143925146_cad1 png" src="https://github.com/user-attachments/assets/26f6d8e7-0f1f-425f-89b8-5b860144c729" />


And here is an example of a Misc unit with a limit of 100 pins per unit:


<img width="960" height="510" alt="153351_1775144031092_cad2 png" src="https://github.com/user-attachments/assets/9e6c6c2f-7740-40a5-a749-50e6cc3f0088" />


The program automatically assigns each pin its correct pin number and pin name.

**Generate a complete KiCad symbol in seconds instead of manually recreating hundreds or even thousands of pins.**

---

### How it works to generate a footprint

_For this example I'm going to use an intel 8th gen SoC chip._

Open the .cad boardview file containing the component you want to export as a KiCad footprint.

Enter the component reference (for example, in the boardview I used, the CPU reference is UC1) into the Component Marking field, then click Analyze. The program will automatically read all pins belonging to the selected component, including their pin numbers and physical locations.

<img width="400" height="366" alt="153906_1775144345788_cad3 png" src="https://github.com/user-attachments/assets/d381ce8b-d536-4cc3-bb40-a988e721e7a7" />

- A preview of the generated footprint is displayed on the left side of the window.
- You can choose whether to generate BGA pads and specify their diameter (in my example, 0.45 mm). If the BGA option is disabled, the program automatically generates 0.2 × 0.2 mm square pads instead.
- Once the settings are configured, simply generate and export the footprint.
- The generated footprint can then be imported directly into KiCad.

<img width="960" height="510" alt="154639_1775144799379_cad4 png" src="https://github.com/user-attachments/assets/56341ad9-db2f-4b19-8dee-2b104ad04a27" />

The program automatically assigns the correct pin numbers to every generated pad.

**This provides a ready-to-use footprint as a starting point, eliminating the need to manually place and number hundreds or even thousands of pads.**

---

### Notes

- This program can be seen as an MVP, that is fully functional, but it can also be used as an idea, so you can make a better tool if you need it.
- The program can only use .cad boardview files.
- The generated dirty files might need some manual corrections, since it's heavily dependent on the boardview files.

The tool is completely free, but if you found it helpful, [you can donate](https://buymeacoffee.com/dominikmuhelye) which is highly appreciated.

