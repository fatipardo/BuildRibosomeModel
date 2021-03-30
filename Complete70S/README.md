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


**How to Prepare the nascent peptide??**

In the directory 'Fixed CIS backbone' we explained how we modeled a new nascent chain that did not contain cis peptide bonds. Here we show how we used this new nascent chain and added it to our 70S model. 

To facilitate our work, we took the tRNA from 3JBU (originally chain v). We then 'cat' the tRNA and the new model of the nascent peptide with the 'Fixed CIS backbone'. 

Notice that you have to renumber the residues in the tRNA chain v. This is because in the original 3JBU structure, the nascent peptide (chain z) and the tRNA (chain v) are in different chains. When we combine them, we will start counting from the nascent peptide and then, add 28 to the residue ID of the tRNA.

The directory 'Build_tRNA' includes the intermediate steps I followed to create the tRNA+NascentPeptide chain.

The file with renumbered tRNA is: tmp_v.pdb
And the combined files in a single structure: ChV_tRNA_WTprot.pdb 

The motivation to do this separately is because it was faster to test if GROMACS could build a successful topology (many times there are typos or minor error that need to fixed when building an structure like this one). Once a successful topology is create, we can procedd to include our new tRNA+NascentPeptide chain to the complete 70S model. 

Combining the tRNA+NascentPeptide chain (we used the ID for chain v)  and 70S can be done in 2 simple ways. 1) edit the text file, delete the original chains 'v' and 'z' and then paste the **new** chain 'v'. This can also be done with a graphic interface using PyMOL.  

Notice that this can be done easily is because the tRNA was taken directly from 3JBU, so the structures aligned perfectly. 



