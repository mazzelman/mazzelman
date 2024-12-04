---
title: Github Pages Domain verbinden mit INWX
date: 2024-11-29
draft: false
tags:
  - github
  - hosting
---
Um eine Domain von <a href="https://www.inwx.de" target="_blank" rel="noopener noreferrer">INWX</a> erfolgreich mit Github bzw. Github Pages zu verbinden, muss man einige Einstellungen vornehmen. Als erstes muss man in Github ein spezielles Repository anlegen. Es muss genau so heißen wie der Benutzername auf Github. Mein Username ist mazzelman. Also heißt das Repository "mazzelman". Dies wird automatisch für Github Pages benutzt. Bei INWX meldet man sich nun an und geht auf "Domainliste". Hier klickt man auf das Zahnrad hinter der Domain die man bearbeiten möchte. In dem Menü das jetzt aufgeht wählt man "DNS-Einträge" aus. Hier fügt man nun folgende Werte hinzu:

| Name | Typ   | Wert                | Prio | TTL  |
| ---- | ----- | ------------------- | ---- | ---- |
|      | A     | 185.199.108.153     |      | 3600 |
|      | A     | 185.199.109.153     |      | 3600 |
|      | A     | 185.199.110.153     |      | 3600 |
|      | A     | 185.199.111.153     |      | 3600 |
| www  | CNAME | username.github.io  |      | 3600 |
|      | AAAA  | 2606:50c0:8000::153 |      | 3600 |
|      | AAAA  | 2606:50c0:8001::153 |      | 3600 |
|      | AAAA  | 2606:50c0:8002::153 |      | 3600 |
|      | AAAA  | 2606:50c0:8003::153 |      | 3600 |

Beim CNAME ersetzt man "username" natürlich durch den eigenen username! Der SOA Eintrag wird von INWX bereit gestellt. Hier nimmt man keine Änderungen vor. Nun wechselt man im Browser zu Github und besucht das Repository. Im "Settings" Bereich des Repositorys gibt es den Eintrag "Pages".

![github_pages_1.png](https://www.marcelepp.de/images/github_pages_1.png)

Im mittleren Bereich gibt es hier den Punkt "Custom Domain". Hier habe ich meine Domain www.marcelepp.de eingetragen und auf "Save" gedrückt. Es erfolgt ein check, ob alles richtig verbunden ist. Es werden dann ggf. 3 Schritte ausgeführt für die Erstellung eines Zertifikates. Wenn dieser Vorgang abgeschlossen ist, kann ein Haken bei "Enforce HTTPS" gesetzt werden.

![github_pages_2.png](https://www.marcelepp.de/images/github_pages_2.png)

Zusätzlich habe ich im Repository noh eine CNAME-Datei erstellt mit dem Inhalt der Domain.

![github_pages_3.png](https://www.marcelepp.de/images/github_pages_3.png)

In der Datei steht nichts anderes als die Domain selbst.

![github_pages_4.png](https://www.marcelepp.de/images/github_pages_4.png)

Zum Schluss, ist noch ganz wichtig, das die Änderungen mehrere Stunden dauern können! Also wäre es ungünstig die Einstellungen zu wechseln, wenn es nicht gleich auf Anhieb funktioniert. 

Happy Githubing! 🥳
