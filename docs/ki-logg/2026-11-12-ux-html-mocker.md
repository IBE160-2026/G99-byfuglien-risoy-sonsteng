# 2026-11-12 — UX: HTML-nøkkelmocker F1, F2 og F4 før BMAD UX Finalize

> **Status:** Utkastet ble laget av Claude Code ved slutten av økten. Sebastian Byfuglien har kontrollert og godkjent loggen 12. november 2026, etter gjennomgang med ChatGPT og tre faktakorrigeringer (se `CLAUDE.md` og `docs/ki-logg/README.md`).

- **Deltakere:** Sebastian Byfuglien
- **KI-verktøy:**
  - Claude Code med modellen Claude Opus 5.5 (`claude-opus-5-5`) i VS Code-utvidelsen. Det ble ikke startet noen ny BMAD-workflow, og ingen underagenter ble brukt. Claude Code fulgte BMAD-standarden for nøkkelskjermer (`.claude/skills/bmad-ux/assets/key-screens.md`). Memlogg-oppføringene ble skrevet med `_bmad/scripts/memlog.py` via `uv`. Claude Code kjørte skillen `sesjonslogg`, slik `CLAUDE.md` krever.
  - ChatGPT (OpenAI) som uavhengig kontrollagent. Ifølge promptene gikk Sebastian gjennom planen og HTML-filene med ChatGPT, og ChatGPT rendret F1, F2 og F4 i Chromium. F4 ble gjennomgått, men ikke endelig godkjent. ChatGPT gjorde ingen endringer i repositoryet.
  - Sebastian Byfuglien tok alle beslutningene. Gruppevedtaket om valgt kalenderår ble opplyst av Sebastian.
- **Kontrollert av:** Sebastian Byfuglien (godkjent 12. november 2026)

## Oppgave

Økten fortsatte den eksisterende BMAD UX-kjøringen på `ux/sebastian-ux-design` fra
`23148c7`. Målet var å forberede BMAD UX Finalize ved å lage statiske HTML-mocker
av nøkkelskjermer, slik BMAD-standarden krever. Ifølge planen skal fire mocker lages:
F1, F2, F4 og F7. F3, F5, F6 og F8 står foreløpig bare i spinene, og dette skal
bekreftes i dekningskontrollen under Finalize. Hver mock ble kontrollert av
Sebastian og ChatGPT før neste ble startet.

## Prompt (ordrett)

Loggen gjengir alle sju promptene som ble sendt til Claude Code 12. november, i
kronologisk rekkefølge og med uendret tekst. Ingen deler er kuttet.
Claude Codes svar mellom promptene er ikke tatt med. Promptene til ChatGPT og
ChatGPTs svar er heller ikke gjengitt.

| Nr. | Prompt |
|---|---|
| 1 | Oppstart og plan for HTML-mocker |
| 2 | Avklaringer etter ChatGPT-gjennomgang og F1-mocken |
| 3 | Rettelse av F1 for mindre PC-skjermer |
| 4 | Gruppevedtak om valgt kalenderår og rettelser i F1 |
| 5 | F2-mocken (månedsvisning) |
| 6 | Godkjenning av F2, memlogg og F4-mocken |
| 7 | Avslutning av økten (denne loggen) |

<details>
<summary><strong>Prompt 1 – Oppstart og plan for HTML-mocker</strong></summary>

> Vi starter en ny arbeidsøkt i IBE160-prosjektet Sambandet.
>
> Vi skal fortsette i den eksisterende BMAD UX-workflowen og forberede UX Finalize.
>
> **Prosjektstatus fra forrige arbeidsøkt:**
> - Repository: `IBE160-2026/G99-byfuglien-risoy-sonsteng`
> - Branch: `ux/sebastian-ux-design`
> - Siste commit: `23148c7c8242c0995c7ea5e2740596b22854072b`
> - Branchen var synkronisert med origin, og arbeidsområdet var rent.
> - Product Brief og PRD er ferdigstilt.
> - DESIGN.md og EXPERIENCE.md har `status: draft`.
> - Alle sju gjeldende Excalidraw-skisser er oppdatert og kontrollert.
> - KI-loggen for 11. november, del 1–4, er godkjent og pushet.
>
> **Åpne avhengigheter:**
> - OQ-7 må avklares før UX-dokumentene kan settes til `final`.
> - OQ-8 er en dokumentert arkitekturavhengighet som ikke blokkerer Finalize.
> - Projektor-, tastatur-, skjermleser- og klassifiseringstester er ikke gjennomført.
>
> **Oppgave i denne første runden:**
>
> 1. Kontroller branch, HEAD og Git-status.
> 2. Les relevante prosjektinstruksjoner i CLAUDE.md og BMAD UX-skillen.
> 3. Finn den eksisterende UX-workflowen og bekreft at vi kan fortsette der vi avsluttet.
> 4. Undersøk hvilke HTML-mocker BMAD Finalize krever, og hvilke eksisterende UX-skisser som skal brukes som grunnlag.
> 5. Foreslå en konkret og avgrenset arbeidsplan for å lage HTML-mockene.
>
> **Viktige begrensninger:**
> - Ikke start en ny UX-workflow.
> - Ikke endre filer.
> - Ikke lag HTML-mocker ennå.
> - Ikke start Finalize-prosessen automatisk.
> - Ikke endre Git-branch.
> - Ikke commit eller push.
> - Ikke start implementering.
> - Ikke sett dokumenter til `final`.
>
> Rapporter funnene og stopp. Jeg skal gjennomgå planen med ChatGPT før vi begynner å lage HTML-mockene.

