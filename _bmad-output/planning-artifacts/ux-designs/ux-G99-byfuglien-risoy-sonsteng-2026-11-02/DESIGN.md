---
name: KI-assistert interaktivt årshjul
description: Lyst, strukturert planleggingsverktøy for PC og projektor – monokrome tokener, luftig formspråk og oransje brukt bare som tastaturfokus.
status: draft
sources:
  - '{planning_artifacts}/prds/prd-G99-byfuglien-risoy-sonsteng-2026-10-19/prd.md'  # PRD updated 2026-11-11 (presisert for OQ-3 og M11-a; 2026-11-05 integrert via merge 8c5c76f)
  - '{planning_artifacts}/prds/prd-G99-byfuglien-risoy-sonsteng-2026-10-19/.memlog.md'
  - '{planning_artifacts}/product-brief.md'
  - '{planning_artifacts}/tilbakemelding-product-brief.md'
  - 'docs/prd-validering/2026-11-01/'
updated: 2026-11-13
colors:
  background: '#FFFFFF'
  panel: '#F3F5F8'
  text: '#0B0B0B'
  text-muted: '#3E3E3E'
  line-hairline: '#BDBDBD'
  line-strong: '#0B0B0B'
  primary: '#0B0B0B'
  on-primary: '#FFFFFF'
  secondary-bg: '#FFFFFF'
  secondary-text: '#0B0B0B'
  secondary-line: '#0B0B0B'
  focus: '#C75000'
  focus-offset: '#FFFFFF'
  status-blocking-text: '#7D1010'
  status-blocking-bg: '#FFFFFF'
  status-blocking-line: '#0B0B0B'
  status-uncertain-text: '#5C4300'
  status-uncertain-bg: '#FFFFFF'
  status-uncertain-line: '#3E3E3E'
  disabled-text: '#4A4A4A'
  disabled-bg: '#E6E6E6'
typography:
  year-in-wheel:
    fontFamily: '"Segoe UI", system-ui, -apple-system, Roboto, "Helvetica Neue", Arial, sans-serif'
    fontSize: 40px
    fontWeight: '700'
    lineHeight: '1.1'
  page-title:
    fontFamily: '"Segoe UI", system-ui, -apple-system, Roboto, "Helvetica Neue", Arial, sans-serif'
    fontSize: 32px
    fontWeight: '600'
    lineHeight: '1.2'
  wheel-count:
    fontFamily: '"Segoe UI", system-ui, -apple-system, Roboto, "Helvetica Neue", Arial, sans-serif'
    fontSize: 28px
    fontWeight: '600'
    lineHeight: '1.1'
  section-title:
    fontFamily: '"Segoe UI", system-ui, -apple-system, Roboto, "Helvetica Neue", Arial, sans-serif'
    fontSize: 24px
    fontWeight: '600'
    lineHeight: '1.25'
  body:
    fontFamily: '"Segoe UI", system-ui, -apple-system, Roboto, "Helvetica Neue", Arial, sans-serif'
    fontSize: 18px
    fontWeight: '400'
    lineHeight: '1.5'
  label:
    fontFamily: '"Segoe UI", system-ui, -apple-system, Roboto, "Helvetica Neue", Arial, sans-serif'
    fontSize: 18px
    fontWeight: '600'
    lineHeight: '1.3'
  metadata:
    fontFamily: '"Segoe UI", system-ui, -apple-system, Roboto, "Helvetica Neue", Arial, sans-serif'
    fontSize: 16px
    fontWeight: '400'
    lineHeight: '1.4'
  month-cell-activity:
    fontFamily: '"Segoe UI", system-ui, -apple-system, Roboto, "Helvetica Neue", Arial, sans-serif'
    fontSize: 16px
    fontWeight: '600'
    lineHeight: '1.3'
rounded:
  full: 9999px
  lg: 16px
  md: 10px
spacing:
  '1': 4px
  '2': 8px
  '3': 16px
  '4': 24px
  '5': 32px
  '6': 48px
  panel-padding: 24px
  gap: 16px
  gap-lg: 24px
  target-min: 44px
