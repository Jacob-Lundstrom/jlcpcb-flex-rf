JLCPCB Flexible PCB RF verification
========================
<img src="readme%20images/Single%20Assembly.png" height=480 class="center"><img src="test%20results/board%201/All%20images/B1-2M-YC-L.bmp" height=320 class="center">

## Summary and justification 

This experiment was created to suppliment another one of my projects, to verify and ensure that JLCPCB's Flexible PCBs would be sufficient for rudimentary RF boards.
Looking through JLCPCB's stackups, all flexible PCBs have identical substrate thicknesses, and the thicker boards merely change the copper wight and accompanying adhesive/coverlay. 
Because of this, the lightest copper weight was chosen for this Experiment. The copper weight is a significant limitation; for the given polyimide substrate dk that is 
specified by JLCPCB of 3.3 and the minimal distance of 25 um between copper layers, controlled impedance is exceedingly difficult to achieve (See the Trace Calculations section at 
the end of this README).

An additional reason to perform this experiment is to charactarize the effect of the coverlay material (Specified by JLCPCB at 2.9) on RF performance.
For this reason, I have included both coverlay and coverlay-removed sections for both the 2 mil and 3 mil traces.
Furthermore, this board will be used in combination with other materials, specifically an epoxy resin, to measure their respective effects on performance as well.

There are a plethora of stiffener materials which are not accounted for that JLCPCB offers. These materials may be tested in future experiments but are 
not charactarized in this experiment.

The order for the first round of boards was placed on 6/13, and assembly and testing were performed on 6/25.

## Methodology

PCBs were designed using KICAD 7, and manufactured at JLCPCB. The PCBs had the standard 1/3 oz copper stackup JLCPCB offers, as presented below.

<img src=readme%20images/jlcpcb-flex-stackup.png height=320>

Within the PCB layout, the sections were split up into 8 lanes, with each lane having some small change between each of them. The following parameters were varied between each lane:
- Trace thickness (2mil/3mil)
- Load element type (50 Ohm Load/Chip Antenna)
- Coverlay (Present/Absent)

All data was collected using a LiteVNA, calibrated with the provided calibration standard in the kit at the end of coaxial cables. The cal standards were then removed, and measurments commenced.

For all measurments, the PCBs were placed on a rubber ESD safe mat over a wood bench. Measurements were taken with port 1 of the VNA connecting to the SMA connector furthest from the load element, and 
port 2 connecting to the corresponding SMA closest to the load element.

## Results

From the collected data, it appears that the flexible PCB stackup offered by JLCPCB is insufficient in allowing for proper RF transmission over large distances.
As shown in the preview images, as the frequency of the incident wave increases, the reflection coefficient approaches 1. This causes extremely poor if not zero RF signal
transmission to a load. The observed and presented result was nearly uniform between all trial lanes, with identical data between the two assembled boards.

It is for this purpose that if any RF signals are to be present on a flexible PCB of this stackup, the conducting traces should be kept as short as possible to minimize the effect
of the charactaristic impedance. Traces should therefore follow the rule of thumb to keep total track length a distance of less 1/10th the wavelength of the active frequency.

Additionally, the presence of flesh (bringing my hand closer to the board) resulted with small but noticeable affects; this may indicate that the RF ring project that I'm working on
may be feasible as no significant effects were observed. However, with the additional results indicating poor RF performance in absence of my hand, it may be that it is doomed to fail.

The additional material planned to be tested has not been selected; I am currently in the process of finding a viable epoxy resin to use in the final implementation for the aforementioned
ring project.


## Trace calculations

For a nominal impedance of 50 Ohms, and a copper weight of 0.33 oz, a trace thickness of 1.5411 mils is required as per IPC 2141 specifications.

<img src="readme%20images/0.11%20mm%20stackup%20controlled%20impedance%20trace%20solution.png" width="480" class="center">

JLCPCB's manufacturing limiations require an absolute minimum trace width of 2 mils, with a recommendataion to stay as far away from 2 mils as possible. 
Again following the IPC 2141 calculations, this yields a charactaristic impedance of 42.11 Ohms. This gives a decent VSWR of 1.187, which should be sufficient for short
distance RF signal transmission.

<img src="readme%20images/0.11%20mm%20stackup%20controlled%20impedance%202%20mil%20impedance.png" width="480">

JLCPCB recommends limitation to 3 mil trace widths.
The downside of the larger trace widths is a lower charactaristic impedance and therefore a higher VSWR. 
However, this provides the benefit of manufacturing consistency. It may be more desireable to have guaranteed manufacturability
at the cost of worse performance. This test is aimed at verifying this too. 

Per the IPC 2141 calculations, a 3 mil trace width gives a charactaristic impedance of 28.93 Ohms, and therefore an ideal VSWR of 1.728. 
This performance is much worse, but may just suffice in extremely short distance communication.

<img src="readme%20images/0.11%20mm%20stackup%20controlled%20impedance%203%20mil%20impedance.png" width="480">

Larger copper thickness require proportionally thinner traces, which becomes impossible to manufacture, especially with the 1 oz copper weight. Therefore, if one
hopes to use flexible PCBs with controlled impedances, only the 0.33 oz copper option should be used.
Shown below are the 0.12 mm and 0.2 mm trace thickness calculations respectively.

<img src="readme%20images/0.12%20mm%20stackup%20controlled%20impedance%20trace%20solution.png" width="480"> <img src="readme%20images/0.2%20mm%20stackup%20controlled%20impedance%20trace%20solution.png" width="480">



