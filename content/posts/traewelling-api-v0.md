---
title: "*klingeling* Träwelling hat was neues!  "
date: 2020-06-13 17:15:48
author: "Das Träwelling Team"
categories: [Bekanntmachungen]
---
Wir haben endlich Notifications!  
Endlich könnt ihr die Funktion, die wir damals wegen Twitter API-Beschränkungen abschaffen mussten wieder nutzen!  
  
Wenn ihr in einem Zug unterwegs seid, könnt ihr jetzt sehen, wenn jemand bei euch eincheckt!  
  
Ebenso seht ihr neue Likes auf eure Checkins und neue Follower!  
  
Wie damals am Ende unseres [Trailers](https://twitter.com/Traewelling/status/1198582106911318022) angekündigt, soll Träwelling irgendwann auch als App verfügbar sein.   
  
Diesen sehr aufwändigen Schritt haben wir leider noch nicht machen können, dafür einen sehr großen in diese Richtung: Träwelling bekommt eine API!   
  
Diese ist für's erste in einer Version Null, die sich jederzeit unangekündigt ändern kann. Leider ist sie für's erste auch auf eine einfache Nutzername-Passwort Autorisierung abgespeckt. (Für Interessierte gibt es die Swagger Doku [hier](https://github.com/Traewelling/traewelling/blob/develop/api-swagger-v0.yml)  
  
Als nächste große Aufgaben werden wir uns aber ans Frontend machen und dieses komplett auf dieser API aufbauen, damit es hoffentlich ein wenig schneller wird.  
  
Außerdem haben wir in diesem großen Update noch:  
  
**Bugfixes**  
 * Fast-Forward Checkins funktionieren jetzt auch bei Zügen, die Früher terminieren  
 * Social-Media-Links zu Mastodon und Twitter auf den Profilen
 * `rel="me"` links auf der Profilseite (Bspw. für verlinkte Profile auf Mastodon, etc.)  
 * Anpassung der Top-Liste falls derzeit weniger als 20 Leute unterwegs sind
 * Ein paar Änderungen, die Träwelling minimal schneller machen sollten
  
**Features**  
 * Durchschnittsgeschwindigkeit in den Top- Listen 
   
**Features für Entwickler**  
* Ein neues Admin-Panel
* Seeder für Checkins, Nutzer, Züge, etc. für schnelleres Entwickeln und Testen
