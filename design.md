# ERWE Immobilien AG — Designsystem

> Verbindliche Quelle für alle weiteren Schritte. Wer hier abweicht, begründet es hier.
> Richtung: **Weiß & Tiefblau** (Richtung 04, gewählt am 2026-08-01).

---

## 1 · Marke & These

**ERWE Immobilien AG** — börsennotierter Bestandshalter und Entwickler von Gewerbeimmobilien
in den A-Lagen deutscher Innenstädte. Kauft leerstehende oder untergenutzte Handelsflächen,
führt sie in gemischte Nutzung über und hält sie im eigenen Bestand.

**These (Displayzeile, unverändert vom Bestand übernommen):**

> **ENTWICKLUNG. VERWALTUNG. WERTSTEIGERUNG.**

Drei gesetzte Wörter, drei Zeilen, kein Fließtext. Sie stehen für die vollständige
Wertschöpfungskette — und dafür, dass ERWE nicht weiterverkauft, sondern hält.
Die Zeile wird typografisch als Signatur behandelt, nicht als Überschrift.

**Lede (zwei Sätze, direkt unter der These):**

> ERWE erwirbt Gewerbeimmobilien in den A-Lagen deutscher Innenstädte und entwickelt sie
> zu Standorten mit gemischter Nutzung. Von Speyer bis Lübeck — gehalten im eigenen
> Bestand, nicht weiterverkauft.

---

## 2 · Zielgruppe & der eine Job

**Reale Zielgruppe dieses Entwurfs:** der ERWE-Vorstand. Die Seite ist ein Pitch. Sie muss
beim ersten Blick beweisen, dass das Unternehmen hier besser vertreten ist als heute.

**Zielgruppe der Seite selbst, priorisiert:**

| # | Wer | Was sie brauchen |
|---|---|---|
| 1 | Investoren & Anleihegläubiger | Zahlen, Berichte, Restrukturierungsstand — transparent und schnell auffindbar |
| 2 | Mieter & Projektpartner | Objekte mit Stadt, Fläche, Nutzung, Status |
| 3 | Verkäufer & Kommunen | Warum ERWE der richtige Käufer für eine leere Innenstadtlage ist |
| 4 | Presse | Mitteilungen, Ansprechpartner, Bildmaterial |

**Der eine Job:** Kontaktaufnahme mit Investor Relations.
Sekundär: Download des aktuellen Geschäftsberichts.

Die Seitenmischung: **Portfolio · Investor Relations · Unternehmen · Presse & Kontakt.**

---

## 3 · Palette

OKLCH ausschließlich. Kein `#000`, kein `#fff`. Jeder Neutralton ist zum Markenblau
(Hue 232–245) hin getönt. **Ein** gesättigter Akzent — sonst nichts Lautes.

```css
:root {
  --bg:      oklch(0.985 0.004 240);  /* Papierweiß   — Seitengrund */
  --surface: oklch(0.955 0.011 235);  /* Lichtfläche  — Karten, Tabellenzeilen, Kästen */
  --sky:     oklch(0.885 0.045 232);  /* Himmelsblau  — große ruhige Farbfelder, Diagramme */
  --ink:     oklch(0.235 0.045 245);  /* Tiefblau     — alle Schrift, Logo, Rahmen */
  --muted:   oklch(0.535 0.024 243);  /* Schiefergrau — Sekundärtext, Labels, Metadaten */
  --accent:  oklch(0.550 0.150 235);  /* ERWE-Signalblau — Links, CTA, W-Linie, Zahlen-Highlight */
  --line:    oklch(0.235 0.045 245 / 0.14); /* Trennlinien */
  --line-strong: oklch(0.235 0.045 245 / 0.30);
}
```

**Herkunft:** `--accent` ist rechnerisch das Petrol der ERWE-Wortmarke (`#236384`),
aufgehellt und gesättigt. Deshalb sieht die Seite nach McKinsey-Haltung aus, aber nicht
nach McKinsey-Farbe (deren Blau ist violettstichig, Hue ≈ 265).

**Einsatzregeln**

- `--accent` niemals als Flächenfarbe über mehr als ~15 % des Viewports. Er ist Signal, nicht Dekor.
- Fließtext immer `--ink` auf `--bg` oder `--surface`. Niemals `--muted` für Fließtext.
- `--sky` nur für Diagramme, Karten-Overlays und maximal ein großes Farbfeld pro Seite.
- Weißer Text ausschließlich auf `--accent` oder `--ink` — und dann `--bg`, nie `#fff`.
- Dark Mode: **nicht vorgesehen.** IR-Inhalte werden gedruckt und gescrollt, hell ist richtig.

