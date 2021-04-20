# Top Plate Preparation

An ITO coated piece of glass is used as the top plate to enclose the droplets and provide the "common" electrode. It must be prepared with a hydrophobic coating, tape spacers to maintain the gap between the top plate and the dielectric, and copper tape for making electrical contact to the ITO.

## Materials

- **ITO Coated Glass Plate**

	The thickness is not critical, and the exact dimensions may depend on your use case. Some examples typically used are: 
	
	- 50x50x1.1mm - Adafruit P/N 1310

	- 50x75x1.1mm - Delta Technologies P/N CB-90IN-S211

- **6mm copper tape with conductive adhesive**

- **Cytonix Fluoropel PFC1101V** (<https://cytonix.com/collections/electrowetting/products/1101v>)

	Alternatively, Teflon AF1600 solution is known to be a good hydrophobic coating for this application, and seems to provide better resistance to fouling in the presence of proteins or streptavidin beads. 

- **Single-pin rectangular receptacle and small wire**

    For soldering onto the copper tape and connecting the top plate to the electronics. These connectors are readily available as prototyping jumper wires, for example [here](https://www.digikey.com/en/products/detail/adafruit-industries-llc/4447/11503291).

## Tools

- Pipette capable of dispensing 400uL
- Tweezers
- Spin coater
- Oven or hot plate
- Soldering station
- Wire cutters/strippers

## Procedure

### Clean ITO side of glass

First, identify which side of the glass is ITO coated using a multimeter to measure resistance; the ITO side will be conductive. 

Clean the surface. You can use isopropyl alcohol and kim wipes, or an ultrasonic bath, if available.

### Place the copper tape

Apply the copper tape over one edge of the ITO glass, so that it folds over approximately equally onto both sides of the glass. The copper tape will provide a conduction path from the ITO to the opposite side of the glass for connection later.

### Spin coat

Place the ITO glass into a spin coater, with the ITO coating face up. Spin at 1000RPM, and apply ~400uL of FPC1101V while spinning using a pipette. Allow to spin for 30 seconds after application. 

### Bake

Remove the glass from the spin coater, being careful not to disturb any active areas of the coating, and place it into an oven -- or on a hot plate -- to bake at 120C for 30 minutes. 

### Solder connector

The connecting wire should be soldered onto the copper tape, on the top (non ITO covered) side of the glass plate. 

```{figure} images/top-plate-assembly/top_plate_1.png
:align: center

Top plate with attached wire
```

Here, you can see that the relatively large guage wire that comes with the jumper was cut off, and a small (34AWG) enamel coated wire (sometimes called "magnet wire") was spliced on to replace it. 
It's helpful to use a small, flexible wire here, as this limits the force the wire will exert on the top plate.

### Attach spacers

Spacers can be used to control the distance between the top-plate and the mylar film surface. The gap size can be varied by adjusting the thickness of the spacers used. A typical gap size used with PurpleDrop is in the range of 0.2 to 0.4mm. To support larger volumes, a larger gap can be used (e.g. 2-3mm), but the splitting of drops will become impossible to achieve. 

There are multiple options that can work for spacers/shims under the top plate. But one simple option that works well is kapton tape. The tape is usually thin (available as thin as 0.025mm, but it varies) and can be layered to achieve different thicknesses. 

To construct kapton spacers, multiple layers of tape should be stacked to the 
desired thickness, and small squares can then be cut out of the stack and placed
onto the top plate (on the ITO side). Here it's useful to re-use the backer from 
the 3M adhesive sheets used to bond the mylar film when building the dielectric
carrier, as it has a low surface energy and will peel away from the tape more 
easily.

```{figure} images/top-plate-assembly/kapton-spacer.jpg
:align: center

Multiplate layers of kapton tape layered onto adhesive backing paper, ready to be cut into small shims for top plate
```

While placing the spacers, it is important to avoid touching the active area of the top plate. The hydrophic coating can be easily damaged, and this can result in drops being unable to move past certain spots on the surface. 

```{figure} images/top-plate-assembly/top_plate_2.png
:align: center

Top plate with spacers
```

### Re-coating

If your surface becomes fouled or damaged, you can generally re-use a top plate by cleaning it well and re-coating.
