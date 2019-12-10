# Data
- minIon sequencing of 2 patients with chromotripsis. Mental retardation and dysmorphic features
- Parental data for both patients
- Long insert jumping library sequencing
- SNP data from GATK PBT of trio data 
- NA12878 MinION samples

# Software and Databases used
- LAST (mapping)
- Delly and Manta for SV calling on Illumina
- Sniffles, Lumpy and NanoSV for MinION
- NanoSim for simulated data
- Pindel, Manta, Delly, FREEC, Mobster, GATK HaplotypeCaller
- DFAM database: transposable elements.
- Whatshap: Haplotyping

# Measures and Terms
- Percentage of identity (PID): The percentage of identical bases between mapped reads and reference genome 
- Karyotpying: The imaging of chromosomes and analysis of the shapes etc. (non-sequencing performed by a cytogeneticist??)
- Random Forest used for extra precision on SV calls. Verified on 1KG and PB data from NA12878
- Phase connection: the relative phase between two consecutive heterozygous SNVs
- N50 etc.
- read based and population based phasing
- Switch errors: Errors in phasing, e.g. when switching incorrectly from paternal to maternal


# Results
- Percentage of identity (PID) : 90% and 85% for 2 patients
- 15% of errors were indel errors
- 5.1% mismatches
- 16x and 11x coverage respectively
- Results support a paternal origin of chromotripsis
- Whole genome SV detection lead to 36,959 and 36,321 variants (including simple repeats etc.)
- 8578 and 6791 SVs after removal of simple repeats and homopolymers
- Validated 274 and 77 SVs with precision of 95 and 96% respectively
- 14% of SVs were found via Nanopore which were not found via short reads
- Nanopore specific sites are on average located at sites with higher GC content (mentioned less GC bias relative to Illumina)
- SINE elements less abundant in Nanopore data
- Many more short deletions discovered than short read data. Expected due to short reads.
- Many more LINE insertions, again expected.
- Many errors in the homopolymer regions as expected by MinION
- All known breakpoints found for patient 1. not for patient 2 but with lower coverage.

# Questions
- Is karyotyping just this simple picture thing?
- Why no sensitivity for Patient 2?
- Precision of only 2%?????
- Important to think about the proportion of LINES/SINES correctly
- Fig5 b & c??
- Discussion red section??
- What are the differences in the kits which are used?

- Are such rearrangements thought to be common? i.e. do similar phenotypes have similar rearrangements? Similar locations?
