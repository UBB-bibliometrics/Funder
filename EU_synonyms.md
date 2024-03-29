# Finding EU funders in funding organisation data

Here, in addition to NIB and CRISTIN data, I also connect the data to CORDIS for H2020 and FP7 ("Project publications" file (https://cordis.europa.eu/projects/en).

## Tableau code for Cristin data

Note that in Cristin these are added as dropdown options on registering (rather than a free-text field), so we don't need to wash/search with alternatives. However, EU is a bit more tricky than the others because there are more variations. 

```
IF 
[Funding Source]= "EU"
OR [Funding Source]= "ESA - den europeiske romfartsorganisasjonen"
OR [Funding Source]= "ERC-European Research Council"
OR [Funding Source]= "EU – Horisont Europa (EC/HEU)"
OR [Funding Source]= "EC/H2020"
OR [Funding Source]= "EC/FP7"
THEN "EU"
ELSE "ANNET"
END
```

## Tableau code for NIB data

In NIB the data is directly from the funding text/acknowledgements, so we need to wash for alternatives.

### Suggestions

These have been considered, but don't give additional results:
* ERDF (European Regional Development Fund - full name already included)
* european fisheries fund / european maritime and fisheries fund / european maritime, fisheries and aquaculture fund?

### Terms used

I was unsure about these, whether they should be considered EU, but have got feedback from the Research and Innovation Department that they can be included for now. 
* ERA-NET, ERA.net and COFUND
* ESA & European Space Agency
* ERASMUS
* European parliament

```
IF 
CONTAINS(LOWER([NIB FO combined]),	"european community"	)
OR CONTAINS(LOWER([NIB FO combined]),	"european union"	)
OR CONTAINS(LOWER([NIB FO combined]),	"european commission"	)
OR CONTAINS(LOWER([NIB FO combined]),	"european parliament"	)
OR CONTAINS(LOWER([NIB FO combined]),	"european research area for "	)
OR CONTAINS(LOWER([NIB FO combined]),	"european research commission"	)
OR CONTAINS(LOWER([NIB FO combined]),	"european research consortium"	)
OR CONTAINS(LOWER([NIB FO combined]),	"european research council"	)
OR CONTAINS(LOWER([NIB FO combined]),	"european science council (erc)"	)
OR CONTAINS(LOWER([NIB FO combined]),	"EU commission"	)
OR CONTAINS(LOWER([NIB FO combined]),	"EU research area"	)
OR CONTAINS(LOWER([NIB FO combined]),	"EU research commission"	)
OR CONTAINS(LOWER([NIB FO combined]),	"EU research consortium"	)
OR CONTAINS(LOWER([NIB FO combined]),	"EU research council"	)
OR CONTAINS([NIB FO combined],	"_ERC"	)
OR CONTAINS([NIB FO combined],	"(ERC)"	)
OR REGEXP_MATCH([NIB FO combined], "\bERC\b")
OR CONTAINS(([NIB FO combined]),	"_EC "	)
OR REGEXP_MATCH([NIB FO combined], "\bEC\b")
OR CONTAINS(([NIB FO combined]),	"_EU "	)
OR CONTAINS(([NIB FO combined]),	"(EU "	)
OR CONTAINS(([NIB FO combined]),	"(EU)"	)
OR REGEXP_MATCH([NIB FO combined], "\bEU\b")

OR REGEXP_MATCH(LOWER([NIB FO combined]), "\beu project")
OR REGEXP_MATCH(LOWER([NIB FO combined]), "\beu program")
OR CONTAINS(LOWER([NIB FO combined]),	"european project"	)
OR CONTAINS(LOWER([NIB FO combined]),	"european program"	)
OR REGEXP_MATCH(LOWER([NIB FO combined]), "\beu funded")
OR REGEXP_MATCH(LOWER([NIB FO combined]), "\beu-funded")
OR REGEXP_MATCH(LOWER([NIB FO combined]), "_eu funded")
OR REGEXP_MATCH(LOWER([NIB FO combined]), "_eu-funded")
OR REGEXP_MATCH(LOWER([NIB FO combined]), "\beu through")
OR REGEXP_MATCH(LOWER([NIB FO combined]), "\beu under")

OR CONTAINS(LOWER([NIB FO combined]),	"european framework program"	)
OR REGEXP_MATCH(LOWER([NIB FO combined]), "\beu framework")
OR CONTAINS(([NIB FO combined]),	"EU FP"	)

OR CONTAINS(LOWER([NIB FO combined]),	"7th research program of the european community"	)
OR CONTAINS(LOWER([NIB FO combined]),	"7th research framework"	)
OR CONTAINS(LOWER([NIB FO combined]),	"7th framework programme"	)
OR CONTAINS(LOWER([NIB FO combined]),	"7th framework eu"	)
OR CONTAINS(LOWER([NIB FO combined]),	"7th european framework"	)
OR CONTAINS(LOWER([NIB FO combined]),	"7th eu framework"	)
OR CONTAINS(LOWER([NIB FO combined]),	"eu 7th framework"	)
OR CONTAINS(LOWER([NIB FO combined]),	"eu's 7"	)
OR CONTAINS(LOWER([NIB FO combined]),	"fp7 project"	)
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
OR CONTAINS([NIB FO combined],	"FP7"	)
OR CONTAINS([NIB FO combined],	"FP6"	)

OR CONTAINS(LOWER([NIB FO combined]),	"eu horizon"	)		
OR CONTAINS(LOWER([NIB FO combined]),	"horizon 2020"	)
OR CONTAINS(LOWER([NIB FO combined]),	"horizon programme"	)
OR CONTAINS(LOWER([NIB FO combined]),	"horizon project"	)
OR CONTAINS(LOWER([NIB FO combined]),	"horizon2020"	)
OR CONTAINS(LOWER([NIB FO combined]),	"h2020"	)
OR CONTAINS(LOWER([NIB FO combined]),	"eu's horizon"	)
OR CONTAINS(LOWER([NIB FO combined]),	"horizon framework program"	)		
OR CONTAINS(LOWER([NIB FO combined]),	"framework programme horizon"	)
OR CONTAINS(LOWER([NIB FO combined]),	"horizon europe"	)
OR REGEXP_MATCH([NIB FO combined], "\bHEU\b")

OR CONTAINS(LOWER([NIB FO combined]),	"(erc grant"	)
OR CONTAINS(LOWER([NIB FO combined]),	"erc starting grant"	)
OR CONTAINS(LOWER([NIB FO combined]),	"erc advanced grant"	)
OR CONTAINS(LOWER([NIB FO combined]),	"erc consolidator grant"	)
OR CONTAINS(LOWER([NIB FO combined]),	"eu starting grant"	)
OR CONTAINS(LOWER([NIB FO combined]),	"eu advanced grant"	)
OR CONTAINS(LOWER([NIB FO combined]),	"eu consolidator grant"	)
OR CONTAINS(LOWER([NIB FO combined]),	"european starting grant"	)
OR CONTAINS(LOWER([NIB FO combined]),	"european advanced grant"	)
OR CONTAINS(LOWER([NIB FO combined]),	"european consolidator grant"	)
OR CONTAINS(([NIB FO combined]),	"FEDER"	)
OR CONTAINS(LOWER([NIB FO combined]),	"european regional development fund"	)
OR CONTAINS(LOWER([NIB FO combined]),	"european social fund"	)

OR CONTAINS(LOWER([NIB FO combined]),	"era-net"	)
OR CONTAINS(LOWER([NIB FO combined]),	"era.net"	)
OR CONTAINS(([NIB FO combined]),	"COFUND"	)

OR CONTAINS(LOWER([NIB FO combined]),	"marie curie"	)
OR CONTAINS(LOWER([NIB FO combined]),	"marie sklodowska"	)
OR CONTAINS(LOWER([NIB FO combined]),	"marie skodowska"	)
OR CONTAINS(LOWER([NIB FO combined]),	"marie-curie"	)
OR CONTAINS(LOWER([NIB FO combined]),	"mcsa"	)
OR CONTAINS(LOWER([NIB FO combined]),	"marie s. curie"	)
		
OR CONTAINS(LOWER([NIB FO combined]),	"cost action"	)
OR REGEXP_MATCH([NIB FO combined], "\bCOST\b")
OR REGEXP_MATCH([NIB FO combined], "_COST\b")
OR CONTAINS(([NIB FO combined]),	"(COST)"	)
OR CONTAINS(([NIB FO combined]),	"european cooperation in science and technology")
OR CONTAINS(LOWER([NIB FO combined]),	"eu - cost"	)

OR CONTAINS(LOWER([NIB FO combined]),	"erasmus"	)

OR REGEXP_MATCH([NIB FO combined], "\bESA\b")
OR CONTAINS(LOWER([NIB FO combined]),	"european space agency"	)

THEN "EU"
ELSE "ANNET"
END
```

