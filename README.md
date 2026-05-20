# STrade — Mockup PWA

Verified trading & echter Fortschritt. Performance-Cockpit für TR, Scalable und IBKR.

Dies ist ein interaktiver Mockup (v6) als installierbare Progressive Web App. Statische HTML-Seite, ein einziges File, keine Build-Tools, keine Server.

---

## Live demo

> Nach dem Deploy hier den URL einsetzen:
> `https://<dein-github-user>.github.io/strade/`

---

## Deploy in 6 Minuten via Claude Code + GitHub Pages

### Voraussetzungen

- GitHub-Account (kostenlos)
- Claude Code installiert ([Anleitung](https://docs.claude.com/en/docs/claude-code/quickstart))
- Lokales Terminal

### Schritt 1 — Repo auf GitHub erstellen

1. Auf [github.com/new](https://github.com/new) gehen
2. Repository-Name: `strade` (oder beliebig)
3. **Public** wählen (sonst funktioniert GitHub Pages auf Free-Tier nicht)
4. „Create repository" klicken
5. URL kopieren, z.B. `https://github.com/moritz/strade.git`

### Schritt 2 — Files lokal sammeln

Alle Dateien aus diesem Ordner (`strade-pwa/`) brauchst du. Wenn du diesen Ordner schon hast, gehe direkt zu Schritt 3.

```
strade-pwa/
├── index.html               # die App selbst (V6 Mockup)
├── manifest.json            # PWA-Identität
├── sw.js                    # Service Worker (offline-Cache)
├── icon-192.png             # App-Icon klein
├── icon-512.png             # App-Icon groß
├── icon-512-maskable.png    # Android adaptive icon
├── apple-touch-icon.png     # iOS Homescreen-Icon
├── favicon.png              # Browser-Tab-Icon
└── README.md                # diese Datei
```

### Schritt 3 — Push mit Claude Code

Im Terminal in den Ordner navigieren und Claude Code starten:

```bash
cd strade-pwa
claude
```

Dann zu Claude sagen:

> „Initialisiere ein git repo hier, mache einen ersten commit mit allen files, und pushe es zu `https://github.com/<dein-user>/strade.git` auf den main-branch."

Claude Code führt das automatisch aus (oder du machst es manuell):

```bash
git init -b main
git add .
git commit -m "Initial commit: STrade v6 mockup as PWA"
git remote add origin https://github.com/<dein-user>/strade.git
git push -u origin main
```

### Schritt 4 — GitHub Pages aktivieren

1. Auf GitHub ins Repo gehen
2. **Settings** → **Pages** (linke Sidebar)
3. Unter **Source**: „Deploy from a branch" wählen
4. Branch: `main`, Folder: `/ (root)`
5. **Save** klicken
6. 1–2 Minuten warten

Die URL erscheint oben in der Pages-Section, z.B.:
`https://moritz.github.io/strade/`

### Schritt 5 — Auf dem iPhone installieren

1. URL in **Safari** öffnen (nicht Chrome — iOS PWA funktioniert nur über Safari)
2. **Teilen-Button** (Quadrat mit Pfeil) tippen
3. **„Zum Home-Bildschirm"** auswählen
4. „Hinzufügen" tippen

STrade erscheint auf dem Homescreen, öffnet im Vollbild ohne Browser-UI.

### Schritt 6 — Auf Android installieren

1. URL in **Chrome** öffnen
2. Drei-Punkte-Menü → **„App installieren"**
3. Bestätigen

Funktioniert genauso für Edge auf Windows und Chrome auf macOS.

---

## Updates pushen

Wenn du an der `index.html` etwas änderst:

```bash
git add .
git commit -m "Update: <was du geändert hast>"
git push
```

GitHub Pages aktualisiert sich automatisch in 30–60 Sekunden.

**Wichtig:** Der Service Worker cached Assets. Wenn User die alte Version sehen, bumpe die Version-Nummer in `sw.js`:

```js
const CACHE_NAME = 'strade-v6.1'; // war v6.0
```

Das invalidiert den Cache beim nächsten Besuch.

---

## Custom Domain (optional, später)

Falls du eine eigene Domain kaufst (z.B. `strade.app`):

1. Domain in den Pages-Settings unter „Custom domain" eintragen
2. DNS bei deinem Registrar setzen (CNAME auf `<user>.github.io`)
3. „Enforce HTTPS" aktivieren

---

## Was die PWA kann

- ✓ Vollständig offline-fähig nach erstem Besuch (Service Worker cached alles)
- ✓ Installierbar auf iOS, Android, Desktop
- ✓ Vollbild ohne Browser-Chrome
- ✓ Eigenes App-Icon auf Homescreen
- ✓ Theme-Color (Statusbar adaptiert sich)
- ✓ Funktioniert komplett ohne Backend

## Was sie NICHT kann (Mockup-Limitierung)

- Keine echte Broker-API-Anbindung
- Keine echten User-Accounts
- Keine Persistenz über Geräte hinweg (localStorage ist gerätelokal)
- Keine Push-Notifications

Das ist gewollt — der Mockup zeigt die Vision, nicht die Implementierung.

---

## Lizenz

Privates Projekt. Mockup nicht für kommerzielle Verwendung freigegeben.
