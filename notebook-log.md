# Reproducibility Notebook 
My data includes mostly Dioon cycads, an ancient plant genus mostly
found in Mexico and that is critically endangered.

FastQC ran on my raw data.

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