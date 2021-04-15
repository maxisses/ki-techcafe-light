# Ü3.1 - Services aufsetzen & Projekt anlegen

#### Beschreibung

Um mit den Daten zu arbeiten müssen wir zuerst dir Umgebung richtig aufsetzten. Hierfür benutzen wir das CloudPak4Data as a Service \(CP4DaaS\), welches auf der IBM Public Cloud kostenlos zur verfügung steht. Zum Bearbeiten unseres Use Cases benötigen wir folgende 3 Services:  
- Watson Studio  
- Object Storage  
- Watson Machine Learning

#### Schritt für Schritt Anleitung

1.Login in die IBM Cloud: [https://cloud.ibm.com/login](https://cloud.ibm.com/login)

2. Im Suchfeld nach **"Watson Studio"** suchen und öffnen.

![](../../../../.gitbook/assets/image%20%2853%29.png)

3. In «Create Tab» folgende **Einstellung für Watson Studio:**

1. Select a location: **Frankfurt \(eu-de\)**
2. Select a pricing plan: **Lite**
3. Service name: z.B. **Watson Studio + «Dein Name»** \(-&gt; Name spielt keine Rolle\)
4. Select a resource group: **Default** \(oder evt. eine andere\)
5. Click **«Create»** um den Service zu deployen

![](../../../../.gitbook/assets/image%20%2854%29.png)

4. Im Suchfeld nach **"Obejct Storage"** suchen und öffnen.

![](../../../../.gitbook/assets/image%20%2884%29.png)

5. In «Create Tab» folgende **Einstellung für Object Storage:**

1. Select: **Cloud Object Storage \(Lite\)**
2. Click **«Create»** um den Service zu deployen
3. Evt. nochmals mit **«Create»** den Lite Service bestätigen

![](../../../../.gitbook/assets/image%20%2891%29.png)

6. Im Suchfeld nach **"Watson Machine Learning"** suchen und öffnen.

![](../../../../.gitbook/assets/image%20%2885%29.png)

7. Im «Create Tab» folgende **Einstellung für Watson Machine Learning**

1. Select a location: **Frankfurt \(eu-de\)**
2. Select a pricing plan: **Lite**
3. Service name: z.B. **Watson Machine Learning + «Dein Name»** \(-&gt; Name spielt keine Rolle\)
4. Select a resource group: **Default** \(oder evt. eine andere\)
5. Click **«Create»** um den Service zu deployen

![](../../../../.gitbook/assets/image%20%2886%29.png)

8. In die persönliche **«Resource List»** wechseln

![](../../../../.gitbook/assets/image%20%2882%29.png)

9. Überpüfe ob alle **3 Services** angelegt worden sind \(Watson Studio, Object Storage, Watson Machine Learning\)

![](../../../../.gitbook/assets/image%20%2879%29.png)

10. Klicke auf die **Watson Studio** Instanz und dann auf **Get Started**  um das Watson Studio / CP4DaaS zu öffnen

![](../../../../.gitbook/assets/image%20%2888%29.png)

Well Done! Du hast jetzt eine Watson Studio Instanz aufgesetzt. In den nächsten Schritten legen wir ein Projekt an und verbinden die anderen Services mit dem Projekt

![](../../../../.gitbook/assets/image%20%2877%29.png)

11. Klicke **«View all projects»** und wechsle zu deinen Porjekten

![](../../../../.gitbook/assets/image%20%2889%29.png)

12. Click **«New Project»** und lege ein neues Projekt an \(Fall kein Projekt vorhanden ist, sieht das User Interface ein wenig anders aus.

![](../../../../.gitbook/assets/image%20%2881%29.png)



13. **«Create Empty project»**

![](../../../../.gitbook/assets/image%20%2883%29.png)

14. Konfiguriere dein Porjekt

1. Name: z.B. **«KI-TechCafe-**_**Vorname-Nachname**_**»**
2. Storage: hier sollte automatisch dein Object Storage erscheinen
3. Click **«Create»**

![](../../../../.gitbook/assets/image%20%2890%29.png)

15. **«Watson Machine Learning»** Service hinzufügen \(Teil1/2\)

1. Wechsle auf das Tab **«Settings»**
2. **Add Services**
3. **Watson**

![](../../../../.gitbook/assets/screenshot-2021-04-14-at-15.46.35.png)



16. **«Watson Machine Learning»** Service hinzufügen \(Teil2/2\)

![](../../../../.gitbook/assets/screenshot-2021-04-14-at-15.48.36.png)

1. Alle Filter löschen \(Reource Group, Locations, None\)
2. Machine Learning Instanz markieren
3. **«Associate service»**

17. Well Done. Die Data Science Umgebung ist jetzt soweit aufgesetzt. Jetzt kann es losgehen.

