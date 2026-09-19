# Elena — Digitale Speisekarte

Eine einzelne HTML-Datei (`index.html`), die sich direkt über **GitHub Pages** hosten lässt.

## So veröffentlichst du sie

1. Neues GitHub-Repository anlegen (z. B. `elena-speisekarte`).
2. `index.html` in das Repository hochladen (Hauptverzeichnis, Dateiname muss genau `index.html` heißen).
3. Im Repository: **Settings → Pages → Branch: main → / (root) → Save**.
4. Nach 1–2 Minuten ist die Karte unter `https://<dein-benutzername>.github.io/<repo-name>/` erreichbar.
5. Den Link als QR-Code generieren (z. B. auf goqr.me) und auf die Tische kleben.

## Preise oder Getränke ändern

Alles befindet sich im `<script>`-Teil der `index.html`, im Objekt `MENU`.
Für jede Sprache (`de` / `en`) gibt es Sektoren (`getraenke`, `essen`, `eis`, …).
Innerhalb von `getraenke` gibt es Kategorien mit einer Liste von `items`.

Ein Getränk sieht z. B. so aus:

```js
{name:"Coca-Cola", p1:"3,50", p2:"5,20"}
```

- `name` – Name des Getränks
- `p1` / `p2` – Preise für die zwei Größen der Kategorie (z. B. 0,2 l / 0,4 l). Wenn es nur eine Größe gibt, `p2` einfach leer lassen (`p2:""`).
- `note` – optionaler kleiner Zusatztext (z. B. Geschmacksrichtungen)

Um eine neue Kategorie unter „Getränke“ hinzuzufügen, einfach ein neues Objekt in das `categories`-Array einfügen (Aufbau wie die bestehenden Kategorien kopieren).

## Weitere Sektoren aktivieren

`essen`, `eis`, `eisbecher`, `kuchen` und `fruehstueck` sind aktuell leer und zeigen nur den Hinweis „Diese Karte wird bald ergänzt.“ Sobald Inhalte feststehen, einfach `type: "empty"` durch `type: "categories"` ersetzen und wie bei „Getränke“ Kategorien und Artikel ergänzen.

## Bestellfunktion (ohne Bezahlung)

Gäste können in der Karte auf einen Preis tippen, um ein Getränk zur Bestellung hinzuzufügen (Mengen mit +/− anpassbar). Unten erscheint eine Leiste mit Anzahl und Zwischensumme; tippt man darauf, öffnet sich die Übersicht mit dem Button „Bestellung an den Kellner übergeben“. Danach erscheint eine Bestätigung, die der Gast dem Kellner zeigen kann.

Wichtig: Es findet **keine Zahlungsabwicklung** statt und die Bestellung wird **nicht automatisch an die Theke gesendet** — es ist eine reine Übersicht auf dem Gäste-Handy. Der Kellner muss weiterhin persönlich zum Tisch kommen, die Bestellung ablesen (oder sich zeigen lassen) und die Rechnung wie gewohnt bringen.

Falls ihr das später erweitern wollt (z. B. Bestellung wird direkt an ein Kellner-Tablet gesendet), braucht ihr einen kleinen Server/Backend — das geht über eine reine GitHub-Pages-Seite hinaus.

## Design

- Sprachumschalter oben rechts (DE/EN)
- Sektor-Reiter (Getränke, Essen, Eis, …) unter dem Header
- Aufklappbare Kategorien mit größerer Schrift, gut lesbar für alle Altersgruppen
- Reine HTML/CSS/JS-Datei, keine Installation oder Build-Schritte nötig
