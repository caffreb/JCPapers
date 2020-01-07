
## Goals
 - Solve the problem of long tandem repeats (LTRs), specifically centromere assembly
 - Assembly of unbridged tandem repeats remains a problem
 - Help towards an end goal of telomere-to-telomere assembly

## Software used/provided/compared

#### Provided
 - centroFlye: software described in this paper
 
#### Used
 - Noise-cancelling repeat finder (NCRF)
 - *fitting alignment* from edlib: C++ library for fast exact sequence alignment using edit distance.
 
## Data and technologies used
#### Technologies applicable
- Pac-bio
- Oxford Nanopore 

#### Input data
- Read set (long reads)
- concensus HOR

### Actual data used
 - Oxford Nanopore reads from Telomere-to-telomere consorstium (Miga et al. 2019)
 - N50 read length: 70kb
 - 7,6m reads with length below 5kb, low effect on assembly
 - 999,562 ultralong reads (>50kb) have greatest effect on assembly
 

 
 
### Pipeline
 - Listed in paper, page 3

## Sources and related Papers
 - Flye [kolmogorov et al. 2019](https://www.nature.com/articles/s41587-019-0072-8)
 - Edlib: A C/C ++ library for fast, exact sequence alignment using edit distance
 - Noise cancelling repeat finder (NCRF) Harris et al. 2019

## Intro
- Centromeres are among the longest tandem repeats in the genome and biggest gaps in the reference
- Linked to Aneuploidy, cancer and infertility
- Complex repeats are unique to hominids


## Results

### Centromere architecure
- Taking model from Miga et al. and extending it for assembly
- Fig 1


### centroFlye and T-to-T assmeblies of cenX
 - Use 2 assemblies from Miga et al. referred to as T2T4 and T2T6
 

### Mapping reads to assemblies
 - for each 2 assemblies they used the shared unique 19-mers to align centromeric reads.
 - These were filtered by removing those rare 19-mers which were also a hamming distance of 1 away from a common 19-mer, i.e. a sequencing error.

### Quality assessment of centromere assemblies
 - Using reference free quality assessment, many measures such as QUAST are not applicable for LTRs
 - Not using simulated sets either.
 
#### Coverage test
 - In the case of uniform coverage, regions with abnormal coverage may point to assembly errors. 
 - Fig 5
 - ONT are characterised by uniform read coverage so spikes are important
 - ONT does have non-uniform read "length" distribution
 - Enter the following tests

#### Discordance test
 - Use kmers as anchors for discrdance
 - Compare two assemblies by counting the number of shared anchors....equation on p5
 - A read is discordant between two assemblies if it has a distance of greater than k between the assemblies
 - A discordant read *votes* for an Assembly A or A' if the distance k is positive(A) or negative (A')
 - Fig 3




### Variations if HORs provide insights into evolutionary history of cenX
 - sub families have been classified as HORs
 - These sub families can provide insights into the evolutionary history of cenX HORs
 - 


## Discussion

## Methods

- Recruits centromeric reads by doing an alignment to known HORs via a threshold. Default here is chosen with some ONT parameters taken into account. 
- Partition centromeric reads into units of one HOR
- Classify reads as prefix, internal or suffix
- Defines a set of rare kmers, uses some expectation of coverage and expected survival rate given the error rate in the reads
- Constructs a distance graph for these rare k-mers and then filters the *rare* 19-mers which are actually short edit distances from common k-mers
- Reconstructing the centromere using system analogous to Flye (Figs 1-3 from that paper) Fig 2 here. 

### Definitions, abbreviations and interesting facts/claims
 - Aneuploidies: An abnormal number of chromosomoes in the cell
 - alpha satellite: A particular satellite region which is on all chromosomes in human. 171bp long
 - Satellite DNA is so called because they have a different density from bulk DNA such that they form a second or 'satellite' band when genomic DNA is separated on a density gradient
 - HOR: Higher order repeat
 - T2T: telomere to telomere consortium
 - a single nucleotide insertion in a k-mer from a genome occurs in an ONT read with a probability of 0.03 



## Useful Figures
 - Figs 1-3 of Flye

## Problmes/Questions
 - Can't find fitting alignment in the paper cited
 - Many errors in wording
 - Some results in the wrong place, i.e. not highlighted as big results (LINE found in the centromere)
 - Are Alus and centromeres linked? hominid origin...?
