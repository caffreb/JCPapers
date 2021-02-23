# Towards a reference genome that captures global genetic diversity

## Software 
### Provided
### Used 
- Supernova (assembly)
- Paragraph (SV detection tool)
- GATK HaplotypeCaller

## Data and technologies used
- PacBio haploid assemblies on 7 human and 2 hydatidiform mole genomes
- 10xG linked reads 
- NCBI RefSeq genes
- gene predictions database
- GTEx RNA-Seq data




## Sources and related Papers

## Methods

## Results

### Human genome sequencing, de novo assembly, and optical mapping.
- 10x Genomics (10xG) whole-genome Linked-Reads were generated in-house on 305 samples. 24 publicly available Linked-Read data sets, polaris and 10xG (2 samples)
- ~60× coverage, with a mean inferred molecular length of 95.6kb
- Average scaffold, and phased block N50s of 39.3 and 4.6Mb respectively
- All data presented here were based on a combined set of 338 genomes
- BioNano optical maps for 309 samples using a combination of BspQ1, BssS1, and DLE1 enzymes

### Identification and characterization of recurrent non-reference unique insertion.
- In total, we identified across different human populations 127,727 recurrent NUIs spanning 18,048,877bp.
- For every genome sequenced with Linked-Reads, we found on average 14,121 NUIs (2,642,883 bp)
- NUIs are biased towards the sub-telomeric and peri-centromeric regions of the chromosomes 
- While 86.9% (110,996) of the NUIs were small (<50 bp), they only made up 9.7% (1.7 Mb) of the overall cumulative length
- 7801 NUIs ≥350 bp with a cumulative length of 14.3 Mb (79.5% of total)
- NUIs (≥1 kb) account for 12.2 Mb (67.9%) of the cumulative length, only 3361 of them (2.6% of total).
- PacBio sequences contributed 2.7% to the small NUI total bases (<50 bp), which roughly equal to the proportion of PacBio sample in the collection
- In contrast, since our pipeline favors sequences that can be fully resolved, PacBio sequences contributed 20% of the large NUI category (≥50 bp). 
- 10xG assemblies often shared these insertions but, due to their inherent limitation in read length, they failed to resolve the entire NUIs in low complexity regions.
- African samples, highest representative NUI contribution proportional to their sample size, almost twice as many

- performed a saturation analysis on the large NUIs.
- To evaluate NUI specificity, we compared the large NUIs ≥1 kb with no undetermined bases chosen for inclusion in the HDR using Bionano optical maps.
- in all, 86.2% of these variants were concordant with insertions identified by Bionano optical mapping on the basis of size and location
- Within our NUI data set, 84.4% and 63.5% of the small and large NUIs, respectively, were never discovered in any of the PacBio samples (Supplementary Fig. S5a).
-  A small proportion of the large NUIs (1.3%) was found only in PacBio samples, suggesting that some of these NUIs were only resolvable by long reads. 
-  We Found that 69.3% of the large NUIs was novel, as compared to 53.1% of the small NUIs. when compared to 1KGP and GNOMAD


### Non-reference unique insertions affecting genic and regulatory elements.
- identified 59,332 NUIs overlapping genic loci.
- Among these, 521 recurrent NUIs are in coding exons, 1738 in 3′UTR, 1200 in 5′UTR, and 55,878 in introns.
- As expected, only 5% of genes affected by out-of-frame small exonic NUIs are extremely intolerant to loss-of-function changes
- Figure 2. Describe

### Detailed genomic analysis of exonic insertions.
- took a closer examination of four insertions affecting coding sequences.
-  METTL21C, an identical amino acid sequence in the same gene in the chimpanzee RefSeq protein database (ID: XP_009425476.2), indicating that this insertion is conserved and thus likely to be ancestral and functional.
-  Figure 3.
-  identified two alternate splicing events in the inserted sequence upstream of the original start codon 
-  Using the HDR, RNA-Seq reads from GTEx can now be mapped precisely across this junction  


### Mapping improvement and the identification of novel poly- morphic site in the Human Diversity Reference.
- aligned sequences from 70 Simons Genome Diversity Project (SGDP) to ref and HDR
- On average, 402,573 previously unmapped reads from each individual could be aligned to the HDR (~40x)
- In other words, for every gained read, only 0.16 read is lost.
- an average of 27,658 SNPs and 11,219 indels in the NUIs.
- Africans have 5238 and 929 more SNPs and indels than the non-African averages. Significant compared to all other groups
- 

### Transcriptomic analysis using previously unmapped reads.
- identified unique RNA-seq read alignment in 4781 genes across all tissues
- 77% of genes have OMIM annotations implying functional importance

### Tissue-specific gene expression analysis.
- Figure 4a, Testes with most DE genes. Stomach with fewest
- GO analysis. Chemical synaptic transmission, neurotransmitter transport, and nervous system development were among the most significant enriched terms in the brain. 
- In the spleen, immune-related processes were significantly enriched while epidermis development genes were among the top in the skin.
- Taken together, these results highlight the transcriptomic diversity found within the NUIs


### Gap closing on the reference genome.
- We targeted 539 gaps in the core reference assemblies for gap closure. We fully filled 220 gaps and minimized an additional 13 (43%)
- Figure 1.

## Discussion
- Need more diversity in sequences samples


### Definitions
- HDR: Human Diversity Reference

### Input files

## Useful Figures



## Notes or interesting claims

## Links to descriptions

## Questions/problems

Return to [JC start](../../)
