# 1. Deploy MQTT Broker

Im ersten Schritt deployen wir unseren Message Broker, der über das leichtgewichtige MQTT Protokoll später die Messages - Sensordaten des Akzelerometers und Gyroskops - aufnehmen und verteilen soll.

Den können wir folgendermaßen deployen:

```text
git clone https://github.com/maxisses/sensorapp.git
cd sensorapp/openshift
oc new-app https://github.com/maxisses/sensorapp.git --context-dir=mosquitto-broker/ --strategy=docker --name=mosquitto -l name=mosquitto -l name=mosquitto -l app.kubernetes.io/part-of=sensorapp
cd mosquitto
oc apply -f mosquitto-lb.yaml
```

Wir machen den Broker sowohl intern als auch extern über den Loadbalancer der Cloud verfügbar. Dazu legen wir einen Kubernetes Service vom Typ Loadbalancer an.  
Anhand der IP des "External Load Balancer" - hier 169.50.26.157  - können wir im Network Loadbalancer der IBM Cloud eine URL inkl. Zertifikat dieser IP zuweisen.

![](../../../../../.gitbook/assets/image%20%2822%29.png)

Dazu führen wir den folgenden Befehl aus und kopieren den entsprechenden Hostnamen - Diesen müssen wir gleich im Frontend als Umgebungsvariable setzen, damit das Smartphone weiß wo die Sensordaten hingeschickt werden sollen.

```text
ibmcloud ks nlb-dns create classic -c <Name des Clusters> --ip <durch IP eures Loadbalancer Dienstes zu ersetzen>
ibmcloud ks nlb-dns ls --cluster OCPclusterPub
```

![](../../../../../.gitbook/assets/image%20%2826%29.png)

Das Deployment war allerdings noch nicht erfolgreich - Wir müssen in die "Zertifikatshölle", damit der entsprechende listener auf Port 8883, den später unser Frontend für verschlüsselte Kommunikation nutzen möchte, geöffnet wird.

![](../../../../../.gitbook/assets/image%20%28127%29.png)

![](../../../../../.gitbook/assets/image%20%28125%29.png)



