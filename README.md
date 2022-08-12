# Hey there!

This is a repository of the resilience-scoring weights for deriving polygenic resilience scores of Alzheimer's disease.

## Description

The resilience-scoring weights were derived from the Design-1 in Hou et al, 2022 (PMID: 35879306). The file contains 8 columns (i.e., MarkerName, Resilience_allele, WEIGHT, Pvalue, Allele1, Allele2, Chromosome, Position). The MarkerName column includes SNPs rsID from dbSNP (https://www.ncbi.nlm.nih.gov/snp/, build 151 of genome reference GRCh37/hg19). You can use Chromosome and Position column to create unique IDs to map the variants in your genotype files. 

Here is the examplary code for deriving polygenic resilience scores by Plink (version 1.9) using clumping and thresholding (C+T) method:

plink --bfile ${your_genotype_file} \
--maf 0.05 --geno 0.02 --mind 0.02 --allow-no-sex \
--score for_AD_resilience_score_formula_design1.txt 1 2 3  include-cnt sum \
--q-score-range ${your_Pvalue_range_file} for_AD_resilience_score_formula_design1.txt 1 4 \
--out ${your_output_file}

## Help

Please email us for questions or issues: 
Jiahui Hou: houji@upstate.edu
Stephen Glatt: glatts@upstate.edu

## Citation

If you use the resilience score in published research, please cite the paper:
Hou J, Hess JL, Armstrong N, Bis JC, Grenier-Boley B, Karlsson IK et al. Polygenic resilience scores capture protective genetic effects for Alzheimer's disease. Transl Psychiatry 2022; 12(1): 296.
