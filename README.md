# plmDCA

This is a MATLAB-implementation of the asymmetric version of plmDCA.
The program uses 'minFunc' by Mark Schmidt (contained in the folder '3rd_party_code'), which can be found at http://www.di.ens.fr/~mschmidt/Software/minFunc.html.


HOW TO USE:

	1) In MATLAB, go to the directory containing mexAll.m, and give the command 
	>mexAll 
	to create mex files appropriate for your system.
  
	2) Call the program as
	plmDCA_asymmetric(fastafile,outputfile,reweighting_threshold,nr_of_cores)

 
INPUTS TO PLMDCA: 

	fastafile:
	Alignment file in FASTA format. Inserts, which should be represented by '.' and lower-case letters (as is standard in the Pfam download), are removed automatically by the program.

	outputfile:
	This becomes a file with N(N-1)/2 rows (N=domain length), each with three entries: residue i, residue j, and interaction score for the pair (i,j).

	reweighting_threshold:
	Required fraction of nonidentical amino acids for two sequences to be counted as independent (typical values: 0.1-0.3).
	Note that this is not the threshold 'x' as defined in the papers, but 1-x.
 	
	nr_of_cores:
	The number of cores to use on the local machine. 
	If this argument is >1, the program calls functions from MATLAB's Parallel Computing Toolbox.


TYPICAL CALL (ON A QUAD-CORE MACHINE):

	plmDCA_asymmetric('PF00014_full.txt','PF00014_scores.txt',0.2,4)
