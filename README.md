# Gene regulatory network analysis

Software for the creation and analysis of Gene Regulatory Networks (GRNs)

Requirements
----------
Python packages:
* Numpy
* Pybedtools
* Networkx
* Json

Software:
* Homer
* Cytoscape

Basic Usage
----------
## <b>build_gene_regulatory_network.py</b> - The main script for building a GRN

python build_gene_regulatory_network.py \<BED file of regulatiry elements\> \<Motif position directory\> \<Gene expression file\> \<TF annoation file\> \<Output file\>

##### Required files
1. A BED file of regulatory elements, such as DNaseI or ATAC-Seq sites that are to be included in the GRN. Sites must be annotated to their associated gene, which should be included as the 4th column in the BED file.
2. A directory of BED files with the genomic coordinates for each TF motif to be included in the GRN. This can be created using the <b>findMotifs.py</b> script included with this software
3. Gene expression data file (tab-delimited) with gene ID (1st column) and gene expression value (e.g. FPKM; 2nd column)
4. Transcription Factor (TF) annotation file with gene ID and name of the motif it can bind to. An annotation file (TF_family_gene_annotation.tsv) is provided with this software.

##### Optional Arguments
<b>-a</b> By default this will build a GRN which only includes transcription factor genes. If you would like to build the full network, which includes all genes, use the <b>-a</b> option<br>
<b>-f</b> An optional BED file of DNaseI/ATAC-Seq footprints to filter the motif positions against<br>
<b>-m</b> Minimium gene expression value for genes to include in the network. Default = 0 (include everything)

##### Output file
The output file is a Cytoscape JSON file (.cyjs) which can be opened and manipulated in Cytoscape

## <b>findMotifs.py</b> - Find the genomic positions for a set of transcription factor binding motifs

python findMotifs.py \<BED file to use for motif search\> \<Directory of motif PWMs to search for\> \<Genome version (e.g. hg38, mm10)\> \<Output directory\>

##### Required files
1. BED file of sites to use for the motif search
2. A directory of Homer compatible motif probabilty weight matrices files. A set of PWMs used in Assi et al (2019) are provided in motif_PWM_database
3. Genome version to use with Homer (e.g. hg38, mm10 etc.)

##### Output
A directory of BED files containing the aligned motif positions



