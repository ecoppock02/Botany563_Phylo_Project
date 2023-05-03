# Reproducibility Notebook 

# DATA

My data includes mostly Dioon cycads, an ancient plant genus mostly
found in Mexico and that is critically endangered. After changing my data
halfway through the semester, the gene of interest is an intergenic spacer
in the chloroplast. 

# ALIGNMENT

# MAFFT Alignment:

I chose MAFFT as the first alignment tool due to the ease of download.
This tool was easier to download than other methods. MAFFT is comparable
to the accuracy of ClustalW and TCoffee while being considered faster.
The ease of download and use when compared to ClustalW and TCoffee was
also a factor in my choice.
https://academic.oup.com/nar/article/30/14/3059/2904316

MAFFT was downloaded from https://mafft.cbrc.jp/alignment/server/
MAFFT folder moved to software folder. 

I input my data file labeled "Dioon_Data_GU.fasta". My output result is
"Dioon_Data_GU_ALIGNED_MAFFT.fasta"

Input file can be found desktop/Botany563_Phylo_Project

Commands used:

mafft Dioon_Data_GU.fasta > Dioon_Data_GU_ALIGNED_MAFFT.fasta

Output file saved in Botany563_Phylo_Project

# MUSCLE Alignment:

I chose MUSCLE as the second alignment tool because of the ease of
download compared to TCoffee and ClustalW, both of which I was not able
to run on my computer. MUSCLE is also very fast when compared to TCoffee
and CLustalW with the same accuracy.
https://academic.oup.com/nar/article/32/5/1792/2380623?login=false

MUSCLE was downloaded from http://www.drive5.com/muscle/
MUSCLE folder moved to software folder.

I input my data file labeled "Dioon_Data_GU.fasta." My output result is
"Dioon_Data_GU_ALIGNED_MUSCLE.fasta"

Input file can be found desktop/Botany563_Phylo_Project

Commands used:

tar -zxvf muscle3.8.31_i86darwin64.tar.gz
cd desktop/Botany563_Phylo_Project
~/desktop/software/muscle3.8.31_i86darwin64 -in Dioon_Data_GU.fasta -out Dioon_Data_GU_ALIGNED_MUSCLE.fasta

Output file saved in Botany563_Phylo_Project

# Inference Tools

# Maximum Likelyhood Inference:

I chose Maximum likelyhood as my first inference method.

Specifcally, I used IQtree. I chose IQtree due to the speed and the ability
to sample starting trees in order to not get stuck in local optima.
IQtree is also very accessable and easy to download and use.
https://academic.oup.com/mbe/article/37/5/1530/5721363?login=false

IQtree was downloaded from
IQtree folder moved to software folder

I input my data labeled "Dioon_Data_GU_ALIGNED_MAFFT.fasta" and
"Dioon_Data_GU_ALIGNED_MUSCLE.fasta" in order to test the differences
between alignments. My output files are

Input file can be found desktop/Botany563_Phylo_Project

Commands used:

software/iqtree-1.6.12-MacOSX/bin/iqtree -s Dioon_Data_GU_ALIGNED_MAFFT.fasta
software/iqtree-1.6.12-MacOSX/bin/iqtree -s Dioon_Data_GU_ALIGNED_MUSCLE.fasta

Output files moved and saved in Botany563_Phylo_Project


# Distance and Parsimony Inference 

I chose Distance

R Studio is kept in the software folder.
Working directory was set to Botany563_Phylo_Project

Commands used:
In R Studio

install.packages("adegenet", dep=TRUE)
install.packages("phangorn", dep=TRUE)

library(ape)
library(adegenet)
library(phangorn)

Dioon_Data_MAFFT <- fasta2DNAbin(file="Dioon_Data_GU_ALIGNED_MAFFT.fasta")
Dioon_Data_MUSCLE <- fasta2DNAbin(file= "Dioon_Data_GU_ALIGNED_MUSCLE.fasta")

Dist_MAFFT <- dist.dna(Dioon_Data_MAFFT, model="K80")
Dist_MUSCLE <- dist.dna(Dioon_Data_MUSCLE, model = "K80")

DDMATree <- nj(Dist_MAFFT)
DDMUTree <- nj(Dist_MUSCLE)

DDMATree <- ladderize(DDMATree)
DDMUTree <- ladderize(DDMUTree)

plot(DDMATree, cex=.3)
title("Dioon Tree with MAFFT")

plot(DDMUTree, cex=.3)
title("Dioon Tree with MUSCLE")

R Markdown file saved to Botany563_Phylo_Project, Trees saved from R
Markdown in Botany_Phylo_Project


# Homework Commits

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