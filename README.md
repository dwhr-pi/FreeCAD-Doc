# FreeCAD-Wiki als PDF-Datei

Diese Suite von Werkzeugen kann verwendet werden, um eine lokale Kopie aus dem FreeCAD-Wiki abzurufen und sie dann zu verwenden, um qhelp- und pdf-Dateien zu generieren.
Das Herunterladen des gesamten Wikis ist jetzt ein riesiger Vorgang, anfällig für Netzwerkfehler, also wurde es in zwei Teile geteilt, einen, um eine Liste der herunterzuladenden Dateien abzurufen, und einen anderen, um die Dateien tatsächlich herunterzuladen.


1) Führen Sie `buildwikiindex.py` aus, um eine Indexdatei zu erstellen, die eine Liste aller herunterzuladenden Dateien enthält

2) Führen Sie `downloadwiki.py` aus. Wenn die Verbindung unterbrochen wird, führen Sie es erneut aus, die bereits heruntergeladenen Dateien werden übersprungen.

3) Führen Sie `buildqhelp.py` aus, um die Dateien `freecad.qhc` und `freecad.qch` zu generieren

4) Führen Sie `buildpdf.py` aus, um `freecad.pdf` zu generieren (wkhtmltopdf muss installiert sein)

5) die qhelp-Dateien können mit `assistant -collectionFile freecad.qhc` getestet werden

6) Wenn Sie bereits das gesamte Wiki heruntergeladen haben, führen Sie unmittelbar danach `update.py` aus, um eine Liste mit Revisions-IDs für jede Seite zu erstellen.

7) Sobald die anfängliche Revisionsliste erstellt wurde, kann das Skript `update.py` jederzeit in der Zukunft ausgeführt werden, um nach Seiten zu suchen, die sich seit der gespeicherten Revisions-ID geändert haben. Das Skript soll zweimal ausgeführt werden, einmal, um eine Liste der geänderten Seiten zu erhalten, und ein weiteres, um die geänderten Seiten (und alle ihre Abhängigkeiten) erneut herunterzuladen.

8) Um die generierte `freecad.qch` in Teile aufzuteilen, die kleiner als 50 MB sind (Github-Grenze): ```split -d --byte=49M localwiki/freecad.qch localwiki/freecad.qch.part```

9) Um die Teile (zum Testen) wieder zusammenzufügen: `cat localwiki/freecad.qch.part* >> test.qch` Überprüfen Sie dann, ob `test.qch` dieselbe md5-Nummer wie `localwiki/freecad.qch` hat

10) Zum Testen: `assistant -collectionFile localwiki/freecad.qhc`

## Videos
[FreeCAD 0.18 Grundlagen #0 Erste Schritte in FreeCAD - CAD Anfänger Tutorial (Deutsch)](https://www.youtube.com/watch?v=rTvgCcOXfuw)  
[FreeCAD 0.18 Grundlagen #1 Saubere Skizzen im Sketcher erstellen - CAD Anfänger Tutorial (Deutsch)](https://www.youtube.com/watch?v=OQodi9WOou4)  

[FreeCAD 0.19 Grundkurs #1 - Dein Start in FreeCAD (DE)](https://www.youtube.com/watch?v=8tvBLCdyjI4)  
[FreeCAD 0.19 Grundkurs #2 - Saubere Skizzen in FreeCAD (DE)](https://www.youtube.com/watch?v=wMkaVCYNrcA)  
[FreeCAD 0.19 Grundkurs #3 - Skizzen für Fortgeschrittene (DE)](https://www.youtube.com/watch?v=iZFet4KjVE8)  
[FreeCAD 0.19 Grundkurs #4 - Abschluss Sketcher (DE)](https://www.youtube.com/watch?v=D3VWkC6DAM4)  
[FreeCAD 0.19 Grundkurs #5 - Stabile Modelle im Part Design von Beginn an (DE)](https://www.youtube.com/watch?v=OfVXgKyfVOg)  
Weitere Kurse findet man in der Youtube Playliste.  

[FreeCAD Facebook-Gruppe](https://www.facebook.com/groups/416491481766626)

## URLs
[FreeCAD-documentation](https://github.com/dwhr-pi/FreeCAD-documentation/edit/main/README.md)  
Original: [FreeCAD-Doc](https://github.com/FreeCAD/FreeCAD-Doc) 
