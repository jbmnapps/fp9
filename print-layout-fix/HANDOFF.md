# Handoff - FP9 note-ark prototype

Sidst opdateret: 2026-05-04

## Start her

Læs i denne rækkefølge:

1. `fp9 note-ark/memory.md`
2. `fp9 note-ark/status.md`
3. `fp9 note-ark/HANDOFF.md`
4. `fp9 note-ark/CLAUDE.md`

Arbejdsmappen er:

`fp9 note-ark/`

Projektroden er:

projektroden

Bemærk: macOS behandler `handoff.md` og `HANDOFF.md` som samme fil her. Brug `HANDOFF.md` i dokumentation for at matche den faktiske filvisning.

## Hvad projektet er nu

Det aktive arbejde er Claude Design prototypen i `fp9 note-ark/`, ikke den gamle rod-HTML i `ark/`.

Prototypen har:

- forside
- 10 ark
- samlet printside
- shared CSS
- screenshots fra roden `screenshots/`

## Seneste session

Jonas bad om review-agenterne. Fire read-only review-agenter blev kørt:

- math-checker
- language-reviewer
- visual-reviewer
- code-reviewer

Der blev derefter rettet:

- matematik-P0
- print-all-teknik
- screenshot-læsbarhed
- index-markup
- Sheets-arkets formelområde

## Vigtige rettelser der er lavet

### Matematik-P0

- `=K0*(1+r)^n` er fjernet som Sheets-formel.
- Renteformel i Sheets er nu konkret: `=5000*(1+0,03)^4`.
- Pythagoras siger nu retvinklet.
- Formelsamlingens vinkelopslag har sin, cos og tan.
- Vækstrate er præciseret: `r = a - 1` som decimaltal, procent = `r * 100%`.

### Sheets-formler

Funktionssprog er en bevidst risiko. Derfor:

- behold engelsk/dansk versioner ved relevante funktioner
- skriv ikke arkene om til kun dansk
- skriv ikke arkene om til kun engelsk

Eksempel:

`=AVERAGE(skriv celler her) / =GENNEMSNIT(skriv celler her)`

Ark 10 bruger nu elev-skabeloner:

- `=SUM(skriv celler her)`
- `fx =SUM(A1:A10)`

### Screenshots

Screenshot-rammer skal bevares.

Zoomede screenshots er lavet og indsat:

- `01-cas-ligning-zoom.png`
- `01b-cas-system-zoom.png`
- `03-geometri-trekant-zoom.png`
- `04-vaerksteder-menu-zoom.png`
- `05-sheets-formel-zoom.png`
- `06-sheets-statistik-zoom.png`
- `07-sheets-diagram-zoom.png`

Ark 10 har nu callout på formel-screenshot:

`Her: skriv formlen i cellen eller i formellinjen.`

### Print-all

`print-all.html` er rettet:

- kloner alle `.sheet`
- scopes lokale styles pr. ark
- bevarer emnefarver
- bruger `forside + 10 ark`

Dette var sandsynligvis en årsag til at samlet print så underligt ud.

## Kendte faldgruber

- Headless Chrome crasher lokalt. Handoff fra tidligere nævner også exit 134.
- Der er ikke `.git` metadata i projektroden.
- `print-all.html` bør stadig kontrolleres visuelt i browser/printdialog.
- Lange ark er stadig principielt 1-2 sider, men mange filer har kun én `.sheet`.
- Hvis der laves eksplicit side 2 senere, skal `print-all.html` kunne klone den. Det kan den nu.

## Næste anbefalede skridt

Foreslå Jonas en kort plan før større arbejde.

Mest oplagt:

1. Åbn/kontroller `print-all.html` visuelt.
2. Gennemgå ark 10 for tæthed efter de nye formelskabeloner.
3. Tag language-reviewer P1'erne:
   - Funktioner: `forskrift`, `skæring`, passiv tekst
   - Procent: `relativ ændring`
   - Trigonometri: `isolér x`, `omvendte knap`
   - Statistik: kvartiler mere handlingsnært
   - GeoGebra: `koordinater`, `Algebra-vinduet`
   - Sheets: `akselabels`
4. Kør math-checker igen efter sprogrettelser.

## Spørg Jonas først

Hvis ny session starter her: spørg Jonas hvad han vil prioritere, før større execution.
