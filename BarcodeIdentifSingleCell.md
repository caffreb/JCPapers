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

## Questions/problems
- Are single cell setups more prone to non-sequencing errors? 
- Inflection point is going to work on all datasets?
- No use of the whitelist? No need?
