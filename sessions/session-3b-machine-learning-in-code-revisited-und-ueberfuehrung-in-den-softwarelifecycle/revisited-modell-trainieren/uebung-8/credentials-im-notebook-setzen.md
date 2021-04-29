# Credentials im Notebook setzen

### Credentials für Watson Machine Learning Dienst anlegen

#### API Key generieren

Hierzu folgt man der Anleitung [https://cloud.ibm.com/docs/account?topic=account-userapikey\#create\_user\_key](https://cloud.ibm.com/docs/account?topic=account-userapikey#create_user_key) und packt ihn entsprechend hier hi

![](../../../../.gitbook/assets/image%20%28134%29.png)

#### URL anpassen

Je nachdem in welcher Region man seinen WML Service angelegt hat tauscht man "us-south" bspw. durch "eu-de" \(Frankfurt\) oder "eu-gb" \(London\) aus.

#### Deployment Space UID

In Übung 6 haben wir einen Deployment Space angelegt. Dort gehen wir hinein und kopieren die Space GUID und legen sie entsprechend an.

![](../../../../.gitbook/assets/image%20%28137%29.png)



### Credentials anlegen um Datei aus dem Objectstorage laden

Das ist deutlich einfacher. Im Notebook klicken wir in die entsprechende Zelle:

![](../../../../.gitbook/assets/image%20%28136%29.png)

Und gehen dann rechts oben auf "Find and add data". Danach fügen wir die \*.pkl Datei Credentials ein und ändern den Namen der Variable auf "credentials\_objectstorage".

![](../../../../.gitbook/assets/image%20%28133%29.png)



