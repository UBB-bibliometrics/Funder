# Terms for NFR

## Tableau code for Cristin data

Note that in Cristin these are added as dropdown options on registering (rather than a free-text field), so we don't need to wash/search with alternatives.

```
IF 
[funding_source]= "Norges forskningsråd" 
THEN "NFR"
ELSE "ANNET"
END
```

## Tableau code for NIB data

In NIB the data is directly from the funding text/acknowledgements, so we need to wash for alternatives.

### Code

```
IF 
CONTAINS(LOWER([NIB FO combined]),"research council of norway")
OR CONTAINS(LOWER([NIB FO combined]),"norwegian research council")
OR CONTAINS(LOWER([NIB FO combined]),"norwegian science council")
OR CONTAINS(LOWER([NIB FO combined]),"nfr forny grant")
OR CONTAINS(LOWER([NIB FO combined]),"nfr biotek2021 grant")
OR CONTAINS(LOWER([NIB FO combined]),"nfr project")
OR CONTAINS(LOWER([NIB FO combined]),"[nfr]")
OR CONTAINS(LOWER([NIB FO combined]),"nfr (norway)")
OR CONTAINS(LOWER([NIB FO combined]),"nfr/frinatek")
OR CONTAINS(LOWER([NIB FO combined]),"nfr/maroff")
OR CONTAINS(LOWER([NIB FO combined]),"(nfr - norway)")
OR CONTAINS(LOWER([NIB FO combined]),"norges forskningsråd")
OR CONTAINS(LOWER([NIB FO combined]),"norges forskningsrad")
OR CONTAINS(LOWER([NIB FO combined]),"nfr in norway")
OR CONTAINS(LOWER([NIB FO combined]),"nfr multival project")
OR CONTAINS(LOWER([NIB FO combined]),"norway (nfr)")
OR CONTAINS(LOWER([NIB FO combined]),"nfr-petromaks2 project")
OR CONTAINS(LOWER([NIB FO combined]),"nfr fri -nat project")
OR CONTAINS([NIB FO combined],"NFR")
OR CONTAINS([NIB FO combined],"RCN")

THEN "NFR"
ELSE "ANNET"
END
```