components:
  primaerknapp:
    background: '{colors.primary}'
    foreground: '{colors.on-primary}'
    radius: '{rounded.full}'
    typography: '{typography.label}'
    minHeight: '{spacing.target-min}'
  sekundaerknapp:
    background: '{colors.secondary-bg}'
    foreground: '{colors.secondary-text}'
    border: '2px solid {colors.secondary-line}'
    radius: '{rounded.full}'
    typography: '{typography.label}'
    minHeight: '{spacing.target-min}'
  tekstlenke:
    foreground: '{colors.text}'
    textDecoration: underline
    typography: '{typography.body}'
  deaktivert-kontroll:
    background: '{colors.disabled-bg}'
    foreground: '{colors.disabled-text}'
    reasonTypography: '{typography.label}'
  panel:
    background: '{colors.panel}'
    border: '1px solid {colors.line-hairline}'
    radius: '{rounded.lg}'
    padding: '{spacing.panel-padding}'
  fokusring:
    outline: '3px solid {colors.focus}'
    outlineOffset: 3px
    offsetColor: '{colors.focus-offset}'
  valgt-aktiv-markering:
    border: '2px solid {colors.line-strong}'
    background: '{colors.panel}'
    typography: '{typography.label}'
  felt-med-etikett:
    background: '{colors.background}'
    border: '1px solid {colors.line-strong}'
    radius: '{rounded.md}'
    labelTypography: '{typography.label}'
    minHeight: '{spacing.target-min}'
  feltstatusmelding-ma-rettes:
    foreground: '{colors.status-blocking-text}'
    background: '{colors.status-blocking-bg}'
    border: '4px solid {colors.status-blocking-line}'
    typography: '{typography.label}'
  feltstatusmelding-kontroller:
    foreground: '{colors.status-uncertain-text}'
    background: '{colors.status-uncertain-bg}'
    border: '1px dashed {colors.status-uncertain-line}'
    typography: '{typography.label}'
  feiloppsummering:
    foreground: '{colors.status-blocking-text}'
    border: '4px solid {colors.status-blocking-line}'
    radius: '{rounded.md}'
  kildeutdragskort:
    background: '{colors.background}'
    excerptBackground: '{colors.panel}'
    border: '1px solid {colors.line-hairline}'
    radius: '{rounded.md}'
    statusTypography: '{typography.label}'
    excerptTypography: '{typography.body}'
  kategorimerke:
    background: '{colors.background}'
    foreground: '{colors.text}'
    border: '1px solid {colors.line-strong}'
    radius: '{rounded.full}'
    typography: '{typography.metadata}'
  modal-dialog:
    background: '{colors.background}'
    border: '1px solid {colors.line-hairline}'
    radius: '{rounded.lg}'
    padding: '{spacing.panel-padding}'
  gjennomgangsindikator:
    background: '{colors.panel}'
    foreground: '{colors.text}'
    border: '1px solid {colors.line-strong}'
    typography: '{typography.label}'
  meldingsstripe:
    background: '{colors.panel}'
    foreground: '{colors.text}'
    border: '1px solid {colors.line-hairline}'
    typography: '{typography.body}'
  periodenavigasjon:
    typography: '{typography.label}'
    minHeight: '{spacing.target-min}'
  arshjulsirkel:
    background: '{colors.background}'
    sectorLine: '{colors.line-strong}'
    yearTypography: '{typography.year-in-wheel}'
    countTypography: '{typography.wheel-count}'
    monthTypography: '{typography.label}'
  manedsrutenett:
    background: '{colors.background}'
    gridLine: '{colors.line-hairline}'
    outsideMonthBackground: '{colors.panel}'
    activityTypography: '{typography.month-cell-activity}'
    activityRadius: '{rounded.md}'
  dagsoversikt:
    background: '{colors.background}'
    border: '1px solid {colors.line-hairline}'
    radius: '{rounded.lg}'
    rowRadius: '{rounded.md}'
  forslagsoversikt:
    background: '{colors.background}'
    rowBorder: '1px solid {colors.line-hairline}'
    rowRadius: '{rounded.md}'
    rowTypography: '{typography.body}'
  demo-modus-merke:
    background: '{colors.background}'
    foreground: '{colors.text}'
    border: '2px dashed {colors.line-strong}'
    typography: '{typography.label}'
  fremdriftsindikator:
    track: '{colors.panel}'
    bar: '{colors.line-strong}'
    border: '1px solid {colors.line-strong}'
---

# KI-assistert interaktivt årshjul – DESIGN.md (utkast)

> **Status: utkast (`status: draft`).** Kanoniske beslutninger står i `.memlog.md`. OQ-3 ble avklart 2026-11-11. Dokumentet blir ikke `final` før OQ-7 er avklart og øvrige krav i workflowen er oppfylt; OQ-8 blokkerer ikke (gruppevedtak 2026-11-11, memlog).
>
> **Statusmarkører i dette dokumentet**
> - umerket = vedtatt (godkjent av Sebastian eller prosjektgruppen, bindende)
> - **[FORELØPIG]** = forslag, ikke godkjent
> - **[ÅPENT: …]** / **[AVHENGER AV: …]** = åpent spørsmål med eier
> - **[VALIDERES]** = må testes på PC, projektor, tastatur eller skjermleser; ikke testet ennå
>
> **Spinene vinner ved konflikt.** DESIGN.md og EXPERIENCE.md går foran alle wireframes og forhåndsvisninger i `wireframes/`, HTML-nøkkelmocker i `mockups/` og arbeidsfiler i `.working/`. Wireframene er lavdetaljerte gråtoneskisser med fiktive data og foreløpig ordlyd. PNG-forhåndsvisningene er laget med en lokal, omtrentlig renderer, ikke eksportert fra Excalidraw. Alle sju gjeldende skisser i `wireframes/` er åpnet i Excalidraw og bekreftet av Sebastian Byfuglien 2026-11-11 (memlog). Det er ikke en test på projektor, med tastatur eller skjermleser.
>
> Visuell referanse for tokenene: [`.working/kombinert-retning-1.html`](.working/kombinert-retning-1.html) og [`.working/kombinert-retning-1.forhandsvisning.png`](.working/kombinert-retning-1.forhandsvisning.png) – historisk arbeidsfil i `.working/` som kan brukes som referanse for palett og formspråk. Den viser godkjent palett, kontrastberegninger og snutter av F1, F7 og F2/F3, men har utdaterte kategoriplassholdere («Kat. A–I») og er ikke styrende for gjeldende kategorier eller funksjonelle UX-regler. Utkastets egne «problem»-notater er vurderinger, ikke beslutninger.