</details>

<details>
<summary><strong>Prompt 2 – Avklaringer etter ChatGPT-gjennomgang og F1-mocken</strong></summary>

> Vi fortsetter dagens økt i Sambandet på branch `ux/sebastian-ux-design`.
>
> ChatGPT har gjennomgått arbeidsplanen for HTML-mocker. Vi følger planen med disse avklaringene:
>
> - Vi lager fire nøkkelmocker: F1, F2, F4 og F7.
> - F2 skal vise dagsoversikten som alternativ tilstand, ikke F3-modalen.
> - Vi bruker «Årshjul (arbeidstittel)» der produktnavnet vises.
> - F3, F5, F6 og F8 beholdes foreløpig som spine-only. Dette bekreftes i Finalize-dekningsgjennomgangen.
> - F6s ordinære opplastingsflyt er ikke avhengig av OQ-7; bare demo-modus er uavklart.
> - OQ-8 hindrer oss i å fastsette tekniske grenser, men vi kan vise en beregnet valideringsfeil som «120 tegn for mye» uten å angi maksimalgrensen.
>
> **Oppgave: Lag kun den første HTML-mocken – F1 årsvisning.**
>
> ### 1. Les relevant grunnlag
>
> Bruk:
> - Gjeldende F1 `.excalidraw`-skisse og PNG.
> - F1-seksjonene i DESIGN.md og EXPERIENCE.md.
> - Relevante gruppevedtak i UX-memloggen.
> - Godkjente design tokens og designretningen i `kombinert-retning-1.html`.
> - Kravene i `.claude/skills/bmad-ux/assets/key-screens.md`.
>
> Ikke les eller endre andre deler av prosjektet unødvendig.
>
> ### 2. Opprett F1-mocken
>
> Lag:
>
> `.working/key-f1-arsvisning.html`
>
> Følg eksisterende BMAD-krav:
> - Én selvstendig HTML-fil.
> - Inline CSS med systemfonter.
> - Ingen JavaScript eller nettverksavhengigheter.
> - Nettleserramme.
> - Kommentar øverst i style-seksjonen med henvisning til relevante spine-seksjoner.
> - Bruk eksisterende UX-layout og godkjente design tokens.
>
> **Hovedtilstand:**
> - Årshjul 2026 med 12 måneder.
> - Totalt antall aktiviteter per måned.
> - Maksimalt to kategorimerker per måned.
> - Restindikator «+N øvrige aktiviteter» der det er aktuelt.
> - Alltid synlig tegnforklaring med de ni godkjente kategoriene.
> - Mars-eksempelet skal være 20 aktiviteter: U 4, M 4 og +12 øvrige.
>
> **Alternativ tilstand:**
> - Pågående dokumentbehandling.
> - Korrekt statusindikator.
> - Opplasting sperret med forklaring.
> - Ikke introduser en ny demo-modus eller andre OQ-7-beslutninger.
>
> ### 3. Visuell kontroll
>
> - Gjengi HTML-filen i headless Chrome.
> - Lag en PNG-forhåndsvisning for gjennomgang, uten å opprette unødvendige permanente filer.
> - Kontroller at layouten samsvarer med gjeldende F1-skisse.
> - Kontroller at kategorikoder, tall og tegnforklaring er korrekte.
> - Kontroller at ingen gamle kategoriplassholdere finnes.
> - Kontroller farger, typografi og fokusmarkering mot UX-spesifikasjonen.
> - Kontroller at mocken ikke innfører nye UX-mønstre.
> - Kjør `git diff --check`.
>
> Dette er en statisk mock og ikke en gjennomført tilgjengelighets-, projektor- eller funksjonstest.
>
> ### 4. Begrensninger
>
> - Opprett kun F1-mocken.
> - Ikke lag F2, F4 eller F7 ennå.
> - Ikke endre eksisterende Excalidraw-skisser.
> - Ikke endre DESIGN.md, EXPERIENCE.md eller PRD.
> - Ikke start en ny BMAD UX-workflow.
> - Ikke sett dokumentene til `final`.
> - Ikke flytt filer til `mockups/` eller `wireframes/`.
> - Ikke ta nye produkt- eller arkitekturbeslutninger.
> - Ikke commit eller push.
> - Ikke opprett KI-logg nå.
> - Vent med UX-memlogg til mocken er gjennomgått og godkjent.
>
> ### 5. Rapporter og stopp
>
> Oppgi:
> 1. Hvilken fil som ble opprettet.
> 2. Hvordan F1-mocken samsvarer med skissen.
> 3. Hvor jeg finner HTML-filen og forhåndsvisningen.
> 4. Eventuelle avvik eller usikkerheter.
> 5. Resultatet av kontrollene.
> 6. Git-status.
>
> Stopp etter F1. Jeg skal kontrollere og godkjenne resultatet med ChatGPT før vi går videre.

