# Übung 6: Modell als API deployen

### Deployment Space anlegen

Über das Menü links oben:

![](../../../.gitbook/assets/image%20%2896%29.png)

Gelangt man im linken Menü zu "Deployments".

![](../../../.gitbook/assets/image%20%2897%29.png)

Hier legt man sich einen neuen Deployment Space an:

![](../../../.gitbook/assets/image%20%28100%29.png)

Nötig sind dafür ein Machine Learning Service und ein Objektstorage. Den solltet ihr bereits haben. Ansonsten erstellt einen über das Dropdown.

![](../../../.gitbook/assets/image%20%2898%29.png)

### Zurück ins Projekt gehen um Modell zu "deployen"

Geht zurück in euer Projekt und wählt euer Modell aus. Dort findet ihr den Button "Promote to deployment space".

![](../../../.gitbook/assets/image%20%28101%29.png)

Im nächsten Screen müsst ihr euren Space auswählen und "Promote" klicken:

![](../../../.gitbook/assets/image%20%2895%29.png)

Dort seht ihr euer Modell als Asset und wenn ihr da drauf geht findet ihr rechts mit Raketensymbol den deploy Button.

![](../../../.gitbook/assets/image%20%2899%29.png)

### API Schnittstelle für das Modell anlegen

Klickt im Folgenden Schritt auf Create.

![](../../../.gitbook/assets/image%20%2892%29.png)

Wechselt danach zu Deployments und et voilá - hier sollte euer Modell - bald im Status "Deployed" sein:

![](../../../.gitbook/assets/image%20%2893%29.png)

**API testen**

{% api-method method="get" host="" path="" %}
{% api-method-summary %}

{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

\*\*\*\*

