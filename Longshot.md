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

## Data and technologies used
 - Genome in a bottle (GIAB) Pacbio data NA12878 (45x) and Ashkenazi trio (NA24385 (64x), NA24149 (29x) and NA24143 (27x) )


## Sources and related Papers

## Methods

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
 
 



## Discussion



### Definitions
 - __Allelotyping:__ 
 - __Genotype Quality (GQ) threshold:__ The Genotype Quality represents the Phred-scaled confidence that the genotype assignment (GT) is correct, derived from the genotype PLs
 - __Switch error rate:__ Errors which 

### Input files

## Useful Figures
