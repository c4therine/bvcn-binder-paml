# Binder for Pitt PAML/codeML lesson

Initially forked from [here](https://github.com/binder-examples/conda). Thank you to the awesome [binder](https://mybinder.org/) team!

[![Binder](https://mybinder.org/badge_logo.svg)](https://gesis.mybinder.org/binder/v2/gh/c4therine/paml-binder-Pitt/master?urlpath=lab)



## Walkthrough

Two comparisons in tutorial: 
(1) Low dN/dS: Compare P. aeruginosa clinical isolate P32_8's wspF gene to homolog in a distantly-related P. aeruginosa strain (PA7)
(2) High dN/dS: Compare a different clinical isolate's wspF gene to PA7

Enter the first direcotry

    cd P32_8_wspF_vs_PA7/

(1) P. aeruginosa P32_8's wspF versus PA7's wspF (PSPA7_1435)

View the FASTA amino acid file (.faa)

    less P32_8_wspF_vs_PA7.faa

Align the FASTA amino acid file using MUSCLE. THe .fa ouutput is the peptide alignment.

    muscle -in P32_8_wspF_vs_PA7.faa -out P32_8_wspF_vs_PA7.fa

Use pal2nal to make a codon alignment from the peptide alignment and nucleotide sequence.

    pal2nal.pl P32_8_wspF_vs_PA7.fa P32_8_wspF_vs_PA7.ffn -output fasta > P32_8_wspF_vs_PA7.codonalign.fa

Check that the correct input/output files are in the codeml.ctl file that I already made.

    less P32_8_wspF_vs_PA7.codeml.ctl

Run codeml using the .ctl file

    codeml P32_8_wspF_vs_PA7.codeml.ctl
    
Examine output and find the dN/dS among other interesting details.

    less -S P32_8_wspF_vs_PA7.codemlOutput.txt
    
The dN/dS value is low (0.0299), suggesting that this gene has evolved under purifying selection in P32_8. 


(2) Compare a different P. aeruginosa clinical isolate (P24_18)'s wspF gene to the same homolog PA7

Open the second directory

    cd ..
    cd P24_18_wspF_vs_PA7

To save time, I have already run codeML for this comparison. Examine the files that are in the directory and find the output file.

    ls 
    less -S P24_18_wspF_vs_PA7.codemlOutput.txt
    
In P24_18, wspF has a higher dN/dS (0.162), but still not likely to indicate that this gene evolved under neutral or positive selection. 
A closer examination of the peptide and codon alignments revealed that a deletion occurred in P24_18's wspF, leading to erroneous amino acids at the C-terminus of the protein. 
