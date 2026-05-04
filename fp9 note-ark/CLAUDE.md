# FP9 note-ark — Skriftlig matematik 9. klasse

## Hvad er det her
Print-venlige A4-ark til en 9. klasse, der skal til skriftlig prøve i matematik. Eleverne er fagligt svage og har manglet forberedelse. Arkene ligger ved siden af dem under prøven.

## Aktuel projektkontekst

Læs disse filer først, hvis du arbejder videre i prototypen:

1. `memory.md`
2. `status.md`
3. `HANDOFF.md`

Vigtige nuværende regler:

- Screenshot-rammer skal bevares og fyldes med PNG'er fra `../screenshots/`.
- Brug zoomede `*-zoom.png`-udsnit når originalen bliver for lille på A4.
- Sheets-formler skal vise engelsk/dansk funktionsnavn ved sprogrisiko.
- I Sheets-arket bruges elev-skabeloner som `=SUM(skriv celler her)` plus konkret eksempel.
- `print-all.html` kloner alle `.sheet`-sektioner og scopes lokale styles pr. ark.

## Brugskontekst
- **Format:** A4, printet på papir. Hvert ark er 1-2 sider.
- **Værktøjer eleverne må bruge:** GeoGebra, Google Sheets, lommeregner.
- **Sprog:** Dansk.
- **Læsestil:** De skal kunne kigge på et ark og finde det rigtige svar/formel/metode på under 10 sekunder.

## Designprincipper

### 1. Find-det-hurtigt
- Stor emne-overskrift øverst på hvert ark (40-48pt) + arknummer i hjørnet ("Ark 5").
- Hver sektion på et ark har sin egen tydelige underoverskrift (16-18pt, accent-farve).
- Ingen lange tekstblokke. Brug bullets, nummererede lister, små bokse.

### 2. Eksempel ved siden af forklaring
- Når noget forklares, står et konkret regneeksempel ved siden af eller under, ikke som separat sektion.
- Format: To kolonner — venstre = "sådan gør du", højre = "eksempel".

### 3. Print-venlig
- Hvid baggrund, mørk tekst. Ingen store farveflader der spiser blæk.
- Farve bruges sparsomt: én accentfarve pr. ark til overskrift, sektionsmarkører og fremhævninger.
- Skriftstørrelse i brødtekst: 12-13pt minimum (ikke 10-11 som standard websider).
- Margin: 15mm rundt om — luft, men maksimer plads.

### 4. Visuelt = funktionelt
- Diagrammer tegnes med inline SVG (trekanter, koordinatsystemer, søjlediagrammer).
- Screenshots af GeoGebra/Sheets vises i tydelige screenshot-rammer. Brug faktiske PNG'er fra `../screenshots/`, ikke tomme placeholders når et relevant billede findes.
- Brug zoomede udsnit eller HTML-callouts, hvis eleven ellers ikke kan aflæse felt, knap eller resultat på print.
- Ikke dekorativ grafik. Hvis et billede ikke hjælper med at forstå, så væk.

### 5. Kort, præcist sprog
- "Sådan gør du" i imperativ, korte sætninger.
- Ingen "I dette ark vil vi se på...". Bare gå til sagen.
- Faglige ord forklares første gang med 1-linjes definition i en grå boks.

## Filstruktur

```
/
  index.html              — forside med oversigt over alle ark + metodik
  ark/
    01-tal-algebra.html
    02-procent.html
    03-ligninger.html
    04-funktioner.html
    05-geometri.html
    06-trigonometri.html
    07-statistik.html
    08-formelsamling.html
    09-geogebra.html
    10-sheets.html
  shared/
    tokens.css            — farver, type, spacing
    sheet.css             — fælles ark-komponenter
    icons/                — små inline SVG hvis nødvendigt
  print-all.html          — alle ark samlet til én print-PDF
```

## Designsystem (kort)

### Farver
Varme neutrale + én accentfarve pr. emne så elever kan sige "kig på det orange ark".

- `--ink: #1f1d1a` — primær tekst
- `--ink-soft: #5a554f` — sekundær tekst
- `--ink-faint: #8b857c` — labels, captions
- `--paper: #ffffff` — baggrund (print)
- `--paper-tint: #faf7f2` — meget svag tone til bokse
- `--rule: #e6e1d8` — streger, dividers
- `--highlight: #fff3d6` — gul markering bag formler

Emnefarver (kun overskrift, sektionsbar, nummerbadge — aldrig store flader):
- Tal/algebra: `#7a4a2e` (rust)
- Procent: `#8a3a3a` (mursten)
- Ligninger: `#5e4a8a` (dæmpet violet)
- Funktioner: `#3a6a5a` (skovgrøn)
- Geometri: `#4a6a8a` (støvet blå)
- Trigonometri: `#7a5a2a` (oker)
- Statistik: `#5a7a4a` (oliven)
- Formelsamling: `#3a3a3a` (kul)
- GeoGebra-guide: `#8a5a2a` (kobber)
- Sheets-guide: `#3a6a4a` (mosgrøn)

### Typografi
- **Headline:** Fraunces eller Source Serif — varme, autoritative, ikke skole-clipart.
- **Brødtekst:** Source Sans 3 eller Inter — meget læsbar i print.
- **Tal/formler:** Same as brødtekst, men i medium weight.
- **Vægte:** 400, 500, 600. Ikke 700 (for tungt på print).
- Faktisk vi vælger: brødtekst = **Source Sans 3**, headlines = **Fraunces** (let, ikke for "skole-agtig").

### Spacing
8/12/16/24/32/48 — hold dig til denne stige.

### Komponenter (genbrug)
- `.sheet` — A4-side wrapper med margin og page-break
- `.sheet-header` — emnefarve-bar + arknummer + emne + undertitel
- `.method-row` — to-kolonne forklaring + eksempel
- `.formula` — fremhævet formel med valgfri gul markering
- `.example-box` — let tonet boks til regneeksempler
- `.note` — lille grå boks til "husk at..." / definitioner
- `.figure` — SVG-illustration med caption
- `.screenshot` — stiplet ramme til faktiske screenshots
- `.screenshot.zoom` — større/tydeligere screenshot-ramme til beskårne udsnit

## Tone

- Kort. Konkret. Ikke nedladende.
- "Træk 7 fra på begge sider" — ikke "Vi skal nu trække 7 fra på begge sider".
- Eksempler bruger virkelige tal de kan møde til prøven, ikke pædagogiske.
- Ingen emoji. Ingen "Du kan det her!" kommentarer.

## Print

- A4 portrait, 15mm margin alle sider.
- Hvert `<section class="sheet">` = én A4-side, page-break-after: always.
- Brug `@media print` til at skjule navigation/links fra forsiden.
- `print-all.html` indlæser ark via skjulte iframes, kloner alle `.sheet`-sektioner ind i samme dokument og scopes hvert arks lokale styles.

## Workflow når jeg bygger et ark

1. Læs eksisterende ark for at matche struktur og tone.
2. Opdel emnet i 3-6 sektioner — ikke flere.
3. For hver sektion: kort forklaring + konkret eksempel + formel hvis relevant.
4. Tegn SVG-figurer hvor det giver mening (ikke for udsmykning).
5. Tjek: kan en svag elev finde det rigtige på under 10 sekunder?
6. Kør i print-preview — passer det på én eller to A4-sider?
