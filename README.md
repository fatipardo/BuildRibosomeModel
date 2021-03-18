This repository contains the steps necessary to build a Ribosome Model. 
In particular, it shows how we built the model for the Ribosome stalled by Ms SecM

1. There is no structure available for Ms Secm, so we used a structure of a stalled ribosome by Ec SecM. We chose structure 3JBU
2. We need to mutate the residues from the nascent peptide to match our experimental system. We did this in PyMOL. 
3. Some of the peptide bonds in the 3JBU nascent chain are in the CIS configuration. These are most likely errors, so we need to fix them.

The bonds we had to fix are: ...

4. Some of the bond were easy to fix. By moving the atom and doing energy minimization. For other we required more work and decided to use KIC implemented in Rosetta.

We generated many models and selected the ones with the best score. The bonds we fix this way are: ... and ... 

