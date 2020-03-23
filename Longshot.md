# Longshot enables accurate variant calling in diploid genomes from single-molecule long read sequencing

## Software 

### Provided
 - Longshot

### Used 
 - SMRT-SV
 - HaplotyperCaller (GATK) (short reads, NA here)
 - FreeBayes (short reads, NA here)
 - HAPCut2 (haplotype phasing), provided by authors (other paper)
 - DeepVariant: deep learning variant caller for long reads.
 - Clairvoyante: deep leearning variant caller
 - WhatsHap: deep learning haplotype phaser
 - Nanopolish, variant caller performing signal level analysis of ONT data.
 - Platnum genomes small variant call set with 17 member pedigree set.
 - 

## Data and technologies used
 - Genome in a bottle (GIAB) Pacbio data NA12878 (45x) and Ashkenazi trio (NA24385 (64x), NA24149 (29x) and NA24143 (27x) )


## Sources and related Papers

## Methods

### Identification of candidate SNVs
 - Identified via pileup of aligned reads via a genotype likelihood calculation.
 - filtered for min coverage (6) and alternate allele number(3) and alternate allele fraction (0.125)

### Local realignment using pair-HMMs
 - Realign parts of the read to a small window around an SNV using a Pair-HMM.
 - Use k-mer anchors on each side.
 - Parameters of HMM (i.e. transitions from A->A, A->T etc.) are estimated from aligned reads prior to realignment.
 - Calculate the probability of the read given the ref and alt sequences. Take the higher prob as the ref.
 - Filtered SNVs which had reads over represented from one allele. 

### Haplotype-informed genotyping

### Variant filtering
 - Filtered according to GQ value, variable threshold for Longshot.
 - Read depth greater than $d+5*sqrt(d)$, d is median read depth
 - Density filter to remove clustering SNVs which could be due to missing information in the reference

### Simulations
- hetero SNV rate of 0.001
- homo SNV rate of 0.0005
- sub rate of 0.001
- SimLord for long reads


## Results

### Method overview
 - 

### Accurate SNV calling using simulated data
 - Simulated paired end Illumina and Pacbio reads after adding SNVs to the reference
 - Aligned the reads to the genome using bwa-mem or BLASR (long reads) 
 - Called SNVs using FreeBayes and Longshot
 - SMS reads have better recall at high coverage (>40x), short reads better at lower (<30x)
 - SMS reads are far better at finding SNVs in segmental duplication regions (Recall: 0.86 vs 0.57)
 - BLASR much better aligner than BWA-Mem or minimap2 for SMS reads.
 - Simulated datasets estimate the theoretical fraction of the genome which is callable with long reads (99.4% at 30x)
 - Simulated datasets estimate the theoretical fraction of the genome which is callable with shirt reads (96.3% at 30x)
 
### Accurate SNV calling using whole-genome PacBio data
 - 4 well known pacbio samples from GIAB 
 - Also Illumina for the same samples
 - GQ threshold linearly proportional to the median read depth was used for filtering
 - Limit to GIAB high confidence regions
 - Steady __recall__ increase (0.9608 to 0.9798) with increased coverage (28x to 64x). 
 - __Precision__ only increased moderately (0.9930 to 0.9936)
 - i.e. coverage increase results in a lowering of false negatives but only slight lowering of false positives. 
 - __Does this mean that the false positives, presumably coming from sequencing & mapping errors need to be addressed in other ways?__
 - The __precision__ of Longshot is worse on real data than simulated data wrt to short read data.
 - False positives of Longshot are often close to an indel, i.e. dependant on the error rate of the technology.
 - False negative are more often in (>5) homopolymers (3.4 times the expected), the pair HMM realignment gives these lower quality scores.
 - Better precision than DeepVariant with similar Recall.
 - Clairvoyante better on high coverage, Longshot better otherwise. WhatsHap is third most often. __Variant Calling__
 - The phased genotyping/haplotype assembly step of Longshot is what makes it better, removing this step results in a drop of recall from 0.959 to 0.905.
 
### Accuracy of Longshot haplotypes
 - Median read lengths were 3587bp (NA12878) and 7235bp (NA24385)
 - N50 of 217.4kb (NA12878 Longshot) and 299.9kb (NA24385 Longshot 30x)
 - Switch error rates of 0.05% (NA12878) and 0.04% (NA24385)
 - Haplotype assigned reads had a median length of 4.3kb vs 2.6kb of those which were unassigned. i.e. longer reads are better.

### SNV calling using Oxford Nanopore reads
 - ONT reads are claimed as higher than PacBio
 - Context specific errors in ONT
 - Longshot had better F1 score than Nanopolish and much quicker.
 
### Analysis of SNV calls in repetitive regions
 - 55% more SNVs were called using SMS reads over Illumina. (Seg dup >95% similarity)
 - 90.3% of bases in segmentally duplicated (>95% similarity) regions were mapped in 45x Pacbio.
 - 4 fold greater SNV calling in segmental duplication regions with >99% similarity
 - Ts/Tv ratio is calculated as 1.9 via long reads and 1.5 with Illumina, expected to be 2.0-2.1 genome wide
 - Mendelian consistency of SNV calls, better in long reads. Many discordant calls clustered in contiguous blocks suggesting mismatched reads or Structural variation in the trio which has not been accurately resolved.
 - Platinum Genomes small variant set has a lot of regions which are not in GIAB. Outside the GIAB regions the concordance of calls dropped from 95.2% to 79.6%. Suggesting that the GIAB regions are great to have but are only a snapshot. 



## Discussion
 - Li et al. claimed that Pacbio is good for assembly at base pair level but not yet accurate enough to call heterozygotes in diploid mammalian genomes.
 - They claim that SNVs can be called using long reads via allelotyping and haplotype-informed genotyping
 - SNVs can be called in segmental duplication regions but is still a problem in regions with extremely high similarity between the duplications. 
 - SMS read mappers with specific optimizations for seg dup regions could help.
 - The GIAB and Platinum genomes datasets may represent regions which have a bias towards short reads since these projects were started with short reads in mind and don't include many seg dup regions. Thus, Longshot could be even better.
 - Recent paper identifies 5900 SNVs that are absent in the GIAB call sets. 
 - Most false positives by Longshot occur in regions with mis-called indels. 
 - Using haplotype separated reads could improve calling with Longshot
 - 


### Definitions
 - __Allelotyping:__ 
 - __Genotype Quality (GQ) threshold:__ The Genotype Quality represents the Phred-scaled confidence that the genotype assignment (GT) is correct, derived from the genotype PLs
 - __Switch error rate:__ Errors which 
 - __Pair HMM:__ Emmisions are paired for sequence alignment. https://web.stanford.edu/class/cs262/archives/notes/lecture8.pdf

### Input files

## Useful Figures
