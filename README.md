# Binder for Pitt PAML/codeML lesson

Initially forked from [here](https://github.com/binder-examples/conda). Thank you to the awesome [binder](https://mybinder.org/) team!

[![Binder](https://mybinder.org/badge_logo.svg)](https://gesis.mybinder.org/binder/v2/gh/c4therine/paml-binder-Pitt/7dcff1f4aa49408525e1f04c9a3b82a9f0591fb5)



## Walkthrough

Enter the first direcotry

    cd interspecies_example//

Align the FASTA amino acid file

    muscle -in MNBX01000583.1_4.faa -out MNBX01000583.1_4.fa

Make a codon alignment from the peptide alignment and nucleotide sequence

    pal2nal.pl MNBX01000583.1_4.fa MNBX01000583.1_4.ffn -output fasta > MNBX01000583.1_4.codonalign.fa

Check that the correct input/output files are in the codeml.ctl file

    less codeml.ctl

Run codeml

    codeml codeml.ctl

