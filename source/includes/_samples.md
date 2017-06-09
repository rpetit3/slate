---
api_root: https://staphopia.emory.edu/api
---

# Samples
In Staphopia, a sample is a single sequenced genome. In the case of genomes publicly available from ENA/SRA, each experiment is a sample. The sample is the central identifier in the API. You will be using sample IDs to gather associated analsis results.

In most cases you can use a simple GET request to get info on a single sample or POST requests to get info on multiple samples. In the cases where sequences (assembly, genes, etc...) are returned the requests will be limited to a single sample at a time.

### GET List All Samples
> Definition

```plaintext
GET https://staphopia.emory.edu/api/sample/

GET https://staphopia.emory.edu/api/sample/?st=INT
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
            "sample_tag": "ERX359411",
            "is_paired": true,
            "is_public": true,
            "md5sum": "4e1afce010e8659b8a3a9729f3914e4e",
            "st_original": "188",
            "st_stripped": 188,
            "st_is_exact_match": true
        },
        {
            "sample_id": 4658,
            "sample_tag": "SRX477069",
            "is_paired": true,
            "is_public": true,
            "md5sum": "869d19fe7147aba68fa5db6410dc8e96",
            "st_original": "8",
            "st_stripped": 8,
            "st_is_exact_match": true
        }
    ]
}
```

Returns a list of samples that either you own or have been made public. The resulting set can be filtered by sequence types.

#### Query Parameters

Parameter | Data Type | Description
--------- | --------- | -----------
st        | integer   | Filter the samples based on a specific sequence type.



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
        },
        {
            "sample_id": 95,
            "is_paired": true,
            "is_public": true,
            "is_published": true,
            "sample_tag": "ERX061507",
            "st_original": "15",
            "st_stripped": 15,
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
        },
        {
            "sample_id": 5667,
            "is_paired": true,
            "is_public": true,
            "is_published": true,
            "sample_tag": "ERX116916",
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