## Brand & Style

Årshjulet er et arbeidsverktøy for en troppssjef, ikke en markedsflate. Retningen er **A – «Lys, strukturert planleggingsverktøy»**: lys flate, tydelig typografisk hierarki, få forstyrrelser og luft rundt det som betyr noe – årshjulet i møtet og det aktive aktivitetsforslaget i gjennomgangen.

Retningen er satt sammen av tre godkjente deler:

| Del | Hentet fra |
|---|---|
| Formspråk og generell layout (avrundede hjørner, luft) | Tema 1 «Kjølig og luftig» |
| Fargetokener (svart, hvitt, nøytrale gråtoner) | Tema 2 «Presis monokrom» |
| Panelfarge `#F3F5F8` | Tema 1 |
| Fokusfarge | Ny: oransje `#C75000`, bare for tastaturfokus |

Inspirasjon – bare som referanse, ingen kopiering av nettsteder, logoer, bilder eller eksakt design, og ingen Forsvaret-profil:

- **Apple:** luftige flater, tydelig hierarki, én primærhandling per flate.
- **Polestar:** presis struktur, hårlinjer, nøktern layout.
- **Langsikt:** metadata og redaksjonelt hierarki (dato, type, tittel).

**Anti-mønster:** dagens Excel-arbeid – tette visninger, oppsplittet informasjon, unødvendig navigasjon og behov for å åpne flere dokumenter for å få oversikt.

Produktnavnet er ikke bestemt (OQ-2). Grensesnittet bruker «Årshjul (arbeidstittel)».

Bare lys modus. Mørk modus er ikke del av retningen.

## Colors

Paletten er monokrom med vilje: på projektor er kontrast og tekst tryggere enn fargekoder. Ingen farge bærer betydning alene (FR-12, NFR-7).

| Token | Hex | Bruk | Brukes ikke til |
|---|---|---|---|
| `{colors.background}` | `#FFFFFF` | Sideflate, modaler, felt | – |
| `{colors.panel}` | `#F3F5F8` | Paneler, meldingsstripe, gjennomgangsindikator, dager utenfor måneden, svak bakgrunn i valgt/aktiv-markering | Eneste skille mot bakgrunnen (1,09:1) |
| `{colors.text}` | `#0B0B0B` | Brødtekst, overskrifter, tall | – |
| `{colors.text-muted}` | `#3E3E3E` | Metadata, hjelpetekst | Status eller handlinger |
| `{colors.line-hairline}` | `#BDBDBD` | Panelkant, rutenett, skillelinjer | Informasjon (dekor, 1,88:1) |
| `{colors.line-strong}` | `#0B0B0B` | Feltrammer, hjulsektorer, valgt/aktiv-kant | – |
| `{colors.primary}` / `{colors.on-primary}` | `#0B0B0B` / `#FFFFFF` | Primærknapp | Status |
| `{colors.secondary-bg}` / `-text` / `-line` | `#FFFFFF` / `#0B0B0B` / `#0B0B0B` | Sekundærknapp | – |
| `{colors.focus}` | `#C75000` | **Bare** tastaturfokus | Valgt, aktiv, kategori, status, feil, destruktive handlinger |
| `{colors.focus-offset}` | `#FFFFFF` | 3 px hvit luft mellom element og fokusring | – |
| `{colors.status-blocking-text}` | `#7D1010` | Tekst i «! Må rettes:» (manglende/ugyldig) | Pynt |
| `{colors.status-blocking-line}` | `#0B0B0B` | Tykk heltrukken ramme (4 px) rundt blokkerende felt/melding | – |
| `{colors.status-uncertain-text}` | `#5C4300` | Tekst i «? Kontroller:» (usikker) | Pynt |
| `{colors.status-uncertain-line}` | `#3E3E3E` | Tynn stiplet ramme (1 px) | – |
| `{colors.status-blocking-bg}` / `{colors.status-uncertain-bg}` | `#FFFFFF` | Flate bak statusmeldinger | – |
| `{colors.disabled-text}` / `{colors.disabled-bg}` | `#4A4A4A` / `#E6E6E6` | Utilgjengelige kontroller, alltid med synlig årsak | – |

**Kontrast for bærende par** (beregnet i `kombinert-retning-1.html`; projektortall er filteranslag, ikke målinger **[VALIDERES]**):