---

## 4 · Typografie

| Rolle | Schrift | Quelle | Wofür |
|---|---|---|---|
| Display | **Zodiak** Bold (700) | Fontshare | These, Seitentitel, Objektnamen, große Zahlen |
| Fließtext | **Switzer** Regular/Medium (400/500/600) | Fontshare | Alles Gelesene |
| Utility | **IBM Plex Mono** (400/500) | Google Fonts | Kennzahlen, WKN, Flächen, Daten, Labels, Eyebrows |

```html
<link href="https://api.fontshare.com/v2/css?f[]=zodiak@400,700&f[]=switzer@400,500,600&display=swap" rel="stylesheet">
<link href="https://fonts.googleapis.com/css2?family=IBM+Plex+Mono:wght@400;500&display=swap" rel="stylesheet">
```

**Skala** (fluid, clamp)

```css
--t-display-xl: clamp(2.6rem, 7vw,   6.4rem);   /* Hero-These          — Zodiak 700, lh 1.03, ls -.01em */
--t-display-l:  clamp(2.2rem, 4.2vw, 4.2rem);   /* Sektionstitel       — Zodiak 700, lh 1.05, ls -.01em */
--t-display-m:  clamp(1.75rem, 2.6vw, 2.8rem);  /* Objektnamen, Zahlen — Zodiak 700, lh 1.07, ls -.01em */
--t-lede:       clamp(1.125rem, 1.4vw, 1.25rem); /* Lede                — Switzer 400, lh 1.6 */
--t-body:       1.125rem;                        /* Fließtext           — Switzer 400, lh 1.7 */
--t-small:      0.8125rem;                       /* Bildunterschrift    — Switzer 400, lh 1.55 */
--t-utility:    clamp(0.875rem, 1vw, 1rem);      /* Labels              — Plex Mono, ls .02em, uppercase */
```

> **Abweichung 2026-08-02:** Größenraster (Endwerte, Letter-Spacing) 1:1 an die gemessenen
> Werte von brookfield.com angeglichen (deren `text-display-64-420`, `text-serif-42-420`,
> Body `18px`, Eyebrow-Tracking `.02em` statt zuvor `.16em`) — auf Wunsch, um „Schriftgröße
> und Anordnung exakt genauso" zu übernehmen. **Nicht** übernommen: Brookfields eigene
> Schriftdateien (`Season Mix`/`Season Sans`, proprietär, Blaze Type) und ihre warme
> Creme-Neutralpalette — Zodiak/Switzer/Plex Mono und die Blau-Palette aus §3 bleiben, weil
> beides nicht angefragt war und §3/§12 sonst widersprechen würde. Siehe §13.

**Do**

- Zeilenlänge im Fließtext auf `62ch` begrenzen, Lede auf `46ch`.
- Utility-Zeilen immer versal, immer gesperrt (`0.16em`), immer `--muted`.
- Zahlen (Fläche, WKN, Kurs, Datum) immer in IBM Plex Mono — auch mitten im Satz.
- Die These bricht auf drei Zeilen um, immer. Auch auf dem Desktop.

**Don't**

- Kein Zodiak unter 20 px — der Kontrast bricht weg.
- Keine Kursive im Fließtext. Betonung über `--ink` in Medium, nicht über Schrägstellung.
- Keine Unterstreichung außer bei Inline-Links im Fließtext.
- Kein Switzer über 32 px. Große Schrift ist Displayschrift.
- Kein Text auf Bildern ohne durchgehende Abdunklung — nie „hoffentlich lesbar“.

---

## 5 · Layout & Raster

- **Raster:** 12 Spalten, Gutter `24px`, Außenrand `clamp(1.25rem, 5vw, 5rem)`.
- **Inhaltsbreite:** max `1280px`. Volle Breite nur für Bilder und Trennlinien.
- **Basiseinheit:** `8px`. Alle Abstände sind Vielfache.
- **Sektionsrhythmus:** `clamp(4rem, 10vw, 8rem)` vertikal zwischen Sektionen.
- **Asymmetrie ist erlaubt und erwünscht:** Sektionstitel in Spalte 1–3, Inhalt ab Spalte 5.
  Das erzeugt die Luft, die die Seite teuer aussehen lässt.
