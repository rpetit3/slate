# Samples
In Staphopia, a sample is a single sequenced genome. In the case of genomes publicly available from ENA/SRA, each exeriment accession is a sample. The sample is the central identifier in Staphopia. You will use sample IDs to gather associated analysis results.

In most cases you can use a simple GET request to get info on a single sample or POST requests to get info on multiple samples. In the cases where sequences (assembly, genes, etc...) are returned the requests will be limited to a single sample at a time.

Below are endpoints to access samples. Methods to access analysis results for a single sample and multiple samples will be described in following sections.

### GET All Samples
> Definition

```plaintext
GET https://staphopia.emory.edu/api/sample/
```

> Example Request

```shell
curl -H "Authorization: Token YOUR_API_TOKEN_HERE" https://staphopia.emory.edu/api/sample/
```

> Example Response

```json
{
    "count": 18521,
    "next": "https://staphopia.emory.edu/api/sample/?page=2",
    "previous": null,
    "results": [
        {
            "sample_id": 2425,
            "is_paired": true,
            "is_public": true,
            "is_published": true,
            "sample_tag": "ERX359411",
            "st_original": "188",
            "st_stripped": 188,
            "st_is_exact_match": true
        }
    ]
}
```

Returns a list of samples that either you own or have been made public. The resulting set can be filtered by sequence types.

#### Options

Option    | Type      | Description
--------- | --------- | -----------
st        | int       | Filter the samples based on a specific sequence type.



### GET Public Samples
> Definition

```plaintext
GET https://staphopia.emory.edu/api/sample/public/
```

> Example Request

```shell
curl -H "Authorization: Token YOUR_API_TOKEN_HERE" https://staphopia.emory.edu/api/sample/public/
```

> Example Response

```json
{
    "count": 18521,
    "next": "https://staphopia.emory.edu/api/sample/public/?page=2",
    "previous": null,
    "results": [
        {
            "sample_id": 94,
            "is_paired": true,
            "is_public": true,
            "is_published": true,
            "sample_tag": "ERX047891",
            "st_original": "2371",
            "st_stripped": 2371,
            "st_is_exact_match": true
        }
    ]
}
```

Returns a list of samples that have been made public.

### GET Published Samples
> Definition

```plaintext
GET https://staphopia.emory.edu/api/sample/published/
```

> Example Request

```shell
curl -H "Authorization: Token YOUR_API_TOKEN_HERE" https://staphopia.emory.edu/api/sample/published/
```

> Example Response

```json
{
    "count": 5947,
    "next": "https://staphopia.emory.edu/api/sample/published/?page=2",
    "previous": null,
    "results": [
        {
            "sample_id": 5666,
            "is_paired": true,
            "is_public": true,
            "is_published": true,
            "sample_tag": "ERX116914",
            "st_original": "8",
            "st_stripped": 8,
            "st_is_exact_match": true,
            "pmid": [
                26873713
            ]
        }
    ]
}
```

Returns a list of samples that have been associated with a publication.


### GET MLST Distinct Sample Set
> Definition

```plaintext
GET https://staphopia.emory.edu/api/sample/unique_st/
```

> Example Request

```shell
curl -H "Authorization: Token YOUR_API_TOKEN_HERE" https://staphopia.emory.edu/api/sample/unique_st/
```

> Example Response

```json
{
    "count": 417,
    "next": null,
    "previous": null,
    "results": [
        {
            "sample_id": 961,
            "st": 1,
            "is_paired": true,
            "is_public": true,
            "is_published": true,
            "sample_tag": "ERX147839",
            "rank": 3
        }
    ]
}
```

Returns a set up samples each having a different seqeunce type (MLST). The priority is to select published samples first, then quality of the sample.

### GET Single Sample
> Definition

```plaintext
GET https://staphopia.emory.edu/api/sample/<sample_id>/
```

> Example Request

```shell
curl -H "Authorization: Token YOUR_API_TOKEN_HERE" https://staphopia.emory.edu/api/sample/500/
```

> Example Response

```json
{
    "count": 1,
    "next": null,
    "previous": null,
    "results": [
        {
            "sample_id": 500,
            "is_paired": true,
            "is_public": true,
            "is_published": true,
            "sample_tag": "ERX105420",
            "st_original": "239",
            "st_stripped": 239,
            "st_is_exact_match": true
        }
    ]
}
```

Returns a single sample which is public or that you own. An empty result will be returned if a request is made for a sample which is not public.

#### Arguments

Property  | Type      | Required | Description
--------- | --------- | -------- | -----------
sample_id | int       | true     | Unique number associated with a sample.



### GET Search Samples
> Definition

```plaintext
GET https://staphopia.emory.edu/api/search/?q=<query_sting>
```

> Example Request

```shell
curl -H "Authorization: Token YOUR_API_TOKEN_HERE" https://staphopia.emory.edu/api/search/?q=PRJEB2756
```

> Example Response

```json
{
    "count": 318,
    "next": "https://staphopia.emory.edu/api/search/?page=2&q=PRJEB2756",
    "previous": null,
    "results": [
        {
            "sample_id": 262,
            "name": "ERX085322",
            "is_published": true,
            "st": 22,
            "rank": "Gold",
            "sample_accession": "SAMEA1317454",
            "strain": "BSAC516",
            "collection_date": "2003-01-01",
            "location": "United Kingdom: England",
            "isolation_source": "blood"
        },
        {
            "sample_id": 263,
            "name": "ERX085323",
            "is_published": true,
            "st": 22,
            "rank": "Gold",
            "sample_accession": "SAMEA1317339",
            "strain": "BSAC519",
            "collection_date": "2003-01-01",
            "location": "United Kingdom: England",
            "isolation_source": "blood"
        },
        {
            "TRUNCATED FOR DEMO PURPOSES": 0
        },
    ]
}
```

Searches a given query string against all metadata fields. Returns a set of samples that matched the query string.

#### Arguments

Property  | Type      | Required | Description
--------- | --------- | -------- | -----------
q         | str       | true     | Query string to search.