</details>

<details>
<summary><strong>Prompt 3 – Rettelse av F1 for mindre PC-skjermer</strong></summary>

> Vi fortsetter arbeidet med F1 HTML-mocken i Sambandet.
>
> ChatGPT har gjennomgått den faktiske HTML-filen ved å rendre den i Chromium på både 1840 og 1366 px.
>
> **Resultat:**
> - Ved 1840 px ser både tilstand A og B riktige ut.
> - Ved 1366 px klippes deler av årshjulet, tegnforklaringen og forklaringsteksten under hjulet.
> - Årsaken er faste bredder i HTML/CSS kombinert med en nettleserramme som skjuler innhold utenfor rammen.
> - Månedsforkortelsene er akseptert.
> - Designet, kategoriene, tallene og tilstand B er ellers foreløpig godkjent.
>
> **Oppgave: Gjør én målrettet rettelse av F1-mockens visning på mindre PC-skjermer.**
>
> Arbeid bare med:
>
> `.working/key-f1-arsvisning.html`
>
> ### Krav
>
> 1. Behold det godkjente utseendet ved 1840 px.
> 2. Sørg for at begge tilstander kan vises uten avkuttede elementer ved 1366 px.
> 3. Behold årshjulet som hovedinnhold, med alle 12 måneder og de samme aktivitetsdataene.
> 4. Behold tegnforklaringen med alle ni kategorier.
> 5. Bruk eksisterende design tokens og respekter minste skriftstørrelser.
> 6. Ikke introduser nye UI-komponenter, navigasjonsregler eller designmønstre.
> 7. Unngå overlapp mellom månedstekst, kategorimerker og sektorlinjer.
> 8. Dersom dette ikke lar seg løse uten et nytt layoutvalg, stopp og presenter alternativene i stedet for å ta beslutningen selv.
>
> ### Kontroller
>
> Render tilstand A og B ved:
> - 1366 px
> - 1440 px
> - 1840 px
>
> Kontroller visuelt at alt er synlig, at ingen tekst klippes eller overlapper, og at bredskjermversjonen ikke har blitt dårligere.
>
> Kontroller også at valgt kalenderår er tydelig nok markert i samsvar med eksisterende designreferanser. Ikke innfør en ny markeringsstil uten grunnlag.
>
> Kjør `git diff --check` og kontroller Git-status.
>
> ### Begrensninger
>
> - Ikke endre Excalidraw-skissene.
> - Ikke endre DESIGN.md eller EXPERIENCE.md.
> - Ikke endre aktivitetsdata eller kategoriregler.
> - Ikke lag andre HTML-mocker.
> - Ikke commit eller push.
> - Ikke skriv ny memlogg eller KI-logg ennå.
> - Ikke start BMAD Finalize.
>
> Rapporter hva som ble endret, resultatet ved de tre skjermbreddene og eventuelle gjenværende problemer.
>
> Stopp etter rettelsen. Jeg skal gjennomgå F1 en siste gang før vi starter F2.

</details>

<details>
<summary><strong>Prompt 4 – Gruppevedtak om valgt kalenderår og rettelser i F1</strong></summary>

