# Top Plate Preparation

An ITO coated piece of glass is used as the top plate to enclose the droplets. It must be prepared with a hydrophobic coating, tape spacers to maintain the gap between the top plate and the dielectric, and copper tape for making electrical contact to the ITO.

## Materials

- **ITO Coated Glass Plate**

	The thickness is not critical, and the exact dimensions may depend on your use case. Some examples typically used are: 
	
	- 50x50x1.1mm - Adafruit P/N 1310

	- 50x75x1.1mm - Delta Technologies P/N CB-90IN-S211

- **6mm copper tape with conductive adhesive**

- **Cytonix Fluoropel PFC1101V** (https://cytonix.com/products/1101v-fs_25-grams)

	Alternatively, Teflon AF1600 solution is known to be a good hydrophobic coating for this application, and seems to provide better resistance to fouling in the presence of proteins or streptavidin beads. 

- **Single-pin rectangular receptacle and small wire**

    For soldering onto the copper tape and connecting the top plate to the electronics.

## Tools

- Pipette capable of dispensing 400uL
- Tweezers
- Spin coater
- Oven or hot plate

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

### Attach spacers

Spacers can be used to control the distance between the top-plate and the mylar film surface. The gap size can be varied by adjusting the thickness of the spacers used. A typical gap size used with PurpleDrop is in the range of 0.2 to 0.4mm. To support larger volumes, a larger gap can be used (e.g. 2-3mm), but the splitting of drops will become impossible to achieve. 

There are multiple options options for spacers/shims for the top plate. One option that works well is kapton tape. The tape is thin (available as thin as 0.025mm, but it varies) and can be layered to achieve different thicknesses. 

To construct kapton spacers, multiple layers of tape can be stacked, and small squares can then be cut out of the stack and placed onto the top plate (on the ITO side). 

While placing the spacers, it is important to carefully avoid touching the active area of the top plate. The hydrophic coating can be easily damaged, and this can result in drops being unable to move past certain spots on the surface. 

```{figure} images/top-plate-assembly/top_plate_2.png
:align: center

Top plate with spacers
```

### Re-coating

If your surface becomes fouled or damaged, you can generally re-use a top plate by cleaning it well and re-coating. 
