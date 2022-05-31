# Terms for Trond Moen Stiftelse

## Tableau code for Cristin data

```
IF 
[funding_source]= "Trond Mohn stiftelse" 
OR [funding_source]= "Bergens forskningsstiftelse" 
THEN "TMS"
ELSE "ANNET"
END
```

## Tableau code for NIB data

#### Consider


#### Code

```
IF 
CONTAINS(LOWER([NIB_FUNDING_organisation]),"bergens forskningsstiftelse")
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),"bergens forsknings stiftelse")
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),"bergen research foundation")
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),"bergen research fund")

OR CONTAINS(LOWER([NIB_FUNDING_organisation]),"bergens medisinske forskningsstiftelse")
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),"bergen medical research foundation")
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),"bergen medical research fund")

OR CONTAINS(LOWER([NIB_FUNDING_organisation]),"trond mohn stiftelse")
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),"trond mohn foundation")
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),"trond mohn fund")
 
THEN "TMS"
ELSE "ANNET"
END
```