> Vi fortsetter UX Finalize-forberedelsene i Sambandet på branch `ux/sebastian-ux-design`.
>
> **Nytt gruppevedtak: Markering av valgt kalenderår i F1**
>
> Prosjektgruppen har godkjent alternativ B:
> - Valgt kalenderår vises med 2 px mørk kant og lys panelbakgrunn.
> - Bruk eksisterende design tokens og eksisterende stilprinsipper for valgt/aktiv tilstand.
> - Markeringen skal være nøytral og tydelig forskjellig fra primærknappen «Ny aktivitet».
> - Oransje brukes fortsatt bare til tastaturfokus.
> - Dette gjelder årsvelgeren i både tilstand A og B.
> - Ikke innfør nye navigasjonsregler eller komponenter.
>
> ### 1. Gjør to avgrensede rettelser
>
> Endre kun:
>
> `.working/key-f1-arsvisning.html`
>
> **Rettelse A – valgt kalenderår**
> - Oppdater CSS for gjeldende år (2026) i årsvelgeren.
> - Bruk 2 px mørk kant og lys panelbakgrunn.
> - Behold øvrige år og navigasjonsknapper uendret.
> - Behold året i sentrum av årshjulet.
>
> **Rettelse B – entallsform**
> - Endre «+1 øvrige aktiviteter» til «+1 øvrig aktivitet» i februar og november.
> - Gjør rettelsen i både tilstand A og B.
> - Behold alle kategoriantall og tilgjengelige navn uendret.
>
> ### 2. Kontroller resultatet
>
> Render HTML-mocken i headless Chrome ved:
> - 1366 px
> - 1440 px
> - 1840 px
>
> Kontroller begge tilstandene ved hver bredde.
>
> Bekreft at:
> 1. Valgt kalenderår er tydelig markert.
> 2. Markeringen ikke ser ut som en ekstra primærknapp.
> 3. Ingen elementer klippes eller overlapper.
> 4. Årshjulet og tegnforklaringen fortsatt vises riktig.
> 5. Mars fortsatt viser 20 aktiviteter, `U 4 · M 4 · +12 øvrige aktiviteter`.
> 6. Entallsformen er rettet i begge tilstander.
> 7. Ingen andre tekster, regler eller fiktive data er endret.
>
> Behold den tidligere skjermtilpasningen for 1366–1840 px.
>
> ### 3. Dokumenter vedtaket
>
> Når rettelsene er kontrollert, legg til én oppføring i eksisterende UX-memlogg med `memlog.py append`, i tråd med prosjektets regler.
>
> Dokumenter at gruppevedtaket om markering av valgt kalenderår er opplyst av Sebastian Byfuglien 12. november 2026.
>
> Beskriv kort:
> - Alternativ B og de vedtatte visuelle egenskapene.
> - At F1-mocken er oppdatert.
> - At entallsformen er språkvasket.
> - At kontrollen ved tre skjermbredder er visuell, ikke en projektor-, tastatur- eller skjermlesertest.
>
> Ikke endre tidligere memlogg-oppføringer.
>
> ### 4. Begrensninger
>
> - Ikke endre Excalidraw-skisser.
> - Ikke endre DESIGN.md, EXPERIENCE.md eller PRD.
> - Ikke opprett andre HTML-mocker.
> - Ikke start BMAD Finalize.
> - Ikke flytt filer til `mockups/`.
> - Ikke commit eller push.
> - Ikke opprett KI-logg eller sesjonslogg ennå.
>
> ### 5. Rapporter og stopp
>
> Oppgi:
> 1. Hvilke filer som ble endret.
> 2. Hvordan valgt kalenderår er markert.
> 3. Resultatet ved 1366, 1440 og 1840 px.
> 4. Om entallsformen er rettet.
> 5. Memlogg-oppføringen.
> 6. Git-status.
>
> Stopp etter kontrollen. Jeg skal gjennomgå resultatet med ChatGPT før vi godkjenner F1 endelig og starter F2.

</details>

<details>
<summary><strong>Prompt 5 – F2-mocken (månedsvisning)</strong></summary>

