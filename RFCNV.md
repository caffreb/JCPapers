# A random forest-based framework for genotyping and accuracy assessment of copy number variations

## Software 

### Provided
 - CNV-JACG
### Used/Compared
 - SVmine & FusorSV: Data mining aproach

## Data and technologies used
- GIAB 
- 1000 GP


## Sources and related Papers
https://academic.oup.com/nargab/article/2/3/lqaa071/5910007

## Intro Summary

### Theory overview
- Define a CNV as a structural variant charecterized by alterations in the number of copies of a DNA segment.
- Known to alter gene dosage, disrupt coding sequences and affect gene regulation.
- Underlie many Mendelian diseases and represent a portion of the missing heritability in human complex diseases and congenital abnormalities

### Existing methods
- Based on Read depth (RD), read pairs (RP), split reads (SR), and assembly.
- Read depth looks for abnormal patterns in read mapping, i.e. diploid genome should have even mapping if there are even copy number. In the case of a duplication of one allele then perhaps there are double or triple the number of reads.
- Read depth have particular trouble in repeat regions. 
- Read pair methods identify CNVs by finding pairs with extreme differences in the insert size relative to background.
- Split read methods use soft clipping to which span breakpoints to detect CNVs.
- Both RP and SR methods have disadvantages in detecting non-allelic homologous recombination-induced CNVs because of low-copy repeat induced junction reads.
- Not much mentioned about assembly methods there.

### Approach problems
- Some filter out problematic regions to improve precision but this obviously leads to a higher number of false negatives.
- Estimate ~55% of human genome is represented in the problematic regions.
- Another approach is to use a "bag of bags" approach. Identify CNVs which are found by multiple tools. This is a problem when there is little overlap. Heavily affected by sample size.
- SVmine & FusorSV: Data mining aproaches to combine results of different tools
- Ultimate tools are experimental and manual. i.e. PCR experiments and IGV viewer. Too expensive and time consuming.

## Methods

## Results

## Discussion



### Definitions

### Input files

## Useful Figures



## Notes or interesting claims

## Links to descriptions

## Questions/problems

Return to [JC start](../../)
