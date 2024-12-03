---
title: SSH Schlüssel unter WSL erstellen
date: 2024-11-29
draft: false
tags:
  - wsl
  - windows
  - ssh
---
Um unter WSL in Windows einen SSH Schlüssel zu generieren und diesen dann mit GitHub zu benutzen, kann man wie folgt vorgehen. Als erstes kann man überprüfen ob ein Schlüssel vorhanden ist.

```Bash
ls -al ~/.ssh
```

Sollte es schon einen SSH Schlüssel geben erscheint eine Ausgabe die in etwa so aussehen kann:

```Bash
id_rsa.pub
id_ecdsa.pub
id_ef25419.pub
```

Wenn keine Ausgabe erfolgt, kann man einen neuen Schlüssel generieren:

```Bash
ssh-keygen -t ef25419 -C "dein.name@gmail.com"
```

Wenn die Abfrage erscheint, wo die Datei gespeichert werden soll, drückt man Enter um den Standard Ort zu wählen. Weiterhin kommt eine Abfrage für eine "Passphrase". Hier kann man ein zusätzliches "Passwort" vergeben. Dieses wird dann ggf. aber auch abgefragt. Als nächstes wird der "ssh-agent" gestartet.

```Bash
eval "$(ssh-agent -s)"
```

Wenn der "ssh-agent" läuft, kann man den Schlüssel mit dem "ssh-agent" bekannt machen.

```Bash
ssh-add ~/.ssh/id_ef25419
```

Nun kann man den Schlüssel bei GitHub angeben. Zuerst liest man den Schlüssel aus mit:

```Bash
cat ~/.ssh/id_ed25519.pub | clip
```

Sollte kein clip auf dem System zur Verfügung stehen, kann man den Befehl ohne clip ausführen und den Schlüssel aus dem Terminal kopieren. Auf Github begibt man sich nun auf die Seite und meldet sich an. Unter "Settings" gibt es dann "SSH and GPG keys". Hier klickt man auf "New SSH key". Als Titel kann man z.B. den Computer angeben, auf dem der Schlüssel liegt. Im "Key" Feld wird der kopierte Schlüssel eingefügt. Um nun die Verbindung zu testen, kann man im Terminal den Befehl absetzen:

```Bash
ssh -T git@github.com
```

In der Regel wird jetzt nach einem "RSA key fingerprint" gefragt. Hier bestätigt man mit yes. Sollte alles geklappt haben, bekommt man eine Meldung das man sich erfolgreich verbunden hat. 😎