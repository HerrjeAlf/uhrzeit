# Klausuruhr

Eine Uhr für den Klassenraum, die bei Klausuren auf dem Smartboard oder Beamer läuft. Sie zeigt groß die Uhrzeit, die Bearbeitungszeit mit Restzeit und Fortschrittsbalken sowie die Hinweise zur Klausur.

**Zur Klausuruhr: https://herrjealf.github.io/uhrzeit/**

Sie läuft direkt im Browser, ohne Anmeldung und ohne Installation.

## Funktionen

- **Große Uhrzeit**, auf Wunsch mit Sekunden und Datum
- **Bearbeitungszeit** mit Restzeit („noch 25 min“) und Fortschrittsbalken. Kurz vor Schluss wird die Anzeige gelb, nach dem Ende rot.
- **Nachteilsausgleich** in Prozent. Die zusätzliche Zeit wird zugunsten der Schüler:innen auf volle Minuten aufgerundet und separat angezeigt.
- **Unterbrechungen**: Die Zeit lässt sich im Notfall anhalten oder nach einer Störung um einige Minuten verlängern (siehe unten).
- **Hinweise** zur Klausur, z. B. zu den Hilfsmitteln. Häufige Hinweise lassen sich per Klick hinzufügen. Die Schriftgröße passt sich automatisch an den freien Platz an.
- **Anzeige**: Hintergrundbilder zur Auswahl, Hinweise unter oder neben der Uhr, Schullogo ein- und ausblendbar
- **Für den Unterricht gemacht**: Vollbild per Knopfdruck. Bedienleiste und Mauszeiger verschwinden nach 4 Sekunden, und der Bildschirm geht nicht in den Ruhezustand, sofern der Browser das unterstützt (aktuelle Versionen von Chrome, Edge, Safari und Firefox).

## Bedienung

1. Klausuruhr öffnen. Solange keine Bearbeitungszeit eingestellt ist, öffnen sich die Einstellungen von selbst.
2. Unter **Bearbeitungszeit** den Beginn eintragen (oder **Jetzt** antippen) und eine Dauer wählen, z. B. **90 min**. Alternativ das Ende direkt eintragen.
3. Bei Bedarf den Nachteilsausgleich wählen und die Hinweise anpassen.
4. **Fertig** antippen und **Vollbild** einschalten.

Alle Änderungen gelten sofort. Die Einstellungen öffnet man wieder, indem man die Maus bewegt oder auf den Bildschirm tippt. Dann erscheint unten rechts die Bedienleiste.

### Unterbrechungen

Für Störungen während der Klausur, z. B. einen Feueralarm, gibt es zwei Möglichkeiten:

- **Zeit anhalten**: Der Knopf erscheint in der Bedienleiste, sobald die Bearbeitungszeit läuft. Er ist auch in den Einstellungen unter **Unterbrechung** zu finden, oder man drückt die Taste <kbd>P</kbd>. Die Restzeit bleibt stehen, und die Anzeige meldet in Blau „Unterbrochen“. Mit **Zeit fortsetzen** läuft sie weiter. Die Dauer der Unterbrechung wird, auf volle Minuten aufgerundet, ans Ende angehängt. Ein versehentliches Anhalten unter 10 Sekunden verlängert nichts.
- **Zeit verlängern**: In den Einstellungen unter **Unterbrechung** die Zeit um +1, +5, +10 oder +15 Minuten verlängern. Die Anzeige nennt dann die neue Endzeit und darunter z. B. „Wegen Unterbrechung um 10 min verlängert – ursprünglich bis 09:30 Uhr“. Darin sind auch die Minuten aus beendeten Pausen enthalten. Mit **zurücknehmen** wird die gesamte Verlängerung wieder entfernt. Während die Zeit angehalten ist, geht das nicht.

Beides gilt für die reguläre Bearbeitungszeit und den Nachteilsausgleich gleichermaßen. Ist die reguläre Zeit schon abgelaufen und schreiben nur noch Schüler:innen mit Nachteilsausgleich, verlängert sich nur deren Zeit.

Wer einen neuen Beginn einträgt, startet eine neue Klausur. Verlängerungen und Unterbrechungen werden dann zurückgesetzt.

### Tastenkürzel

| Taste | Wirkung |
| --- | --- |
| <kbd>E</kbd> | Einstellungen öffnen und schließen |
| <kbd>F</kbd> | Vollbild ein und aus |
| <kbd>P</kbd> | Zeit anhalten und fortsetzen |
| <kbd>Esc</kbd> | Einstellungen schließen |

## Datenschutz

Die Klausuruhr setzt keine Cookies, nutzt kein Tracking und lädt nichts von fremden Servern. Die Einstellungen liegen nur im Browser des jeweiligen Geräts (`localStorage`). Titel, Zeiten, Verlängerungen und Unterbrechungen werden am nächsten Tag automatisch gelöscht. Hinweise und Anzeigeoptionen bleiben erhalten. Einzelheiten stehen in [Impressum und Datenschutz](impressum.html).

## Technik

Die ganze Anwendung steckt in einer Datei, [index.html](index.html), mit HTML, CSS und JavaScript. Es gibt keine Abhängigkeiten und keinen Build-Schritt. Veröffentlicht wird die Seite über GitHub Pages, Änderungen am Branch `main` sind nach kurzer Zeit online.

```
index.html       Klausuruhr
impressum.html   Impressum und Datenschutz
img/             Hintergrundbilder und Schullogo
```

### Lokal ausprobieren

Am einfachsten öffnet man `index.html` direkt im Browser. Alternativ startet man einen kleinen Webserver:

```sh
python3 -m http.server 8000
# dann http://localhost:8000 öffnen
```

### Hintergrundbild hinzufügen

1. Das Bild in `img/` ablegen, am besten im Format 16:9 und mindestens 1920 px breit.
2. In `index.html` einen Eintrag in der Liste `HINTERGRUENDE` ergänzen. Der Wert `helligkeit` bestimmt, wie stark das Bild abgedunkelt wird (0 = schwarz, 1 = unverändert), damit die Schrift gut lesbar bleibt.
3. Jedes Hintergrundbild wird unten links als „KI-generiert“ gekennzeichnet, weil das bisher auf alle Bilder zutrifft. Für ein Foto oder eine Grafik aus anderer Quelle muss diese Kennzeichnung angepasst werden (in `anzeigeAufbauen()`), und die Quelle gehört ins [Impressum](impressum.html) unter „Bildnachweis“.

### Mitarbeit mit Claude

Wer in einem Issue oder Pull Request `@claude` erwähnt, startet einen Claude-Code-Agenten, der Fragen beantwortet oder Änderungen vorschlägt. Eingerichtet ist das in [.github/workflows/claude.yml](.github/workflows/claude.yml).
