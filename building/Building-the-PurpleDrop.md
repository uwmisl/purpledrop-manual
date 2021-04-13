

# Building the PurpleDrop


```{toctree}
:hidden:
:titlesonly:

MylarFilmAssembly/Mylar-Film-Carrier-Assembly
Top-Plate-Preparation
Bootloading-the-PurpleDrop-using-DFU
Electrode-board-designs
```

Building a PurpleDrop requires building the main circuitboard, and the electrode board, which are standard electrical printed cicuit boards (PCBs) and can be built at common PCB fabrication companies. It also requires fabricating the the hydrophobic surfaces for drops to operate on requires which requires some specialized skills and tools. 

## Building the Main Board

The PurpleDrop PCB design can be found at [https://github.com/uwmisl/purpledrop]. The PCB can be built by pretty much any prototype PCB fab. If you have the tools and some SMD soldering skills, it is possible to assemble by hand, however due to the large number of parts -- some of which are fairly small/fine-pitched SMD parts -- you may prefer to have them assembled by a board assembly house.

## Building the Electrode Board

The mainboard has two 64-pin Samtec FTS-132-03-F-DV board-to-board connectors for plugging in a separate electrode board. We typically fabricate the electrode array that the drops operate on as PCBs, although it is also possible to drive other types of electrode arrays, such as patterned chrome or ITO coated glass with an appropriate connection adapter. 

See this [list of electrode board designs](Electrode-board-designs) for some examples of electrode boards, or [creating a custom electrode board]() for a guide on how to create a new design with KiCad.

