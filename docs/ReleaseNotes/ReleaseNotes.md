

## Release 3.0 6/28/2022

The Release 3.0 of CDA searches across data from the Genomics Data Commons (GDC), the Proteomics Data Commons (PDC), and the Imaging Data Commons (IDC) to aggregate and return data to users via a single application programming interface (API). CDA leverages the work and data model that is concurrently being developed by the [Center for Cancer Data Harmonization](https://datascience.cancer.gov/data-commons/center-cancer-data-harmonization-ccdh) (CCDH). CCDH will provide a single data model that harmonizes syntax and semantics across the CRDC systems and services.

## Datasets & Fields

* All datasets updated as follows
    * GDC: v31.0, 03/17/2022
    * PDC: v2.7, 03/18/2022
    * IDC: v.4.0, 03/09/2022[^1]

[^1]:Information pulled from the PDC API may contain embargoed data.

## Enhanced query functionality

* Added support for IN and LIKE SQL statements
* The Subjects query has been simplified to not return file information, instead the new files Q method can be used for files
* Counts function added to Q that gives total counts for each Data Commons given a query
* Filter flag added to Q's run method which allows horizontal filtering of results
* Verbose flag added to Q's run method to hide/show Q actions when running a query
* Query's on text fields are now case insensitive
* Added to_dataframe to Q's Result object that converts the JSON structure to a pandas dataframe
* Added paginator to Q's Result object that allows for pagination through result pages. This also has a flag for paginating as a dataframe.


## Metadata Changes

* See [CDA Schema Field Mapping](../Schema/overview_mapping.md)

* Summary
    * Previous table format now called Subjects endpoint
        * Replaced all File entities with Files - a list of file ids associated with the entity that the list is located in. e.g
            * File -> Files
            * ResearchSubject.File -> ResearchSubject.Files
            * ResearchSubject.Specimen.File -> ResearchSubject.Specimen.Files
    * Files endpoint added:
        * Endpoint oriented around File information
        * Includes all information regarding the file's associated entities(Subject, ResearchSubject, and Specimen)
    * Newly available fields:
        * None
    * Renamed fields (old -> new):
        * None


## Bug fixes

* Fixed issue where queries on list columns that were not lists of json objects (i.e. subject_associated_project) would fail
* Duplicate files should no longer be returned


## Known bugs and issues

* `unique_terms` are not sorted when they return
* tumor stages are not harmonized, there are redundant terms (complicates query)
* Days_to_birth should be reformatted (currently negative) or have an example query
* Docker jupyter notebook does not work if a notebook is already open in port 8888

<!-- Footnotes themselves at the bottom. -->
