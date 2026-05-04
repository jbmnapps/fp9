# Memory - Cheat Sheets prototype

Sidst opdateret: 2026-05-04

## Arbejdsmappe

Arbejd primært i:

`/Users/jonasbenjamin/WORKSPACES/Cheat Sheets-CODEX/cheat sheets/`

Projektroden indeholder stadig `AGENTS.md`, `reviewers/` og `screenshots/`.

## Arbejdsform

- Spar med Jonas før større execution.
- Små, aftalte rettelser må laves direkte.
- Ingen destruktive operationer uden bekræftelse.
- Hvis næste arbejde handler om prototypen, læs først:
  1. `cheat sheets/memory.md`
  2. `cheat sheets/status.md`
  3. `cheat sheets/HANDOFF.md`
  4. `cheat sheets/CLAUDE.md`

## Aktuel prototype

Claude Design prototypen består af:

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

## Vigtige beslutninger

### Screenshots

- Screenshot-rammer skal bevares.
- Brug rigtige PNG'er fra roden `screenshots/`.
- Brug zoomede udsnit når fuldskærmsscreenshots bliver for små på A4.
- Zoomede filer må ligge ved siden af originalerne med `-zoom.png`.

Aktuelle zoom-filer:

- `01-cas-ligning-zoom.png`
- `01b-cas-system-zoom.png`
- `03-geometri-trekant-zoom.png`
- `04-vaerksteder-menu-zoom.png`
- `05-sheets-formel-zoom.png`
- `06-sheets-statistik-zoom.png`
- `07-sheets-diagram-zoom.png`

### Google Sheets

- Sheets-formler skal vise begge funktionssprog, når der er sprogrisiko.
- Skriv ikke kun engelsk og ikke kun dansk.
- Eksempel:
  - `=AVERAGE(A1:A10) / =GENNEMSNIT(A1:A10)`
  - `=MAX(A1:A10) / =MAKS(A1:A10)`
  - `=QUARTILE(A1:A10;1) / =KVARTIL(A1:A10;1)`
- Ark 10 bruger nu elev-skabeloner som `=SUM(skriv celler her)` plus et konkret eksempel.
- Brug teksten: `Brug den version, der virker i din Sheets-fil.`

### Print

- `print-all.html` kloner nu alle `.sheet`-sektioner, ikke kun den første.
- Lokale styles scopes pr. ark i `print-all.html`, så ens klassenavne i forskellige ark ikke overskriver hinanden.
- Headless Chrome crasher lokalt i denne workspace. Brug statiske checks, in-app browser eller WeasyPrint hvis render-check er nødvendig.

## Reviewstatus

Alle fire review-agenter blev kørt 2026-05-04:

- Math checker: rettelser nødvendige, P0 rettet.
- Language reviewer: rettelser nødvendige, P0 rettet, flere P1-poleringer står tilbage.
- Visual reviewer: rettelser nødvendige, print og screenshots delvist rettet.
- Code reviewer: rettelser nødvendige, `print-all.html` og index-markup rettet.

## Ting der ikke må regrediere

- Ret ikke `=AVERAGE(...) / =GENNEMSNIT(...)` tilbage til kun én version.
- Fjern ikke screenshot-rammer.
- Erstat ikke zoomede screenshots med fuldskærm, hvis det gør dem ulæselige på print.
- Genindfør ikke `=K0*(1+r)^n` som Sheets-formel.
- Genindfør ikke Pythagoras uden "retvinklet trekant".
- Genindfør ikke generel "Find vinkel = sin⁻¹(...)" uden cos/tan-alternativer.