> Vi fortsetter UX Finalize-forberedelsene i Sambandet på eksisterende branch `ux/sebastian-ux-design`.
>
> **Status:**
> - HEAD: `23148c7`.
> - F1 HTML-mocken er nå godkjent av Sebastian etter gjennomgang med ChatGPT.
> - `.working/key-f1-arsvisning.html` er ny og ikke committet.
> - UX-`.memlog.md` har en ny oppføring om gruppevedtaket for valgt kalenderår.
> - Begge endringene skal bevares.
> - DESIGN.md og EXPERIENCE.md har fortsatt `status: draft`.
>
> **Oppgave: Lag kun HTML-mock nummer 2 – F2 Månedsvisning.**
>
> ### 1. Kontroller grunnlaget
>
> Les bare relevante deler av:
> - Gjeldende F2/F3 v3 Excalidraw-skisse og PNG i `.working/`.
> - F2-seksjonene i DESIGN.md og EXPERIENCE.md.
> - Relevante regler i UX-memloggen.
> - `.claude/skills/bmad-ux/assets/key-screens.md`.
> - Godkjente design tokens og F1 HTML-mocken for visuell konsistens.
>
> Bruk eksisterende skisse som fasit for layout. Ikke bruk historiske skisser som styrende grunnlag.
>
> ### 2. Lag F2-mocken
>
> Opprett:
>
> `.working/key-f2-manedsvisning.html`
>
> Følg samme BMAD-standard som for F1:
> - Selvstendig HTML med inline CSS og systemfonter.
> - Ingen JavaScript eller nettverksavhengigheter.
> - Nettleserramme og kommentar om styrende spine-seksjoner.
> - Godkjente design tokens.
> - Statisk illustrasjon, ikke fungerende applikasjon.
>
> **Hovedtilstand A – mars 2026:**
> - Månedsvisning for mars 2026.
> - Mandag som første ukedag og korrekte ISO-ukenummer.
> - Bruk de eksisterende 20 fiktive marsaktivitetene fra gjeldende F2/F3-skisse.
> - Vis aktivitetskoder etter vedtatte regler.
> - Maks to synlige aktiviteter per dag.
> - Vis «+N flere» ved flere aktiviteter samme dag.
> - Vis videreføring av aktiviteter over månedsskiftet i tråd med M6-1.
> - Behold navigasjon, layout og visuelle mønstre fra gjeldende F2-skisse.
>
> Ikke konstruer nye aktiviteter for å fylle kalenderen.
>
> **Alternativ tilstand B – dagsoversikt:**
> - Vis dagsoversikten som åpnes via «+N flere».
> - Bruk en dag og eksisterende aktiviteter fra den gjeldende F2/F3-skissen.
> - Dagsoversikten skal være **ikke-modal**.
> - Aktivitetstittel på første linje.
> - Datoer og kategorikode på neste linje.
> - Fullt kategorinavn skal være representert i tilgjengelig tekst.
> - Behold prinsippet om at dagsoversikten kan lukkes og fokus returneres til riktig utløser, men ikke implementer interaksjonen i den statiske mocken.
> - Ikke vis F3-modalen som alternativ tilstand.
>
> Dersom skissen ikke gir tilstrekkelig grunnlag for en realistisk dagsoversikt, rapporter hva som mangler i stedet for å finne på data.
>
> ### 3. Kontroller visningen
>
> Render begge tilstander i headless Chrome ved:
> - 1366 px
> - 1440 px
> - 1840 px
>
> Kontroller:
> 1. At hele kalenderen og relevant informasjon er synlig uten klipping eller uønsket horisontal scrolling.
> 2. At ukedager, datoer og ISO-uker er korrekte for mars 2026.
> 3. At aktivitetene er de samme som i den gjeldende F2/F3-skissen.
> 4. At månedsvisningen følger maks-to-regelen.
> 5. At «+N flere» og dagsoversikten er konsistente.
> 6. At kategori- og datovisning følger gruppevedtakene.
> 7. At tekst, merker og kontroller ikke overlapper.
> 8. At utformingen er konsistent med F1 og godkjente design tokens.
>
> Lag PNG-forhåndsvisninger i scratchpad utenfor repoet.
>
> Skill mellom visuell kontroll og faktisk funksjonalitets- eller tilgjengelighetstesting. Ikke påstå at tastatur, skjermleser eller projektor er testet.
>
> ### 4. Bevar eksisterende arbeid
>
> - Ikke endre eller overskriv F1-mocken.
> - Ikke endre eksisterende Excalidraw-skisser.
> - Ikke endre DESIGN.md, EXPERIENCE.md, PRD eller Product Brief.
> - Ikke lag F3, F4 eller F7-mocker.
> - Ikke start BMAD Finalize.
> - Ikke flytt filer til `mockups/` eller `wireframes/`.
> - Ikke ta nye produktbeslutninger.
> - Ikke commit eller push.
> - Ikke opprett KI-logg eller sesjonslogg nå.
> - Vent med ny UX-memlogg til F2 er gjennomgått og godkjent.
>
> Kjør `git diff --check` og kontroller at de eksisterende F1-endringene er bevart.
>
> ### 5. Rapporter og stopp
>
> Oppgi:
> 1. Filen som ble opprettet.
> 2. Hvilke eksisterende aktiviteter og UX-regler som er brukt.
> 3. Hvordan hovedtilstand A og alternativ tilstand B er utformet.
> 4. Resultatet av visuell kontroll ved de tre skjermbreddene.
> 5. Eventuelle avvik eller usikkerheter.
> 6. Git-status.
>
> Stopp etter F2. Jeg skal gjennomgå mocken med ChatGPT før vi godkjenner den og starter F4.

