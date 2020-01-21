# Nebula: Ultra-efficient mapping-free structural variant genotyper

## Software 

### Provided
 - Nebula
### Used/Listed/Compared
 - Lumpy
 - SVtyper


## Data and technologies used
 - WGS data
 - Simulated data from GRCh37 with random deletions at SV sites in 1000GP
 - wgsim for paired-end sequencing reads
 - Read data from 1000 GP

## Sources and related Papers

## Methods

### Overview
 - kmer processing phase: Takes a set of SVs and selects a set of k-mers whose frequency is different to the reference
 - Genotyping phase: 
 
### kmer selection
 - 32-mers chosen to be long enough for uniqueness but short enough to not expect too many errors, 32 is a multiple of 2.
 - inner k-mers: k-mers 
 - gapped k-mers:
 
### Genotyping phase
 - count k-mers in newly sequenced samples
 - estimate the optimal real valued relaxed version of the genotypes (0<=z<=1)
 - Rounding the real valued relaxed version of genotypes into discrete genotypes
 


## Results
 - Not 100% clear if is better than SVtyper and Lumpy on simulations but there is no mapping step (Fig 3). 1/1 prediction is more difficult.
 - Little difference in terms of coverage needed (Simulated 15x and 40x)
 - No real data comparison?


## Discussion and my questions
 - How good are we at simulating a dataset? Can we simulate sequence sets and/or genomes which are indestinguishable from real data?


