# BA662A VCA 

SPICE Model for the BA662A VCA IC

(THIS MODEL DOES NOT USE THE CORRECT TRANSISTORS, HOWEVER THE GAIN RESPONSE IS THE SAME AS A REAL BA266A).

IN THE JUNO VCA SIM, NE5532's WERE USED FOR OPAMPS, RATHER THAN THE TA75558S's USED IN THE JUNO, BUT THIS HAS NO REAL IMPACT ON THE SIMULATION'S ACCURACY

Whilst re-capping a Juno-6 it occured to me that the THD of the signal path could be lowered further by switching a set of electrolytic caps in the signal path with film capacitors. However, the electrolytics were between 10-50uF, and so film caps of this capacitance would be too large (physically) to fit on the board. As the caps each formed a HPF, lower capacitance capacitors would raise the cutoff frequency, unless the impedance of the 'R' seciton of each CR filter was also raised. 

<img width="538" height="530" alt="image" src="https://github.com/user-attachments/assets/8951ca5a-d029-45ed-b577-10a125e54719" />

Specifically, C8 formed an RC filter with R38 + VR4, and so raising the R of R38 would also change the impedance seen by the VCA, which would change the gain at it's output. There isn't a large amount of documentation on this VCA chip, and I didn't want to change any component values and risk damaging it. However, the chip has been cloned by OpenMusicLabs, and on their Wiki they detail the circuit diagram. This allowed me to draw the chip up in LTSpice, along with the control section of the cirucit dedicated to the VCA, and allowed me to check the effects of changing the values of R38. 

Ultimately, changing the impedance of R38 to a value that would allow me to put an appropiately sized film cap in, pushed the gain too high and clipped the voice summing circuit so this ended up being somewhat of a dead-end. Alongside this, raising the capacitance of the electrolytic would've also dropped the THD, allowing me to drop the R value instead (and reduce the johnson noise!), but I only realised this after finishing the re-cap process. 

However, I hope this SPICE model may be of some use for other people! I have also included the cirucit of the VCA stage.
