# "Machine Learning Inferencing"-Backend deployen

Nun binden wir unser Modell an die bereits bestehende Webanwendung für das Mobiltelefon.  
Eigentlich müssten wir natürlich hier im Sinne des Anwendungsfalls eine Extrafunktionalität für den "Enkel" bauen. Für den Showcase hier reicht es uns beides in einer Anwendung zu halten.

Dazu wird eine weitere Funktionalität installiert, welche die Datentransformation durchführt und die Daten an das in Watson Machine Learning als API zur Verfügung gestellte Modell sendet.  
Diese liegt erneut im GitRepo, welches wir aus Übung 1 kennen.

### Umgebungsvariablen prüfen die wir aus Übung 1 kennen

Bevor wir deployen können müssen wir allerdings wieder einige Umgebungsvariablen mitgeben.  
Im Ordner "openshift" des gecloned GitRepos liegen bereits die pg-datenbank.env \(in die Datenbank, werden die Antworten/Predictions des Modells geschrieben\) und die backend-env.env Datei.  
Ebenfalls wie die backend-Funktionalität greift das Inferencing-Backend auch nicht von außerhalb \(so wie das Frontend vom Browser des jeweiligen Nutzers\) auf den Cluster zu und deshalb nutzen wir hier wieder die gleiche backend-env.env Umgebungsvariablen des Brokers. Hier sollte nichts zu tun sein.

### API Endpunkt des Modells und API-Key mitgeben

Um die Informationen wieder als Umgebungsvariablen in die Anwendung zu geben, legen wir im "openshift" Ordner ein weiteres File mit dem Namen "ibm-wml.env" an, welches durch eigene Werte angepasst werden muss.

Diese erhält man indem man einen IAM API Key in der IBM Cloud Oberfläche generiert: [https://cloud.ibm.com/docs/account?topic=account-userapikey\#create\_user\_key](https://cloud.ibm.com/docs/account?topic=account-userapikey#create_user_key)

Und den Scoring Endpunkt haben sehen wir CloudPak4Data bzw. Watson Studio im Deployment des Modells

![](../../../../.gitbook/assets/image%20%28123%29.png)



```text
WML_API_KEY=****************************
SCORING_ENDPOINT=https://us-south.ml.cloud.ibm.com/ml/v4/deployments/fa153c9b-10b6-46f8-a4da-2d1e1c495f44/predictions?version=******
```

![](../../../../.gitbook/assets/image%20%28124%29.png)

### Deployen der Komponente

Auf der Kommandozeile geht man in den "openshift" Ordner und loggt sich ggf. nochmal neu in den OpenShift Cluster ein \(Vgl. Übung 1\). Danach kann man die Anwendung mit Folgendem Befehl deployen:

```text
oc new-app https://github.com/maxisses/sensorapp.git --context-dir=inference-app/ --strategy=docker --env-file=ibm-wml.env --env-file=pg-datenbank.env --env-file=backend-env.env --name=ml-inferencing-backend -l name=ml-inference -l app.kubernetes.io/part-of=sensorapp
```

{% hint style="danger" %}
Die Raute \(\#\) wird wieder gefressen und muss nachgetragen werden!
{% endhint %}

