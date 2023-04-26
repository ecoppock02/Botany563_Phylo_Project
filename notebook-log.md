# Reproducibility Notebook 

ClustalW and TCoffee did not work with my mac. Instead, I downloaded MAFFT
and used it on both the Primates data and my own. I also combined the
multiple fasta files for each sequence into one titled "Cycad_Seq.fasta"

MAFFT is comparable to the accuracy of ClustalW and TCoffee while being
considering faster. The ease of download and use when compared to ClustalW
and TCoffee was also a factor in my choice. 

Code used "mafft Cycad_Seq.fasta > Cycad_Seq_ALIGNED.fasta"
Output file seen in folder

In R, a distance and parsimony tree was build using my data
I've recieved more data and will be using it in an updated tree shortly.

Maximum likelyhood tree made with some of the new data I recieved from my
lab. Will be making changes to include new data with previous steps.
I chose IQtree as the ML method because of the ability to customize on
IQtree 2.

Command used = software/iqtree-1.6.12-MacOSX/bin/iqtree -s Dioon_Data_GU_ALIGNED.fasta

I haven't fully updated all of the previous steps for my new data yet.
here are the commands I will use on my data for Bayesian in MrBayes


begin mrbayes;
 set autoclose=yes;
 prset brlenspr=unconstrained:exp(10.0);
 prset shapepr=exp(1.0);
 prset tratiopr=beta(1.0,1.0);
 prset statefreqpr=dirichlet(1.0,1.0,1.0,1.0);
 lset nst=2 rates=gamma ngammacat=4;
 mcmcp ngen=10000 samplefreq=10 printfreq=100 nruns=1 nchains=3 savebrlens=yes;
 outgroup Anacystis_nidulans;
 mcmc;
 sumt;
end;

Note: this will be edited for my data, specifically the ngen number.

cat algaemb.nex mbblock.txt > algaemb-mb.nex

Note: this will also be edited to be specific to my data so the output
is a nexus file.

mb algaemb-mb.nex

Note: again edited from my data/file name.

I dont believe I will need to use this method for my data since I do not
have a set with multiple genes. Using a toy data set I will:

Use Mrbayes for each gene
create a new file for my Mrbayes output with mbsum
Next I will run BUCKy with all appropriate options
Output will be a .out, .input, .gene, .cluster, .concordance, All labeled
"Dioon_Data_BUCKy"

#DATA

My data includes mostly Dioon cycads, an ancient plant genus mostly
found in Mexico and that is critically endangered. After changing my data
halfway through the semester, the gene of interest is an intergenic spacer
in the chloroplast. 

#ALIGNMENT

#MAFFT Alignment:

I chose MAFFT as the first alignment tool due to the ease of download.
This tool was easier to download than other methods.MAFFT is comparable to the accuracy of ClustalW and TCoffee while being
considering faster. The ease of download and use when compared to ClustalW
and TCoffee was also a factor in my choice.
https://academic.oup.com/nar/article/30/14/3059/2904316

MAFFT was downloaded from https://mafft.cbrc.jp/alignment/server/
MAFFT folder moved to software folder. 

I input my data file labeled "Dioon_Data_GU.fasta". My output result is
"Dioon_Data_GU_ALIGNED.fasta"

Input file can be found desktop/Botany563_Phylo_Project

Commands used:

mafft Dioon_Data_GU.fasta > Dioon_Data_GU_ALIGNED_MAFFT.fasta

Output file saved in Botany563_Phylo_Project

#MUSCLE Alignment:



