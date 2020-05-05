# Barcode identification for single cell genomics

## Software 
### Provided
- Sircel
### Used
- kalisto

## Data and technologies used

### Simulated
- Single cell data: Simulated and real
- Simulated data has poisson errors at uniformly random positions.
- Separate simulated datasets for mismatch, insertion, deletion and all errors.
- Varied the barcode abundance alters the ability to detect and correct barcodes
- Edit distance to assign reads leads to greater rate of correct read assigments

### Real data
- some existing species mixing drop-Seq data
- Similar experiment for Seq-Well protocol (both human and mouse)



## Sources and related Papers

## Methods
- Circularize bacodes
- take an extra base for insertion detection
- take one less base for deletion detection
- take normal barcode length for mismatch detection
- Count kmers
- Construct a directed, weighted deBruijn graph
- - nodes representsubsequences of length k-1
- - edges represent nodes adjacent in at least 1 k-mer
- - weights represent the number of times these k-mers were adjacent in the whole dataset
- - direction of k-mers can be identified in experiments with stranded-ness 
- Capacity defined as the minimum weight of an edge within a path
- In short, traverse the graph in order to find loops which are the same size as k and start and end at the same node.


## Results

- Can identify the error-free barcode sequences independent of the number of errors per read.
- mismatch errors are better tolerated than insertion and deletion errors.
- barcode abundance distribution hugely affects the correction of errors.
- 

## Discussion



### Definitions
__Levenschtein distance:__ The edit distance. Not to be confused with the hamming distance.

### Input files

## Useful Figures

## Notes or interesting claims
- up to 25% of barcodes have an error? reference 10.

## Questions/problems
- Are single cell setups more prone to non-sequencing errors? 
- Inflection point is going to work on all datasets?
- No use of the whitelist? No need?
