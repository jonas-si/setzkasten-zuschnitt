# Setzkasten Zuschnitt

Konfigurator für den Eigenbau eines Setzkastens (Regal mit Fächern und Stegen) aus einer Platte.
Die Seite rechnet aus Fachanzahl, Fachmaßen und Plattenstärke `y`:

- den Plattenbedarf als Formel, zum Beispiel `4480 + 540·y + 20·y²` cm² für 4 × 3 Fächer à 10 × 12 cm,
- die Zuschnittliste für den Zuschnittservice im Baumarkt,
- eine geordnete Aufteilung auf der Platte mit nummerierter Schnittfolge, damit möglichst wenig und möglichst gerade gesägt wird.

Alles läuft im Browser, es gibt keinen Build-Schritt und keine Abhängigkeiten außer den Google Fonts.

## Aufbau des Kastens

| Teil | Anzahl | Maß (Länge × Breite) |
|---|---|---|
| Rückwand | 1 | `(r·h + (r+1)·y) × (c·w + (c+1)·y)` |
| Seitenwand | 2 | `(r·h + (r+1)·y) × Tiefe` |
| Fachboden | `r + 1` | `(c·w + (c−1)·y) × Tiefe` |
| Steg | `(c−1) · r · Stege je Fach` | `Steglänge × Tiefe` |

`c` = Spalten, `r` = Reihen, `w` = Fachbreite, `h` = Fachhöhe. Die Seitenwände laufen in voller Höhe durch, die Fachböden sitzen dazwischen und sind deshalb 2·y kürzer als die Rückwand breit ist.

## Lokal ansehen

```bash
python3 -m http.server 8000
```

Dann `http://localhost:8000` öffnen. Die Datei `index.html` funktioniert auch direkt per Doppelklick.

## Veröffentlichen mit GitHub Pages

Im Repository unter **Settings → Pages** als Quelle den Branch `main` und den Ordner `/ (root)` wählen. Die Seite liegt danach unter `https://<benutzername>.github.io/<repository>/`.
