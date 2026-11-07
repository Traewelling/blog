---
title: "SSRF-Lücke bei Webhooks"
date: 2026-11-07T18:00:00+02:00
author: "jannik"
categories: [ Bekanntmachungen, Changelog ]
---

[_english version below_](#english-version)

Das Träwelling-Team hat einen Security Advisory über GitHub bekommen, dass die Webhook-Komponente von Träwelling anfällig für Server-Side Request Forgery ist. Dies ist ein Problem für Träwelling-Instanzen, denn es ermöglicht den Zugriff auf Webserver, die der Träwelling-Server sieht, die aber unter Umständen nicht im Internet stehen. Das könnten interne Anwendungen auf dem selben Server (oder dem selben Netzwerk) sein.

Personenbezogene Daten von Träwelling-Nutzenden waren durch diese Lücke nicht zugänglich.

Aus gegebenen Anlass rufen wir die Betreiber\*innen von Träwelling-Instanzen auf, ihre Server auf die aktuelle Version [2026.11.07](https://github.com/Traewelling/traewelling/releases/tag/2026.11.07) zu updaten. Es gibt einen `artisan` Command, welcher die konfigurierten Webhooks auf die Lücke prüft (siehe Changelog!).

## Ablauf

| Datum | Was ist passiert? |
| --- | --- | 
| 2026-11-05 | [Security Advisory auf GitHub](https://github.com/Traewelling/traewelling/security/advisories/GHSA-4h3f-pf38-2rhj) durch den Reporter "Florian Kabashi" |
| 2026-11-06 | Entwicklung einer Prüfung und des `artisan` Commands zum Prüfen. |
| 2026-11-07 | Code Review der Codeänderung, Deployment der Fix-Version, Veröffentlichung des Blogposts |

## Credits

Wir danken [Florian Kabashi](https://github.com/apocalypse-agent) für den Report.

---

# English version

The Träwelling team has been informed via GitHub's Security Advisory service, that the Träwelling webhook component is vulnerable to Server-Side Request Forgery (SSRF).
This is an issue for deployments of Träwelling, because it allows external access to webservers that are accessable to the Träwelling deployment, but not to the public internet. These could be internal tools deployed to the same server (or private network).

Personal data of Träwelling users has not been accessable by this problem.

For this reason, we call administrators of Träwelling servers to update their servers to the current version [2026.11.07](https://github.com/Traewelling/traewelling/releases/tag/2026.11.07).
We have added an `artisan` command that checks the configured webhooks (see changelog!).

## Timeline

| Date | Action |
| --- | --- | 
| 2026-11-05 | [Security Advisory in GitHub](https://github.com/Traewelling/traewelling/security/advisories/GHSA-4h3f-pf38-2rhj) by the reporter "Florian Kabashi" |
| 2026-11-06 | Development of a check in the webhook code and the `artisan` commands. |
| 2026-11-07 | Code review of the Change, deployment of the fix version, release of this blog post |

## Credits

We thank [Florian Kabashi](https://github.com/apocalypse-agent) for the report.
