# Funder

This repo contains a list of synonyms used in searching for funding organisation, specifically the EU, Norwegian Research Council and Trond Mohn Stiftelse (Bergen). The terms are used to search data from two datasources:
* [CRISTIN](https://www.cristin.no/) via [DUCT](https://www.cristin.no/ressurser/duct/dokumentasjon/datakilder-i-duct_ny.html), via the field `Funding source`.
* Norsk Infrastruktur for Bibliometri, in a field constructed via a Python script where (unwashed) funder names from the article "Funding text"/"Acknowledgements" are concatenated, separated by `_`. This data sources covers only publications found in Web of Science (Clarivate). 

The terms are formatted for use in Tableau. 
