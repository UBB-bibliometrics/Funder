# Finding EU funders in funding organisation data

Here, in addition to NIB and CRISTIN data, I also connect the data to CORDIS for H2020 and FP7 ("Project publications" file (https://cordis.europa.eu/projects/en).

## Tableau code for Cristin data

Note that in Cristin these are added as dropdown options on registering (rather than a free-text field), so we don't need to wash/search with alternatives. However, EU is a bit more tricky than the others because there are more variations. 

```
IF 
[funding_source]= "EU"
OR [funding_source]= "ESA - den europeiske romfartsorganisasjonen"
OR [funding_source]= "ERC-European Research Council"
OR [funding_source]= "EC/H2020"
OR [funding_source]= "EC/FP7"

THEN "EU"
ELSE "ANNET"
END
```

## Tableau code for NIB data

In NIB the data is directly from the funding text/acknowledgements, so we need to wash for alternatives.

### Suggestions

These have been considered, but don't give additional results:
* ERDF (European Regional Development Fund - full name already included)
* european fisheries fund / european maritime and fisheries fund / european maritime, fisheries and aquaculture fund

### Issues

Some have "ERC" listed in funding organisation, but ERC is contained within a number of other funders. However, if we use  "NOT CONTAINS" as below, then we will lose results that are funded by ERC and NSERC, for example.

```
OR CONTAINS(([NIB_FUNDING_organisation]),	"ERC"	) 
AND NOT CONTAINS(([NIB_FUNDING_organisation]),	"NSERC"	) 
AND NOT CONTAINS(([NIB_FUNDING_organisation]),	"CERC"	)
AND NOT CONTAINS(([NIB_FUNDING_organisation]),	"NERC"	)  
AND NOT CONTAINS(([NIB_FUNDING_organisation]),	"CERCA"	) 
AND NOT CONTAINS(([NIB_FUNDING_organisation]),	"ERCA"	) 
AND NOT CONTAINS(([NIB_FUNDING_organisation]),	"ERCIM"	) 
AND NOT CONTAINS(LOWER([NIB_FUNDING_organisation]),	"supercom"	)
AND NOT CONTAINS(LOWER([NIB_FUNDING_organisation]),	"recherche"	)
AND NOT CONTAINS(([NIB_FUNDING_organisation]),	"Recherche"	)
AND NOT CONTAINS(([NIB_FUNDING_organisation]),	"NSERC"	)
```

In the current version, I have used `OR CONTAINS([NIB_FUNDING_organisation],"_ERC") OR CONTAINS([NIB_FUNDING_organisation], "(ERC)")`, seems to work ok and no extra results were found with only searching for `ERC`.

### Terms used

```
IF 
CONTAINS(LOWER([NIB FO combined]),	"7th research program of the european community "	)
OR CONTAINS(LOWER([NIB FO combined]),	"7th research framework programme "	)
OR CONTAINS(LOWER([NIB FO combined]),	"7th framework programme "	)
OR CONTAINS(LOWER([NIB FO combined]),	"7th framework eu project "	)
OR CONTAINS(LOWER([NIB FO combined]),	"7th european framework programme"	)
OR CONTAINS(LOWER([NIB FO combined]),	"7th eu framework programme"	)
OR CONTAINS(LOWER([NIB FO combined]),	"eu 7th framework integrated program"	)
OR CONTAINS(LOWER([NIB FO combined]),	"eu - fp7 project"	)
OR CONTAINS(LOWER([NIB FO combined]),	"eu 7th framework project"	)
OR CONTAINS(LOWER([NIB FO combined]),	"seventh framework program"	)
OR CONTAINS(LOWER([NIB FO combined]),	"eu fp7"	)
OR CONTAINS(LOWER([NIB FO combined]),	"eu-fp7"	)
OR CONTAINS(LOWER([NIB FO combined]),	"eu vii"	)
OR CONTAINS(LOWER([NIB FO combined]),	"eus 7th fp"	)
OR CONTAINS(LOWER([NIB FO combined]),	"f7 research and infrastructure grant"	)
OR CONTAINS(LOWER([NIB FO combined]),	"fp7 eu"	)
OR CONTAINS(LOWER([NIB FO combined]),	"fp-7 of the eu"	)
OR CONTAINS(LOWER([NIB FO combined]),	"fp7/erc"	)
OR CONTAINS(LOWER([NIB FO combined]),	"european fp7"		)

OR CONTAINS(LOWER([NIB FO combined]),	"eu horizon"	)		
OR CONTAINS(LOWER([NIB FO combined]),	"horizon 2020"	)
OR CONTAINS(LOWER([NIB FO combined]),	"horizon programme"	)
OR CONTAINS(LOWER([NIB FO combined]),	"horizon project"	)
OR CONTAINS(LOWER([NIB FO combined]),	"horizon2020"	)
OR CONTAINS(LOWER([NIB FO combined]),	"h2020"	)
OR CONTAINS(LOWER([NIB FO combined]),	"horizon, european union"	)
OR CONTAINS(LOWER([NIB FO combined]),	"horizon/european union"	)
OR CONTAINS(LOWER([NIB FO combined]),	"european union's horizon"	)
OR CONTAINS(LOWER([NIB FO combined]),	"european union horizon"	)
OR CONTAINS(LOWER([NIB FO combined]),	"european comission horizon"	)
OR CONTAINS(LOWER([NIB FO combined]),	"eu's horizon"	)
OR CONTAINS(LOWER([NIB FO combined]),	"horizon framework program"	)		
OR CONTAINS(LOWER([NIB FO combined]),  "european commission under horizon")
OR CONTAINS(LOWER([NIB FO combined]),	"framework programme horizon"	)

OR CONTAINS(LOWER([NIB FO combined]),	"marie curie"	)
OR CONTAINS(LOWER([NIB FO combined]),	"marie sklodowska-curie"	)
OR CONTAINS(LOWER([NIB FO combined]),	"marie-curie"	)
OR CONTAINS(LOWER([NIB FO combined]),	"marie sklodowska curie"	)
OR CONTAINS(LOWER([NIB FO combined]),	"mcsa"	)
OR CONTAINS(LOWER([NIB FO combined]),	"marie s. curie"	)
		
OR CONTAINS(LOWER([NIB FO combined]),	"cost action"	)		
OR CONTAINS(([NIB FO combined]),	"COST "	)
OR CONTAINS(([NIB FO combined]),	"(COST)"	)
OR CONTAINS(([NIB FO combined]),	"european cooperation in science and technology")
OR CONTAINS(([NIB FO combined]),	"COST-"	)
OR CONTAINS(LOWER([NIB FO combined]),	"eu - cost"	)
		
OR CONTAINS(LOWER([NIB FO combined]),	"european commission"	)
OR CONTAINS(LOWER([NIB FO combined]),	"european community"	)
OR CONTAINS(LOWER([NIB FO combined]),	"european union"	)
OR CONTAINS(LOWER([NIB FO combined]),	"european research area for "	)
OR CONTAINS(LOWER([NIB FO combined]),	"european research commission"	)
OR CONTAINS(LOWER([NIB FO combined]),	"european research consortium"	)
OR CONTAINS(LOWER([NIB FO combined]),	"european research council"	)
OR CONTAINS(LOWER([NIB FO combined]),	"european framework program"	)
OR CONTAINS(LOWER([NIB FO combined]),	"(eu grant)"	)
OR CONTAINS(LOWER([NIB FO combined]),	"eu project)"	)
OR CONTAINS(LOWER([NIB FO combined]),	"european project"	)
OR CONTAINS(LOWER([NIB FO combined]),	"eu program)"	)
OR CONTAINS(LOWER([NIB FO combined]),	"european program"	)
OR CONTAINS(LOWER([NIB FO combined]),	"eu funded"	)
OR CONTAINS(LOWER([NIB FO combined]),	"eu-funded"	)
OR CONTAINS(LOWER([NIB FO combined]),	"eu through"	)
OR CONTAINS(LOWER([NIB FO combined]),	"eu under"	)

OR CONTAINS(([NIB FO combined]),	"FEDER"	)
OR CONTAINS(LOWER([NIB FO combined]),	"european regional development fund"	)
OR CONTAINS(LOWER([NIB FO combined]),	"european social fund"	)
		
OR CONTAINS(LOWER([NIB FO combined]),	"european research council's starting grant"	)
OR CONTAINS(LOWER([NIB FO combined]),	"european research council's advanced grant"	)
OR CONTAINS(LOWER([NIB FO combined]),	"european research council's consolidator grant"	)
OR CONTAINS(LOWER([NIB FO combined]),	"erc advanced grant"	)
OR CONTAINS(LOWER([NIB FO combined]),	"erc consolidator grant"	)
OR CONTAINS(LOWER([NIB FO combined]),	"erc starting grant"	)
OR CONTAINS(LOWER([NIB FO combined]),	"european science council (erc)"	)
OR CONTAINS(LOWER([NIB FO combined]),	"european union/erc"	)
OR CONTAINS(LOWER([NIB FO combined]),	"erc grant"	)
OR CONTAINS([NIB FO combined],	"_ERC"	)
OR CONTAINS([NIB FO combined],	"(ERC)"	)

THEN "EU"
ELSE "ANNET"
END
```
