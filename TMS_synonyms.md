# Terms for Trond Moen Stiftelse

Information from TMS:
* 2019: Bergens forskningsstiftelse skifter navn til Trond Mohn stiftelse.
* 2014: Bergens medisinske forskningsstiftelse overtar ved fusjon Bergens forskningsstiftelse og Frank Mohns Stiftelse den 1. januar 2014, og samme dag endrer stiftelsen navn til Bergens forskningsstiftelse.
* 2004: Bergens forskningsstiftelse og Bergens medisinske forskningsstiftelse blir etablert 
* (1996: Frank Mohns Stiftelse blir etablert; formelt korrekt å ta med, men det er neppe noen publikasjoner som har nevnt denne stiftelsen som bidragsyter)
 
Følgende forkortelser er brukt:
•	Trond Mohn stiftelse: TMS
•	Bergens forskningsstiftelse: BFS
•	Bergen Medisinske forskningsstiftelse: BMFS

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
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),"bergen forskningsstiftelse")
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),"bergens forsknings stiftelse")
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),"bergen forsknings stiftelse")
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),"bergen research foundation")
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),"bergen research fund")

OR CONTAINS(LOWER([NIB_FUNDING_organisation]),"bergens medisinske forskningsstiftelse")
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),"bergen medisinske forskningsstiftelse")
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),"bergen medical research foundation")
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),"bergen medical research fund")
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),"bergen medical foundation")

OR CONTAINS(LOWER([NIB_FUNDING_organisation]),"trond mohn")
OR CONTAINS(LOWER([NIB_FUNDING_organisation]),"_tms starting grant")
 
THEN "TMS"
ELSE "ANNET"
END
```
