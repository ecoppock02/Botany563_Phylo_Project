# Reproducibility Notebook 
My data includes mostly Dioon cycads, an ancient plant genus mostly
found in Mexico and that is critically endangered.

FastQC ran on my raw data.

ClustalW and TCoffee did not work with my mac. Instead, I downloaded MAFFT
and used it on both the Primates data and my own. I also combined the
multiple fasta files for each sequence into one titled "Cycad_Seq.fasta"

Code used "mafft Cycad_Seq.fasta > Cycad_Seq_ALIGNED.fasta"
Output file seen in folder