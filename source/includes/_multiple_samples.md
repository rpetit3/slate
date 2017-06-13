# Working With Multiple Samples

###  POST Metadata
> Definition

```plaintext
POST https://staphopia.emory.edu/api/metadata/bulk_by_sample/
```

> Example Request

```shell
curl -H "Authorization: Token YOUR_API_TOKEN_HERE" \
     -H "Content-Type: application/json" \
     https://staphopia.emory.edu/api/metadata/bulk_by_sample/ \
     -d '{"ids" : [500,501]}'
```

> Example Response

```json
{
    "count": 2,
    "results": [
        {
            "sample_id": 500,
            "contains_ena_metadata": true,
            "study_accession": "PRJEB2756",
            "study_title": "Staphylococcus aureus (BSAC) study",
            "study_alias": "Staphylococcus_aureus__BSAC__study-sc-2011-11-15T19:00:43Z-2036",
            "secondary_study_accession": "ERP001012",
            "sample_accession": "SAMEA1464583",
            "secondary_sample_accession": "ERS072738",
            "submission_accession": "ERA131752",
            "experiment_accession": "ERX105420",
            "experiment_title": "Illumina HiSeq 2000 paired end sequencing",
            "experiment_alias": "SC_EXP_7712_8#27",
            "tax_id": 1280,
            "scientific_name": "Staphylococcus aureus",
            "instrument_platform": "ILLUMINA",
            "instrument_model": "Illumina HiSeq 2000",
            "library_layout": "PAIRED",
            "library_strategy": "WGS",
            "library_selection": "RANDOM",
            "center_name": "Sanger Institute",
            "center_link": "http://www.sanger.ac.uk/",
            "first_public": "2012-05-28",
            "cell_line": "",
            "collected_by": "",
            "collection_date": "2003-01-01",
            "country": "United Kingdom: England",
            "description": "7712_8#27",
            "environmental_sample": "false",
            "biosample_first_public": "2012-05-28",
            "germline": "false",
            "isolate": "",
            "isolation_source": "blood",
            "location": "",
            "serotype": "Not known",
            "serovar": "Not known",
            "sex": "",
            "submitted_sex": "",
            "strain": "st697",
            "sub_species": "",
            "tissue_type": "",
            "biosample_tax_id": "1280",
            "biosample_scientific_name": "Staphylococcus aureus",
            "sample_alias": "BSAC697-sc-1304334",
            "checklist": "ERC000011",
            "biosample_center_name": "The Wellcome Trust Sanger Institute",
            "environment_biome": "",
            "environment_feature": "",
            "environment_material": "",
            "project_name": "",
            "host": "Homo sapien",
            "host_tax_id": "",
            "host_status": "Carriage",
            "host_sex": "",
            "submitted_host_sex": "",
            "host_body_site": "",
            "investigation_type": "",
            "sequencing_method": "",
            "broker_name": ""
        }
    ]
}
```

Returns metadata associated with a given set of Sample IDs.

#### Arguments
Property  | Type      | Required | Description
--------- | --------- | -------- | -----------
ids       | int array | true     | An array of sample IDs as integers.

###  POST Sequencing Metrics
> Definition

```plaintext
POST https://staphopia.emory.edu/api/sequence-quality/bulk_by_sample/
```

> Example Request

```shell
curl -H "Authorization: Token YOUR_API_TOKEN_HERE" \
     -H "Content-Type: application/json" \
     https://staphopia.emory.edu/api/sequence-quality/bulk_by_sample/ \
     -d '{"ids" : [500,501]}'
```

> Example Response

```json
{
    "count": 2,
    "results": [
        {
            "sample_id": 500,
            "is_original": true,
            "rank": 3,
            "total_bp": 418786000,
            "coverage": 148.78,
            "read_total": 4187860,
            "read_min": 100,
            "read_mean": 100.0,
            "read_std": 0.0,
            "read_median": 100,
            "read_max": 100,
            "read_25th": 100,
            "read_75th": 100,
            "qual_mean": 34.5463,
            "qual_std": 2.7428,
            "qual_median": 36,
            "qual_25th": 34,
            "qual_75th": 36
        }
    ]
}
```

