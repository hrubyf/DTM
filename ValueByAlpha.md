# Value By Alpha Maps in QGIS 

## Datenquelle (Wahlgeometrien & Wahlergebnisse)
[Bundestagswahl 2021](https://www.bundeswahlleiterin.de/bundestagswahlen/2021/ergebnisse.html)

Tabelle (kerg1.csv) mit Wahlergebnissen bereinigen:
![image](https://github.com/hrubyf/DTM/assets/46536216/355e6497-cb2c-40b9-925c-16d7a71fd39f)

## QGIS

1.) Vergleich SPD vs. CDU: Stimmenstärkere Partei regelbasiert darstellen

Regel "Olaf"
```
 "SPD" >  "CDU" 
```
Regel "Armin"
```
 "SPD" <  "CDU" 
```

2.) Ebene "Alpha" ergänzen und auf Symbolebene 1 setzen  

![image](https://github.com/hrubyf/DTM/assets/46536216/e27c9c49-0fa4-4046-8203-ec17c5a431ab)


3.) Regel für Ebene "Alpha": Über "Einfache Füllung" unter "Füllfarbe" > "Datendefinierte Übersteuerung" > "Bearbeiten"

![image](https://github.com/hrubyf/DTM/assets/46536216/7135aae1-1f25-4743-94f2-fe8601a336ca)

Grundprinzip:
```
set_color_part(
'black',
'alpha',
126)
```

Statt einem festen Alpha-Wert, wird dieser wertebasiert aus einem anderen Attribut für jede Bezugseinheit berechnet
```
set_color_part(
'black',
'alpha',
scale_linear(
 "G",
 100000, 200000,
 230,0)
)
```
