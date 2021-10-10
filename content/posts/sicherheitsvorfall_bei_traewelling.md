---
title: "Sicherheitsvorfall bei Traewelling"
date: 2021-06-20 13:51:26
---
*(english version below)*

Heute Morgen (Sonntag, den 20.06.2021) ist einem unserer Entwickler eine Schwachstelle in Träwelling aufgefallen, welche mit der Anbindung der Social Media-Konten (Twitter und Mastodon) zusammenhängt.

Die Kommunikation mit diesen externen Diensten benötigt mehrere Schlüssel:
Zunächst zwei Anwendungsschlüssel ("AppId" und "Secret"), welche Träwelling einmalig vorhält und dann für jeden User private Schlüssel ("Client Secrets"), mit denen Träwelling im Namen dieses Users z.B. Tweets/Toots posten darf. 

Beim Aufruf einzelner Endpunkte der Träwelling-API konnten die Client-Secrets für Twitter und Mastodon vereinzelter User zeitweise im Klartext ausgelesen werden.
Es besteht derzeit kein Verdacht, dass diese Schwachstelle ausgenutzt wurde. Die AppId und das AppSecret sind von der Lücke nicht betroffen.

Träwelling speichert diese Daten [verschlüsselt](https://laravel.com/docs/8.x/encryption) in der Datenbank, um die Zugangsdaten besonders zu schützen.

## Was wurde getan?

Nach dem Bekanntwerden der Schwachstelle haben wir umgehend [einen Patch](https://github.com/Traewelling/traewelling/pull/441) veröffentlicht und eingespielt, sodass keine User-Schlüssel mehr preisgegeben werden. 

Außerdem haben wir unsere Anwendungsschlüssel zurückgesetzt, sodass alle User-Schlüssel jetzt ungültig sind und daher nicht mehr verwendet werden können.

## Was muss ich tun?

Da wir die Verbindung zu deinen Twitter-und Mastodon-Konten getrennt haben, musst du diese erneut verbinden. Dies ist durch einfaches Abmelden und Anmelden mittels der Provider in den Einstellungen von Träwelling behoben.


## Umgang mit Sicherheitsvorfällen

Träwelling wird nur von einem kleinen Team betrieben, deswegen brauchen wir jede Hilfe, um Fehler und Probleme zu finden.
Wenn Du eine Sicherheitslücke in Träwelling findest, schreibe uns gerne eine Email.
Unsere Emailadressen und PGP-Schlüssel findest Du in der [security.txt](https://traewelling.de/security.txt).

Wir versuchen stets, die Sicherheit der uns anvertrauten Daten zugewährleisten, und eventuelle Probleme offen mit den Nutzer\*innen von Träwelling zu kommunizieren. Bei Fragen sind wir zudem über die Social Media-Kanäle von Träwelling ([@Traewelling](https://twitter.com/traewelling) auf Twitter und [@traewelling@chaos.social](https://chaos.social/@traewelling) bei Mastodon) erreichbar.

---

# English version

This morning, one of our developers noticed a vulnerability in Träwelling, which is related to the connection of the social media accounts (Twitter and Mastodon). 


This communication with the social media services ask for multiple keys to establish a connection.
Two of those keys are used throughout Träwelling ("application id" and "secret"), the other keys are user-specific ("client secrets") and authorize Träwelling to post under your name. Träwelling stores these keys [encrypted](https://laravel.com/docs/8.x/encryption) in our database.

When calling specific endpoints of the Träwelling API, the client secrets for Twitter and Mastodon of individual users could be read in plain text. There is currently no reason to suspect that the vulnerability has been exploited. AppId and AppSecret are not affected by this.




## What have we done?

After discovering this vulnerability, we immediately developed and deployed [a patch](https://github.com/Traewelling/traewelling/pull/441) to stop the leak of more user data.

In addition, we reset all user keys for Twitter and Mastodon, so those keys are no longer valid.

## What do you need to do?

To continue posting your journeys to these platforms, you need to reconnect your Träwelling account with Twitter and Mastodon. This can be done by simply logging off and logging on through these providers.

## Handling security vulnerabilies
A small team works on the development of Träwelling, so we need every help to find bugs and loopholes.
If you find a security issue with Träwelling, please send us an email.
You can find our addresses and encryption keys in our [security.txt](https://traewelling.de/security.txt).

We always try our best to preserve the security of our user's data, and communicate problems with the users of Träwelling.
For any questions, please contact us via our social media channels ([@Traewelling](https://twitter.com/traewelling) on Twitter and [@traewelling@chaos.social](https://chaos.social/@traewelling) on Mastodon).


