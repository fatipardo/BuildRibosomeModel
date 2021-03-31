## How to build a model of _E.coli_ 70S ribosome stalled with _M.succininiproducens_ SecM (no cis bonds) 

The original notes written while creating the model can be found here:
- url: https://mynotebook.labarchives.com/
- username: fati.pardo@gmail.com

We have built our model around the structure PDB 3JBU ([Zhang et al., 2015](https://elifesciences.org/articles/09684)).  

The .pdb file can be downloaded from the [RCSB Protein Data Bank](https://www.rcsb.org/structure/3JBU), and the two output .pdb files should be combined into a single file using the `cat` command in bash in the command line interface (CLI).  

### Generating a topology file in GROMACS to run energy minimization on the structure


> NOTE: In order to successfully generate a topology file in GROMACS, your operating system needs to be able to differentiate between lower and upper case (be case sensitive). This is because the ribosome contains more than 26 chains, so you can have both chain A and chain a. If your operating system is not case sensitive, it will overwrite the files as the topology is being generated. 

Modifications to the existing model (3JBU):

* Substitution of the nascent peptide (originally chain z in 3JBU obtained after combining the .pdf files bundle1 and bundle2). This is detailed in the section 'Generating the Nascent Peptide'. 

In addition, the following atoms/residues were removed because they were either not complete, or produced an error when creating a topology. All these residues were at terminal positions and not located in proximity to our area of interest. 

* Amino acid ARG 11 from chain y: This residue was not complete and was therefore removed. 

* The terminal atom P, and atoms OP1, OP2, OP3 from chains A, X, a, b, v. 

* Nucleic acid A119 from RNA chain a. 


### Generating the Nascent Peptide.

In [FixCisbonds](https://github.com/fatipardo/BuildRibosomeModel/tree/main/FixCisBonds), we explained how we modeled a new nascent chain where the _cis_ peptide bonds were removed from the original nascent chain in 3JBU. This section details how this resulting nascent chain was added to the _E.coli_ 70S model. 

We used the tRNA from 3JBU (originally chain v) and ran `cat`in bash to 'fuse' the tRNA and the new model of the nascent peptide (check repository [FixCisBonds](https://github.com/fatipardo/BuildRibosomeModel/tree/main/FixCisBonds)). 

Note that the residues in chain v- tRNA need to be renumbered. This is because in the original 3JBU structure, the nascent peptide (chain z) and the tRNA (chain v) are separate chains. When they are combined as has been described here, we start counting from the nascent peptide and then add 28 to the residue ID of the tRNA.

[Build_tRNA](https://github.com/fatipardo/BuildRibosomeModel/tree/main/Complete70S/Build_tRNA) includes the intermediate steps that were followed to create the tRNA+NascentPeptide chain.

The file with renumbered tRNA is: tmp_v.pdb
And the combined files in a single structure: ChV_tRNA_WTprot.pdb 

This was done separately because it was faster to test if GROMACS could build a successful topology (many times there are typos or minor errors that need fixing when building a structure like this one). Once a successful topology is generated, we can proceed with adding the new tRNA+NascentPeptide chain to the complete 70S model. 

Combining the tRNA+NascentPeptide chain (we used the ID for chain v) and 70S can be done in 2 simple ways. 

1) Edit the text file, delete the original chains 'v' and 'z'.

2) Paste the **new** chain 'v'.

This can also be done with a graphic interface using PyMOL.  

Notice that this can be done easily is because the tRNA was taken directly from 3JBU, so the structures aligned perfectly. 



