# Internship-bachelorthesis

1. On the first week:

Few notes of interest, with detailled explanation coming from the Galaxy pipeline tutorial (will have to source everything into []).

Tuesday 04/02/2020    | Galaxy Sequence duplication level Fastqc     | (galaxy tutorial)[[[[[[[[[[[ 

In a diverse library most sequences will occur only once in the final set. A low level of duplication may indicate a very high level of coverage of the target sequence, but a high level of duplication is more likely to indicate some kind of enrichment bias.

Two sources of duplicate reads can be found:

    PCR duplication in which library fragments have been over-represented due to biased PCR enrichment

    It is a concern because PCR duplicates misrepresent the true proportion of sequences in the input.

    Truly over-represented sequences such as very abundant transcripts in an RNA-Seq library

    It is an expected case and not of concern because it does faithfully represent the input.

FastQC counts the degree of duplication for every sequence in a library and creates a plot showing the relative number of sequences with different degrees of duplication. There are two lines on the plot:

    Blue line: distribution of the duplication levels for the full sequence set
    Red line: distribution for the de-duplicated sequences with the proportions of the deduplicated set which come from different duplication levels in the original data.

For whole genome shotgun data it is expected that nearly 100% of your reads will be unique (appearing only 1 time in the sequence data). Most sequences should fall into the far left of the plot in both the red and blue lines. This indicates a highly diverse library that was not over sequenced. If the sequencing depth is extremely high (e.g. > 100x the size of the genome) some inevitable sequence duplication can appear: there are in theory only a finite number of completely unique sequence reads which can be obtained from any given input DNA sample.

More specific enrichments of subsets, or the presence of low complexity contaminants will tend to produce spikes towards the right of the plot. These high duplication peaks will most often appear in the blue trace as they make up a high proportion of the original library, but usually disappear in the red trace as they make up an insignificant proportion of the deduplicated set. If peaks persist in the red trace then this suggests that there are a large number of different highly duplicated sequences which might indicate either a contaminant set or a very severe technical duplication.

It is usually the case for RNA sequencing where there is some very highly abundant transcripts and some lowly abundant. It is expected that duplicate reads will be observed for high abundance transcripts:

]]]]]]]]]] 

  Tuesday 04/02/2020    | Galaxy per base quality score Fastqc         | 

The explanation of the quality score is similar to the one we had during our classes with Mr Coornaert, although here there are some details that helps in having a better understanding of how it works, and so it will allows people to do better analysis.

These details are :
(galaxy tutorial)[[[[[[[ Per base sequence quality score

    Signal decay

The fluorescent signal intensity decays with each cycle of the sequencing process. Due to the degrading fluorophores, a proportion of the strands in the cluster are not being elongated. The proportion of the signal being emitted continues to decrease with each cycle, yielding to a decrease of quality scores at the 3’ end of the read.

    Phasing

The signal starts to blur with the increase of number of cycles because the cluster looses synchronicity. As the cycles progress, some strands get random failures of nucleotides to incorporate due to:

    Incomplete removal of the 3’ terminators and fluorophores
    Incorporation of nucleotides without effective 3’ terminators
This leads to a decrease in quality scores at the 3’ end of the read.



    Overclustering

   Sequencing facilities can overcluster the flow cells. It results in small distances between clusters and an overlap in the signals. Two clusters can be interpreted as a single cluster with mixed fluorescent signals being detected, decreasing signal purity. It generates lower quality scores across the entire read.

    Instrumentation breakdown

   Some issues can occasionally happen with the sequencing instruments during a run. Any sudden drop in quality or a large percentage of low quality reads across the read could indicate a problem at the facility. Some examples of such issues (expalining graph in the tutorial, will need to cite it as a source):

        Manifold burst


        Cycles loss

        Read 2 failure

   With such data, the sequencing facility should be contacted for discussion. Often, a resequencing then is needed (and from our experience also offered by the company).
]]]]]]]]]]]]

Wednesday 05/02/2020  | Articles reading and understanding of Galaxy | 

- 1-s2.0-S0092867415013537-main.pdf

- 2018_Svenson-scRNA-seq.pdf

- krnb-14-05-1201618.pdf

- scmethods.pdf

Need to look at the DE tutorials in Galaxy. 

 Friday 07/02/2020     | Samples for test on Galaxy                   | 

I took the SRA files, from this study "Transcriptome analysis of MCF-7 breast cancer cell population to reveal the transcriptional diversity at the single cell level".
I'm still reading how they processed, and i'll try later on to reproduce the results for my first step in Galaxy, i'll begin to do so on Monday next week, maybe during the week-end.


2. On the second week:

    Monday 10/02/2020     | Process of Data                   | 

(From Single cell transcriptome analysis of MCF-7 reveals consistently and inconsistently expressed gene groups each associated with distinct cellular localization and functions)
[
Data processing comprised the following steps: quality sequence extraction, decontamination, mapping with Tophat, and gene annotation with Cufflinks.

In more detail, we used a cutoff value of 5 in the ‘remove reads containing color quality below this value’ parameter selection box to select quality reads. Sequence reads containing vector sequences or homopolymers (≥ 9 bp) were discarded. 

Quality reads were mapped to hg19 with Tophat originally designed for short read alignment for RNA-Seq experiments. We allowed two mismatches for each 35 bp read. ‘Minimum isoform fraction: filter out junctions supported by too few alignments’ was set to zero, and all other parameters were retained as default. 

Sequence reads with ≤ 10 hits were used and subjected to Cufflinks for annotation. To maximize sensitivity, both ‘min-isoform fraction’ and ‘pre-MRNA fraction’ were set to 0.0, and the parameter for ‘max-intron-length’ was changed from 300,000 to 500,000. 

To exclude singleton transfrags (transcribed fragments), we changed ‘min-frags-per-transfrag’ from 10 to 2 in program coding. All the other Cufflinks parameters were retained as default.
]

   Tuesday 11/02/2020 	|Presentation of a PhD student 	|

The subject of the PhD student was on the property of essential oils to prevent the growth of bacteria. The presentation was done in Slovakian, so i didn't understood everything she said. I'll have to read her article, which can be freely accessed through google scholar.

   Tuesday 11/02/2020 	|Presentation of the methods in this article: "High-throughput targeted long-read single cell sequencing reveals the clonal and transcriptional landscape of lymphocytes"|

Lubos just asked me to prepare a brief summary of this article, and to present it in a few days.
