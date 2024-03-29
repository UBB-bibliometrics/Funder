# Terms for Trond Moen Stiftelse (Bergen)

Information from TMS Bergen:
* 2024: TMS skifter navn til Trond Mohn forskningsstiftelse (Trond Mohn Research Foundation), med forkortelsen "TMF"
* 2019: Bergens forskningsstiftelse skifter navn til Trond Mohn stiftelse (TMS).
* 2014: Bergens medisinske forskningsstiftelse overtar ved fusjon Bergens forskningsstiftelse og Frank Mohns Stiftelse den 1. januar 2014, og samme dag endrer stiftelsen navn til Bergens forskningsstiftelse.
* 2004: Bergens forskningsstiftelse og Bergens medisinske forskningsstiftelse blir etablert 
* (1996: Frank Mohns Stiftelse blir etablert; formelt korrekt å ta med, men det er neppe noen publikasjoner som har nevnt denne stiftelsen som bidragsyter)
 
The following abbreviations are used:
*	Trond Mohn stiftelse: TMS
*	Bergens forskningsstiftelse: BFS
*	Bergen Medisinske forskningsstiftelse: BMFS

Terms were evaluated together with TMS representatives October 2022.

## Tableau code for Cristin data

Note that in Cristin these are added as dropdown options on registering (rather than a free-text field), so we don't need to wash/search with alternatives.

```
IF 
[funding_source]= "Trond Mohn stiftelse" 
OR [funding_source]= "Bergens forskningsstiftelse" 
THEN "TMS"
ELSE "ANNET"
END
```

## Tableau code for NIB data

In NIB the data is directly from the funding text/acknowledgements, so we need to wash for alternatives.

#### Considered

`BMFS` AND `BFS` do not add any results (and are outdated names now). 

#### Code

Note that `Mohn stiftelse` and `Mohn foundation` can refer to other regional departments of Mohn (particularly Tromsø). Not an issue if the analysis is limited to UiB?

```
IF 
CONTAINS(LOWER([NIB FO combined]),"bergens forskningsstiftelse")
OR CONTAINS(LOWER([NIB FO combined]),"bergen forskningsstiftelse")
OR CONTAINS(LOWER([NIB FO combined]),"bergens forsknings stiftelse")
OR CONTAINS(LOWER([NIB FO combined]),"bergen forsknings stiftelse")
OR CONTAINS(LOWER([NIB FO combined]),"bergen research foundation")
OR CONTAINS(LOWER([NIB FO combined]),"bergen research fund")

OR CONTAINS(LOWER([NIB FO combined]),"bergens medisinske forskningsstiftelse")
OR CONTAINS(LOWER([NIB FO combined]),"bergen medisinske forskningsstiftelse")
OR CONTAINS(LOWER([NIB FO combined]),"bergen medical research foundation")
OR CONTAINS(LOWER([NIB FO combined]),"bergen medical research fund")
OR CONTAINS(LOWER([NIB FO combined]),"bergen medical foundation")

OR CONTAINS(LOWER([NIB FO combined]),"trond mohn")
OR CONTAINS(LOWER([NIB FO combined]),"_tms starting grant")
OR CONTAINS(LOWER([NIB FO combined]),"tmf starting grant")
OR CONTAINS(LOWER([NIB FO combined]),"frank mohn")
OR CONTAINS(LOWER([NIB FO combined]),"mohn foundation")
OR CONTAINS(LOWER([NIB FO combined]),"mohn stiftelse")
 
THEN "TMS"
ELSE "ANNET"
END
```