</details>

<details>
<summary><strong>Prompt 6 – Godkjenning av F2, memlogg og F4-mocken</strong></summary>

> Vi fortsetter UX Finalize-forberedelsene i Sambandet på branch `ux/sebastian-ux-design`.
>
> ChatGPT har kontrollert den faktiske F2 HTML-filen visuelt i Chromium ved 1366, 1440 og 1840 px.
>
> **Resultat:** F2 er godkjent som statisk HTML-mock. Ingen rettelser er nødvendige.
>
> ### 1. Dokumenter F2-kontrollen
>
> Legg til én kort hendelsesoppføring i eksisterende UX-memlogg, i tråd med prosjektets regler.
>
> Dokumenter:
> - F2-mocken er gjennomgått og godkjent i ChatGPTs visuelle kontroll.
> - Tilstand A viser mars 2026 og tilstand B viser ikke-modal dagsoversikt for 18. mars.
> - De 20 aktivitetene og «+N flere»-reglene er bevart.
> - Gjengivelse er kontrollert ved 1366, 1440 og 1840 px.
> - Projektor, tastatur, skjermleser og faktisk interaksjon er ikke testet.
>
> Dette er en kontrollhendelse, ikke et nytt gruppevedtak.
>
> ### 2. Lag HTML-mock nummer 3 – F4 aktivitetsskjema
>
> Opprett bare:
>
> `.working/key-f4-aktivitetsskjema.html`
>
> Les først:
> - Gjeldende F4 Excalidraw-skisse og PNG.
> - Relevante F4-seksjoner i DESIGN.md og EXPERIENCE.md.
> - Gjeldende UX-regler og M11-a-vedtak i UX-memloggen.
> - `.claude/skills/bmad-ux/assets/key-screens.md`.
> - F1- og F2-mockene for visuell konsistens.
>
> **Tilstand A – opprett aktivitet:**
> - Vis aktivitetsskjemaet som modal, i tråd med F4-skissen.
> - Vis de spesifiserte feltene og hvilke som er obligatoriske.
> - Bruk de ni godkjente kategoriene der kategorivalget illustreres.
> - Merknad er valgfritt.
> - Bruk eksisterende knappetekster, hjelpetekster, modalregler og design tokens.
> - Ikke finn på nye felter eller produktregler.
>
> **Tilstand B – ugyldig skjema:**
> - Vis den eksisterende feiloppsummeringen og feltfeilene fra F4.
> - Vis eksempel på merknad som overskrider en grense, slik som «120 tegn for mye».
> - Ikke fastsett noen maksimal tegngrense; OQ-8 er fortsatt åpen.
> - Behold regelen om at ugyldige merknader hindrer lagring, og at teksten aldri forkortes automatisk.
> - Vis riktig handling for å rette feil og forsøke lagring på nytt.
>
> ### 3. Følg BMAD-standarden
>
> - Én selvstendig HTML-fil.
> - Inline CSS og systemfonter.
> - Ingen JavaScript eller nettverkskall.
> - Nettleserramme.
> - Kommentar øverst i style-seksjonen med styrende spine-seksjoner.
> - Kun eksisterende UX-mønstre og godkjente design tokens.
> - Statisk illustrasjon, ikke fungerende applikasjon.
>
> ### 4. Visuell kontroll
>
> Render begge tilstander i headless Chrome ved 1366, 1440 og 1840 px.
>
> Kontroller:
> - At modalene vises i sin helhet.
> - At alle felter, feilmeldinger og knapper er lesbare.
> - At ingenting klippes eller overlapper.
> - At knapper, tekst og mellomrom følger eksisterende UX-regler.
> - At feilmeldingene er konsistente med DESIGN.md og EXPERIENCE.md.
> - At den ugyldige merknaden ikke forkortes automatisk.
> - At det ikke introduseres nye UX-beslutninger.
>
> Opprett PNG-forhåndsvisninger i scratchpad utenfor repoet.
>
> ### 5. Bevar eksisterende arbeid
>
> Eksisterende ucommittede endringer skal bevares:
> - UX-`.memlog.md`
> - `.working/key-f1-arsvisning.html`
> - `.working/key-f2-manedsvisning.html`
>
> Ikke endre F1 eller F2.
>
> Ikke endre Excalidraw-skisser, DESIGN.md, EXPERIENCE.md, PRD eller Product Brief.
>
> Ikke lag F7 ennå. Ikke start BMAD Finalize, flytt filer, opprett KI-logg, commit eller push.
>
> Vent med egen memlogg-oppføring om F4 til den er gjennomgått.
>
> ### 6. Rapporter og stopp
>
> Oppgi:
> 1. F4-filen som ble opprettet.
> 2. Hvordan tilstand A og B følger F4-skissen.
> 3. Hvilke felt- og valideringsregler som vises.
> 4. Resultatet av visuell kontroll ved de tre skjermbreddene.
> 5. Eventuelle avvik eller usikkerheter.
> 6. Git-status og bekreftelse på at F1 og F2 er bevart.
>
> Stopp etter F4. Jeg skal kontrollere HTML-filen med ChatGPT før neste steg.