Returns sequencing quality metrics associated with a given set of Sample IDs. By default the error corrected and quality filtered results are returned.

#### Arguments

Property  | Type      | Required | Description
--------- | --------- | -------- | -----------
ids       | int array | true     | An array of sample IDs as integers.

#### Options

Option    | Type      | Description
--------- | --------- | -----------
original  | bool      | Return sequencing quality of the original input FASTQ file. 

### POST Assembly Metrics
> Definition

```plaintext
POST https://staphopia.emory.edu/api/assembly/stat/bulk_by_sample/
```

> Example Request

```shell
curl -H "Authorization: Token YOUR_API_TOKEN_HERE" \
     -H "Content-Type: application/json" \
     https://staphopia.emory.edu/api/assembly/stat/bulk_by_sample/ \
     -d '{"ids" : [500,501]}'
```

> Example Response

```json
{
    "count": 2,
    "results": [
        {
            "sample_id": 500,
            "is_scaffolds": false,
            "is_plasmids": false,
            "total_contig": 165,
            "total_contig_length": 3032220,
            "min_contig_length": 56,
            "median_contig_length": 534,
            "mean_contig_length": 18377.0,
            "max_contig_length": 254900,
            "n50_contig_length": 130552,
            "l50_contig_count": 9,
            "ng50_contig_length": 130552,
            "lg50_contig_count": 9,
            "contigs_greater_1k": 71,
            "contigs_greater_10k": 41,
            "contigs_greater_100k": 9,
            "contigs_greater_1m": 0,
            "percent_contigs_greater_1k": 43.0,
            "percent_contigs_greater_10k": 24.8,
            "percent_contigs_greater_100k": 5.5,
            "percent_contigs_greater_1m": 0.0,
            "contig_percent_a": 33.56,
            "contig_percent_t": 33.77,
            "contig_percent_g": 16.01,
            "contig_percent_c": 16.65,
            "contig_percent_n": 0.0,
            "contig_non_acgtn": 0.0,
            "num_contig_non_acgtn": 0
        }
    ]
}
```

Returns assembly related metrics associated with a given set of Sample IDs. By default metrics for the assembled contigs is returned.

#### Arguments

Property  | Type      | Required | Description
--------- | --------- | -------- | -----------
ids       | int array | true     | An array of sample IDs as integers.

#### Options

Option     | Type      | Description
---------- | --------- | -----------
scaffolds  | bool      | Return assembly metrics for the generated scaffolds. 
plasmids   | bool      | Return assembly metrics for the assembled plasmids. 

### POST SRST2 Based Sequence Type
> Definition

```plaintext
POST https://staphopia.emory.edu/api/mlst/srst2/bulk_by_sample/
```

> Example Request

```shell
curl -H "Authorization: Token YOUR_API_TOKEN_HERE" \
     -H "Content-Type: application/json" \
     https://staphopia.emory.edu/api/mlst/srst2/bulk_by_sample/ \
     -d '{"ids" : [500,501]}'
```

> Example Response

```json
{
    "count": 2,
    "results": [
        {
            "sample_id": 500,
            "st_original": "239",
            "st_stripped": 239,
            "is_exact": true,
            "arcc": "2",
            "aroe": "3",
            "glpf": "1",
            "gmk": "1",
            "pta": "4",
            "tpi": "4",
            "yqil": "3",
            "mismatches": "0",
            "uncertainty": "-",
            "depth": 101.145,
            "maxMAF": 0.025641
        }
    ]
}
```

Returns the SRST2 based sequence type associated with a given set of Sample IDs. 

#### Arguments

Property  | Type      | Required | Description
--------- | --------- | -------- | -----------
ids       | int array | true     | An array of sample IDs as integers.

### POST BLAST Based Sequence Type
> Definition

```plaintext
POST https://staphopia.emory.edu/api/mlst/blast/bulk_by_sample/
```