| Par | Forhold | Projektoranslag | Mål |
|---|---|---|---|
| Tekst på bakgrunn | 19,68:1 | ~12,81:1 | ≥ 7 (min. 4,5) |
| Tekst på panel | 18,02:1 | ~11,93:1 | ≥ 7 |
| Dempet tekst på bakgrunn | 10,70:1 | ~6,73:1 | ≥ 7 |
| Dempet tekst på panel | 9,79:1 | ~6,27:1 | ≥ 7 |
| Primærknapp-tekst på primær | 19,68:1 | ~12,81:1 | ≥ 7 |
| «Må rettes» på bakgrunn / panel | 10,75:1 / 9,84:1 | ~7,57 / ~7,05:1 | ≥ 7 |
| «Kontroller» på bakgrunn / panel | 9,30:1 / 8,52:1 | ~6,09 / ~5,67:1 | ≥ 7 |
| Deaktivert tekst på deaktivert flate | 7,10:1 | ~4,81:1 | unntatt; ønsket ≥ 4,5 |
| Fokus mot bakgrunn | 4,59:1 | ~3,62:1 | ≥ 3 (1.4.11) |
| Fokus mot panel | 4,20:1 | ~3,38:1 | ≥ 3 |
| Fokus mot svart primærknapp | 4,29:1 | ~3,53:1 | ≥ 3 |
| Fokus mot deaktivert flate | 3,68:1 | ~3,02:1 | ≥ 3 – liten margin **[VALIDERES]** |
| Sterk linje mot panel | 18,02:1 | ~11,93:1 | ≥ 3 |
| Panel mot bakgrunn | 1,09:1 | ~1,07:1 | ingen krav – derfor hårlinjekant |

Kontrast måles mot WCAG 2.1 kriterium 1.4.3 (NFR-7). Under simulert deuteranopi er «Må rettes»-rød og «Kontroller»-brun nesten like. Det er akseptert fordi statusen bæres av tekst og linjetype.

**Kategoriliste og bokstavkoder** (gruppevedtak 2026-11-11, OQ-3 avklart, memlog): **Ø** Øvelser og oppdrag · **U** Utdanning og trening · **S** Seremonier og oppstillinger · **M** Møter og planlegging · **P** Personell og velferd · **L** Materiell og logistikk · **E** Inspeksjon og evaluering · **F** Frister · **A** Annet. Klassifiseringsreglene står i EXPERIENCE.md › Kategoriliste og klassifisering. F3, F4 og F7 viser kode og fullt navn i formatet «Ø – Øvelser og oppdrag». F1 har en synlig, kompakt tegnforklaring for alle ni kodene ved siden av hjulet (vedtatt 2026-11-11); størrelse og plassering **[VALIDERES]** på projektor.

**Kategorifarger: ingen er vedtatt** **[ÅPENT – krever eget vedtak]**. Kategoriidentitet er bokstavkode + antall, og «kode – fullt navn» der flaten viser kategorifeltet (F3, F4, F7). Kategoriene skal kunne gjenkjennes uten farge. Farge kan senere bare forsterke, aldri bære identiteten alene (FR-12). Oransje er aldri en kategorifarge.

## Typography

Systemfontstabel: `"Segoe UI", system-ui, -apple-system, Roboto, "Helvetica Neue", Arial, sans-serif`. Ingen webfont. Bare vektene 400, 600 og 700. **Tabulære tall** (`font-variant-numeric: tabular-nums`) for datoer, ukenumre og antall.

| Rolle | Token | Størrelse / linjehøyde / vekt | Brukes til |
|---|---|---|---|
| År i hjulet | `{typography.year-in-wheel}` | 40 / 1,1 / 700 | Kalenderåret i hjulets sentrum |
| Sidetittel | `{typography.page-title}` | 32 / 1,2 / 600 | «Mars 2026», «Gjennomgang – …» |
| Antall i hjulet | `{typography.wheel-count}` | 28 / 1,1 / 600 | Antall aktiviteter per måned |
| Seksjonstittel | `{typography.section-title}` | 24 / 1,25 / 600 | «Aktivt forslag 4 av 15», «Kildeutdrag (2)» |
| Brødtekst | `{typography.body}` | 18 / 1,5 / 400 | Feltverdier, merknader, kildeutdrag, meldinger |
| Etikett/knapp | `{typography.label}` | 18 / 1,3 / 600 | Feltetiketter, knapper, statusord, månedsnavn i hjulet |
| Metadata | `{typography.metadata}` | 16 / 1,4 / 400 | Datoer under titler, kategorimerke, tegnteller |
| Aktivitet i månedscelle | `{typography.month-cell-activity}` | 16 / 1,3 / 600 | Aktivitetsblokker i månedsrutenettet |

Regler:

- Minst 16 px som hovedregel. Informasjon som er viktig for status og handling, er minst 18 px.
- Linjelengde for brødtekst maks ca. 75 tegn.
- Fulle månedsnavn i månedsvisningen. Tre bokstaver i hjulet («mar»), med fullt navn for skjermleser («Mars 2026, 20 aktiviteter»).
- Datoer alltid med årstall i gjennomgangen (FR-21).
- Størrelsene er et designgrunnlag, ikke bevis på lesbarhet på projektor **[VALIDERES]**.

## Layout & Spacing

8 px-system: `{spacing.1}` 4 · `{spacing.2}` 8 · `{spacing.3}` 16 · `{spacing.4}` 24 · `{spacing.5}` 32 · `{spacing.6}` 48.

