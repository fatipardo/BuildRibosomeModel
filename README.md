This repository contains the steps necessary to build a Ribosome Model. 
In particular, it shows how we built the model for the Ribosome stalled by Ms SecM

1. There is no structure available for Ms Secm, so we used a structure of a stalled ribosome by Ec SecM. We chose structure 3JBU
2. Some of the peptide bonds in the 3JBU nascent chain are in the CIS configuration. These are most likely errors, so we need to fix them.

Below is the E coli SecM sequence. The CIS peptide bonds in 3JBU are in **bold**: 

KLISE**ED**LFSTP**VW**ISQAQ**GI-RA**G

3. We need to mutate the residues from the nascent peptide to match our experimental system. We did this in PyMOL. We did this residue mutation before fixing the CIS peptide bonds. A comparison between the E. coli and Ms SecM sequences is shown below: 

Ec   KLISE**ED**LFSTP**VW**ISQAQ**GI-RA**G

Ms SGSGGSG**SG**SGSGS**GS**GSGHA**PI-RG**S


4. Some were "easy" to fix. Just "flip" the oxygen of the NH (this can be done by manually changing the coordinates, but this is also how VMD "fixes" CIS bonds), followed by energy minimization to correct the geometry. For the other bonds, we decided to use KIC implemented in Rosetta (directory that contains reference papers: ./SecM_Remodel_Ref_Papers/ ) We defined the loops as 4 residues centered at the cis bond

The specific 'mover' used is genKIC (the same method for cyclic peptide modeling):
https://www.rosettacommons.org/docs/latest/scripting_documentation/RosettaScripts/composite_protocols/generalized_kic/GeneralizedKIC


We generated many models and selected the ones with the best score. The bonds we fix this way are: ... and ... 

