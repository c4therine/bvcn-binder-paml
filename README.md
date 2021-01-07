# Binder for Pitt PAML/codeML lesson

Initially forked from [here](https://github.com/binder-examples/conda). Thank you to the awesome [binder](https://mybinder.org/) team!

[![Binder](https://mybinder.org/badge_logo.svg)](https://gesis.mybinder.org/binder/v2/gh/c4therine/paml-binder-Pitt/master?urlpath=lab)



## Walkthrough

Enter the first direcotry

    cd pseudomonas/

Two comparisons in tutorial: 
(1) Interspecies: Compare P. aeruginosa clinical isolate P32_8's lip2 gene (PA1666) to homolog in another Pseudomonas species (P. syringiae)
(2) Intraspecies: Compare same clinical isolate's gene to a homolog in a distantly-related P. aeruginosa strain (PA7)

(1) P. aeruginosa P32_8's lip2 versus P. syringiae's lip2

Align the FASTA amino acid file

    muscle -in 20200106_P32_8_PA1666_vs_Psyring.faa.txt -out 20200106_P32_8_PA1666_vs_Psyring.fa

Use pal2nal to make a codon alignment from the peptide alignment and nucleotide sequence

    pal2nal.pl 20200106_P32_8_PA1666_vs_Psyring.fa 20200106_P32_8_PA1666_vs_Psyring.ffn -output fasta > 20200106_P32_8_PA1666_vs_Psyring.codonalign.fa

Check that the correct input/output files are in the codeml.ctl file

    less 20200106_P32_8_PA1666_vs_Psyring.codeml.ctl.txt

Run codeml

    codeml 20200106_P32_8_PA1666_vs_Psyring.codeml.ctl.txt


(2) Compare same P. aeruginosa clinical isolate's lip2 gene (PA1666) to homolog in a distantly-related P. aeruginosa strain (PA7)

Align the FASTA amino acid file

    muscle -in 20200106_P32_8_PA1666_vs_PA7.faa.txt -out 20200106_P32_8_PA1666_vs_PA7.fa

Use pal2nal to make a codon alignment from the peptide alignment and nucleotide sequence

    pal2nal.pl 20200106_P32_8_PA1666_vs_PA7.fa 20200106_P32_8_PA1666_vs_PA7.ffn -output fasta > 20200106_P32_8_PA1666_vs_PA7.codonalign.fa

Check that the correct input/output files are in the codeml.ctl file

    less 20200106_P32_8_PA1666_vs_PA7.codeml.ctl.txt

Run codeml

    codeml 20200106_P32_8_PA1666_vs_PA7.codeml.ctl.txt
