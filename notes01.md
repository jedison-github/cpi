Notes on the Chemical-Protein Interaction Datasets
==================================================

**Note that the STRING site cited is version 7, and version 10 is available.**

According to the Readme from STITCH (http://stitch1.embl.de/download/README), the protein dictionary can be found in another database, STRING. The file is `protein.aliases.v7.1.txt`. Its first two lines are:

```
##  species_ncbi_taxon_id ##  protein_id ##  alias ##    source ##
    117 RB2638  1,4-alpha D-glucan:1,4-alpha D-glucan 6-glucosyl- transferase	paralign_SWISSPROT_DE
```

However, when queried on RefSeq, this tag does not return the same aliases, but rather simply "glycogen branching enzyme".

Looking around STRING we see that they have a map of their [datasets] (http://string71.embl.de/newstring_download/database.schema.v7.1.pdf). In it they explain that the protein tag comes from third party databases: GenomeReviews, RefSeq, or Ensembl. However, GenomeReviews is now defunct and forwards to Ensembl.

As an example, consider the CPI pair (in Python dictionary format):

```python
'CID000007215' : ('117.RB7803', '229')
```

`117` is the species, and `RB7803` is the protein.

The protein can be found in [RefSeq](https://www.ncbi.nlm.nih.gov). It actually points to a DNA sequence, but it has a protein associated with it (uroporphyrinogen III synthase, uroporhyrinogen decarboxylase)

For another CPI pair,
```python
'CID006918553' : ('7955.ENSDARP00000041069', '278')
```

`ENSDARP00000041069`... points to a DNA sequence on [Ensembl](http://useast.ensembl.org). This only points to a DNA sequence, but the search result yields "ENSDARG00000032319", which is associated with the protein "mest". `"ENSDARP00000041069"`, however, does return results for a DNA sequence that is associated with "mest". I do not understand why this protein tag does not link directly to its associated gene.

The species dictionary is located in file the `species.v7.1.txt`.

The first two lines are:

```
 taxon_id	  STRING_type	  STRING_name_compact	    official_name_NCBI
      117	  core	        Rhodopirellula baltica	Rhodopirellula baltica (strain 1)
```

The chemicals dictionary is in `chemicals.v1.10.tsv`. The first two lines are:

```
chemical	     name	               molecular_weight	 SMILES_string
CID000000001	 acetyl-L-carnitine	 203.236	          CC(=O)OC(CC(=O)[O-])C[N+](C)(C)C
```