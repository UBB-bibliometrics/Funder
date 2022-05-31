# Finding EU funders in funding organisation data

## Issues

Some have "ERC" listed in funding organisation, but ERC is contained within a number of other funders.

However, if we use  "NOT CONTAINS" as below, then we will lose results that are funded by ERC and NSERC, for example.

```
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

## Tableau code for NIB data

Consider:
* ERDF (European Regional Development Fund)
* FP7 alone? 
* horizon europe
* european fisheries fund / european maritime and fisheries fund / european maritime, fisheries and aquaculture fund

```
IF 
CONTAINS(LOWER([NIB_FUNDING_organisation]),	"7th research program of the european community "	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"7th research framework programme "	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"7th framework programme "	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"7th framework eu project "	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"7th european framework programme"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"7th eu framework programme"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"eu 7th framework integrated program"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"eu - fp7 project"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"eu 7th framework project"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"seventh framework program"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"eu fp7"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"eu-fp7"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"eu vii"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"eus 7th fp"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"f7 research and infrastructure grant"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"fp7 eu"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"fp-7 of the eu"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"fp7/erc"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"european fp7"		)
OR CONTAINS(([NIB_FUNDING_organisation]),	"EU FP6"		)

OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"eu horizon"	)		
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"horizon 2020"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"horizon programme"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"horizon project"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"horizon2020"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"h2020"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"horizon, european union"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"horizon/european union"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"european union's horizon"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"european union horizon"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"european comission horizon"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"eu's horizon"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"horizon framework program"	)		
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),  "european commission under horizon")
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"framework programme horizon"	)

OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"marie curie"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"marie sklodowska-curie"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"marie-curie"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"marie sklodowska curie"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"mcsa"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"marie s. curie"	)
		
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"cost action"	)		
OR CONTAINS(([NIB_FUNDING_organisation]),	"COST "	)
OR CONTAINS(([NIB_FUNDING_organisation]),	"(COST)"	)
OR CONTAINS(([NIB_FUNDING_organisation]),	"european cooperation in science and technology")
OR CONTAINS(([NIB_FUNDING_organisation]),	"COST-"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"eu - cost"	)
		
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"european commission"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"european community"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"european union"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"european research area for "	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"european research commission"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"european research consortium"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"european research council"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"european framework program"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"(eu grant)"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"eu project)"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"european project"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"eu program)"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"european program"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"eu funded"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"eu-funded"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"eu through"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"eu under"	)

OR CONTAINS(([NIB_FUNDING_organisation]),	"FEDER"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"european regional development fund"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"european social fund"	)
		
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"european research council's starting grant"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"european research council's advanced grant"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"european research council's consolidator grant"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"erc advanced grant"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"erc consolidator grant"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"erc starting grant"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"european science council (erc)"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"european union/erc"	)
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),	"erc grant"	)
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

THEN "EU"
ELSE "ANNET"
END
```
