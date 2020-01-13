
# Structural variants identified by Oxford Nanopore PromethION sequencing of teh human genome

## Software 
### Provided
 - github.com/wdecoster/nano-snakemake
 
### Used 
#### Mappers
 - NGMLR
 - minimap2
 - LAST
 - bwa-mem
 #### SV callers
 - SVIM
 - MANTA
 - LUMPY
 - Sniffles
 - npInv (inversion specific caller)


## Data and technologies used

### Tech
 - Oxford Nanopore (ONT)

### Data
 - NA19240 (lymphoblastic cell line)
 

## Sources and related Papers

## Methods

## Results

### Comparing MinION and PromethION
- PromethION has greater identity of mapped reads, i.e. fewer sequencing errors.
- 88.8% vs 84.7%

### Comparing aligners
 - mapping leads to very similar median identity levels
 - LAST maps more shorter reads
 - NGMLR has better identity Fig2b shows a little dot at top of violin
 - use minimap2 with pbsv params (best mapping)
 - minimap2 and LAST have best coverage, NGLMR is lowest.
 - All callers were better at deletions than gain of sequence events.

  - 

### SV calling
 - Sniffles is best if used with minimap2 or NGMLR
 - SVIM performance is independant of mapper
 - Sniffles often misclassifies zygocity
 - 

### Combining call sets
 - Using all callers together yields best results
 - Still many of the callers overlap in their false positives, suggesting that something is still wrong with the theoretical setup of the algorithms/tech

### Parameter optimization
 - Number of supporting reads has big effects
 - 1/4 or 1/3 of the median genome coverage was a good cut-off

### Description of detected variables
 - Nothing huge here
 

## Discussion

 - Use a modern aligner
 - Use long read tuned callers
 - Use Sniffles and SVIM callers is the take home
 - Inversions are dreadful


### Definitions

### Input files

## Useful Figures
