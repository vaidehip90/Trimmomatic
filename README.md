# Trimmomatic

Trimmomatic is read trimming tool for Illumina NGS data for single end and pair end data.In simple words, trimmomatic tool can be used to filter and trim poor quality reads.The trimmomatic tool has many options/paramter that can be used for trimming steps ;


ILLUMINACLIP: Cut adapter and other illumina-specific sequences from the read.

SLIDINGWINDOW: Perform a sliding window trimming, cutting once the average quality within the window falls below a threshold.

LEADING: Cut bases off the start of a read, if below a threshold quality

TRAILING: Cut bases off the end of a read, if below a threshold quality

CROP: Cut the read to a specified length

HEADCROP: Cut the specified number of bases from the start of the read

MINLEN: Drop the read if it is below a specified length

TOPHRED33: Convert quality scores to Phred-33

TOPHRED64: Convert quality scores to Phred-64

PE : paired end file as input

SE : single end file as input 


# Data from SRA

prefetch SRR6956031

fastq-dump -F--split-files--gzip SRR6956031

 # Quality check of data fastq.gz files

fastqc SRR6956031_1.fastq.gz

fastqc SRR6956031_2.fastq.gz

 # Trimmomatic Usuage 

trimmomatic SE -phred33 SRR6956031_1.fastq.gz SRR6956031_1.trim.fastq.gz LEADING:3 TRAILING:3 SLIDINGWINDOW:4:20 MINLEN:100

trimmomatic SE -phred33 SRR6956031_2.fastq.gz SRR6956031_2.trim.fastq.gz LEADING:3 TRAILING:3 SLIDINGWINDOW:4:20 MINLEN:100

 # Quality Check of Trimmed files

fastqc SRR6956031_1.trim.fastq.gz

fastqc SRR6956031_2.trim.fastq.gz


