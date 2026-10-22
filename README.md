# Phyluce-for-UCE
This is a Hydra pipeline that uses read assemblies as input for Phyluce and output UCE fasta files. I modified and updated the scripts found in the Phyluce Training Tutorial for the Smithsonian Target Enrichment Workshop (https://github.com/SmithsonianWorkshops/Targeted_Enrichment/blob/master/phyluce.md), which was in turn modified from Brant Faircloth's (http://phyluce.readthedocs.org/en/latest/tutorial-one.html).

1. Finding UCE Loci (command: phyluce_assembly_match_contigs_to_probes)

2. Extracting UCE Loci (command: phyluce_assembly_get_match_counts)

3. Get FASTA Data for Taxa in Our Taxon Set (command: phyluce_assembly_get_fastas_from_match_counts)

4. Exploding the Monolithic FASTA File (command: phyluce_assembly_explode_get_fastas_file)

Before you begin, you need:
 
* a directory where assemblies are saved.
* assemblies with file names compatible with Phyluce ("[sample_name].contigs.fasta"). The file name must begin with a letter, not a number.
* UCE probes in FASTA format.
