#Building 70S Ribosome stalled by SECM

We use 3JBU as our reference structure 
We noticed that the backbone of the nascent chain contains 4 peptide bonds with the omega dihedral in the cis configuration, which in my opinion is hard to justify (cis omega dihedrals are rare and the resolution is not high enough to model a cis configuration).
So the first step is to fix the cis bonds. 
The details can be found in the FixCisBonds directory of this repo.
After fixing the cis bonds, we used the same nascent peptide for all our models. 
The details can be found in the Complete70S directory of this repo. 