- **Kanten sind hart.** `border-radius: 0` überall, außer auf Formularfeldern (`2px`).
- **Keine Schatten** als Gestaltungsmittel. Tiefe entsteht durch Fläche (`--surface`) und Weißraum.

**Breakpoints:** `640px` · `900px` · `1280px`. Mobile zuerst, einspaltig, Sektionstitel über dem Inhalt.

---

## 6 · Signaturelement — die W-Linie

Das `W` in der ERWE-Wortmarke ist ein durchgezogener Zickzack. Diese Zacke ist das
wiederkehrende, ownable Element der Seite.

```html
<svg class="wline" viewBox="0 0 1200 26" preserveAspectRatio="none" aria-hidden="true">
  <path d="M0,25 L1160,25 M1160,25 L1172,1 L1181,25 L1190,1 L1199,25"/>
</svg>
```

```css
.wline path { fill: none; stroke: var(--accent); stroke-width: 1.25; vector-effect: non-scaling-stroke; }
```

**Einsatz**

- Als Abschluss jeder Sektionstrennlinie (rechtsbündig, die Zacke sitzt am Ende).
- Als Hover-/Focus-Unterstreichung bei Navigationslinks — die Zacke wandert von links ein.
- Einmal groß, als einziges grafisches Element im Kontaktbereich.

**Nicht** als Icon, Aufzählungszeichen, Muster oder Hintergrundtextur. Höchstens **zwei**
W-Linien pro Viewport.

---

## 7 · Motion

**Strukturell** (trägt Bedeutung, bleibt)

- Sektionseinstieg: `opacity 0→1`, `translateY 12px→0`, `420ms`, `cubic-bezier(.2,.6,.2,1)`.
  Gestaffelt in max. 3 Stufen à `60ms`. Einmal pro Element, nicht bei jedem Scroll.
- Sticky-Header: schrumpft von `88px` auf `60px` beim ersten Scroll, `240ms`.

**Politur** (verzichtbar, aber schön)

- W-Linie zeichnet sich beim Sektionseintritt über `stroke-dashoffset`, `600ms`.
- Links: Farbwechsel `--ink → --accent` in `160ms`. Sonst nichts.
- Bildkarten (Objektkarten, Medienfläche): `transform: scale(1.05)` auf Hover/Focus,
  `transition: transform .3s ease-in-out` — 1:1 der Hover-Zoom-Effekt von brookfield.com
  (Abweichung 2026-08-02, auf Wunsch). Kein Parallax, keine Bewegung ohne Interaktion.

**Zurückhaltungsregel**

> Maximal **eine** sich bewegende Sache pro Viewport. Kein Parallax, keine hochzählenden
> Zahlen, keine Karussells, kein Scroll-Hijacking, kein Auto-Play. Bei einem Unternehmen in
> Restrukturierung liest der Markt Verspieltheit als Ablenkung.

```css
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after { animation: none !important; transition: none !important; scroll-behavior: auto !important; }
}
```

---

## 8 · Komponenten

| Komponente | Verhalten |
|---|---|
| **Header** | Logo links (`--ink`), 4 Navigationspunkte, rechts „Investor Relations“ als `--accent`-Button. Sticky, schrumpfend. |
| **Hero** | These dreizeilig, Lede, Kennzahlenleiste. Vollbild-Fotostrecke (Crossfade, reale ERWE-Motive) liegt als Hintergrund hinter dem Text, mit Scrim für Lesbarkeit (Abweichung 2026-08-02, auf Wunsch). |
| **Kennzahlenleiste** | Horizontale Reihe, oben und unten `--line`, Plex Mono versal. Label `--muted`, Wert `--ink`. |
| **Objektkarte** | Bild 4:3, darüber Utility-Zeile mit Stadt, darunter Objektname in Zodiak, drei Datenzeilen (Nutzung / Fläche / Status). Kein Rahmen, kein Schatten. |
| **Portfolio-Tabelle** | Echte `<table>`. Zeilen durch `--line` getrennt, Zahlen Plex Mono rechtsbündig, Kopfzeile Utility. |
| **IR-Downloadliste** | Zeile = Titel + Datum + Dateigröße + Format. Ganze Zeile klickbar, Hover setzt `--surface`. |
| **Pressezeile** | Datum (Plex Mono, `--muted`) · Titel (Switzer Medium) · W-Linie beim Hover. |
| **Zitat** | Zodiak, `--t-display-m`, max `40ch`, Name und Funktion in Utility darunter. Keine Anführungsgrafik. |
| **Kontakt-CTA** | `--accent`-Fläche, Text in `--bg`, echte Ansprechpartnerin mit Name, Telefon, E-Mail. |
| **Footer** | Vier Spalten, Pflichtangaben (Impressum, Datenschutz, Pflichtveröffentlichungen) gleichrangig sichtbar. |

