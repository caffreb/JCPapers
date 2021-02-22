# Comparative genome analysis using sample-specific string detection in accurate long reads

# Summary
- Comparative genome analysis using sample specific strings
- no need for mapping


## Problem Definition
- Targets and a reference (of some sort), interested in identifying substrings of targets that are not in reference
- _More complex forms of genomic variation, e.g., an inversion-duplication, can be seen as combinations of variants and therefore are not further considered here._
- there should exist for each variant at least one substring of T that is not found in R.
- We postulate, and will later experimentally verify, that with long and accurate enough reads virtually all variants can be found in substrings of T that do not appear in R.
- PRoblem 1 is naively O(n^3), they propose new algorithm with O(n^2) using FM-index
- Propose a heuristic algorithm with O(n) time
- 


## Software 

### Provided
https://github.com/Parsoa/PingPong
### Used or compared
- ntEdit
- BBMap
- minimap2
- PGSIM
- BCFtools
- BEDTOOLS
- kmc_tools (Compared)


## Data and technologies used
- Simulated trios
- SVs in trios from 1KGP, first parents then inherited child
- 6115 insertions and deletions?? More info?
- Simulated recombination
- Introduced 17,595 de novo insertions/deletions/inverstions impacting 7,9m bases
- 4 coverage levels 5->30 (PBSIM), HiFi reads, 0.1% error

## Sources and related Papers

## Methods

## Results
### Simulations
- Compared recall and precision of at different coverage levels. 
- Filter set according to Tau, i.e. specific strings occurring less Tau times.
- Figure 3 compares Precision, recall and Tau. 
- Low Tau cutoff not good wrt Precision at high coverage, 5x coverage not enough for recall (basically)

- 98% recall and 82% precision at recovering simulated de novo variations. T=5.
- mapped child specific strings to trio, child specific map 83%, compared to M+P, Fig Sup 1. Looks good

### Specific string detection in real human HiFi data
- We considered the HG00733 child (Puerto Rican trio) and the NA19240 child (Yoruba trio). 30x
- Compared Exact and relaxed ping pong search (Exact is better) Fig S3
- Contig analysis from HGSVC2 consortium. Fig 4, 80% of child specific strings map perfectly. ????
- C-precision (contigs-based precision) metric introduced. The exact version of our algorithm therefore achieved a C-precision of 79.47%. On the other hand, the relaxed version achieved a C-precision of 90.61%.

- specific strings computed by exact algorithm intersect most of the HG00733-specific alleles (> 98%), covering nearly all alleles coming from SNPs and indels (> 98% and > 95%, respectively) and most of alleles coming from SVs (> 92%).
- Table 1.
- majority of the variants not covered by the sample- specific strings were indels in stretches of A or T sequences
- Fig 4 c/d
- investigate why ∼ 27% of the specific strings align well to the HG00733 haplotypes but do not represent a specific portion of them
- 



## Discussion Points
- Intro? Anything obvious
- Data looks ok?
- Methods are solid?
- Other tools which could be compared?
- Other analyses which could be performed?


## Writing problems
- some things introduced in the wrong place?
- Format is ok?



### Definitions

### Input files

## Useful Figures



## Notes or interesting claims

## Links to descriptions

## Questions/problems

Return to [JC start](../../)