> Example Request

```shell
curl -H "Authorization: Token YOUR_API_TOKEN_HERE" \
     -H "Content-Type: application/json" \
     https://staphopia.emory.edu/api/mlst/blast/bulk_by_sample/ \
     -d '{"ids" : [500,501]}'
```

> Example Response

```json
{
    "count": 14,
    "results": [
        {
            "sample_id": 500,
            "locus_name": "arcC",
            "locus_id": 2,
            "bitscore": 843,
            "slen": 456,
            "length": 456,
            "gaps": 0,
            "mismatch": 0,
            "pident": 100.0,
            "evalue": 0.0
        }
    ]
}
```

Returns the BALST based sequence type associated with a given set of Sample IDs. 

#### Arguments

Property  | Type      | Required | Description
--------- | --------- | -------- | -----------
ids       | int array | true     | An array of sample IDs as integers.

### POST SCCmec Primer Hits
> Definition

```plaintext
POST https://staphopia.emory.edu/api/sccmec/primer/bulk_by_sample/
```

> Example Request

```shell
curl -H "Authorization: Token YOUR_API_TOKEN_HERE" \
     -H "Content-Type: application/json" \
     https://staphopia.emory.edu/api/sccmec/primer/bulk_by_sample/ \
     -d '{"ids" : [500,501]}'
```

> Example Response

```json
{
    "count": 54,
    "results": [
        {
            "sample_id": 500,
            "title": "ccrA1",
            "length": 24,
            "bitscore": 30,
            "evalue": 0.01,
            "identity": 16,
            "mismatch": 0,
            "gaps": 0,
            "hamming_distance": 8,
            "query_from": 7,
            "query_to": 22,
            "hit_from": 79024,
            "hit_to": 79009,
            "align_len": 16,
            "qseq": "TATCATCAATCAGTAC",
            "hseq": "TATCATCAATCAGTAC",
            "midline": "||||||||||||||||",
            "contig_id": 104617,
            "program_id": 7
        }
    ]
}
```

> Example Response ('predict' option active)

```json
{
    "count": 2,
    "results": [
        {
            "sample_id": 500,
            "I": false,
            "II": false,
            "III": true,
            "IV": false,
            "V": false,
            "VI": false,
            "VII": false,
            "VIII": false,
            "IX": false,
            "X": false,
            "XI": false
        }
    ]
}
```

Returns the BLAST results of hits against SCCmec Primer sequences associated with a given set of Sample IDs. 

#### Arguments

Property  | Type      | Required | Description
--------- | --------- | -------- | -----------
ids       | int array | true     | An array of sample IDs as integers.

#### Options

Option     | Type      | Description
---------- | --------- | -----------
exact_hits | bool      | Return on those hits that were exact matches.
predict    | bool      | Predict SCCmec type based on presence of exact matches.

<aside class="warning">SCCmec types with a prediction of 'false' may or may not be accurate. An exact match against the primer is required to make a prediction. Partial hits are not taken into account. Therefore, you will need to review the blast results for false hits. </aside>

### POST SCCmec Subtype Hits
> Definition

```plaintext
POST https://staphopia.emory.edu/api/sccmec/subtype/bulk_by_sample/
```

> Example Request

```shell
curl -H "Authorization: Token YOUR_API_TOKEN_HERE" \
     -H "Content-Type: application/json" \
     https://staphopia.emory.edu/api/sccmec/subtype/bulk_by_sample/ \
     -d '{"ids" : [500,501]}'
```

> Example Response

```json
{
    "count": 40,
    "results": [
        {
            "sample_id": 500,
            "title": "ivh-r",
            "length": 20,
            "bitscore": 23,
            "evalue": 1.19,
            "identity": 12,
            "mismatch": 0,
            "gaps": 0,
            "hamming_distance": 8,
            "query_from": 2,
            "query_to": 13,
            "hit_from": 33879,
            "hit_to": 33890,
            "align_len": 12,
            "qseq": "AAACACTGATAT",
            "hseq": "AAACACTGATAT",
            "midline": "||||||||||||",
            "contig_id": 104718,
            "program_id": 7
        }
    ]
}
```

