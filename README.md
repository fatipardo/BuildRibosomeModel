## Building the 70S Ribosome stalled by the _Mannheimia succiniciproducens_ arrest peptide SecM

We used [3JBU](https://www.rcsb.org/structure/3JBU) as our reference structure. 

This structure is based on a cryo-electron density map of the _Escherichia coli_ ribosome stalled during translation by the 17 amino acid long arrest peptide SecM ([Zhang et al. 2015](https://elifesciences.org/articles/09684)). It is so-far the best available structure of translational arrest by SecM, which is why we used it for the present study.

While building the model, we noticed that the backbone of the nascent chain contains 4 peptide bonds with the omega dihedral in the _cis_ configuration, which are hard to justify since _cis_ omega dihedrals are rare. Moreover, the cryoEM density of the map in this region is not high enough to justify modelling a _cis_ configuration, and this led us to replace the _cis_ bonds in this region to _trans_ as the first step. 

The details of this process can be found in [FixCisBonds](https://github.com/fatipardo/BuildRibosomeModel/tree/main/FixCisBonds).

**Note:** After fixing the cis bonds, we used the same nascent peptide for all our models. The details can be found in the Complete70S directory of this repo. 



