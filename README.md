# cFLSeq

# 1. Introduction

cFLSeq v1.0.0 (circRNA full-length sequences) is a computational tool that utilizes both back-splice junction (BSJ) and junction contig (JC) features to reconstruct full-length sequences of circular RNAs from RNA-seq datasets. cFLSeq integrates junction reads and junction contigs for the assembly of all circRNAs. The BSJ feature is employed to accurately determine the boundaries of circRNAs, while the JC feature acts as an extension of junction reads, exhibiting superior performance in assembling circRNAs with low expression levels.

# 2. Prerequisites

> ### Software Prerequisites:
>> cFLSeq is implemented in perl under Linux system.

>> A de novo transcript assemlers (one of them)
* [Trinity](https://github.com/trinityrnaseq/trinityrnaseq)
* [SPAdes](https://github.com/ablab/spades)
* [SOAPdenovo-Trans](https://github.com/aquaskyline/SOAPdenovo-Trans)

>> Aligner
* [BWA](https://sourceforge.net/projects/bio-bwa/files/)

> ### Input files:
>> cFLSeq works with six input files. A GTF annotation file, pair-end RNA-seq data, a contig file was generated from Trinity, a genome sequence file, and a circRNA junction list.

>>> Contig file can be obtained by de novo transcript assemblers
>>>> Trinity (trinity/inchworm.DS.fa)
>>>> SPAdes (spades/K31/transcripts.fasta)
>>>> SOAPdenovo-Trans (SOAP/soap.contig)

>>> CircRNA lists containing circRNA location (chromosome, start, end), host gene, strand, junction reads ID. 

# 3. Usage 

```bash
	Command:
		-C circ -G genome -F annotation -O out_dir -P 8 --read1 read_1.fq --read2 read_2.fq --contig contig.fa
	Arguments:

    -C, --circ
          input circRNA file, which including chromosome，start site, end site, host gene, and junction reads ID (required).
    -O, --output
          directory of output (required).
    -G, --genome
          FASTA file of all reference sequences. Please make sure this file is
          the same one provided to prediction tool (required).
    -F, --annotation
          gene annotation file in gtf format. Please make sure this file is
          the same one provided to prediction tool.
    -P, --thread
          set number of threads for parallel running (required).
    --read1
          RNA-Seq data, read_1 (paired end, fastq format).
    --read2
          RNA-Seq data, read_1 (paired end, fastq format).
    --contig
          contig sequences (required).
    -H, --help
          show this help information.
```
		  
# 4. Note

> * The RNA-seq data shoule be paired end, and same file when running de novo assemlby.
> * cFLSeq use the GTF annotation file with UCSC compatable GTF format. <br>
> * The GTF annotation file should be the same one when running cFLSeq and its upstream softwares. <br> 

# 5. Output file

> * Two columns of fragment_final.txt (split by tabs)
	1) circRNA location
	2) Location of circRNA fragments on genome

> * circ_full_seq.fa is assembly result of circRNA full length sequences.

# 6. Reference
[article](https://www.sciencedirect.com/)
# 7. Contact
	Please contact Jingjing Zhang (zhangjj@siat.ac.cn) for questions and comments.
