# Terms for NFR

## Tableau code for Cristin data

```
IF 
[funding_source]= "Norges forskningsråd" 
THEN "NFR"
ELSE "ANNET"
END
```

## Tableau code for NIB data

#### Consider

* "_RCN"

#### Code

```
IF 
CONTAINS(LOWER([NIB_FUNDING_organisation]),"research council of norway")
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),"research council norway")
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),"reserach council of norway")
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),"norwegian research council")
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),"norwegian science council")
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),"nfr forny grant")
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),"nfr biotek2021 grant")
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),"nfr project")
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),"[nfr]")
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),"nfr (norway)")
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),"nfr/frinatek")
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),"nfr/maroff")
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),"(nfr - norway)")
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),"norges forskningsråd")
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),"norges forskningsrad")
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),"nfr in norway")
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),"nfr multival project")
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),"norway (nfr)")
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),"nfr-petromaks2 project")
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),"nfr fri -nat project")
OR CONTAINS([NIB_FUNDING_organisation],"NFR")

THEN "NFR"
ELSE "ANNET"
END
```
