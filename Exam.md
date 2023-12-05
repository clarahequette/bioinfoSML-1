#EXAM 2023 - BIOINFORMATIQUE 
##Exercice 1

Dans un premier temps, les trois dernières files du projet SRP021469 sont téléchargés via le site NCBI. Les numéros d'accessions de nos séquences SRA sont les suivantes :
- SRR1754715
- SRR1754722
- SRR1754730

Afin de pouvoir utiliser ces données, il faut les déziper : 
```
gunzip SRR1754715.fastq.gz
gunzip SRR1754722.fastq.gz
gunzip SRR1754730.fastq.gz
```
Maintenant que les fichiers sont dézipés, on les runs via le logiciel FastQC en utilisant trois script (batch_fastqc.sh ; run_fastqc.sh ; parsing_fastqc.sh)
```
./batch_fastqc.sh SRR1754715.fastq SRR1754722.fastq SRR1754730.fastq 
```
On s'assure que les scripts ont bien fonctionné : 
```
cat Results_fastq_parsing.txt
```