**Zustände (für alle interaktiven Elemente Pflicht):** default · hover · focus-visible · active · disabled.

```css
:where(a, button, input, select, summary):focus-visible {
  outline: 2px solid var(--accent);
  outline-offset: 3px;
}
```

Touch-Ziele mindestens `44 × 44px`. Kontrast mindestens WCAG AA (4.5:1 Text, 3:1 UI).

---

## 9 · Textregeln

- **Deutsch, Sie-Form.** Englische Begriffe nur, wo sie Fachsprache sind (Investor Relations, Basic Board, Asset).
- **Zahlen statt Adjektive.** Nicht „attraktive Innenstadtlage“, sondern „Maximilianstraße, 120 m zum Dom“.
- **Ort nennen.** Jede Objektaussage bekommt Stadt und Straße.
- **Keine Superlative.** Kein „führend“, „innovativ“, „ganzheitlich“, „Ihr Partner für“.
- **Kapitalmarktvorsicht.** Keine Prognosen, keine Renditeversprechen, keine Aussage über künftige
  Kursentwicklung. Restrukturierung wird benannt, nicht umschrieben — Verschweigen kostet mehr
  Glaubwürdigkeit als Zugeben.
- **Überschriften sind Aussagen, keine Etiketten.** Nicht „Unser Portfolio“, sondern
  „Neun Standorte, alle im Bestand“.
- **Sätze unter 20 Wörtern.** Ein Gedanke pro Satz.

---

## 10 · Bildkonzept

Die bestehende Seite führt mit einem Stockfoto verwischter Geschäftsleute in einer
Flughafenpassage. Das wird ersatzlos gestrichen. **Gezeigt werden Gebäude.**

| Ort | Motiv | Look | Quelle |
|---|---|---|---|
| Hero | Postgalerie Speyer, Frontalansicht der Sandsteinfassade | Vormittagslicht, Himmel oben leicht angeschnitten, streng frontal | Objektfoto ERWE, neu fotografieren lassen; für den Pitch: bestehende Aufnahme, farbkorrigiert |
| Portfolio | Je ein Objekt, gleiche Perspektive | Alle 4:3, alle frontal, alle Tageslicht — die Serie muss als Serie lesbar sein | ERWE-Bestand; Lücken durch Architekturaufnahmen deutscher Innenstadtbauten schließen |
| Unternehmen | Innenraum einer laufenden Umnutzung, als Vollbild-Medienfläche mit Eyebrow+Headline unten (`.media-feature`, Abweichung 2026-08-02) | Rohbau oder frisch übergebene Fläche, natürliches Licht, keine Personen im Fokus | Gemuteter Auto-Loop `assets/unternehmen-loop.mp4` (Stockvideo, Pexels-Lizenz, s. §13); Standbild `unternehmen.jpg` (ERWE-Bestand) als Poster/Fallback bei `prefers-reduced-motion` |
| Kontakt | Kein Bild | Die `--accent`-Fläche trägt allein | — |

**Bildregeln**

- Keine hochskalierten Bilder. Lieber kleiner ausspielen als unscharf.
- Keine erkennbare fremde Stadt. Kein Manhattan, kein Dubai, keine anonyme Glasfassade.
- Keine Menschen als Stockmotiv. Menschen nur, wenn es echte ERWE-Menschen sind.
- Keine Weitwinkelverzerrung, keine gekippten Horizonte, keine HDR-Optik.
- Format `.webp`, `srcset` in 640/1280/1920, `loading="lazy"` außer im Hero, `alt` immer gesetzt.
- Farbkorrektur: alle Bilder leicht zum Blau der Palette hin, damit die Serie zusammenhält.

Alle Assets liegen in `assets/`. Logo: `assets/erwe-logo.svg` (Original in `#236384`/`#6e6e6e`),
`assets/erwe-logo-ink.svg` (einfarbig über `currentColor`).

