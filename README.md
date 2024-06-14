JLCPCB Flex verification

This experiment was created to suppliment another one of my projects, to verify and ensure that JLCPCB's Flexible PCBs would be sufficient for rudimentary RF boards.
Looking through JLCPCB's stackups, all flexible PCBs have identical substrate thicknesses, and the thicker boards merely change the copper wight and accompanying adhesive/coverlay. 
Because of this, the lightest copper weight was chosen for this Experiment. The copper weight is a significant limitation; for the given polyimide substrate dk that is 
specified by JLCPCB of 3.3 and the minimal distance of 25 um between copper layers, controlled impedance is exceedingly difficult to achieve. For a nominal impedance of
50 Ohms, and a copper weight of 0.33 oz a trace thickness of 1.5411 mils is required, as per IPC 2141 specifications.

![Alt text](readme%20images/0.11%20mm%20stackup%20controlled%20impedance%20trace%20solution.png "Width Solution For 50 Ohm Impedance on 0.11mm Flex PCBs")

JLCPCB's manufacturing limiations require an absolute minimum trace width of 2 mils, with a recommendataion to stay as far away from 2 mils as possible. 
Again following the IPC 2141 calculations, this yields a charactaristic impedance of 42.11 Ohms. This gives a decent VSWR of 1.187, which should be sufficient for short
distance RF signal transmission.

![Alt text](readme%20images/0.11%20mm%20stackup%20controlled%20impedance%202%20mil%20impedance.png "2 mil Charactaristic Impedance Calculation on 0.11mm Flex PCBs")

JLCPCB recommends limitation to 3 mil trace widths.
The downside of the larger trace widths is a lower charactaristic impedance and therefore a higher VSWR. 
However, this provides the benefit of manufacturing consistency. It may be more desireable to have guaranteed manufacturability
at the cost of worse performance. This test is aimed at verifying this too. 

Per the IPC 2141 calculations, a 3 mil trace width gives a charactaristic impedance of 28.93 Ohms, and therefore an ideal VSWR of 1.728. 
This performance is much worse, but may just suffice in extremely short distance communication.

![Alt text](readme%20images/0.11%20mm%20stackup%20controlled%20impedance%203%20mil%20impedance.png "3 mil Charactaristic Impedance Calculation on 0.11mm Flex PCBs")


Larger copper thickness require proportionally thinner traces, which becomes impossible to manufacture, especially with the 1 oz copper weight. Therefore, if one
hopes to use flexible PCBs with controlled impedances, only the 0.33 oz copper option should be used.
Shown below are the 0.12 mm and 0.2 mm trace thickness calculations respectively.

![Alt text](readme%20images/0.12%20mm%20stackup%20controlled%20impedance%20trace%20solution.png "Title")
![Alt text](readme%20images/0.2%20mm%20stackup%20controlled%20impedance%20trace%20solution.png "Title")


An additional reason to perform this experiment is to charactarize the effect of the coverlay material (Specified by JLCPCB at 2.9) on RF performance.
For this reason, I have included both coverlay and coverlay-removed sections for both the 2 mil and 3 mil traces.
Furthermore, this board will be used in combination with other materials, specifically an epoxy resin, to measure their respective effects on performance as well.

There are a plethora of stiffener materials which are not accounted for that JLCPCB offers. These materials may be tested in additional experiments but are 
not planned to be charactarized right now.

The order for the first round of boards was placed on 6/13, and experiments will commence when they arrive.