- Panelpadding `{spacing.panel-padding}` (24 px). Avstand mellom elementer `{spacing.gap}`–`{spacing.gap-lg}` (16–24 px).
- God luft rundt hjulet; hjulet er hovedinnholdet i F1.
- Klikkmål minst `{spacing.target-min}` (44 px) høye.
- Målflate: PC-skjerm og projektor, vurdert i 1920 × 1080 i wireframene (NFR-8). Ingen mobilbrytpunkter.
- Fast struktur på alle flater: toppfelt → (gjennomgangsindikator / meldingsstripe i full bredde) → hovedinnhold.

| Flate | Grunnoppsett | Wireframe |
|---|---|---|
| F1 Årsvisning | Toppfelt med kalenderårvelger, «Ny aktivitet», «Last opp dokument»; hjulet som hovedinnhold med tegnforklaringen ved siden av (skisse oppdatert 2026-11-11) | [`wireframes/flow-f1-arsvisning-2026-11-03.forhandsvisning.png`](wireframes/flow-f1-arsvisning-2026-11-03.forhandsvisning.png) ([kilde](wireframes/flow-f1-arsvisning-2026-11-03.excalidraw)) – hovedtilstand, gjennomgang pågår, tomt kalenderår |
| F2 Månedsvisning | Toppfelt med månedsnavigasjon og «Til årsvisning»; rutenett med ukenummerkolonne og mandag–søndag | [`wireframes/flow-f2-f3-manedsvisning-v3-2026-11-03.forhandsvisning.png`](wireframes/flow-f2-f3-manedsvisning-v3-2026-11-03.forhandsvisning.png) ([kilde](wireframes/flow-f2-f3-manedsvisning-v3-2026-11-03.excalidraw)) – rutenett, dagsoversikt, F3 som modal (C valgt, D sidepanel IKKE VALGT) |
| F3 Aktivitetsdetaljer | Modal over dempet månedsvisning (og eventuelt dagsoversikten); lesevisning med tittelen «Aktivitetsdetaljer», alle felt og «Rediger», «Slett» og «Lukk» | [`wireframes/flow-f2-f3-manedsvisning-v3-2026-11-03.forhandsvisning.png`](wireframes/flow-f2-f3-manedsvisning-v3-2026-11-03.forhandsvisning.png) ([kilde](wireframes/flow-f2-f3-manedsvisning-v3-2026-11-03.excalidraw)) – C F3 som modal (D sidepanel IKKE VALGT). Ingen HTML-mock; dekket av skisse og spine (gruppevedtak 2026-11-13) |
| F4 Aktivitetsskjema | Modal over dempet visning (i skissen og mocken: månedsvisningen mars 2026); «Tittel» i full bredde, «Startdato» \| «Sluttdato» og «Kategori» \| «Ansvarsområde» i to kolonner, «Merknader» med tegnteller i full bredde; «Lagre» og «Avbryt» nederst. Ved «Lagre» med feil: feiloppsummering øverst i modalen | [`wireframes/flow-f4-aktivitetsskjema-2026-11-09.forhandsvisning.png`](wireframes/flow-f4-aktivitetsskjema-2026-11-09.forhandsvisning.png) ([kilde](wireframes/flow-f4-aktivitetsskjema-2026-11-09.excalidraw)) – tomt skjema med innfelt datovelger og kategoriliste, lagring stoppet. Skissens teller «0 / [grense] tegn» er erstattet av formuleringen under Felt med etikett |
| F5 Slettebekreftelse | Erstatter F3-innholdet i samme modal, med samme ramme, posisjon og størrelse; tittelraden «Aktivitetsdetaljer › Slett», spørsmålet «Slette aktiviteten?» og knappene med trygt standardvalg «Avbryt» først/til venstre og destruktiv handling til høyre. Sletting som feiler, vises i samme modal | [`wireframes/flow-f5-sletting-2026-11-09.forhandsvisning.png`](wireframes/flow-f5-sletting-2026-11-09.forhandsvisning.png) ([kilde](wireframes/flow-f5-sletting-2026-11-09.excalidraw)) – bekreftelse, avbrutt, slettet fra månedsvisning og dagsoversikt, slettefeil. Ingen HTML-mock; dekket av skisse og spine (gruppevedtak 2026-11-13) |
| F6 Dokumentopplasting og analyse | Modal over F1 eller F2, åpnet med «Last opp dokument» i toppfeltet; påminnelse om fiktive dokumenter, filvalg og «Analyser dokumentet»; fremdriftsindikator med statustekst under analyse; ved feil «Prøv igjen» (primær) og «Lukk» | [`wireframes/flow-f6-opplasting-analyse-2026-11-09.forhandsvisning.png`](wireframes/flow-f6-opplasting-analyse-2026-11-09.forhandsvisning.png) ([kilde](wireframes/flow-f6-opplasting-analyse-2026-11-09.excalidraw)) – velg fil, avvisning, analyse pågår, forslag → F7, ingen funnet, feilet, demo-modus, opplasting sperret. Demo-modus avhenger av OQ-7 og grenser av OQ-8. Ingen HTML-mock; dekket av skisse og spine (gruppevedtak 2026-11-13) |
| F7 Gjennomgang | Toppfelt med teller og «← Til årshjulet»; tre soner: forslagsoversikt (kan skjules) · aktivt forslag · kildeutdrag; handlingsrad nederst | [`wireframes/flow-f7-gjennomgang-v3-2026-11-03.forhandsvisning.png`](wireframes/flow-f7-gjennomgang-v3-2026-11-03.forhandsvisning.png) ([kilde](wireframes/flow-f7-gjennomgang-v3-2026-11-03.excalidraw)) – A oversikt synlig (standard), B oversikt skjult. Kolonnebreddene fra skissen er utgangspunkt, ikke validert **[VALIDERES]** |
| F8 Oppsummering, fullføring og forkasting | Oppsummering som eget bekreftelsessteg etter F7: antall som lagres og forkastes, berørte kalenderår og påminnelsen om duplikater; «Tilbake til gjennomgangen» og «Fullfør og lagre». Forkasting er en dialog over F7 («Forkaste gjennomgangen?») med «Fortsett gjennomgangen» som trygt, fremhevet standardvalg og «Forkast uten å lagre» | [`wireframes/flow-f8-oppsummering-forkasting-2026-11-03.forhandsvisning.png`](wireframes/flow-f8-oppsummering-forkasting-2026-11-03.forhandsvisning.png) ([kilde](wireframes/flow-f8-oppsummering-forkasting-2026-11-03.excalidraw)) – oppsummering, vellykket lagring, lagringsfeil, forkasting. Ingen HTML-mock; dekket av skisse og spine (gruppevedtak 2026-11-13) |

