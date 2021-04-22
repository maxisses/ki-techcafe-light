# Zertifikatshölle

{% hint style="warning" %}
Leider müssen wir das entsprechende Zertifikat für eine verschlüsselte Verbindung zB über eine ConfigMap in den Container des MQTT Broker reinmounten.   
Diese laufen aller 90 Tage ab - der Prozess ist hier noch nicht mit LetsEncrypt und regelmäßiger Aktualisierung automatisiert - erstens aus Zeitgründen, und zweitens ist es ein gutes Learning :\). Nach 90 Tagen wird der MQTT Broker also vom Frontend keine Daten mehr akzeptieren, außer man macht das nachfolgende wieder manuell.

Die durch den Loadbalancer der Cloud automatisch erzeugten Zertifikate werden hier \(siehe Screenshot\) abgelegt und können abgerufen werden um sie auch in den MQTT Broker zu importieren.
{% endhint %}

### 1. Zertifikat herunterladen

In der IBM Cloud gelangt man über die Ressourcenliste und dort den Bereich "Services" zum entsprechenden Certificate Manager des Clusters. Dort kann man die Dateien, des relevanten   als \*.zip herunterladen.

![](../../../../../.gitbook/assets/image%20%2815%29.png)

### 2. Kubernetes ConfigMap für Mosquitto Konfiguration anpassen und erstellen

Gleich werden wir unserem Mosquitto Broker eine spezielle Konfigurationsdatei als ConfigMap zur Verfügung stellen. Dafür müssen wir diese Configmap auf dem Cluster anlegen und den Namespace enstprechend anpassen auf euer OpenShift Projekt.  
Die Datei liegt im Unterordner "mosquitto" des "openshift"-Ordners und kann dort angepasst werden.

```text
apiVersion: v1
kind: ConfigMap
metadata:
  name: mosquitto-config
  namespace: <euer namespace>
  labels:
    app: sensorapp  
data:
  mosquitto.conf: |    
    persistence false
    # mqtt
    listener 1883
    protocol mqtt
    # websockets
    # websockets over ssl
    listener 8883
    protocol websockets
    certfile /etc/mosquitto/certs/certfile_default.pem
    cafile /etc/mosquitto/certs/cafile_default_intermediate.pem
    keyfile /etc/mosquitto/certs/keyfile_default.key
    allow_anonymous true
```

Um sie dann zu deployen \(hier aus dem Hauptfolder heraus\):

```text
oc apply -f openshift/mosquitto/ocp-mosquitto-config.yaml
```

### 3. Kubernetes Secret für Mosquitto Konfiguration anpassen und erstellen

Nun müssen noch die aktuell im zip liegenden bzw. oben in der ConfigMap referenzierten 3 Zertfikatsdateien im Cluster angelegt werden. Dazu erstellen wir ein Kubernetes Secret, welches als Datei im gleichen Ordner liegt \("openshift/mosquitto/ocp-mosquitto-nlb-cert-secret.yaml"\).

```text
apiVersion: v1
kind: Secret
metadata:
  name: mosquitto-cert
  namespace: sensorapp-dummymax
data:
  keyfile_default.key: |-
    <hier key base64 encoded aus dem zip-File reinpasten>
  certfile_default.pem: |-
    <hier pem base64 encoded aus dem zip-File reinpasten>
  cafile_default_intermediate.pem: |-
    <hier intermediate pem base64 encoded aus dem zip-File reinpasten>
```

{% hint style="info" %}
In Unix kann man auf Kommandozeile bspw mit:  
"echo "...Zertifikat..." \| base64  
den kodierten Wert erstellen
{% endhint %}

Danach wird das File ebenfalls deployed:

```text
oc apply -f openshift/mosquitto/ocp-mosquitto-nlb-cert-secret.yaml
```

### 4. Mosquitto deployment anpassen

Beim anlegen des Mosquitto Deployments sind wir den "leichten Weg" gegangen mit **oc new-app.**  
Aber dabei werden selbstverständlich YAML-Dateien angelegt. Nämlich automatisiert.

Im Cluster können wir in unserem Projekt das Deployment in der Topologie anwählen und in das YAML des Deployment gehen.

{% hint style="info" %}
oc new-app .... not .. . sondern yaml files ziehen für prod in helm chart packen
{% endhint %}

Diese müssen im Kubernetes 

