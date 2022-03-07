

# Building the PurpleDrop


```{toctree}
:hidden:
:titlesonly:

Bootloading-the-PurpleDrop-using-DFU

```

Building a PurpleDrop requires building the main circuitboard, and at least one
electrode board, which are standard electrical printed cicuit boards (PCBs)
which can be built by common PCB fabrication companies. It also requires
fabricating the the hydrophobic surfaces for drops to operate on requires which
requires some specialized skills and tools. This section is about the main
circuit boards, for instructions on how to assemble the drop surfaces, see
[](/building-dmf-surface/index).

## Building the Main Board

The PurpleDrop PCB design can be found at [https://github.com/uwmisl/purpledrop]. The PCB can be built by pretty much any prototype PCB fab from the gerber files. If you have the tools and some SMD soldering skills, it is possible to assemble by hand, however due to the large number of parts -- some of which are fairly small SMD parts -- you may prefer to have them assembled by a board assembly shop.

## Building the Electrode Board

The mainboard has two 64-pin Samtec FTS-132-03-F-DV board-to-board connectors for plugging in a separate electrode board. We typically fabricate the electrode array that the drops operate on as PCBs, although it is also possible to drive other types of electrode arrays, such as patterned chrome or ITO coated glass with an appropriate connection adapter. The electrode board typically has only a few components, including the two connectors that mate with the main board, so the PCB can be assembled by hand much more easily than the main board.

See this [list of electrode board designs](Electrode-board-designs) for some examples of electrode boards, or [creating a custom electrode board](Designing-Custom-Electrode-Board) for a guide on how to create a new design with KiCad.
