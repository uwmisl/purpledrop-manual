

# Building the PurpleDrop


```{toctree}
:hidden:
:titlesonly:

MylarFilmAssembly/Mylar-Film-Carrier-Assembly
Top-Plate-Preparation
Bootloading-the-PurpleDrop-using-DFU
Designing-Custom-Electrode-Board
Electrode-board-designs
```

Building a PurpleDrop requires building the main circuitboard, and the electrode board, which are standard electrical printed cicuit boards (PCBs) and can be built at common PCB fabrication companies. It also requires fabricating the the hydrophobic surfaces for drops to operate on requires which requires some specialized skills and tools. 

## Building the Main Board

The PurpleDrop PCB design can be found at [https://github.com/uwmisl/purpledrop]. The PCB can be built by pretty much any prototype PCB fab. If you have the tools and some SMD soldering skills, it is possible to assemble by hand, however due to the large number of parts -- some of which are fairly small/fine-pitched SMD parts -- you may prefer to have them assembled by a board assembly house.

## Building the Electrode Board

The mainboard has two 64-pin Samtec FTS-132-03-F-DV board-to-board connectors for plugging in a separate electrode board. We typically fabricate the electrode array that the drops operate on as PCBs, although it is also possible to drive other types of electrode arrays, such as patterned chrome or ITO coated glass with an appropriate connection adapter. The electrode board typically has only a few components, including the two connectors that mate with the main board, so the PCB can be assembled by hand much more easily than the main board.

See this [list of electrode board designs](Electrode-board-designs) for some examples of electrode boards, or [creating a custom electrode board](Designing-Custom-Electrode-Board) for a guide on how to create a new design with KiCad.

## Other components

See the pages on the navigation menu for further instructions on how to build other parts such as the hydrophobic dielectric film and top plate.