## How to build a model of 70S with our SecM model (no cis bonds) 

The original notes written while creating the model can be found here:
url: https://mynotebook.labarchives.com/
username: fati.pardo@gmail.com


We are using structure with PDB ID0 3JBU. 
When the structure is downloaded as PDB file, it is divided into 2 PDB files. 
In order to have a single file, I combined the 2 pdb-like structures by using the 'cat' shell command. 

**My goal from this step is to be able to successfully generate a topology file in GROMACS and be able to run energy minimization on the structure.**

```
NOTE: In order to successfully generate a topology, your operating system needs to be able to differentiate between 
lower and upper case (be case sensitive).
This is because the ribosome contains more than 26 chains, so you can have both chain A and chain a. 
If your operating system is not case sensitive, it will overwrite the files as the topology is being generated. 
```

I also need to make some modifications to the structure:

1) Change the nascent peptide (originally chain z in 3jbu from combining bundle1 and bundle2), see section below for more details on this! 

The following atoms/residues were removed because they were either not comple or produced an error when creating a topology. In all these cases the residues were at terminal positions. Furthermore, the residues were not located in proximity to our area of interest. 

2) ARG y  11 : This residues is not complete, thus I removed it

3)  Remove the terminal P, OP1, OP2, OP3 from chain A, X, a, b, v

4)  RNA chain a / residue A119


March 11,2020

How to Prepare the nascent peptide??

I combined the tRNA from the 3JBU crystal structure, and the new model of the nascent peptide with the 'Fixed CIS backbone' (initial structure of WT from our current MD simulations).

What I MUST do is to renumber the tRNA numbering for chain v!! I am working on it in the following directory: 

/Users/fatima/Stanford/70S/test/3jbu-pdb-bundle/Build_tRNA

The file with renumbered tRNA is: tmp_v.pdb

I already combined the files into a single structure: ChV_tRNA_WTprot.pdb 

Now I have to insert protein+tRNA into the complete ribosome. This should be easy because the tRNA was taken directly from 3JBU