</details>

<details>
<summary><strong>Prompt 7 – Avslutning av økten (denne loggen)</strong></summary>

> Vi avslutter arbeidsøkten 12. november 2026 i IBE160-prosjektet Sambandet.
>
> Vi skal ikke gjøre flere UX-endringer i kveld. Målet er å dokumentere økten og sikre at arbeidet enkelt kan gjenopptas i morgen.
>
> Repository: `IBE160-2026/G99-byfuglien-risoy-sonsteng`
> Branch: `ux/sebastian-ux-design`
> Siste kjente HEAD: `23148c7`
>
> ### 1. Kontroller status
>
> Kontroller Git-status og bekreft at følgende arbeid er bevart:
> - F1 HTML-mock – godkjent.
> - F2 HTML-mock – godkjent.
> - F4 HTML-mock – opprettet og visuelt gjennomgått, men IKKE endelig godkjent.
> - UX-memlogg – vedtak om F1 og kontrollhendelse for F2.
>
> ### 2. Avslutt dokumentasjonen
>
> Følg prosjektets `CLAUDE.md`, `AGENTS.md` og `docs/ki-logg/README.md`.
>
> Opprett nødvendig KI-logg for dagens arbeid og avslutt sesjonsloggen etter prosjektets eksisterende konvensjoner.
>
> Bruk faktiske prompts og resultater fra dagens økt. Ikke konstruer manglende prompttekst eller påstå at testing er utført når den ikke er det.
>
> Hold dokumentasjonen kort, men komplett nok til refleksjonsrapporten.
>
> Ikke start en kommando som automatisk utfører commit eller push.
>
> ### 3. Lag tydelig overlevering til neste økt
>
> Dokumenter følgende:
>
> **F4 – gjenstående arbeid:**
> 1. Endre synlig tegnteller i A fra `0 / [grense] tegn` til `0 tegn`.
> 2. Endre synlig tegnteller i B fra `[grense] + 120 / [grense] tegn` til `120 tegn over grensen`.
> 3. Erstatt `␣␣␣` i Ansvarsområde med tre faktiske mellomrom. Behold feilmeldingen.
> 4. Kontroller F4 visuelt på nytt ved 1366, 1440 og 1840 px.
> 5. Etter godkjenning: legg inn F4-kontrollhendelse i memloggen.
>
> **Etter F4:**
> - Lag F7 HTML-mock.
> - Deretter vurderes BMAD UX Finalize.
> - OQ-7 er fortsatt en sperre for `status: final`.
> - Ikke utfør nye produktbeslutninger uten godkjenning.
>
> ### 4. Stopp før Git-lagring
>
> Kjør `git status` og `git diff --check`.
>
> Ikke endre HTML-mockene, UX-spinene eller Excalidraw-skissene.
>
> IKKE utfør commit eller push ennå.
>
> Rapporter:
> - Hva som er dokumentert.
> - Alle endrede og nye filer.
> - Git-status og branch.
> - Eventuelle problemer.
> - En kort oppsummering som kan brukes til oppstart i morgen.
>
> Stopp for menneskelig gjennomgang før commit og push.

</details>

## Hva KI leverte

- **Plan (prompt 1):** Claude Code kontrollerte branch, HEAD og Git-status, leste `CLAUDE.md` og BMAD UX-skillen og fant den eksisterende arbeidsmappen. Svaret var en plan for HTML-mockene som Finalize krever. Ingen filer ble endret.
- **F1 Årsvisning:** [`key-f1-arsvisning.html`](../../_bmad-output/planning-artifacts/ux-designs/ux-G99-byfuglien-risoy-sonsteng-2026-11-02/.working/key-f1-arsvisning.html) (prompt 2–4).
  - Tilstand A er årshjulet 2026 med tolv måneder, antall per måned, kategorimerker og tegnforklaring.
  - Tilstand B viser en pågående gjennomgang: indikatorstripen vises, og «Last opp dokument» er sperret med synlig forklaring.
  - Prompt 3: mocken ble tilpasset for 1366 px med smalere marger og tegnforklaring. Hjulet ble ikke krympet.
  - Prompt 4: markeringen av valgt kalenderår ble endret etter gruppevedtaket (alternativ B), og «+1 øvrige aktiviteter» ble språkvasket til «+1 øvrig aktivitet».