> Die Ink-Variante muss **inline** ins HTML — als `<img src>` geladen erbt sie `currentColor`
> nicht und rendert reinschwarz. Siehe `index.html`.

---

## 11 · Conversion

1. **IR-Kontakt** im Header sichtbar, als Sektion am Seitenende, und im Footer. Immer mit
   echtem Namen, Durchwahl und E-Mail — keine anonymen Formulare.
2. **Geschäftsbericht** als prominenter Download, mit Datum und Dateigröße.
3. **Aktienkennzahl** im Hero: WKN, ISIN, Handelssegment. Kein Live-Kurs-Widget.
4. **Ad-hoc- und Pressemitteilungen** mit Datum, absteigend, ohne Paginierung auf der Startseite (5 Stück).
5. **Pflichtangaben** (Impressum, Datenschutz, Pflichtveröffentlichungen nach WpHG) im Footer,
   gleichrangig — bei einem börsennotierten Unternehmen ist das Vertrauen, nicht Kleingedrucktes.
6. **Keine Cookie-Wand vor dem Inhalt.** Nur technisch notwendige Cookies, dann keine Wand nötig.

---

## 12 · Anti-Muster

- Stockfotos mit verwischten Geschäftsleuten, Handschlägen, Rollkoffern, Meetingräumen.
- Reines `#fff` / `#000`. Alles ist getönt.
- Verlaufstext, Glassmorphism, Neon-Glow, Neumorphismus.
- Creme + Serifenschrift + Terrakotta. Fast-Schwarz + eine grelle Akzentfarbe. Zeitungs-Haarlinien als Deko.
- Mehr als eine gesättigte Farbe.
- Hero-Karussell, Auto-Play-Video, hochzählende Zahlen, Parallax.
- Icon-Reihen ohne Inhalt („Kompetenz · Erfahrung · Vertrauen“).
- Runde Ecken über `2px`, Schlagschatten, Farbverläufe auf Flächen.
- Inter als Fließtextschrift.
- Englische Marketingfloskeln in deutschem Text.

---

## 13 · Referenzen

| Was | Wofür |
|---|---|
| [mckinsey.de](https://www.mckinsey.de) | Struktur, Weißraum, Register: weißer Grund, tiefblaue Schrift, ein Akzent. **Nicht** die Farbe übernehmen. |
| ERWE-Wortmarke (`#236384`, `#6e6e6e`) | Herkunft des Akzentblaus und der W-Zacke. |
| Postgalerie Speyer — Sandsteinfassade, Mansarddach | Material- und Lichtreferenz für die Bildserie. |
| [erwe-ag.com](https://www.erwe-ag.com) (Bestand) | Inhaltliche Vollständigkeit — Struktur und Optik werden ersetzt. |
| [brookfield.com](https://www.brookfield.com) (Abweichung 2026-08-02) | Größenraster (Endwerte, Tracking), Hover-Zoom auf Bildkarten, Vollbild-Medienfläche mit Eyebrow+Headline unten verankert (`.media-feature`), inkl. gemutetem Auto-Loop-Video wie im Original (nicht nur Standfoto, Nachtrag 2026-08-02: reales ERWE-Videomaterial existiert nicht, geprüft auf erwe-ag.com — deshalb ein thematisch passendes, lizenzfreies Stockvideo: „Construction Inside A Building" von Pixly Videos, [pexels.com/video/1538132](https://www.pexels.com/video/construction-inside-a-building-1538132/), Pexels-Lizenz — kostenlose kommerzielle Nutzung, keine Zuschreibung nötig, dennoch dokumentiert; Standfoto bleibt Poster & `prefers-reduced-motion`-Fallback). **Nicht** übernommen: deren Schriftdateien (proprietär), Creme-Palette, Karussells. |

---

## 14 · Qualitätsuntergrenze

- Responsiv bis `320px` Breite, keine horizontale Scrollleiste.
- Sichtbarer Fokusring auf allen interaktiven Elementen.
- `prefers-reduced-motion` respektiert.
- Semantisches HTML: `header`, `nav`, `main`, `section`, `article`, `table`, `footer`.
- Bilder mit `alt`, Sprache `lang="de"`, Überschriftenhierarchie ohne Sprünge.
- Kontrast AA oder besser, in beiden Richtungen geprüft.
