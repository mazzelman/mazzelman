---
title: Die Powershell in Windows hübscher machen
date: 2023-11-29
draft: false
tags:
  - powershell
  - windows
---
Über die Jahre ist die Microsoft Eingabeaufforderung (CMD) immer besser geworden. Seit einiger Zeit, bietet Microsoft auch das Programm "Terminal" an, welches ich hier in diesem Beitrag verwende. Sollte das Terminal nicht installiert sein, kann man es bequem aus dem <a href="https://www.microsoft.com/store/productId/9N0DX20HK701?ocid=pdpshare" target="_blank" rel="noopener noreferrer">Microsoft Store</a> installieren. Wenn man nun das Terminal startet, sollte das ganze in etwa so aussehen:

![Terminal_1.png](https://www.marcelepp.de/images/Terminal_1.png)

Um zusätzlich die neue Windows Powershell zu verwenden, habe ich das Paket von Microsoft installiert. Die Powershell 7 kann <a href="https://learn.microsoft.com/de-de/powershell/scripting/install/installing-powershell-on-windows?view=powershell-7.4" target="_blank" rel="noopener noreferrer">hier</a> herunter geladen werden. In den Einstellungen kann dann die neue Powershell als Standardprofil ausgewählt werden.

![Terminal_2.png](https://www.marcelepp.de/images/Terminal_2.png)

Nun hat man die Powershell der Version 7 als Standard.

![Terminal_3.png](https://www.marcelepp.de/images/Terminal_3.png)

Um das ganze jetzt etwas informativer und schöner zu gestalten, kann man sich zu der Seite <a href="https://ohmyposh.dev/" target="_blank" rel="noopener noreferrer">"Oh My Posh"</a> begeben. Hier kann im Bereich Installation auf English nachschauen, wie die Installation funktioniert. Ich gehe die Installation aber auch hier Stück für Stück durch.

Als erstes installiert man sich "Oh My Posh" mit folgendem Befehl. Hier wird dazu der in Windows 11 integrierte Paketmanager "WinGet" benutzt.

```Powershell
winget install JanDeDobbeleer.OhMyPosh -s winget
```

Wenn alles funktioniert hatte sollte es ungefähr so aussehen:

![Terminal_4.png](https://www.marcelepp.de/images/Terminal_4.png)

Wichtig! Jetzt muss das Terminal einmal neu gestartet werden, damit der Befehl akzeptiert wird.

Mit dem Befehl "oh-my-posh version", kann man jetzt überprüfen ob alles funktioniert. Bei mir wird die Version 24.11.2 ausgegeben.

```Powershell
oh-my-posh version
```

Der nächste Schritt ist eine Schriftart zu installieren, die mit den Symbolen umgehen kann. Wie auf der Hauptseite erwähnt nehme ich ebenfalls die Schriftart "meslo" (Nerdfonts). Der Befehl dafür lautet:

```Powershell
oh-my-posh font install meslo
```

Wenn der Download über das Terminal nicht funktioniert, kann man die Schrift auch manuell von <a href="https://github.com/ryanoasis/nerd-fonts/releases/latest/download/meslo.zip" target="_blank" rel="noopener noreferrer">Github</a> herunter laden und installieren. Eine erfolgreiche Installation schaut so aus:

![Terminal_5.png](https://www.marcelepp.de/images/Terminal_5.png)

Um die Schriftart nun im Terminal zu verwenden, muss man nun die JSON-Datei öffnen. Also "Einstellungen -> JSON-Datei öffnen" anklicken.

![Terminal_6.png](https://www.marcelepp.de/images/Terminal_6.png)

Das öffnet den Code-Editor eurer Wahl. Bei mir ist es VS-Code. Hier sucht man die Stelle mit "profiles" und "defaults" heraus und fügt folgenden Befehl in die zwei geschwungen Klammern bei "defaults" ein.

```JSON
"font":{"face": "MesloLGM Nerd Font"}
```

Das sieht dann ggf. so aus:

![Terminal_7.png](https://www.marcelepp.de/images/Terminal_7.png)

Dann noch speichern und das Terminal neu starten. Die Schrift sollte nun ein ganz klein wenig anders aussehen. Jetzt kann man "Oh my Posh" zum ersten Mal aktivieren. Dazu muss man das Profile der Powershell anpassen. Ich mache das mit:

```Powershell
code $PROFILE
```

Sollte man kein VS Code installiert haben, geht es auch mit dem in Windows mitgelieferten Notepad.

```Powershell
notepad $PROFILE
```

Jetzt wir die Datei mit dem Namen "Microsoft.Powershell_profile.ps1" bearbeitet. Hier fügt man in die Datei folgendes hinzu:

```ps1
oh-my-posh init pwsh | Invoke-Expression
```

Danach das Terminal neu starten. Wenn alles geklappt hat, sollte die Powershell nun so aussehen: 

![Terminal_8.png](https://www.marcelepp.de/images/Terminal_8.png)

Um nun ein anderes Theme zu benutzen kann man unter dem Bereich <a href="https://ohmyposh.dev/docs/themes" target="_blank" rel="noopener noreferrer">Themes</a> nachschauen. Ich mag das Theme "hul10" sehr gerne. Also lade ich mir die JSON-Datei direkt herunter und lege die Datei unter Dokumente -> Powershell ab. Jetzt öffne ich die Powershell Konfiguration erneut mit:

```Powershell
code $PROFILE
```

Hier ersetze ich den vorhanden Text und speichere das Profil.

```Powershell
oh-my-posh init pwsh --config C:\Users\maz\Documents\PowerShell\hul10.omp.json | Invoke-Expression
```

Hat alles geklappt, sieht das Terminal jetzt so aus:

![Terminal_9.png](https://www.marcelepp.de/images/Terminal_9.png)

Optional: Um in VS Code auch die richtige Schrift zu bekommen, kann man in der "settings.json" folgendes hinzufügen:

```JSON
"terminal.integrated.fontFamily": "MesloLGM Nerd Font",
```

Happy Hacking! 🥳