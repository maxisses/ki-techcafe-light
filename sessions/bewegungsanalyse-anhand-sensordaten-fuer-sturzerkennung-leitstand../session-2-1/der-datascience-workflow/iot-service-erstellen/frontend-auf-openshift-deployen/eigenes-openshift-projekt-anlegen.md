# eigenes OpenShift Projekt anlegen



Die Ressource Project ist eine OpenShift spezifische Erweiterung von Kubernetes. Jedes Projekt erhält auch seinen gleichnamigen Kubernetes Namespace. Projekte können u. a. für folgende Use Cases genutzt werden:

* Separate Namespaces für Applikationen und andere Ressourcen.
* Berechtigungen können auf Projektebene vergeben werden, um z. B. nur bestimmten Teams Zugriff zu gewähren.
* Trennung der Projekte auf Netzwerkebene durch _NetworkPolicies_.
* Definition von Resource Quotas auf Projektebene.
* nicht zuletzt kann durch die Kombination der oberen Punkte eine komplette Mandantentrennung vollzogen werden.

Damit wir unsere neue Applikation bauen und deployen können müssen wir uns zunächst ein neues Projekt anlegen.

## OC CLI

```text
oc new-project sensorapp-<eure initialien> (klein geschrieben)
```

## Web UI

{% hint style="info" %}
Projekte anlegen ist beim Administrator angesiedelt.
{% endhint %}

![](../../../../../../.gitbook/assets/image%20%2820%29.png)

