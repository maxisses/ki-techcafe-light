# 1. Deploy MQTT Broker

Im ersten Schritt deployen wir unseren Message Broker, der über das leichtgewichtige MQTT Protokoll später die Messages - Sensordaten des Akzelerometers und Gyroskops - aufnehmen und verteilen soll.

Den können wir folgendermaßen deployen:

```text
git clone https://github.com/maxisses/sensorapp.git
cd openshift
oc new-app https://github.com/maxisses/sensorapp.git --context-dir=mosquitto-broker/ --strategy=docker --name=mosquitto -l name=mosquitto -l name=mosquitto -l app.kubernetes.io/part-of=sensorapp
oc apply -f mosquitto-lb.yaml
```

Wir machen den Broker sowohl intern als auch extern über den Loadbalancer der Cloud verfügbar. Dazu legen wir einen Kubernetes Service vom Typ Loadbalancer an.  
Anhand der IP des "External Load Balancer" - hier 169.50.26.157  - können wir im Network Loadbalancer der IBM Cloud herausfinden, welche URL mit der IP assoziert ist.

![](../../../../../../.gitbook/assets/image%20%2813%29.png)

Dazu führen wir den folgenden Befehl aus und kopieren den entsprechenden Hostnamen - Diesen müssen wir gleich im Frontend als Umgebungsvariable setzen, damit das Smartphone weiß wo die Sensordaten hingeschickt werden sollen.

```text
ibmcloud ks nlb-dns ls --cluster OCPclusterPub
```

![](../../../../../../.gitbook/assets/image%20%2815%29.png)

{% hint style="warning" %}
Tatsächlich müssten wir eigentlich auch das entsprechende Zertifikat für eine verschlüsselte Verbindung zB über eine ConfigMap in den Container des MQTT Broker reinmounten. Um das abzukürzen liegt im GitRepo bereits ein Zertifikat, welches beim Bauen des Containers an die richtige Stelle abgelegt wird.  
Diese laufen aller 90 Tage ab - der Prozess ist hier noch nicht mit bspw. LetsEncrypt automatisiert. Nach 90 Tagen wird der MQTT Broker also vom Frontend keine Daten mehr akzeptieren.
{% endhint %}

