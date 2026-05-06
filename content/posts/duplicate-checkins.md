---
title: "Doppelte Checkins: Bitte aufräumen bis zum 31. Mai"
date: 2026-05-06 00:00:00
author: "MrKrisKrisu"
categories: [ Bekanntmachungen ]
---

*(english version below)*

**TL;DR:** Schaut bitte auf [traewelling.de/statuses/duplicates](https://traewelling.de/statuses/duplicates) und löscht
eure doppelten Checkins. Ab dem 31. Mai 2026 erledigen wir das automatisch.

---

Wir haben ein kleines Datenbankproblem, das wir gerne gemeinsam mit euch bereinigen möchten,
bevor wir es automatisiert erledigen müssen.

## Was ist passiert?

Vor einigen Jahren haben wir beim Umbauen unserer Datenbankstruktur versehentlich einen
sogenannten **UNIQUE-Constraint** auf der Tabelle für Checkins entfernt. Ein UNIQUE-Constraint
ist eine Datenbankregel, die dafür sorgt, dass eine bestimmte Kombination von Werten nur einmal
vorkommen darf. In unserem Fall: ein User darf nicht zweimal in dieselbe Fahrt vom selben
Startpunkt einchecken.

Ohne diese Regel war es technisch möglich, denselben Checkin mehrfach zu speichern. In der
Praxis hat dabei ein weiterer Umstand geholfen: Der Eincheck-Button auf Träwelling ließ sich
bis vor einigen Wochen mehrfach klicken, ohne dass die Seite das verhindert hat. Wer also auf
schlechtem Internet unterwegs war und ungeduldig geklickt hat. Herzliches Willkommen im Club,
ihr seid nicht allein.

## Was genau ist ein Duplikat in unserem Fall?

Ein Duplikat entsteht, wenn für denselben User zwei oder mehr Checkins mit derselben
**Fahrt** (`trip_id`) und demselben **Abfahrtsstopp** (`origin_stopover_id`) existieren.
Der Abfahrtsstopp ist dabei eindeutig durch Station und geplante Abfahrtszeit definiert,
also wäre "ICE 74, Abfahrt Karlsruhe Hbf 10:37 Uhr" eine eindeutige Kombination.

Technisch gesehen: Der UNIQUE-Constraint, den wir wiederherstellen wollen, liegt auf
`(user_id, trip_id, origin_stopover_id)` in der `train_checkins`-Tabelle.

## Warum löscht ihr das nicht einfach?

Das wäre natürlich der einfachste Weg. Aber eure Checkins sind eure Reisedaten, und wir
möchten nicht einfach irgendwelche Einträge löschen, ohne dass ihr die Chance hattet, das
selbst zu kontrollieren. Vielleicht habt ihr einen der doppelten Checkins nachträglich
bearbeitet, eine andere Destination gesetzt oder einen Kommentar hinzugefügt, der euch
wichtig ist.

Deshalb haben wir eine temporäre Seite eingerichtet:

## [traewelling.de/statuses/duplicates](https://traewelling.de/statuses/duplicates)

Dort seht ihr alle eure Checkins, die als Duplikat gelten, gruppiert nach Fahrt und
Abfahrtsstopp. Ihr könnt selbst entscheiden, welchen ihr behalten möchtet, und die anderen
löschen.

## Was passiert nach dem 31. Mai 2026?

Ab dem **31. Mai 2026** werden wir automatisiert alle verbleibenden Duplikate bereinigen.
Dabei gilt folgende Regel: **Der älteste Checkin einer Gruppe bleibt erhalten**, also der
mit der niedrigsten ID, sprich der, der zuerst angelegt wurde. Alle neueren Duplikate werden
gelöscht.

Wenn euch das egal ist und ihr euren ältesten Checkin eh behalten wollt, müsst ihr nichts
tun. Wenn ihr aber selbst die Kontrolle haben möchtet, schaut bis dahin bitte auf der
Duplikate-Seite vorbei.

Sorry für die Umstände. :(

---

# Duplicate Check-ins: Please clean up by 31 May

**TL;DR:** Please check [traewelling.de/statuses/duplicates](https://traewelling.de/statuses/duplicates) and delete your
duplicate check-ins. After 31 May 2026, we will do it automatically.

---

We have a small database issue that we'd like to clean up together with you, before we have
to do it automatically.

## What happened?

A few years ago, while restructuring our database, we accidentally removed a
**UNIQUE constraint** on the check-ins table. A UNIQUE constraint is a database rule that
ensures a specific combination of values can only appear once. In our case: a user should
not be able to check in to the same trip from the same starting point more than once.

Without this rule, it was technically possible to save the same check-in multiple times.
In practice, another issue made this worse: until a few weeks ago, Träwelling's check-in
button could be clicked multiple times without the app preventing it. If you were on a bad
connection and impatiently tapping away. You're not alone, we've heard from a few of you.

## What exactly is a duplicate?

A duplicate occurs when two or more check-ins for the same user share the same
**trip** (`trip_id`) and the same **origin stop** (`origin_stopover_id`). The origin stop
is uniquely defined by a station and its planned departure time, so "ICE 74, departing
Karlsruhe Hbf at 10:37" would be one unique combination.

Technically speaking: the UNIQUE constraint we want to restore covers
`(user_id, trip_id, origin_stopover_id)` in the `train_checkins` table.

## Why not just delete them automatically?

That would obviously be the easiest path. But your check-ins are your travel data, and we
don't want to just delete entries without giving you a chance to review them first. Maybe
you edited one of the duplicate check-ins, set a different destination, or added a note
that matters to you.

That's why we've set up a temporary page:

## [traewelling.de/statuses/duplicates](https://traewelling.de/statuses/duplicates)

There you can see all your check-ins flagged as duplicates, grouped by trip and origin stop.
You decide which one to keep, and delete the rest.

## What happens after 31 May 2026?

Starting **31 May 2026**, we will automatically clean up all remaining duplicates. The rule
is simple: **the oldest check-in in a group is kept**, that's the one with the lowest ID,
i.e. the one created first. All newer duplicates will be deleted.

If you're fine with that and happy to keep your oldest check-in, you don't need to do
anything. But if you'd like to stay in control, please visit the duplicates page before then.

Sorry for the mess. :(
