# EXAM 2023 - BIOINFORMATIQUE 
## Exercice 1

Dans un premier temps, les trois dernières files du projet SRP021469 sont téléchargés via le site NCBI. Les numéros d'accessions de nos séquences SRA sont les suivantes :
- SRR1754715
- SRR1754722
- SRR1754730

Afin de pouvoir utiliser ces données, il faut les déziper : 
```
gunzip SRR1754715.fastq.gz
gunzip SRR1754722.fastq.gz
gunzip SRR1754730.fastq.gzwget --output-document sratoolkit.tar.gz https://ftp-trace.ncbi.nlm.nih.gov/sra/sdk/current/sratoolkit.current-ubuntu64.tar.gz

```
Maintenant queexport BLASTDB=/Téléchargements/bioinfo/cleandata/ITS:$BLASTDB  les fichiers sont dézipés, on les runs via le logiciel FastQC en utilisant trois script (batch_fastqc.sh ; run_fastqc.sh ; parsing_fastqc.sh)
```
./batch_fastqc.sh SRR1754715.fastq SRR1754722.fastq SRR1754730.fastq 
```
On s'assure que les scripts ont bien fonctionné : 
```
cat Results_fastq_parsing.txt
```
Ensuite on passe nos séquences sur Trimmomatic :
```
java -jar trimmomatic-0.39.jar SE -phred33 ~/Téléchargements/bioinfo/rawdata/SRR1754715.fastq ~/Téléchargements/bioinfo/cleandata/SRR1754715_out.fastq ILLUMINACLIP:TruSeq3-SE.fa:2:30:10 LEADING:3 TRAILING:3 SLIDINGWINDOW:4:15 MINLEN:36
java -jar trimmomatic-0.39.jar SE -phred33 ~/Téléchargements/bioinfo/rawdata/SRR1754722.fastq ~/Téléchargements/bioinfo/cleandata/SRR1754722_out.fastq ILLUMINACLIP:TruSeq3-SE.fa:2:30:10 LEADING:3 TRAILING:3 SLIDINGWINDOW:4:15 MINLEN:36
java -jar trimmomatic-0.39.jar SE -phred33 ~/Téléchargements/bioinfo/rawdata/SRR1754730.fastq ~/Téléchargements/bioinfo/cleandata/SRR1754730_out.fastq ILLUMINACLIP:TruSeq3-SE.fa:2:30:10 LEADING:3 TRAILING:3 SLIDINGWINDOW:4:15 MINLEN:36
```
Préparation des séquences ITS_eucaryotes_sequences : 
téléchargement de ces séquences sur bash via le site NCBI
```
wget ftp://ftp.ncbi.nlm.nih.gov/blast/db/ITS_eukaryote_sequences.tar.gz
```
Extraction des séquences des fichiers télécharger
```
tar -xzvf ITS_eukaryote_sequences.tar.gz
```
Envoyé les données extraire vers le PATH 
```
export BLASTDB=/Téléchargements/bioinfo/cleandata/ITS:$BLASTDB
```



