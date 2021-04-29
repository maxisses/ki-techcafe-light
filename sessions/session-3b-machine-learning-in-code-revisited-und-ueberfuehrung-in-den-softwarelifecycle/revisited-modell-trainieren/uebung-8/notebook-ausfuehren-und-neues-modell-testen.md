# Notebook ausführen und neues Modell testen

### Ausführen

Mit folgendem Befehl kann man das Notebook einmal durchlaufen lassen und auf Fehler prüfen:

![](../../../../.gitbook/assets/image%20%28136%29.png)



Nun wird im entsprechenden Deployment Space ein weiteres Modell deployed, nämlich das in diesem Notebook trainierte. 

### Testen

Um es direkt im Notebook zu testen \(allerletzte Zelle\) muss man dort in der Vorvorletzten Zeile die URL für das Modell anpassen:

![](../../../../.gitbook/assets/image%20%28135%29.png)

Die bekommt raus indem man in seinen Deployment Space geht.

![](../../../../.gitbook/assets/image%20%28141%29.png)

Dort sollten 2 Modelle sein. Das mit "AutoAI" trainierte und das "manuell" eben im Notebook trainierte, Das  manuell trainierte trägt den Namen "Smartphone Classification at XX". Das wählt man aus und kopiert die entsprechende URL aus dem Feld "Endpoint": 

![](../../../../.gitbook/assets/image%20%28142%29.png)

