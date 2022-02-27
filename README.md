[FreeCAD 0.18 Grundlagen #0 Erste Schritte in FreeCAD - CAD Anfänger Tutorial (Deutsch)](https://www.youtube.com/watch?v=rTvgCcOXfuw)
[FreeCAD 0.18 Grundlagen #1 Saubere Skizzen im Sketcher erstellen - CAD Anfänger Tutorial (Deutsch)](https://www.youtube.com/watch?v=OQodi9WOou4)
[FreeCAD 0.19 Grundkurs #1 - Dein Start in FreeCAD (DE)](https://www.youtube.com/watch?v=8tvBLCdyjI4)
[FreeCAD 0.19 Grundkurs #2 - Saubere Skizzen in FreeCAD (DE)](https://www.youtube.com/watch?v=wMkaVCYNrcA)
[FreeCAD 0.19 Grundkurs #3 - Skizzen für Fortgeschrittene (DE)](https://www.youtube.com/watch?v=iZFet4KjVE8)
[FreeCAD 0.19 Grundkurs #4 - Abschluss Sketcher (DE)](https://www.youtube.com/watch?v=D3VWkC6DAM4)
[FreeCAD 0.19 Grundkurs #5 - Stabile Modelle im Part Design von Beginn an (DE)](https://www.youtube.com/watch?v=OfVXgKyfVOg)
[]()
[]()

This suite of tools can be used to retrieve a local copy from the FreeCAD wiki and then use it to generate qhelp and pdf files.  
The downloading of the entire wiki is now a huge operation, prone to network errors, so it has been cut into 2 parts, one to retrieve a list of files to download and another to actually download the files.  

1) run "buildwikiindex.py" to build an index file containing
   a list of all the files to download

2) run "downloadwiki.py". If connection drops, run it again, 
   the already downloaded files will be skipped.

3) run "buildqhelp.py" to generate freecad.qhc and freecad.qch
   files

4) run "buildpdf.py" to generate freecad.pdf (wkhtmltopdf must be installed)

5) the qhelp files can be tested with "assistant -collectionFile freecad.qhc"

6) If you have already downloaded the whole wiki, run "update.py" immediately 
   after, to create a list of revision IDs for each page.
   
7) Once the initial revisions list has been created, the "update.py" script
   can be ran anytime in the future, to check for pages that have changed
   since the stored revision ID. The script is meant to run twice, one to get
   a list of pages that have changed, and another one to download the changed
   pages (and all their dependencies) again.

8) To split the generated freecad.qch into parts that are smaller than 50Mb 
   (github limit): split -d --byte=49M localwiki/freecad.qch localwiki/freecad.qch.part
   
9) To join the parts again (for testing): cat localwiki/freecad.qch.part* >> test.qch
   Then check that test.qch has the same md5 number than localwiki/freecad.qch

10) To test: assistant -collectionFile localwiki/freecad.qhc