HTML-nøkkelmocker (statiske illustrasjoner; spinene vinner ved konflikt): [`mockups/key-f1-arsvisning.html`](mockups/key-f1-arsvisning.html) · [`mockups/key-f2-manedsvisning.html`](mockups/key-f2-manedsvisning.html) · [`mockups/key-f4-aktivitetsskjema.html`](mockups/key-f4-aktivitetsskjema.html) · [`mockups/key-f7-gjennomgang.html`](mockups/key-f7-gjennomgang.html). Se EXPERIENCE.md › Visuelle referanser for hva hver mock viser.

F7 prioriterer ett aktivt forslag med kildeutdragene sine. Felt og kildeutdrag vises samtidig (FR-27).

## Elevation & Depth

Kanter, ikke skygger.

- Panel mot bakgrunn har bare 1,09:1 kontrast. Paneler får derfor 1 px `{colors.line-hairline}`-kant når de må skilles fra bakgrunnen.
- Skygge brukes aldri som eneste skille. Den forsvinner på projektor.
- Modaler ligger over en dempet bakgrunn. Dempingen i skissene er utgangspunkt, ikke validert **[VALIDERES]**.
- Bare ett modalnivå (se EXPERIENCE.md).

## Shapes

| Form | Token | Brukes til |
|---|---|---|
| Pille | `{rounded.full}` | Knapper, kategorimerker |
| 16 px | `{rounded.lg}` | Paneler, modaler, dagsoversikt |
| 10 px | `{rounded.md}` | Felt, kort (kildeutdrag, forslag i oversikten, aktivitetsblokker), valgt kalenderår i F1 |

Hjulet er en sirkel med 12 like sektorer, januar øverst, med klokka.

## Components

Visuell spesifikasjon. Atferd står i EXPERIENCE.md › Component Patterns med samme navn.

Statiske illustrasjoner (spinene vinner ved konflikt): Årshjulsirkel, Periodenavigasjon og Valgt/aktiv-markering i [`mockups/key-f1-arsvisning.html`](mockups/key-f1-arsvisning.html) · Månedsrutenett og Dagsoversikt i [`mockups/key-f2-manedsvisning.html`](mockups/key-f2-manedsvisning.html) · Modal/dialog, Felt med etikett, Feltstatusmelding og Feiloppsummering i [`mockups/key-f4-aktivitetsskjema.html`](mockups/key-f4-aktivitetsskjema.html) · Forslagsoversikt, Kildeutdragskort og Deaktivert kontroll med årsak i [`mockups/key-f7-gjennomgang.html`](mockups/key-f7-gjennomgang.html).

