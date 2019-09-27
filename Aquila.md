
# Aquila stLFR - pipeline for stLFR variant calling and/or hybrid approach used in tandem with 10s linked reads


## Software used 

 - bwa mem for mapping
 - SPAdes for assembly
 - Freebayes for vcf file creating
 - minimap2 and paftools for hybrid mode
 - QUAST

## Data and technologies used
 - stLFR from MGI
 - 10x linked reads from 10x Genomics

## Sources and related Papers
 - https://github.com/maiziex/Aquila_stLFR
 - https://github.com/maiziex/Aquila
 - https://www.biorxiv.org/content/10.1101/660605v1

## Methods

 - Reference-assisted local de novo assembly pipeline
 - reference used to bin long fragments
 - Figure 1 pipeline
 - local assembly performed on small phased chuncks
 - Barcode deconvolution....2 long frags with the same barcodes need to be separated (>50kb distance between nearest locations)


### Haplotyping algorithm
 - Recursive clustering algorithm to perform haplotyping reconstructed LFRs
 - Uses 01, 10 notation for alleles 
 - 00 and 11 ican exist and are ruled out using Bayesian probability model
 - recursively aggregates small clusters into big clusters for each haplotype
 - Merging error percentage .....
 - again with 5.... 


### Linear local assembly
 - Using Aquila, diploid personal genome assembly using linked reads
 - breaks large phase blocks into smaller chunks based on high confidence boundary point profiles
 - Consists of human genomic regions not overlapping with repeats and with sufficient reads. 
 - Linear local assembly using SPAdes

### High conf boundary points
 - Umap from hoffmann mappability
 - use a k to generate all k-mers
 - use Bowtie to map kmers
 - only keep regions with kmers which map uniquely

### Assembly based variant calling
 - using minimap2 and paftools call variants from haploid assemblies
 - Pairwise comparison between breakpoints of variants from two haploid assemblies
 - 


### Hybrid assembly for stLFR and 10x linked reads
 - Aquila hybrid used to create the same structures as for the stLFR reads
 - Performs efficient haplotyping
 - Based on phasing information, if the phase block length is beyond a threshold (200kb)
 - Merges reads from both chunks of different technologies

### Barcode 0_0_0
 - Very confusing?


## Results

### Characteristics of Aquila_stLFR and Aquila_hybrid assemblies
 - 2 stLFR libraries and 2 10x libraries
 - optimal coverage is between 332X and 823X
 - optimal W_uFL: 50-150kb
 - 10x looks clearly better. Larger reads.
 - N50 comparison, NA50

### Assembly based detection of SNPs and small indels in diploid assemblies
 - reference based calls and assembly based calls roughly equal at 3.8m
 - Sensitivities of assembly based calls are around 94%
 - Again the GiaB stat comes up, it is correct but not complete.
 - Genomtype errors are 0.772-1.172%
 - indels of mod2 are more common than -1/+1 ??? Why?
 - Sensitivity of small indels is ~83%
 - genotype errors of ~3%

### Assembly based detection of SVs
 - 13400 SVs
 - No bias to the type of SVs which are discovered Fig S4
 - 27% of stLFR SVs overlap with 33% of 10x
 - hybrid assemblies have a bias towards 10x reads.
 - Table 5

## Discussion
 - Key is that Aquila_stLFR guarantees a diploid assembly (why? because it ignores repeats?)
 - low u_FL is a key factor causing lower contiguity
 - Provide a high confidence set by using hybrid approach

 



### Definitions
 - **stLFR:** single tube Long Fragment Read 
 - **N50:** Defines the assembly quality in terms of contiguity. N50 is defined as the sequence length of the shortest contig at 50% of the total genome. i.e. Sort the contigs by size. Start adding their lengths together, when you go over (Genome Length)/2 then note the length of the contig that knocked you over.
 - **NA50:** aligned N50, i.e. map all contigs to the reference, split those that map erronously and make new contigs, map those. It's the N50 of these split aligned contigs. NA50 is always <= N50
 - **C_F:** Average coverage of the genome by long fragments
 - **C_R:** Read coverage per fragment 
 - **N_F:** number of fragments per partition
 - **u_F:** average unweighted DNA fragment length
 - **W_uFL:** Weighted fragment length. 
 - **Phasing:** The process of assigning alleles to the paternal or maternal chromosomes.


### Input files

Raw paired reads in fastq format.
Bam file (from bwa mem)
VCF file (from FreeBayes)

## Useful Figures

### stLFR experimental protocol

![](../IMAGES/stLFR.jpg)

### stLFR barcodes
![](../IMAGES/stLFR-bars.png)
 - 1538 uniq 10-mer barcodes
 - 3.6 billion barcode options

### 10x barcodes
![](../IMAGES/10x-barcodes.png)
 - 4.7 million uniq 16-mer barcodes

