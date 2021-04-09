# optional 4. eigene PostgreSQL im Cluster

Natürlich kann man auch eigene PostgreSQL Datenbank im OpenShift nutzen.

![](../../../../../.gitbook/assets/image%20%2813%29.png)

Hat man das Template instantiiert, einen Usernamen und Passwort gesetzt wird die Datenbank provisioniert. Setzt man im Deployment noch das Kubernetes Label, dann erhalt die Datenbank auch das entsprechende PostgreSQL Icon.

```text
app.kubernetes.io/name=postgresql
```

![](../../../../../.gitbook/assets/image%20%2811%29.png)

Natürlich muss man nun im Deployment "backend"  die entsprechenden Umgebungsvariablen der neuen DB setzen. Entweder durch ein neues Deployment oder Anpassung des bestehenden z.B. \(je nach gesetzten Werten\) so:

![](../../../../../.gitbook/assets/image%20%2812%29.png)

{% hint style="info" %}
Aktuell ist die Datenbank NUR für Anwendungen im Cluster erreichbar!
{% endhint %}

Um die Daten später auch im CloudPak4Data nutzen zu können sollten wir Datenbank \(ggf. sogar nur temporär\) für Zugriffe von außerhalb zugänglich machen. Dazu müssen wir lediglich den Kubernetes Service anpassen bspw. auf den Typ "NodePort". Dazu editieren wir das YAML-File an der Stelle "type:" und änder von "ClusterIP" auf "NodePort" und drücken auf save.

![](../../../../../.gitbook/assets/image%20%2828%29.png)

In der Folge können wir die Datenbank von außerhalb erreich und sie z.B. auch in ein lokales Datenbankmonitoring aufnehmen. Ein Blick ins pgAdmin zeigt, dass Daten geschrieben werden und alles funktioniert.

![](../../../../../.gitbook/assets/image%20%2819%29.png)

