Merging VCFs
---------------

1. Left Align and Trim variants
Indel variants are not always normalized,
meaning the same variant may be represented in multiple forms.
This make merging impossible. To overcome this, we normalize indel
variants by:  
    - Aligning them to the left-most position of the indel repeat (if any) in the reference.
    - Trimming the variants to remove bases which overlap the reference

This produces a canonical form of the variant that, harmonizing calls from different runs.

To do this process, we'll use the GATK:
```

```

2. vcf\_to\_tsv

3. Merge TSV
