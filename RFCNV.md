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

### Initial summary
- 21 features
- Used Random Forest (RF) classifier 
- Input: genomic coordinates of CNVs and BAM files

### Scaling read depth
- Normalization is needed for read depth related features
- Used invariant genomic regions that are depleated of CNVs
- used 100 WGS in house samples
- One region for each autosome with mean read depth resembling the average, with the lowest Standard deviation and not overlapping CNVs from databases
- Used these means as a denominator to scale read depth related features

### Feature Extraction

#### Features around breakpoints
- Left repeat and right repeat. Is the left or right breakpoint within a repeat region
- Orientation of read pair at the breakpoint (Left.RL and Right.RL). Scaled number of pairs supporing RL/LL/RR etc.
- Support of soft clipped reads (SCR). number of soft clipped reads at the left/right/both breakpoints
- two more features (DI and IN) correspond to the SCRs in direct/inversed mapping orientation for clipped and non-clipped sequence.

#### Features for the region encompassed by the CNV
- Mean read depth
- Length of the CNV
- Microhomology: compare CIGAR strings and find if they indicate a discrepancy.
- GC content
- Repeat Percentage
- Number of common SNPs (MAF>0.1)

#### Called variants within the CNV
- number of heterozygous SNPs, defined heterozygous if >3 reference allele support reads, >3 alternative allele support reads, proportion of alternative allele support reads >0.2
- Probability of heterozygosity, mean of all probabilities of SNPs from 1000GP

### Defining true and false training CNVs
- Used parent-offspring trios with good diversity-to-noise ratios
- True set were selected:
- - inherited from one of the parents
- - detected by at least 3 tools
- Negative set:
- - Not inherited
- - detected by only 1 tool
- - Not in Database

### Training data and construction of random forest model training
- 9 in house trios
- built two classifiers, 1 for deletions and 1 for duplications
- Used the Random forest from R package having extracted the features
- tuned the parameters ntree and mtry for each classifier
- Feature importance was assesed by RF standard output and Boruta algorithm
- Assessed the relationship between the OOB error and size of training set by down-sampling the training data

### Sequencing data
- 6 paired end WGS datasets plus 9 trios(healthy parents+one child with Hirschsprung disease)


## Results

### Training of random forest
- assembled 19,525 true and 25,268 false deletions
- 570 true and 1506 false duplications
- Down sampling shows a negative correlation between OOB error rate and the number of training deletions. Indicating TRaining data needs to be large enough. Duh.
- standard RF output showed the ranked importance of each feature via Mean Decreased Accuracy and Mean decreased Gini.


## Discussion



### Definitions

### Input files

## Useful Figures



## Notes or interesting claims

## Links to descriptions

## Questions/problems

Return to [JC start](../../)
