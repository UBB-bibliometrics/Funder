# Funder

This repo contains a list of terms used for searching publications for information about funding organisations, specifically the EU, Norwegian Research Council and Trond Mohn Stiftelse (Bergen). The terms are used to search data from two datasources (both delivered by Sikt):
* [CRISTIN](https://www.cristin.no/) via [DUCT](https://www.cristin.no/ressurser/duct/dokumentasjon/datakilder-i-duct_ny.html), via the field `Funding source`.
* [Norsk Infrastruktur for Bibliometri](https://www.cristin.no/bibliometri/), in a field constructed via a Python script where (unwashed) funder names from the article "Funding text"/"Acknowledgements" are concatenated, separated by `_`. This data sources covers only publications found in Web of Science (Clarivate). 

For finding EU-funded publications, the datasources are also connected to CORDIS for H2020/FP7 ("Project publications" file, https://cordis.europa.eu/projects/en).

The terms in the files are formatted for use in Tableau. 
