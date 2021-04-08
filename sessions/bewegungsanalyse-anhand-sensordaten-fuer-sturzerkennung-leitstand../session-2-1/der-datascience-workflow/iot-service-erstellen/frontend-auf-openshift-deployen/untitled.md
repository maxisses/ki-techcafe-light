# Verbinden mit dem OpenShift Cluster

Geht auf cloud.ibm.com und wählt euren OpenShift Cluster aus. Um über eure CLI mit dem Cluster zu kommunizieren, müsst ihr eine kubeconfig erstellen. Dazu braucht ihr einen token, den ihr über die GUI des OpenShift Clusters erhaltet. Öffnet die GUI zw. Console über den blauen Button.

![](../../../../../../.gitbook/assets/image%20%2816%29.png)

Rechts oben findet ihr ein Dropdown mit eurem Nutzernamen. Geht auf "copy login command" und kopiert euch den gesamten Befehl, wie unten in dem Bild dargestellt.

![](../../../../../../.gitbook/assets/image%20%2817%29.png)

![](../../../../../../.gitbook/assets/image%20%2813%29.png)

Jetzt habt ihr die Wahl - entweder ihr habt das oc CLI Tool lokal. Alternativ könnt ihr die IBM Cloud CLI verwenden. Ihr findet sie auf der Startseite [www.cloud.ibm.com ](https://cloud.ibm.com/)rechts oben. Im Bild das Symbol ganz links, welches euch einen Terminal öffnet wo "oc", "kubectl" usw. schon vorinstalliert ist.

![](../../../../../../.gitbook/assets/image%20%2814%29.png)

![](../../../../../../.gitbook/assets/image%20%2812%29.png)



{% hint style="info" %}
oc ist eine Erweiterung zu kubectl. Ihr könnt also auch mit kubectl mit dem OpenShift Cluster arbeiten. Aber oc bietet noch mehr Funktionalitäten. Hier ein Beispiel:
{% endhint %}

![](../../../../../../.gitbook/assets/image%20%2815%29.png)