| Komponent | Visuell spesifikasjon |
|---|---|
| **Primærknapp** (`primaerknapp`) | Svart fylt pille, hvit tekst i `{typography.label}`, min. 44 px. Én per flate. I bekreftelsesdialoger får det trygge standardvalget den fremhevede stilen. |
| **Sekundærknapp** (`sekundaerknapp`) | Hvit pille med 2 px svart kant, svart tekst. |
| **Tekstlenke** (`tekstlenke`) | Understreket tekst. Pil (→) bare når lenken fører til en annen flate (f.eks. «Gå til januar 2027 →»). |
| **Deaktivert kontroll med årsak** (`deaktivert-kontroll`) | `{colors.disabled-bg}` / `{colors.disabled-text}`. Alltid med synlig årsakstekst i `{typography.label}` ved kontrollen, f.eks. «Kan ikke godkjennes ennå: Sluttdato og Ansvarsområde må rettes.» Aldri bare grå knapp. |
| **Panel** (`panel`) | `{colors.panel}`, `{rounded.lg}`, padding 24 px, 1 px hårlinjekant ved behov. |
| **Fokusring** (`fokusring`) | 3 px `{colors.focus}` med 3 px hvit avstand (`outline-offset`). Vises bare ved tastaturfokus (`:focus-visible`). |
| **Valgt/aktiv-markering** (`valgt-aktiv-markering`) | Nøytral: 2 px `{colors.line-strong}`-kant, `{colors.panel}`-bakgrunn og tydelig tekst («Valgt: Mars 2026», «Aktiv») (vedtatt 2026-11-09). Valgt kalenderår i årvelgeren i F1 bruker samme markering: 2 px `{colors.line-strong}`-kant, `{colors.panel}`-bakgrunn, min. 44 px høy og `{rounded.md}` (10 px), slik at den skilles fra pilleknappene og tydelig fra primærknappen «Ny aktivitet»; gjelder begge F1-tilstander (gruppevedtak 2026-11-12, alternativ B). I kalenderårvelgeren bæres teksten av årstallet (f.eks. «2026») sammen med markeringen og `aria-current`; ordet «Valgt:» kreves ikke der. Presiseringen gjelder bare denne velgeren (gruppevedtak 2026-11-13). Ikke helsvart sektor, aldri oransje. Må skilles fra den tykke rammen i «Må rettes» – teksten bærer forskjellen **[VALIDERES]**. |
| **Felt med etikett** (`felt-med-etikett`) | Synlig etikett over feltet i `{typography.label}`. Obligatoriske felt merkes med tekst «(obligatorisk)», valgfrie med «(valgfritt)» – ikke bare stjerne. Felt `{rounded.md}`, 1 px sterk linje, min. 44 px. Tegnteller under merknadsfeltet i `{typography.metadata}`; ordlyden i teller og feilmeldinger står i EXPERIENCE.md › Felt med etikett og Voice and Tone. Selve tegngrensen er ikke fastsatt **[AVHENGER AV: OQ-8 – arkitektur]**. Datofelt i formatet dd.mm.åååå med tastaturinntasting og datovelger (vedtatt 2026-11-09). |
| **Feltstatusmelding** – «Må rettes» (`feltstatusmelding-ma-rettes`) | Rett under feltet: «! Må rettes: Ugyldig – sluttdato er før startdato». Tekst `{colors.status-blocking-text}`, 4 px heltrukken `{colors.status-blocking-line}`-ramme rundt felt og melding. Brukes for *manglende* og *ugyldig*. |
| **Feltstatusmelding** – «Kontroller» (`feltstatusmelding-kontroller`) | Rett under feltet: «? Kontroller: Usikker – sammenlign med kildeutdraget». Tekst `{colors.status-uncertain-text}`, 1 px stiplet `{colors.status-uncertain-line}`-ramme. Brukes for *usikker*. |
| **Feiloppsummering** (`feiloppsummering`) | Boks øverst i skjema eller aktivt forslag: «! 4 felt må rettes før lagring:» med feltnavnene. Samme ramme som «Må rettes» (utgangspunkt fra skissen, ikke validert **[VALIDERES]**). Hvert feltnavn er en lenke som flytter fokus til feltet (vedtatt 2026-11-09). |
| **Kildeutdragskort** (`kildeutdragskort`) | Kort per kildeutdrag: statuslinje + utdragstekst i `{colors.panel}`-boks som ren tekst. Status: «Verifisert – Teksten finnes i dokumentet. Det betyr ikke at forslaget er riktig.» (heltrukken kant) / «Ikke verifisert – Teksten ble ikke funnet i dokumentet. Kontroller forslaget selv.» (stiplet kant) / «Mangler» (ingen kildeutdrag, eller tomt utdrag). Kanttype per status er utgangspunkt fra skissen, ikke validert **[VALIDERES]**; statusord og forklaring er vedtatt. Aldri «korrekt» eller «bekreftet». |
| **Kategorimerke** (`kategorimerke`) | Pille med bokstavkode og eventuelt antall («Ø 8»). Kant og flate (hvit, 1 px sterk kant) er utgangspunkt fra skissen **[VALIDERES]**. Bokstavkodene er Ø, U, S, M, P, L, E, F og A (gruppevedtak 2026-11-11, OQ-3). Ingen kategorifarger uten eget vedtak. Bokstavstørrelse i hjulet kan være for liten på projektor **[VALIDERES]**. |
| **Modal/dialog** (`modal-dialog`) | Hvit flate, `{rounded.lg}`, 1 px hårlinjekant, padding 24 px, dempet bakgrunn bak. Tittel i `{typography.section-title}`. Knapper: trygt standardvalg først/til venstre, destruktiv handling til høyre (vedtatt 2026-11-09). |
| **Gjennomgangsindikator** (`gjennomgangsindikator`) | Stripe i full bredde under toppfeltet i F1 og F2: «Gjennomgang pågår: 8 av 15 forslag gjenstår» + sekundærknapp «Gå til gjennomgangen». Panel med 1 px sterk kant. |
| **Meldingsstripe** (`meldingsstripe`) | Stripe i full bredde under toppfeltet for bekreftelser og feil, f.eks. «Aktiviteten «Skytedag» er lagret (24.03.2026).» Panel med hårlinjekant og «Lukk». Forsvinner ikke automatisk (vedtatt 2026-11-09). |
| **Periodenavigasjon** (`periodenavigasjon`) | Kalenderårvelger «◀ 2025 \| 2026 \| 2027 ▶» i F1 og månedsnavigasjon «◀ Februar 2026 \| Mars 2026 \| April 2026 ▶» + «Til årsvisning (2026)» i F2. Knapper min. 44 px. Valgt kalenderår i F1 har valgt/aktiv-markering (se den raden; gruppevedtak 2026-11-12, alternativ B). Oransje brukes bare til tastaturfokus. |
| **Årshjulsirkel** (`arshjulsirkel`) | Sirkel med 12 like sektorer, sterke sektorlinjer. Per sektor: månedsnavn (`label`), antall (`wheel-count`) og kategorifordeling (gruppevedtak 2026-11-11): inntil to kategorimerker med kode og antall («Ø 8», «U 5») og eventuelt restindikatoren «+N øvrige aktiviteter». Hvilke kategorier som vises, sorteringen, beregningen av N og månedens tilgjengelige navn står i EXPERIENCE.md › Årshjulsirkel. Ingen restindikator når det ikke finnes øvrige aktiviteter. Ved siden av hjulet, når det er plass: alltid synlig, kompakt tegnforklaring med alle ni koder og fulle navn. Størrelse, plassering og lesbarhet **[VALIDERES]** på PC og projektor. Måned med 0 viser «0» og «Ingen aktiviteter», uten kategorimerker. Sentrum: kalenderåret (`year-in-wheel`) – aldri summen av månedstall. Valgt måned: valgt/aktiv-markering. Fokus: fokusring rundt sektoren. |
| **Månedsrutenett** (`manedsrutenett`) | Ukenummerkolonne + mandag–søndag. Alle ISO-uker som berører måneden; dager utenfor måneden i `{colors.panel}` med dempet dato. Maks to aktivitetsblokker per dag (tittel + bokstavkode, f.eks. «Skyteøvelse [Ø]»), deretter knappen «+N flere». Flerukesaktiviteter vises som én blokk per ukerad med fortsettelsesmerking («forts. →», «← forts.»). |
| **Dagsoversikt** (`dagsoversikt`) | Utvidbar liste i månedsvisningen – ikke modal og ikke egen dagsvisning: overskrift «Onsdag 18. mars 2026 – 5 aktiviteter», én rad per aktivitet: tittel på første linje, datoer og kategorikode på neste (fullt kategorinavn i tilgjengelig tekst og i F3; gruppevedtak 2026-11-11 gjelder innholdet, ikke plasseringen), «Lukk». |
| **Forslagsoversikt** (`forslagsoversikt`) | Kompakt liste i F7: nummer + kort tittel; linje 2 = behandlingsstatus (Ubehandlet/Godkjent/Avvist) og separate problemmerker («! 2 må rettes», «? Usikker», «Kilde ikke verifisert», «Ingen kilde»). Aktivt forslag har valgt/aktiv-markering og ordet «Aktiv». «Skjul»-knapp. |
| **Demo-modus-merke** (`demo-modus-merke`) | Fast merke i toppfeltet: «DEMO-MODUS – forhåndsdefinerte forslag, ingen språkmodell». Tekst + ramme, ingen fargebetydning. Stiplet 2 px ramme og plassering i toppfeltet er utgangspunkt fra skissen **[VALIDERES]**; ordlyd foreløpig, språkvaskes **[FORELØPIG]**. |
| **Fremdriftsindikator** (`fremdriftsindikator`) | Ubestemt, bevegelig felt i et spor med sterk kant. Ingen prosent eller tidsestimat. Med statustekst «Analyserer «filnavn» …». Utseende er utgangspunkt fra skissen **[VALIDERES]**. |

