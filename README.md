# Phyluce-for-UCE
Hydra job files that use trimmed reads as input for Phyluce and output UCE fasta files. I modified and updated the scripts found in the Phyluce Training for the Smithsonian Target Enrichment Workshop (https://github.com/SmithsonianWorkshops/Targeted_Enrichment/blob/master/phyluce.md)

1. Finding UCE Loci (command: phyluce_assembly_match_contigs_to_probes)

2. Extracting UCE Loci (command: phyluce_assembly_get_match_counts)

3. Get FASTA Data for Taxa in Our Taxon Set (command: phyluce_assembly_get_fastas_from_match_counts)

4. Exploding the Monolithic FASTA File (command: phyluce_assembly_explode_get_fastas_file)

Before you begin, you need:
 
* a directory to the trimmed reads.
* Trimmed reads in the correct format for Phyluce ("[sample_name].contigs.fasta"). The file name must begin with a letter.
* a FASTA file of UCE probes.
