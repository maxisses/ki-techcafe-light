# Verbindung testen

Im besten Falle können wir auf die Webseite gehen und Trainingsdaten generieren:

![](../../../../../../.gitbook/assets/image%20%2833%29.png)

Und sehen in den Logs des Backends wie fleißig Daten in die PostgreSQL geschrieben werden:

![](../../../../../../.gitbook/assets/image%20%2823%29.png)

{% hint style="danger" %}
Jetzt stellt ihr fest es geht nicht - und ein Fehler ist tatsächlich noch drin! \(falls sonst alles wie geplant geklappt hat :\) \)
{% endhint %}

Nach etwas debugging und Vergleich der Umgebungsvariablen wird klar, dass eine Umgebungsvariable des Backends nicht richtig übertragen wurde - nämlich dem MQTT\_TRAIN_\__TOPIC fehlt hinten die Raute \#.

Das kann man im Deployment des Backends anpassen und dann sollte es so aussehen wie oben.

![](../../../../../../.gitbook/assets/image%20%2814%29.png)