## Do's and Don'ts

| Gjør | Ikke gjør |
|---|---|
| Bruk oransje `{colors.focus}` bare som tastaturfokus | Oransje for valgt måned, aktivt forslag, kategori, status, feil eller destruktive handlinger |
| La status bæres av tekst («! Må rettes:», «? Kontroller:») og linjetype | Status med farge alene, eller bare ikon |
| Gi paneler hårlinjekant når de skal skilles fra bakgrunnen | Skille flater med skygge alene |
| Hold tekst ≥ 16 px, og ≥ 18 px for status og handling | Tekst under 16 px |
| Vis kategori som bokstavkode + antall | Innføre kategorifarger uten eget vedtak |
| Kall et verifisert kildeutdrag «Verifisert» med forklaring | Kalle et kildeutdrag «korrekt» eller «bekreftet» |
| Vis en utilgjengelig kontroll med synlig årsak | Grå knapp uten forklaring, eller forklaring bare i verktøytips |
| Én primærknapp per flate; trygt valg fremhevet i bekreftelser | Fremheve den destruktive handlingen som standard |
| Vis kalenderåret i hjulets sentrum | Vise summen av månedstall som om det var antall aktiviteter |
| Marker valgt/aktiv nøytralt med kant, svak flate og tekst | Helsvart sektor som valgt-markering |
| Ren tekst for kildeutdrag, merknader og feltverdier (NFR-9) | Formatert eller tolket innhold fra dokumentet |
