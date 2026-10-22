# Komma Katze – Startseite

Kinderfreundliche Startseite für die Primarstufe unter **prima.kommakatze.de**. (Unter www.kommakatze.de liegt die Sprachdetektei „Komma ermittelt“ für ältere Kinder; beide Seiten verweisen im Fuß aufeinander.) Katze Komma begrüßt die Kinder, und vier große Kacheln führen zu den Lernangeboten:

| Kachel | Ziel | Inhalt | Klang beim Antippen |
|---|---|---|---|
| Lesen | https://silbe.kommakatze.de/ | Silbenexpress – silbisches Lesenlernen | Zugpfeife |
| Malen | https://atelier.kommakatze.de/ | Kommas Atelier – Malprogramm | Pinselwischer mit Plopp |
| Musik | https://orchester.kommakatze.de/ | Kommas Orchester – Soundboard | Dreiklang aufwärts |
| Rechnen | https://rechnen.kommakatze.de/ | Kommas Zählrahmen – Mengen und Zahlen | drei Kugel-Klacks und ein Pling |

## Aufbau

Die ganze Seite besteht aus **einer Datei**: `index.html` (HTML, CSS und JavaScript in einer Datei). Es gibt keine Abhängigkeiten, keinen Build-Schritt und keine Bilddateien.

- **Pixelgrafiken** (Katze, Symbole (Buch, Palette, Note, Zählrahmen), Wolken, Blumen) werden per JavaScript aus Zeichenrastern in `MAPS` gezeichnet. Jeder Buchstabe steht für ein Pixel, die Farben stehen im Objekt `C`.
- **Klänge** werden mit der Web Audio API im Browser erzeugt, Audiodateien sind nicht nötig. Damit der Klang hörbar ist, öffnet sich das Ziel nach etwa 0,4 Sekunden.
- **Katze Komma** blinzelt alle paar Sekunden. Tippt man sie an, hüpft sie und miaut.
- **Hell- und Dunkelmodus** folgen automatisch der Geräteeinstellung.
- **Barrierearmut:** Die Seite lässt sich mit der Tastatur bedienen und hat sichtbare Fokusrahmen. Wer „Bewegung reduzieren“ eingestellt hat, sieht keine Animationen. Auf großen Bildschirmen stehen die Kacheln im 2×2-Raster, auf dem Handy untereinander.

## Gemeinsame Regeln für alle Apps

- **Rechtstexte:** Impressum, Datenschutz und Lizenz folgen derselben Vorlage (Muster: Silbenexpress) mit Stand-Datum.
- **Speichern:** nur mit Einwilligung eines Erwachsenen („Eine Frage an die Erwachsenen“), Widerruf im Elternmenü löscht sofort alles.
- **Elternmenü:** 2 Sekunden gedrückt halten.
- **Zur Startseite:** Haus-Knopf in jeder App, offline ausgeblendet.
- **Kopf jeder Datei:** `<!doctype html>`, `<html lang="de">`, Content-Security-Policy ohne Verbindungen nach außen, `no-referrer`, Favicon, Titel „App – Komma Katze“.
- **Transparenzhinweis** im Lizenz-Text jeder App.

## Datenschutz (DSGVO)

- Die Seite verwendet keine Cookies, kein `localStorage`, kein Tracking und keine Analyse.
- Sie lädt keine externen Ressourcen: keine Google Fonts, kein CDN, keine eingebetteten Inhalte. Es werden nur Systemschriften genutzt.
- Personenbezogene Daten fallen nur beim Hosting an (Server-Logs von GitHub Pages). Das ist in der Datenschutzerklärung beschrieben.

Impressum, Datenschutzerklärung und Lizenzhinweis stehen in der Wiese am Seitenende. Ein Klick öffnet den jeweiligen Text in einem Fenster.

## Anpassen

| Was | Wo in `index.html` |
|---|---|
| Kachel-Ziele | `href` der vier `<a class="tile …">` |
| Kachel-Texte | `.label` und `.sub` in den Kacheln |
| Farben | CSS-Variablen in `:root` (hell) und in den beiden Dunkel-Blöcken |
| Klänge | Objekt `SFX` im Skript (`lesen`, `malen`, `musik`, `rechnen`) |
| Impressum / Datenschutz / Lizenz | `<section class="pane" id="p-imp">`, `id="p-ds"`, `id="p-liz"` |

**Neue Kachel hinzufügen:**
1. Einen weiteren `<a class="tile …">`-Block anlegen.
2. In `:root` (und in beiden Dunkel-Blöcken) zwei Farben dafür festlegen.
3. Eine Regel `.tile.neu{--c:…;--c2:…}` ergänzen.
4. Ein Symbol in `MAPS` und einen Klang in `SFX` hinzufügen.
5. Das Raster `.tiles` hat zwei Spalten. Bei einer ungeraden Anzahl Kacheln steht die letzte allein; dann ggf. `grid-template-columns` in `.tiles` anpassen (z. B. `repeat(3,1fr)` bei sechs Kacheln).

## Veröffentlichen (GitHub Pages)

1. `index.html` und `README.md` in das Repository legen (Hauptzweig, Wurzelverzeichnis).
2. Unter *Settings → Pages* als Quelle den Branch wählen.
3. Die eigene Domain `prima.kommakatze.de` eintragen (dabei entsteht die Datei `CNAME`) und *Enforce HTTPS* aktivieren.
4. Beim Domain-Anbieter die DNS-Einträge für GitHub Pages setzen. Die Subdomains `silbe`, `atelier`, `orchester` und `rechnen` zeigen jeweils auf ihr eigenes Repository.

## Lizenz

Inhalte, Grafiken und die Figur Katze Komma: **CC BY-SA 4.0**, Sebastian Wolf
https://creativecommons.org/licenses/by-sa/4.0/deed.de

Namensnennung: „Komma Katze von Sebastian Wolf, CC BY-SA 4.0“

## Kontakt

Sebastian Wolf · s.w.oer@outlook.de

**Transparenzhinweis:** Programmiert mit Unterstützung von KI (Claude, Anthropic). Idee, Inhalte und fachliche Prüfung: Sebastian Wolf.
