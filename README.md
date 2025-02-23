## Table of contents
1. [Introduction](https://github.com/cgpu/rnaseq_tutorial#introduction)
  1. [Description of the lab](https://github.com/cgpu/rnaseq_tutorial#description-of-the-lab)
  2. [Requirements](https://github.com/cgpu/rnaseq_tutorial#requirements)
  3. [Compatibility](https://github.com/cgpu/rnaseq_tutorial#compatibility)
  4. [Data Set for IGV](https://github.com/cgpu/rnaseq_tutorial#compatibility)
2. [Visualization Part 1: Getting familiar with IGV](https://github.com/cgpu/rnaseq_tutorial#visualization-part-1-getting-familiar-with-igv)
  1. [Get familiar with the interface](https://github.com/cgpu/rnaseq_tutorial#get-familiar-with-the-interface)
    1. [Load a Genome and Data Tracks](https://github.com/cgpu/rnaseq_tutorial#load-a-genome-and-some-data-tracks)
    2. [Navigation](https://github.com/cgpu/rnaseq_tutorial#navigation)
  2. [Region Lists](https://github.com/cgpu/rnaseq_tutorial#region-lists)
  3. [Loading Read Alignments](https://github.com/cgpu/rnaseq_tutorial#loading-read-alignments)
  4. [Visualizing read alignments](https://github.com/cgpu/rnaseq_tutorial#visualizing-read-alignments)
3. [Visualization Part 2: Inspecting SNPs, SNVs, and SVs](https://github.com/cgpu/rnaseq_tutorial#visualization-part-2-inspecting-snps-snvs-and-svs-)
  1. [Neighbouring somatic SNV and germline SNP](https://github.com/cgpu/rnaseq_tutorial#neighbouring-somatic-snv-and-germline-snp)
  2. [Homopolymer repeat with indel](https://github.com/cgpu/rnaseq_tutorial#homopolymer-repeat-with-indel)
  3. [Coverage by GC](https://github.com/cgpu/rnaseq_tutorial#coverage-by-gc)
  4. [Heterozygous SNPs on different alleles](https://github.com/cgpu/rnaseq_tutorial#heterozygous-snps-on-different-alleles)
  5. [Low mapping quality](https://github.com/cgpu/rnaseq_tutorial#low-mapping-quality)
  6. [Homozygous deletion](https://github.com/cgpu/rnaseq_tutorial#homozygous-deletion)
  7. [Mis-alignment](https://github.com/cgpu/rnaseq_tutorial#mis-alignment)
  8. [Translocation](https://github.com/cgpu/rnaseq_tutorial#translocation)
4. [Visualization Part 3: Automating Tasks in IGV](https://github.com/cgpu/rnaseq_tutorial#visualization-part-3-automating-tasks-in-igv)


## Introduction 

### Description of the lab

Welcome to the lab for **Genome Visualization**! This lab will introduce you to the [Integrative Genomics Viewer]**(http://www.broadinstitute.org/igv/home)**, one of the most popular visualization tools for High Throughput Sequencing (HTS) data.

Lecture files that accompany this tutorial:
* [IGV Lecture - Brief](LectureFiles/cshl/2016/IGV_Tutorial_Brief.pdf)
* [IGV Lecture - Long, from Broad Institute](LectureFiles/cshl/2016/IGV_Tutorial_Long_BroadInstitute.pdf)

After this lab, you will be able to:
* Visualize a variety of genomic data
* Quickly navigate around the genome
* Visualize read alignments
* Validate SNP/SNV calls and structural re-arrangements by eye

Things to know before you start:
* The lab may take between **1-2 hours**, depending on your familiarity with genome browsing. Do not worry if you do not complete the lab. It will remain available to review later.
* There are a few thought-provoking **Questions** or **Notes** pertaining to sections of the lab. These are **optional**, and may take more time, but are meant to help you better understand the visualizations you are seeing. These questions will be denoted by boxes, as follows:
 **Question(s):**

```
Thought-provoking question goes here
```

### Requirements

* [Integrative Genomics Viewer](http://www.broadinstitute.org/igv/home)
* Ability to run Java
* Note that while most tutorials in this course are performed on the cloud, IGV will always be run on your **local** machine

### Compatibility

This tutorial was intended for **IGV v2.3**, which is available on the [IGV Download](http://www.broadinstitute.org/software/igv/download) page. It is *strongly* recommended that you use this version.

### Data Set for IGV
We will be using publicly available Illumina sequence data from the HCC1143 cell line. The HCC1143 cell line was generated from a 52 year old caucasian woman with breast cancer. Additional information on this cell line can be found here: <a href="http://www.atcc.org/products/all/CRL-2321.aspx">HCC1143</a> (tumor, TNM stage IIA, grade 3, primary ductal carcinoma) and <a href="http://www.atcc.org/products/all/CRL-2362.aspx">HCC1143/BL</a> (matched normal EBV transformed lymphoblast cell line).

* Sequence read alignments generated from a cell line HCC1143 that have been filtered to this region:
* Chromosome 21: 19,000,000-20,000,000
* [HCC1143.normal.21.19M-20M.bam](https://xfer.genome.wustl.edu/gxfer1/project/gms/testdata/bams/hcc1143/HCC1143.normal.21.19M-20M.bam)
* [HCC1143.normal.21.19M-20M.bam.bai](https://xfer.genome.wustl.edu/gxfer1/project/gms/testdata/bams/hcc1143/HCC1143.normal.21.19M-20M.bam.bai)

# Visualization Part 1: Getting familiar with IGV

We will be visualizing read alignments using [IGV](http://www.broadinstitute.org/igv/home), a popular visualization tool for HTS data.

First, lets familiarize ourselves with it.

## Get familiar with the interface

### Load a Genome and some Data Tracks

By default, IGV loads Human hg19. If you work with another version of the human genome, or another organism altogether, you can change the genome by clicking the drop down menu in the upper-left. For this lab, we will be using Human hg19.  

We will also load additional tracks from **Server** using (`File` -> `Load from Server...`):

* Ensembl genes (or your favourite source of gene annotations)
* GC Percentage
* dbSNP 1.3.1 or 1.3.7

**Load hg19 genome and additional data tracks**
![Load hg19 genome and additional data tracks](Images/IGV/load.data.tracks.png)

### Navigation

You should see listing of chromosomes in this reference genome. Choose ***1***, for chromosome 1.

**Chromosome chooser**
![Chromosome chooser](Images/IGV/chromosomes.png)


Navigate to **chr1:10,000-11,000** by entering this into the location field (in the top-left corner of the interface) and clicking `Go`. This shows a window of chromosome 1 that is 1,000 base pairs wide and beginning at position 10,000.

**Navigition using Location text field. Sequence displayed as thin coloured rectangles.**
![Navigition using Location text field. Sequence displayed as thin coloured rectangles.](Images/IGV/1.png)


IGV displays the sequence of letters in a genome as a sequence of colours (e.g. A = green, C = blue, etc.). This makes repetitive sequences, like the ones found at the start of this region, easy to identify. Zoom in a bit more using the `+` button to see the individual bases of the reference genome sequence.

You can navigate to a gene of interest by typing it in the same box the genomic coordinates are in and pressing Enter/Return. Try it for your favourite gene, or *BRCA1* if you can not decide. 

**Gene model**<br>
![Gene model](Images/IGV/gene_model.png)

Genes are represented as lines and boxes. Lines represent intronic regions, and boxes represent exonic regions. The arrows indicate the direction/strand of transcription for the gene. When an exon box become narrower in height, this indicates a UTR.

When loaded, tracks are stacked on top of each other. You can identify which track is which by consulting the label to the left of each track.

## Region Lists

Sometimes, it is really useful to save where you are, or to load regions of interest. For this purpose, there is a **Region Navigator** in IGV. To access it, click `Regions` > `Region Navigator`. While you browse around the genome, you can save some bookmarks by pressing the `Add` button at any time.

**Bookmarks in IGV**<br>
![Bookmarks in IGV](Images/IGV/bookmarks.png)

## Loading Read Alignments
We will be using the breast cancer cell line HCC1143 to visualize alignments. For speed, only a small portion of chr21 will be loaded (19M:20M). 

**HCC1143 Alignments to hg19:** 
* [HCC1143.normal.21.19M-20M.bam](https://xfer.genome.wustl.edu/gxfer1/project/gms/testdata/bams/hcc1143/HCC1143.normal.21.19M-20M.bam)
* [HCC1143.normal.21.19M-20M.bam.bai](https://xfer.genome.wustl.edu/gxfer1/project/gms/testdata/bams/hcc1143/HCC1143.normal.21.19M-20M.bam.bai)

Copy the files to your local drive, and in IGV choose `File` > `Load from File...`, select the bam file, and click `OK`. Note that the bam and index files must be in the same directory for IGV to load these properly.

**Load BAM track from File**
![Load BAM track from File](Images/IGV/load_bam.png)

## Visualizing read alignments

Navigate to a narrow window on chromosome 21: `chr21:19,480,041-19,480,386`.

To start our exploration, right click on the track-name, and select the following options:
* Sort alignments by `start location`
* Group alignments by `pair orientation`

Experiment with the various settings by right clicking the read alignment track and toggling the options. Think about which would be best for specific tasks (e.g. quality control, SNP calling, CNV finding).

**Changing how read alignments are sorted, grouped, and colored**<br>
![Changing how read alignments are sorted, grouped, and colored](Images/IGV/sort_and_group.png)

You will see reads represented by grey or white bars stacked on top of each other, where they were aligned to the reference genome. The reads are pointed to indicate their orientation (i.e. the strand on which they are mapped). Mouse over any read and notice that a lot of information is available. To toggle read display from `hover` to `click`, select the yellow box and change the setting.

**Changing how read information is shown (i.e. on hover, click, never)**
![Changing how read information is shown (i.e. on hover, click, never)](Images/IGV/show_details_on_click.png)

Once you select a read, you will learn what many of these metrics mean, and how to use them to assess the quality of your datasets.  At each base that the read sequence **mismatches** the reference, the colour of the base represents the letter that exists in the read (using the same colour legend used for displaying the reference).

**Viewing read information for a single aligned read**
![Viewing read information for a single aligned read](Images/IGV/click_read.png)

# Visualization Part 2: Inspecting SNPs, SNVs, and SVs

In this section we will be looking in detail at 8 positions in the genome, and determining whether they represent real events or artifacts.

## Two neighbouring SNPs

* Navigate to region `chr21:19,479,237-19,479,814`
* Note two heterozygous variants, one corresponds to a known dbSNP (`G/T` on the right) the other does not (`C/T` on the left)
* Zoom in and center on the `C/T` SNV on the left, sort by base (window `chr21:19,479,321` is the SNV position)
* Sort alignments by `base`
* Color alignments by `read strand`

**Example1. Good quality SNVs/SNPs**
![Example1. Good quality SNVs/SNPs](Images/IGV/example1_color.png)

**Notes:**
* High base qualities in all reads except one (where the alt allele is the last base of the read) 
* Good mapping quality of reads, no strand bias, allele frequency consistent with heterozygous mutation

**Question(s):**
```
* What does *Shade base by quality* do? How might this be helpful?
* How does Color by *read strand* help?
```

## Homopolymer region with indel

Navigate to position `chr21:19,518,412-19,518,497`

**Example 2a**
* Group alignments by `read strand`
* Center on the `A` within the homopolymer run (`chr21:19,518,470`), and `Sort alignments by` -> `base`

![Example 2a](Images/IGV/example2a.png)


**Example 2b**
* Center on the one base deletion (`chr21:19,518,452`), and `Sort alignments by` -> `base`

![Example 2b](Images/IGV/example2b.png)

**Notes:**
* The alt allele is either a deletion or insertion of one or two `T`s
* The remaining bases are mismatched, because the alignment is now out of sync
* The dpSNP entry at this location (rs74604068) is an A->T, and in all likelihood an artifact 
* i.e. the common variants from dbSNP include some cases that are actually common misalignments caused by repeats

## Coverage by GC

Navigate to position `chr21:19,611,925-19,631,555`. Note that the range contains areas where coverage drops to zero in a few places.

**Example 3**
* Use `Collapsed` view
* Use `Color alignments by` -> `insert size and pair orientation`
* Load GC track 
* See concordance of coverage with GC content

![Example 3](Images/IGV/example3.png)

**Question:**
```
* Why are there blue and red reads throughout the alignments?
```

## Heterozygous SNPs on different alleles

Navigate to region `chr21:19,666,833-19,667,007`

**Example 4**
* Sort by base (at position `chr21:19,666,901`)

![Example 4](Images/IGV/example4.png)

**Note:**
* There is no linkage between alleles for these two SNPs because reads covering both only contain one or the other

## Low mapping quality 

Navigate to region `chr21:19,800,320-19,818,162`
* Load repeat track (`File` -> `Load from server...`)

**Load repeats**<br>
![Load repeats](Images/IGV/load_repeats.png)

**Example 5**
![Example 5](Images/IGV/example5.png)

**Notes:**
* Mapping quality plunges in all reads (white instead of grey).  Once we load repeat elements, we see that there are two LINE elements that cause this.

## Homozygous deletion

Navigate to region `chr21:19,324,469-19,331,468`

**Example 6**
* Turn on `View as Pairs` and `Expanded` view
* Use `Color alignments by` -> `insert size and pair orientation`
* Sort reads by insert size
* Click on a red read pair to pull up information on alignments

![Example 6](Images/IGV/example6.png)

**Notes:**
* Typical insert size of read pair in the vicinity: 350bp
* Insert size of red read pairs: 2,875bp
* This corresponds to a homozygous deletion of 2.5kb

## Mis-alignment

Navigate to region `chr21:19,102,154-19,103,108`

**Example 7**
![Example 7](Images/IGV/example7.png)

**Notes:**
* This is a position where AluY element causes mis-alignment.  
* Misaligned reads have mismatches to the reference and well-aligned reads have partners on other chromosomes where additional ALuY elements are encoded.
* Zoom out until you can clearly see the contrast between the difficult alignment region (corresponding to an AluY) and regions with clean alignments on either side

## Translocation

Navigate to region `chr21:19,089,694-19,095,362`

**Example 8**
* Expanded view
* `Group alignments by` -> `pair orientation`
* `Color alignments by` -> `pair orientation`

![Example 8](Images/IGV/example8.png)

**Notes:**
* Many reads with mismatches to reference
* Read pairs in RL pattern (instead of LR pattern)
* Region is flanked by reads with poor mapping quality (white instead of grey)
* Presence of reads with pairs on other chromosomes (coloured reads at the bottom when scrolling down)

# Visualization Part 3: Automating Tasks in IGV

We can use the Tools menu to invoke running a batch script. Batch scripts are described on the IGV website:
* Batch file requirements: https://www.broadinstitute.org/igv/batch
* Commands recognized in a batch script: https://www.broadinstitute.org/software/igv/PortCommands
* We also need to provide sample attribute file as described here: http://www.broadinstitute.org/software/igv/?q=SampleInformation

Download the batch script and the attribute file for our dataset:
* Batch script: [Run_batch_IGV_snapshots.txt](https://raw.githubusercontent.com/cgpu/rnaseq_tutorial/master/scripts/Run_batch_IGV_snapshots.txt)
* Attribute file: [Igv_HCC1143_attributes.txt](https://raw.githubusercontent.com/cgpu/rnaseq_tutorial/master/scripts/Igv_HCC1143_attributes.txt)

Now run the file from the `Tools` menu:

**Automation**
![Automation](Images/IGV/run_batch_script.png)

**Notes:**
* This script will navigate automatically to each location in the lab
* A screenshot will be taken and saved to the screenshots directory specified

## Contributors/acknowledgements

This tutorial is forked from the wiki of [griffithlab/rnaseq_tutorial](https://github.com/griffithlab/rnaseq_tutorial)

The contributors are listed below:
Malachi Griffith, Sorana Morrissy, Jim Robinson, Ben Ainscough, Jason Walker, Obi Griffith
