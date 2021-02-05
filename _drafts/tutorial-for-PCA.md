---
title: "Test Draft"

---
# A Beginner's Guide to PCA
Principal Component Analysis -- the bread and butter of population geneticists. When I was learning how to create my first PCA plot for the 1000 Genomes Project, I struggled for the longest time trying to get the plot to make sense.
I finally asked one of the Research Fellows at my University and he taught me how to filter my dataset.

*Disclaimer: I am not an expert. If you have any questions, concerns, queries, comments, please consult your local pop gen specialist.

## 1. Preparing the VCF files 
For the PCA, I concatenated all the autosomal chromosome VCF files into one file using ```bcftools concat```.
Then I split the VCF file into their populations (AFR, EUR, SAS, EAS and AMR) using ```bcftools view --samples-file```. In the command, I included a newline-delimited text file listing all the samples from the population.

## 2.

# Resources


