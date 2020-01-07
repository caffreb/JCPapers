
## Goals
 - Solve the problem of long tandem repeats (LTRs), specifically centromere assembly
 - Assembly of unbridged tandem repeats remains a problem
 - Help towards an end goal of telomere-to-telomere assembly

## Software used/provided/compared

### Provided
 - centroFlye: software described in this paper
 
### Used
 - Noise-cancelling repeat finder (NCRF)
 - *fitting alignment* from edlib: C++ library for fast exact sequence alignment using edit distance.
 
## Data and technologies used
### Technologies applicable
- Pac-bio
- Oxford Nanopore 

### Input data
- Read set (long reads)
- concensus HOR

### Actual data used
 - Oxford Nanopore reads from Telomere-to-telomere consorstium (Miga et al. 2019)
 - N50 read length: 70kb
 - 7,6m reads with length below 5kb, low effect on assembly
 - 999,562 ultralong reads (>50kb) have greatest effect on assembly
 
### centroFlye and T-to-T assmeblies of cenX
 - Use 2 assemblies from Miga et al. referred to as T2T4 and T2T6

### Mapping reads to assemblies
 - for each 2 assemblies they used the shared unique 19-mers to align centromeric reads.
 - 
 
 
### Pipeline

## Sources and related Papers
 - Flye [kolmogorov et al. 2019](https://www.nature.com/articles/s41587-019-0072-8)
 - 

## Intro
- Centromeres are among the longest tandem repeats in the genome and biggest gaps in the reference
- Linked to Aneuploidy, cancer and infertility
- Complex repeats are unique to hominids


## Results

### Centromere architecure
- Taking model from Miga et al. and extending it for assembly

### centroFlye pipeline
- 

## Discussion

## Methods

- Defines a set of rare kmers

### Definitions, abbreviations and interesting facts/claims
 - Aneuploidies: An abnormal number of chromosomoes in the cell
 - alpha satellite: A particular satellite region which is on all chromosomes in human. 171bp long
 - Satellite DNA is so called because they have a different density from bulk DNA such that they form a second or 'satellite' band when genomic DNA is separated on a density gradient
 - HOR: Higher order repeat
 - T2T: telomere to telomere consortium
 - a single nucleotide insertion in a k-mer from a genome occurs in an ONT read with a probability of 0.03 


## Useful Figures
