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

Klickt auf euer Deployment. Wählt oben den Tab "Test" aus und wählt hier "Provide Input as JSON":

![](../../../.gitbook/assets/image%20%28119%29.png)

Dort könnt ihr folgendes reinkopieren und auf predict klicken um euer deployment zu testen.

```text
{
	"input_data": [
		{
			"fields": [
				"x_1",
				"y_1",
				"z_1",
				"x_2",
				"y_2",
				"z_2",
				"x_3",
				"y_3",
				"z_3",
				"x_4",
				"y_4",
				"z_4",
				"x_5",
				"y_5",
				"z_5",
				"x_6",
				"y_6",
				"z_6",
				"x_7",
				"y_7",
				"z_7",
				"x_8",
				"y_8",
				"z_8",
				"x_9",
				"y_9",
				"z_9",
				"x_10",
				"y_10",
				"z_10",
				"classes"
			],
			"values": [
				[0, 0.1, 9.600000000000001, 0, 0.1, 9.600000000000001, 0, 0.1, 9.600000000000001, 0, 0.1, 9.600000000000001, 0, 0.1, 9.600000000000001, 0, 0.1, 9.600000000000001, 0, 0.1, 9.600000000000001, 0, 0.1, 9.600000000000001, 0, 0.1, 9.600000000000001, 0, 0.1, 9.600000000000001], [7.800000000000001, -6, -0.30000000000000004, 9.5, -6.7, -1, 9.600000000000001, -7.2, 2.8000000000000003, 11.600000000000001, -8.3, -6.300000000000001, 7, -7.300000000000001, 2.3000000000000003, 5, -8.3, 2, 7.7, -8.700000000000001, 0.30000000000000004, 7.800000000000001, -6.2, -1.3, 3.4000000000000004, -5.1000000000000005, -1.2000000000000002, 2.7, -4.9, -0.30000000000000004],[5.9, -8, 3.1, 5.2, -5.4, -4.9, 4.7, -7.1000000000000005, -0.30000000000000004, 11.5, -4.9, -2.4000000000000004, 7.300000000000001, -5, 0, 7.9, -4.800000000000001, -1.9000000000000001, 7.4, -5, -2.5, 8, -4.9, -0.9, 10.600000000000001, -5, -3.9000000000000004, 12.200000000000001, -4.800000000000001, -1.8], [-0.2, 3.7, 11.3, 1.9000000000000001, 4.3, 5.5, 0.1, 5.5, 4.7, -1.1, 5.4, 5.800000000000001, -0.30000000000000004, 5.7, 7.300000000000001, 0.30000000000000004, 6.2, 7.800000000000001, 0.1, 5.800000000000001, 7.4, 0.4, 6.2, 7.800000000000001, 0.9, 6.300000000000001, 6.800000000000001, 0.6000000000000001, 6.5, 7.5], [3.5, -8.6, 0.9, 3.8000000000000003, -8.9, -0.30000000000000004, 5, -9.200000000000001, 0.9, 3.9000000000000004, -9.8, 0.9, 6.4, -12.4, -1.6, 3.2, -12.5, -3.6, 0.1, -11, -1.5, 3.6, -10.3, -1.2000000000000002, 2.9000000000000004, -9.9, -0.5, 3, -7.4, -1], [3.4000000000000004, -10.4, -1.9000000000000001, 7.4, -12.3, -2.4000000000000004, 2.5, -12.200000000000001, -0.4, 2.1, -10.5, 0.7000000000000001, 2.9000000000000004, -11.3, -0.9, 3, -7.1000000000000005, -1.1, 1.6, -4.9, -1.1, 0.2, -4.800000000000001, -0.6000000000000001, -1, -5.4, -1, 6.800000000000001, -8.8, -6]
			]
		}
	]
}
```