- **F2 Månedsvisning:** [`key-f2-manedsvisning.html`](../../_bmad-output/planning-artifacts/ux-designs/ux-G99-byfuglien-risoy-sonsteng-2026-11-02/.working/key-f2-manedsvisning.html) (prompt 5).
  - Tilstand A er mars 2026 med ISO-uke 9–14 og de 20 fiktive aktivitetene fra F2/F3 v3-skissen. Maks to blokker vises per dag, med «+1 flere» og «+3 flere».
  - Tilstand B er den ikke-modale dagsoversikten for 18. mars.
- **F4 Aktivitetsskjema:** [`key-f4-aktivitetsskjema.html`](../../_bmad-output/planning-artifacts/ux-designs/ux-G99-byfuglien-risoy-sonsteng-2026-11-02/.working/key-f4-aktivitetsskjema.html) (prompt 6).
  - Tilstand A er en tom modal over dempet månedsvisning, med innfelt datovelger og kategoriliste med de ni kategoriene.
  - Tilstand B viser lagring stoppet: feiloppsummering, fire feltfeil og en merknad over grensen («120 tegn for mye»). Merknaden forkortes ikke, og ingen grense er fastsatt.
  - Bakgrunnen er F2 tilstand A, kopiert uendret med skript.
- **UX-memlogg:** to nye oppføringer i `.memlog.md`.
  - Prompt 4: gruppevedtaket om valgt kalenderår i F1.
  - Prompt 6: kontrollhendelsen for F2. Den er registrert som hendelse, ikke som vedtak.
- **Denne loggen og sesjonsloggen** (prompt 7).

## Hva vi endret og hvorfor

- **F1, klipping ved 1366 px:** ChatGPTs rendring viste at mocken ble klippet ved 1366 px. Sebastian ba om en målrettet rettelse uten nye mønstre (prompt 3).
- **F1, valgt kalenderår:** gruppen valgte alternativ B, nøytral valgt/aktiv-markering (prompt 4).
- **«+1 øvrig aktivitet»:** entallsformen ble rettet samtidig med kalenderårsmarkeringen.
- **F2 og F4:** Sebastian og ChatGPT godkjente F2 uten rettelser (prompt 6).
- **F4 er ikke godkjent.** ChatGPT foreslo tre rettelser etter gjennomgangen av F4, og de ble lagt til neste arbeidsøkt (prompt 7). Dette er ikke et formelt gruppevedtak:
  - tegnteller i A: «0 tegn»
  - tegnteller i B: «120 tegn over grensen»
  - tre faktiske mellomrom i stedet for «␣␣␣»
- **Beholdt:** ingen spines, skisser, PRD eller Product Brief ble endret. Ingen nye produktbeslutninger ble tatt av KI.

## Testing

Det ble ikke testet noen fungerende applikasjon. Kontrollene gjaldt statiske HTML-mocker uten JavaScript. Dette ble faktisk kjørt:

- **Visuell kontroll i headless Chrome (Claude Code):** hver mock ble rendret ved 1366, 1440 og 1840 px. PNG-ene ble lagret i scratchpad utenfor repoet.
- **Måling i nettleseren:** layouten ble målt med et midlertidig skript i en kopi utenfor repoet, og kopien ble slettet etterpå.
  - Kontrollert: horisontal scroll, klipping, overlapp, overflytende tekst og klikkmål på minst 44 px.
  - I F2 ble det også kontrollert at det er maks to blokker per dag.
  - I F4 ble det kontrollert at merknadsfeltet viser hele teksten.
- **Kontroll av innholdet i filene:** ingen `<script>`, eksterne lenker, `url()` eller `@import`, og ingen «Kat.». Fargene ble sammenlignet med tokenene.
- **`git diff --check`:** exit 0 etter hvert steg.
- **ChatGPT (ifølge promptene og Sebastians opplysninger):** rendret F1 ved 1840 og 1366 px, og F2 og F4 ved 1366, 1440 og 1840 px i Chromium. F4 ble ikke endelig godkjent.

**Ikke testet:** projektor, tastatur, skjermleser og faktisk interaksjon. Mockene har ingen JavaScript. F4 er ikke kontrollert på nytt etter de foreslåtte rettelsene, fordi rettelsene ikke er gjort ennå.