> Example Response ('predict' option active)

```json
{
    "count": 2,
    "results": [
        {
            "sample_id": 500,
            "Ia": false,
            "IIa": false,
            "IIb": false,
            "IIIa": true,
            "IVa": false,
            "IVb": false,
            "IVc": false,
            "IVd": false,
            "IVg": false,
            "IVh": false
        }
    ]
}
```

Returns the BLAST results of hits against SCCmec Subtype Primer sequences associated with a given set of Sample IDs. 

#### Arguments

Property  | Type      | Required | Description
--------- | --------- | -------- | -----------
ids       | int array | true     | An array of sample IDs as integers.

#### Options

Option     | Type      | Description
---------- | --------- | -----------
exact_hits | bool      | Return on those hits that were exact matches.
predict    | bool      | Predict SCCmec subtype based on presence of exact matches.

<aside class="warning">SCCmec subtypes with a prediction of 'false' may or may not be accurate. An exact match against the primer is required to make a prediction. Partial hits are not taken into account. Therefore, you will need to review the blast results for false hits. </aside>

### POST SNPs
> Definition

```plaintext
POST https://staphopia.emory.edu/api/variant/snp/bulk_by_sample/
```

> Example Request

```shell
curl -H "Authorization: Token YOUR_API_TOKEN_HERE" \
     -H "Content-Type: application/json" \
     https://staphopia.emory.edu/api/variant/snp/bulk_by_sample/ \
     -d '{"ids" : [500,501]}'
```

> Example Response

```json
{
    "count": 74966,
    "results": [
        {
            "sample_id": 500,
            "snp_id": 184,
            "annotation_id": 1,
            "reference_position": 62,
            "reference_base": "G",
            "alternate_base": "A",
            "reference_codon": ".",
            "alternate_codon": ".",
            "reference_amino_acid": ".",
            "alternate_amino_acid": ".",
            "amino_acid_change": ".",
            "is_synonymous": 9,
            "is_transition": 1,
            "is_genic": 0,
            "AC": "[1]",
            "GT": "1",
            "AD": "[0, 74]",
            "GQ": "99",
            "AF": "1.0",
            "MQ": "60.0",
            "PL": "[3305, 0]",
            "DP": "74",
            "QD": "35.89",
            "quality": "3275",
            "feature_id": 1,
            "reference_id": 1,
            "filters_id": 9
        }
    ]
}
```

Returns the SNPs associated with a given set of Sample IDs. 

#### Arguments

Property  | Type      | Required | Description
--------- | --------- | -------- | -----------
ids       | int array | true     | An array of sample IDs as integers.

### POST InDels
> Definition

```plaintext
POST https://staphopia.emory.edu/api/variant/indel/bulk_by_sample/
```

> Example Request

```shell
curl -H "Authorization: Token YOUR_API_TOKEN_HERE" \
     -H "Content-Type: application/json" \
     https://staphopia.emory.edu/api/variant/indel/bulk_by_sample/ \
     -d '{"ids" : [500,501]}'
```

> Example Response

```json
{
    "count": 4605,
    "results": [
        {
            "sample_id": 500,
            "indel_id": 1784,
            "annotation_id": 1,
            "reference_position": 14111,
            "reference_base": "AT",
            "alternate_base": "A",
            "is_deletion": true,
            "feature_id": 1,
            "reference_id": 1,
            "AC": "[1]",
            "GT": "1",
            "AD": "[0, 89]",
            "GQ": "99",
            "AF": "1.0",
            "MQ": "60.12",
            "PL": "[3841, 0]",
            "DP": "93",
            "QD": "26.9",
            "quality": "3801.97",
            "filters_id": 9
        }
    ]
}
```

Returns the InDels associated with a given set of Sample IDs. 

#### Arguments

Property  | Type      | Required | Description
--------- | --------- | -------- | -----------
ids       | int array | true     | An array of sample IDs as integers.
