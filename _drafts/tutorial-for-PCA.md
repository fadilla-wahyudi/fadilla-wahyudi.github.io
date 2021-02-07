---
title: "Test Draft"

---
# A Beginner's Guide to PCA
Principal Component Analysis -- the bread and butter of population geneticists. When I was learning how to create my first PCA plot for the 1000 Genomes Project, I struggled for the longest time trying to get the plot to make sense.
I finally asked one of the Research Fellows at my University and he taught me how to filter my dataset.

*Disclaimer: I am not an expert. If you have any questions, concerns, queries, comments, please consult your local pop gen guru.

This is the workflow that I used when I was starting out bioinformatics. I hope this tutorial helps! 

## Preparing the VCF files 
I used three software programmes to create the PCA plot: BCFtools, PLINK and RStudio.
For the PCA, I concatenated all the autosomal chromosome VCF files into one file using ```bcftools concat```.
Then I split the VCF file into their populations (AFR, EUR, SAS, EAS and AMR) using ```bcftools view --samples-file```. In the command, I included a newline-delimited text file listing all the samples from the population.

## Filtering the dataset
**Step 1: Exclude duplicated SNPs**
```
zgrep -v "#" [VCF FILE] | cut -f3 | sort | uniq -d > [OUTPUT FILE]
```
- ```zgrep -v``` inverts the sense of matching, to select non-matching lines. This would remove the metadata and header of the VCF file 
- ```cut -f3``` only reports the third column, which in this case is the ID column.
- ```uniq``` reports or filters out repeated lines in a file.
- ```-d``` only print duplicated lines.

Exclude the duplicated SNPs
```
plink --vcf [VCF FILE] --exclude [OUPUT FILE] --recode vcf bgz --keep-allele-order --out [OUTPUT VCF FILE 1]
```
I used ```keep-allele-order``` because the version of PLINK that I was using would sometimes switch the REF and ALT allele when producing the VCF file.

---

**Step 2: Extract biallelic SNPs only**
```
bcftools view  --max-alleles 2  --min-alleles 2 --types snps --output-type z  --output-file [OUTPUT VCF FILE 2] [OUTPUT VCF FILE 1]
```
---

**Step 3: Filter based on on missing rate per SNP, minor allele frequency (MAF) and Hardy-Weinberg equilibrium**
I used the following parameters for each filter:
- ```--geno 0.05``` excludes SNPs that have a missing genotype rate of 0.05.
-```--maf 0.01``` excludes SNPs that have a minor allele frequency of less than or equal to 0.01.
-```--hwe 0.0000001``` excludes SNPs that fail the HWE threshold: 0.0000001

```
plink --vcf  [OUTPUT VCF FILE 2] z --geno 0.05 --maf 0.01 --hwe 0.0000001 --keep-allele-order --recode vcf bgz --out [OUTPUT VCF FILE 3]
```
---

**Step 4: Missing rate per person**
I removed individuals that have more than 5% missing genotype (```--mind 0.05```). 
```
plink --vcf  [OUTPUT VCF FILE 3] --mind 0.05 --keep-allele-order --recode vcf bgz --out [OUTPUT VCF FILE 4]
```
---

**Step 5: Create a VCF file SNPs that are polymorphic in all populations**
Create a list of SNPs for each populations.
```
zgrep -v “#” [OUTPUT VCF FILE 4] | cut -f3 | sort > [SNPS IN POP1]
```

Create a list of SNPs that are polymorphic in all populations.
```
comm -12 [SNPS IN POP1] [SNPS IN POP2] | comm -12 [SNPS IN POP3] - | comm -12 [SNPS IN POP4] - | comm -12 [SNPS IN POP5] - > [LIST OF SHAREDD SNPS]
```
```comm -12``` prints out lines that are are present in both files.

Use ```bcftools merge``` to merge the VCF file together.
Extract the SNPs that are polymorphic in all populations using PLINK's ```--extract``` or BCFtools' ```view```.  

**Step 6: Linkage disequilibrium (LD) pruning**


# Resources


