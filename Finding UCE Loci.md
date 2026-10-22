Finding UCE Loci
---

This script uses ```phyluce_assembly_match_contigs_to_probes``` command to match UCE probe sequences to assembled reads. 
Before you start,
1. Make sure the command is in one line. No comments and no hard returns. The comments are included in the script for clarification only.
2. If the total size of assemblies are very large, increase the memory allocation. If you don't allocate enough memory, the job will die prematurely.

```
# /bin/sh 
# ----------------Parameters---------------------- # 
#$ -S /bin/sh 
#$ -pe mthread 2 
#$ -q mThC.q 
#$ -l mres=20G,h_data=10G,h_vmem=10G,himem 
#$ -cwd 
#$ -j y 
#$ -N matchcontigs 
#$ -o matchcontigs.log 
#$ -m bea 
#$ -M seim@si.edu 
# 
# ----------------Modules------------------------- # 
module load bioinformatics/phyluce/1.7.3 
# ----------------Your Commands------------------- # 
# 
echo + `date` job $JOB_NAME started in $QUEUE with jobID=$JOB_ID on $HOSTNAME 
echo + NSLOTS = $NSLOTS 
# 
phyluce_assembly_match_contigs_to_probes  
--contigs "path/to/assembly/directory"   
# this path must lead to a directory, not a file 
--probes "path/to/probes/directory/UCEprobes.fasta"
# 
--output uce-search-results 
# 
echo = `date` job $JOB_NAME done
```
### To run this job

The assembled reads must conform to the format ```[samplename].contigs.fasta```, and the file name must begin with a letter.

Edit these items in the job file:
1. --contigs "path to assembly directory"
   
Replace "path to assembly directory" with a full path to the assemblies.

2. --probes "path to probes directory/UCEprobes.fasta"
   
Replace "path to probes directory/UCEprobes.fasta" with a full path to the UCE probe file.

After the job is edited, save it as 'matchcontigs.job' and run the job on hydra (qsub matchcontigs.job).

If the script needs to be rerun, remove the output directory (```rm -r```) before you re-submit the job.

### Options
1. Relax match criteria

This relaxes match criteria; optional but recommended.
```
--min-identity 70 
--min-coverage 70
```
2. Cull short contigs from assembly

This removes short contigs from assembly (less than 200 bp in this example).
```
module load bio/seqkit 
mkdir -p contigsforUCE-gt200 
for x in contigsforUCE/*fasta; do SEQ=$(basename $x); echo $SEQ; seqkit seq $x -w 0 --min-len 200 -o contigsforUCE-gt200/${SEQ}; done
```
