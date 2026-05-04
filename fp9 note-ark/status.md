# Status - FP9 note-ark prototype

Sidst opdateret: 2026-05-04

## Kort status

Projektet i `fp9 note-ark/` er en printvenlig Claude Design prototype med forside, 10 FP9 note-ark og samlet printside.

Aktuel status: brugbar prototype, men ikke færdig-godkendt. De største P0-matematikfejl fra review er rettet. Print og screenshot-læsbarhed er forbedret. Der mangler stadig visuel/sproglig finpolering og en reel printkontrol.

## Filer

- `index.html`
- `print-all.html`
- `ark/01-tal-algebra.html`
- `ark/02-procent.html`
- `ark/03-ligninger.html`
- `ark/04-funktioner.html`
- `ark/05-geometri.html`
- `ark/06-trigonometri.html`
- `ark/07-statistik.html`
- `ark/08-formelsamling.html`
- `ark/09-geogebra.html`
- `ark/10-sheets.html`
- `shared/tokens.css`
- `shared/sheet.css`

## Rettet i seneste session

### Matematik

- `ark/02-procent.html`: Sheets-formlen `=K0*(1+r)^n` er skiftet til konkret formel `=5000*(1+0,03)^4`.
- `ark/10-sheets.html`: samme fejl rettet, og formeltabellen er gjort mere elevnær.
- `ark/10-sheets.html`: statistiknavne skal nu skrives i C-kolonnen, så de ikke overskriver data i A1:A7.
- `ark/08-formelsamling.html`: Pythagoras markeret som kun retvinklet.
- `ark/08-formelsamling.html`: "Find vinkel" er splittet i sin, cos og tan.
- `ark/06-trigonometri.html`: Pythagoras-tekst præciserer retvinklet trekant.
- `ark/04-funktioner.html`: `r = a - 1` præciseret som decimaltal, med procentregel.
- `ark/01-tal-algebra.html`: potens- og kvadratrodsregler har nu betingelser.

### Print og kode

- `print-all.html`: kloner nu `querySelectorAll('.sheet')`.
- `print-all.html`: lokale styles fra hvert ark scopes med `data-print-source`, så klasser som `.frow` ikke kolliderer.
- `print-all.html`: teksten siger nu `forside + 10 ark`.
- `shared/sheet.css`: `print-color-adjust: exact` tilføjet.
- `shared/sheet.css`: flere komponenter har `break-inside: avoid`.
- `index.html`: ugyldig `<span>` omkring `<div>` i arkoversigten er rettet.

### Screenshots

Nye zoomede PNG'er i `screenshots/`:

- `01-cas-ligning-zoom.png`
- `01b-cas-system-zoom.png`
- `03-geometri-trekant-zoom.png`
- `04-vaerksteder-menu-zoom.png`
- `05-sheets-formel-zoom.png`
- `06-sheets-statistik-zoom.png`
- `07-sheets-diagram-zoom.png`

Indsat i:

- `ark/03-ligninger.html`
- `ark/09-geogebra.html`
- `ark/10-sheets.html`

### Google Sheets-arket

- Formel-screenshot har zoom og callout.
- Første metodeformulering siger nu: `Først skal du skrive = for at lave en formel.`
- Formeltabellen bruger nu skabeloner som:
  - `=SUM(skriv celler her)`
  - `fx =SUM(A1:A10)`
- Note siger: `Brug den version, der virker i din Sheets-fil. Skift "skriv celler her" ud med dine celler.`

## Verificering kørt

- Billedsti-check på ark 10 og senere alle relevante billedstier.
- `print-all.html` script parse-check med Node.
- Målrettet søgning efter gamle risikomønstre:
  - `=K0`
  - `alle 11 ark`
  - gamle screenshot-stier i brug
  - tomme screenshot-placeholders

## Kendte begrænsninger

- Lokalt headless Chrome crasher stadig ved render-check.
- Der er ikke `.git` metadata i projektroden, så normal `git diff` virker ikke.
- `print-all.html` er statisk tjekket, men bør stadig ses i rigtig browser/printdialog.
- Flere sproglige P1-fund fra language reviewer står tilbage.

## Anbefalet næste arbejde

1. Visuel/printkontrol af `print-all.html` i browser.
2. Sproglig P1-polering:
   - `forskrift` -> `formel`
   - `skæring` -> `tallet hvor linjen rammer y-aksen`
   - `relativ ændring` -> konkret divider-handling
   - `akselabels` -> `navn på x-akse og y-akse`
3. Overvej om ark 10 stadig er for tæt efter formelskabelonerne.
4. Kør math-checker igen efter sprogrettelser.
