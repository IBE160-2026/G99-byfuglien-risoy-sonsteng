# 2026-11-13 — UX: F4 og F7 godkjent, Finalize-forberedelser og språkvask

> **Status:** Utkastet ble laget av Claude Code ved slutten av økten. Sebastian Byfuglien har kontrollert og godkjent loggen 13. november 2026, etter gjennomgang med ChatGPT (se `CLAUDE.md` og `docs/ki-logg/README.md`).

- **Deltakere:** Sebastian Byfuglien
- **KI-verktøy:**
  - Claude Code med modellen Claude Opus 5.5 (`claude-opus-5-5`) i VS Code-utvidelsen. Den eksisterende BMAD UX-kjøringen ble videreført; ingen ny BMAD-workflow ble startet, og ingen underagenter ble brukt. Claude Code fulgte BMAD UX-skillen (`.claude/skills/bmad-ux/`) og leste `bmad-review` med lensene `structure` og `prose`; lensene ble kjørt sekvensielt i økten, uten underagenter, og ingen rapportfil ble skrevet. Memlogg-oppføringene ble skrevet med `_bmad/scripts/memlog.py` via `uv`. Sesjonslogg og `issues.md` ble oppdatert etter formatet i skillen `sesjonslogg`, men ikke committet, fordi Sebastian ba om at ingenting skulle committes før gjennomgang.
  - ChatGPT (OpenAI) som uavhengig kontrollagent. Ifølge promptene gikk Sebastian gjennom hver rapport med ChatGPT før neste steg, og ChatGPT rendret F7 A og B i Chromium ved 1366, 1440 og 1840 px (prompt 4). Prompt 12 inneholder ChatGPTs vurdering, som Sebastian limte inn sammen med neste oppgave. ChatGPT gjorde ingen endringer i repositoryet.
  - Sebastian Byfuglien tok alle beslutningene. Gruppevedtakene 151–154 og 156 ble bekreftet av Sebastian på vegne av prosjektgruppen; det finnes ikke møtereferat i repoet.
- **Kontrollert av:** Sebastian Byfuglien (godkjent 13. november 2026)

## Oppgave

Økten fortsatte den eksisterende BMAD UX-kjøringen på `ux/sebastian-ux-design` fra `02cb630`. Målene var å fullføre og godkjenne F4-mocken, lage og godkjenne den siste nøkkelmocken (F7), sikre mockene i Git, og deretter forberede BMAD UX Finalize: dekningskontroll, organisering av godkjente artefakter, konsolidering av spinene, BMAD-review og språkvask. Formell Finalize er ikke gjennomført, fordi OQ-7 fortsatt blokkerer `status: final`.

## Prompt (ordrett)

Loggen gjengir alle 14 promptene som ble sendt til Claude Code 13. november, i kronologisk rekkefølge og med uendret tekst. Ingen deler er kuttet. Claude Codes svar mellom promptene er ikke tatt med. Promptene til ChatGPT og ChatGPTs svar er ikke gjengitt, bortsett fra det Sebastian limte inn i prompt 12.

| Nr. | Prompt |
|---|---|
| 1 | Oppstart og read-only-kontroll |
| 2 | Tre rettelser i F4-mocken |
| 3 | F4 godkjent, memlogg og F7-mocken |
| 4 | To rettelser i F7-mocken |
| 5 | F7 godkjent, memlogg og plan for Finalize (read-only) |
| 6 | Commit og push av F4 og F7 |
| 7 | Dekningskontroll og flytting til `mockups/` og `wireframes/` |
| 8 | Konsolidering av DESIGN.md og EXPERIENCE.md |
| 9 | Valgt kalenderår, memlogg-referanser og BMAD-review (read-only) |
| 10 | Navigasjonskart, typografi i F7, Layout og metadata |
| 11 | Fire gruppevedtak (151–154) |
| 12 | ChatGPT-vurdering, change-oppføring og plan for språkvask |
| 13 | Gruppevedtak B1–B4 og språkvask A1–A12 |
| 14 | Sluttkontroll og logger (denne loggen) |

<details>
<summary><strong>Prompt 1 – Oppstart og read-only-kontroll</strong></summary>

> Vi starter en ny arbeidsøkt 13. november 2026 i IBE160-prosjektet Sambandet.
>
> Vi fortsetter i eksisterende BMAD UX-workflow, ikke en ny kjøring.
>
> **Prosjektstatus fra forrige økt:**
> - Repository: `IBE160-2026/G99-byfuglien-risoy-sonsteng`
> - Branch: `ux/sebastian-ux-design`
> - Siste commit: `02cb630`
> - Commit er pushet til origin, og arbeidsområdet var rent.
> - Product Brief og PRD er ferdigstilt.
> - DESIGN.md og EXPERIENCE.md har `status: draft`.
> - F1 og F2 HTML-mocker er godkjent.
> - F4 HTML-mock er opprettet og visuelt gjennomgått, men ikke endelig godkjent.
> - F7 HTML-mock er ikke startet.
> - KI-logg og sesjonslogg for 12. november er godkjent og pushet.
>
> **Første oppgave – READ ONLY:**
>
> 1. Bekreft riktig branch, HEAD og Git-status.
> 2. Les relevante prosjektinstruksjoner i `CLAUDE.md` og `AGENTS.md`.
> 3. Les siste sesjonslogg og `issues.md`.
> 4. Finn eksisterende BMAD UX-workflow.
> 5. Kontroller at F1, F2 og F4 HTML-mockene ligger på riktig sted.
> 6. Bekreft de tre gjenstående F4-rettelsene:
>    - Tilstand A: `0 / [grense] tegn` → `0 tegn`.
>    - Tilstand B: `[grense] + 120 / [grense] tegn` → `120 tegn over grensen`.
>    - Tilstand B: erstatt `␣␣␣` i Ansvarsområde med tre faktiske mellomrom, og behold feilmeldingen.
>
> **Begrensninger:**
> - Ikke endre filer ennå.
> - Ikke start ny BMAD-workflow.
> - Ikke endre branch.
> - Ikke opprett nye mocker.
> - Ikke start Finalize.
> - Ikke commit eller push.
> - Ikke opprett logger i denne kontrollrunden.
>
> Rapporter kort:
> - Git-status.
> - Bekreftelse på eksisterende workflow og filer.
> - Eventuelle avvik.
> - Konkret forslag til hvordan de tre F4-rettelsene skal utføres og kontrolleres.
>
> Stopp etter rapporten. Jeg skal gjennomgå den med ChatGPT før vi gjør endringer.

</details>

<details>
<summary><strong>Prompt 2 – Tre rettelser i F4-mocken</strong></summary>

> Vi fortsetter arbeidsøkten 13. november 2026 i Sambandet.
>
> Read-only-kontrollen er gjennomgått og godkjent av ChatGPT.
>
> **Oppgave: Fullfør de tre gjenstående rettelsene i F4 HTML-mocken.**
>
> Arbeid kun i:
>
> `_bmad-output/planning-artifacts/ux-designs/ux-G99-byfuglien-risoy-sonsteng-2026-11-02/.working/key-f4-aktivitetsskjema.html`
>
> ### 1. Rett tegntellerne
>
> **Tilstand A:**
> - Endre `0 / [grense] tegn` til `0 tegn`.
>
> **Tilstand B:**
> - Endre `[grense] + 120 / [grense] tegn` til `120 tegn over grensen`.
> - Behold eksisterende feilmelding om 120 tegn for mye.
> - Behold hele merknadsteksten uten forkorting.
>
> Dette er illustrasjoner av tegnantall og validering, ikke en beslutning om maksimal tegngrense. OQ-8 er fortsatt åpen.
>
> ### 2. Rett feltet Ansvarsområde
>
> I tilstand B:
> - Erstatt `value="␣␣␣"` med nøyaktig tre vanlige mellomrom: `value="   "`.
> - Fjern klassen `vis-mellomrom` og CSS-regelen som bare brukes av denne.
> - Behold `aria-invalid`, `aria-describedby` og feilmeldingen.
> - Feltet skal se tomt ut, selv om det inneholder tre mellomrom.
>
> ### 3. Oppdater tilhørende forklaringer
>
> Oppdater kun kommentarene og tilstandsnotatene som ellers ville blitt feilaktige:
> - Kommentaren om OQ-8 øverst i filen.
> - Tilstandsnotatet under A.
> - Tilstandsnotatet under B.
>
> Forklar at tegntellerne ikke fastsetter en maksimalgrense, og at Ansvarsområde i B inneholder tre faktiske mellomrom.
>
> Ikke endre andre tekster eller UX-regler.
>
> ### 4. Kvalitetskontroll
>
> Render begge tilstander i headless Chrome ved:
> - 1366 px
> - 1440 px
> - 1840 px
>
> Kontroller at:
> 1. Begge tilstander vises uten klipping eller uønsket horisontal scrolling.
> 2. Ingen felt, knapper eller feilmeldinger overlapper.
> 3. Tegntellerne viser de nye formuleringene.
> 4. Tilstand B fortsatt har fire valideringsfeil.
> 5. Ansvarsområde ser tomt ut, men inneholder tre mellomrom.
> 6. Alle ni kategorier og eksisterende aktivitetsdata er uendret.
> 7. Modalens utforming og fokusring er bevart.
>
> Kontroller at de gamle symbolene og den ubrukte CSS-klassen er fjernet.
>
> Kjør `git diff --check`, kontroller LF-linjeskift og vis `git diff --stat`.
>
> Dette er kun visuell kontroll av en statisk mock. Ikke påstå at prosjektor, tastatur, skjermleser eller interaksjon er testet.
>
> ### 5. Begrensninger
>
> - Ikke endre F1 eller F2.
> - Ikke endre DESIGN.md, EXPERIENCE.md, PRD eller Excalidraw-skisser.
> - Ikke oppdater memlogg, KI-logg, issues.md eller sesjonslogg nå.
> - Ikke lag F7 ennå.
> - Ikke start BMAD Finalize.
> - Ikke commit eller push.
>
> ### 6. Rapporter og stopp
>
> Rapporter kort:
> 1. Hvilke rettelser som ble utført.
> 2. Resultatet ved de tre skjermbreddene.
> 3. Eventuelle gjenværende avvik.
> 4. Git-status.
>
> Stopp etter rettelsen. F4 skal gjennomgås med ChatGPT før endelig godkjenning.

</details>

<details>
<summary><strong>Prompt 3 – F4 godkjent, memlogg og F7-mocken</strong></summary>

> Vi fortsetter arbeidsøkten 13. november 2026 i Sambandet.
>
> Branch: `ux/sebastian-ux-design`
> Siste commit: `02cb630`
>
> **Status:**
> - F1 er godkjent.
> - F2 er godkjent.
> - F4 er nå godkjent som statisk HTML-mock etter tre målrettede rettelser.
> - F7 er den siste planlagte HTML-mocken før BMAD UX Finalize.
> - F4-endringene ligger foreløpig ucommittet og skal bevares.
>
> ### 1. Dokumenter godkjenningen av F4
>
> Legg til én kort kontrollhendelse i eksisterende UX-`.memlog.md` med prosjektets vanlige `memlog.py append`.
>
> Dokumenter:
> - F4 er gjennomgått og godkjent som statisk HTML-mock 13. november 2026.
> - A viser opprettelse av aktivitet, og B viser fire valideringsfeil.
> - Tegntellerne er språkvasket uten å fastsette OQ-8-grensen.
> - Ansvarsområde med bare mellomrom vises nå realistisk som et tilsynelatende tomt felt.
> - Visuell kontroll i headless Chrome er gjennomført ved 1366, 1440 og 1840 px.
> - Projektor, tastatur, skjermleser og faktisk interaksjon er ikke testet.
> - Dette er en kontrollhendelse, ikke et nytt gruppevedtak.
>
> Behold tidligere memlogg-oppføringer uendret.
>
> ### 2. Lag den siste HTML-mocken – F7 KI-gjennomgang
>
> Opprett:
>
> `.working/key-f7-gjennomgang.html`
>
> Bruk den eksisterende UX-workflowen.
>
> **Les først:**
> - Gjeldende `flow-f7-gjennomgang-v3-2026-11-03.excalidraw` og tilhørende PNG.
> - F7-seksjonene i DESIGN.md og EXPERIENCE.md.
> - Relevante gruppevedtak i UX-memloggen.
> - `.claude/skills/bmad-ux/assets/key-screens.md`.
> - F1, F2 og F4 for visuell konsistens.
>
> Ikke bruk historiske skisser som styrende grunnlag.
>
> ### 3. Innhold i F7-mocken
>
> **Tilstand A – aktiv KI-gjennomgang**
>
> Vis den etablerte F7-layouten med:
> - Gjeldende forslag og fremdriftsindikator.
> - Felt og feltstatus slik skissen spesifiserer.
> - Kildeutdrag/dokumentasjon som brukeren kan kontrollere mot forslaget.
> - Tydelig visning av usikker eller manglende informasjon.
> - Mulighet for å illustrere redigering, godkjenning og avvisning i henhold til eksisterende UX-regler.
> - De ni vedtatte kategoriene der kategorivalg vises.
> - Eksisterende navigasjon og kontrollhandlinger.
>
> Bruk bare godkjente fiktive data fra gjeldende F7-skisse og UX-dokumentasjonen. Ikke konstruer nye forslag eller kildesitater.
>
> **Tilstand B – godkjenning blokkert**
>
> Illustrer den relevante feil- eller sperretilstanden fra den gjeldende F7-skissen:
> - Vis hvorfor forslaget ikke kan godkjennes.
> - Vis hvilke opplysninger brukeren må rette eller kontrollere.
> - Vis sperrede handlinger med forklaring.
> - Behold muligheten til å rette eller avvise i tråd med UX-spesifikasjonen.
> - Ikke innfør nye valideringsregler.
>
> Dersom skissen viser en annen viktig alternativ tilstand enn dette, følg skissen og forklar avviket i rapporten.
>
> ### 4. BMAD-krav
>
> - Én selvstendig HTML-fil.
> - Inline CSS, systemfonter og nettleserramme.
> - Ingen JavaScript eller nettverksavhengigheter.
> - Kommentar i style-seksjonen med henvisning til styrende spine-seksjoner.
> - Én hovedtilstand og én relevant alternativ tilstand.
> - Eksisterende design tokens, typografi, knapper og fokusprinsipper.
> - Ingen nye UX-mønstre eller produktbeslutninger.
>
> Husk:
> - KI-forslag er ikke lagrede aktiviteter før den vedtatte lagringsflyten er fullført.
> - Ikke introduser «Godkjenn alle».
> - Ikke introduser demo-modus eller løs OQ-7.
> - Ikke fastsett nye OQ-8-grenser.
> - Ikke påstå at KI har kontrollert informasjon som den ikke har kontrollert.
> - Behold godkjennings- og avvisningsreglene fra spinene.
>
> ### 5. Visuell kontroll
>
> Render begge tilstander i headless Chrome ved:
> - 1366 px
> - 1440 px
> - 1840 px
>
> Kontroller at:
> 1. Alle viktige felt, knapper og kildeutdrag er synlige og lesbare.
> 2. Ingen tekst eller komponenter klippes eller overlapper.
> 3. Fremdrift, feltstatus og sperrede handlinger samsvarer med gjeldende F7-skisse.
> 4. Kategoriene og eksempeldataene stemmer med UX-dokumentasjonen.
> 5. Ingen uavklarte beslutninger fremstilles som avgjort.
> 6. Den visuelle utformingen er konsistent med F1, F2 og F4.
>
> Lag PNG-forhåndsvisninger utenfor repoet.
>
> Skill mellom visuell kontroll og faktisk testing av interaksjon, tastatur, skjermleser eller projektor.
>
> ### 6. Begrensninger
>
> - Ikke endre F1, F2 eller F4.
> - Ikke endre Excalidraw-skisser.
> - Ikke endre DESIGN.md, EXPERIENCE.md, PRD eller Product Brief.
> - Ikke oppdater `issues.md`, KI-logg eller sesjonslogg i denne runden.
> - Ikke start BMAD Finalize.
> - Ikke flytt filer til `mockups/` eller `wireframes/`.
> - Ikke commit eller push.
>
> ### 7. Rapporter og stopp
>
> Oppgi:
> 1. F4-kontrollhendelsen i memloggen.
> 2. Filen som ble opprettet for F7.
> 3. Hvordan F7 tilstand A og B følger gjeldende skisse.
> 4. Hvilke data og UX-regler som er brukt.
> 5. Resultatet av visuell kontroll ved de tre skjermbreddene.
> 6. Eventuelle avvik eller beslutninger som krever avklaring.
> 7. Git-status.
>
> Kjør `git diff --check` og bekreft at den godkjente F4-endringen er bevart.
>
> Stopp etter F7. Jeg skal gjennomgå HTML-filen med ChatGPT før videre arbeid.

</details>

<details>
<summary><strong>Prompt 4 – To rettelser i F7-mocken</strong></summary>

> Vi fortsetter Sambandet på `ux/sebastian-ux-design`.
>
> ChatGPT har gjennomgått den faktiske F7 HTML-mocken og rendret A og B i Chromium ved 1366, 1440 og 1840 px.
>
> Layouten, innholdet, kildeutdragene og valideringsstatusene er tilfredsstillende. Før godkjenning ønsker vi to små rettelser.
>
> Endre kun `.working/key-f7-gjennomgang.html`.
>
> ### 1. Synlig fokus på skjemafelt
>
> CSS fjerner i dag standard fokusmarkering fra `.felt`, men definerer ikke `:focus-visible` for skjemafeltene.
>
> Legg til fokusmarkering for tekstfelt og tekstområder ved tastaturfokus, med de allerede vedtatte fokustokenene:
> - 3 px oransje fokusring
> - 3 px avstand
> - hvit offset
>
> Ikke endre feltets utseende når det ikke har fokus.
>
> Ikke legg inn en permanent/statisk fokusring i A eller B. Skissen spesifiserer ikke innledende fokusplassering.
>
> ### 2. Presiser de sju forslagene som ikke er vist
>
> Erstatt teksten `… 7 til (rull: 9–15)` med en kort og tydelig formulering som forteller at sju forslag ikke er vist i den statiske mocken.
>
> Oppdater tilstandsnotatet slik at det skiller mellom:
> - Den statiske mocken, som bare illustrerer forslag 1–8.
> - Den planlagte applikasjonen, der listen kan rulles for å vise resten.
>
> Ikke konstruer forslag 9–15, og ikke legg til ny funksjonalitet.
>
> ### 3. Kontroll
>
> Gjengi begge tilstander ved 1366, 1440 og 1840 px.
>
> Kontroller:
> - Ingen klipping, overlapp eller uønsket horisontal scrolling.
> - Programmatisk fokus på et tekstfelt gir synlig oransje fokusring.
> - Alle eksisterende forslag, tellerverdier, kildeutdrag, feltstatus og sperrede handlinger er uendret.
> - Endringene er begrenset til F7-filen.
>
> Kjør `git diff --check`, og kontroller LF-linjeskift.
>
> ### Begrensninger
>
> Ikke endre F1, F2, F4 eller UX-memloggen. Den godkjente F4-endringen og eksisterende F4-kontrollhendelse skal bevares.
>
> Ikke start Finalize, oppdater logger eller utfør commit/push.
>
> Rapporter kort hva som ble endret, kontrollresultatene og Git-status. Stopp for gjennomgang med ChatGPT.

</details>

<details>
<summary><strong>Prompt 5 – F7 godkjent, memlogg og plan for Finalize (read-only)</strong></summary>

> Vi fortsetter arbeidsøkten 13. november 2026 i IBE160-prosjektet Sambandet.
>
> Branch: `ux/sebastian-ux-design`
> Siste commit: `02cb630`
>
> **Status:**
> - Alle fire HTML-nøkkelmocker (F1, F2, F4 og F7) er nå godkjent som statiske illustrasjoner etter gjennomgang med ChatGPT.
> - F4-rettelsene og F4-kontrollhendelsen ligger ucommittet.
> - F7 er en ny, ikke-sporet HTML-fil.
> - DESIGN.md og EXPERIENCE.md har fortsatt `status: draft`.
> - OQ-7 er fortsatt uavklart og blokkerer `status: final`.
>
> ### 1. Dokumenter F7-godkjenningen
>
> Legg til nøyaktig én kontrollhendelse (`event`) i eksisterende UX-`.memlog.md` med prosjektets vanlige `memlog.py append`.
>
> Dokumenter:
> - F7 HTML-mocken er gjennomgått og godkjent 13. november 2026 som statisk illustrasjon.
> - A viser gjennomgang med synlig forslagsoversikt, B viser samme forslag med oversikten skjult.
> - Begge viser blokkerende feltfeil, usikker kategori og kildeutdrag med verifiseringsstatus.
> - «Godkjenn» og «Gå til oppsummering» er sperret med synlige begrunnelser.
> - Forslag 9–15 er ikke konstruert i mocken.
> - Fokusmarkering for skjemafelt er korrigert.
> - Visuell kontroll i headless Chrome er gjennomført ved 1366, 1440 og 1840 px.
> - Faktisk interaksjon, tastaturbetjening, skjermleser og projektor er ikke testet.
> - Godkjenningen er en kontrollhendelse, ikke et nytt gruppevedtak.
>
> Behold tidligere memloggoppføringer uendret. Sikre LF-linjeskift.
>
> ### 2. Forbered BMAD UX Finalize – READ ONLY
>
> Les gjeldende BMAD UX-skill, relevante Finalize-instruksjoner og eksisterende UX-dokumentasjon.
>
> Ikke kjør Finalize ennå.
>
> Undersøk og rapporter:
>
> 1. Hvilke konkrete steg den eksisterende workflowen krever for Finalize.
> 2. Hvilke deler av DESIGN.md og EXPERIENCE.md som må ferdigstilles.
> 3. Hvordan de fire HTML-mockene skal flyttes eller organiseres i `mockups/`.
> 4. Hvordan de sju gjeldende Excalidraw-skissene og tilhørende PNG-er skal organiseres i `wireframes/`.
> 5. Hvilke filreferanser som må oppdateres ved flytting, uten å endre dem ennå.
> 6. Hvordan F1–F8 skal dekkes i sluttkontrollen, med F1, F2, F4 og F7 som HTML-mocker og øvrige flyter dokumentert i spinene/skissene.
> 7. Hvilken konkret beslutning OQ-7 krever før dokumentene kan få `status: final`.
> 8. Hvilke andre åpne spørsmål som må dokumenteres, og hvilke som eventuelt blokkerer Finalize.
>
> Skill tydelig mellom:
> - Allerede godkjente UX-beslutninger.
> - Dokumenterte, åpne tekniske avhengigheter.
> - Beslutninger som krever godkjenning fra prosjektgruppen.
>
> Ikke foreslå nye funksjoner eller løs åpne spørsmål på egen hånd.
>
> ### 3. Begrensninger
>
> - Ikke endre F1, F2, F4 eller F7.
> - Ikke endre Excalidraw-skisser eller PNG-er.
> - Ikke endre DESIGN.md, EXPERIENCE.md, PRD eller Product Brief.
> - Ikke flytt eller gi nytt navn til filer ennå.
> - Ikke endre `status: draft`.
> - Ikke oppdater KI-logg, sesjonslogg eller issues.md i denne runden.
> - Ikke start ny BMAD-workflow.
> - Ikke commit eller push.
>
> ### 4. Kontroller og rapporter
>
> Kjør `git status` og `git diff --check`.
>
> Bekreft at:
> - Den godkjente F4-endringen er bevart.
> - Den nye F7-filen er bevart.
> - Memloggen inneholder både F4- og F7-kontrollhendelsen.
> - Ingen andre filer er endret.
>
> Lever en konkret, nummerert arbeidsplan for BMAD UX Finalize med eventuelle beslutningspunkter tydelig markert.
>
> Stopp etter rapporten. Planen skal gjennomgås med ChatGPT før videre endringer.

</details>

<details>
<summary><strong>Prompt 6 – Commit og push av F4 og F7</strong></summary>

> Vi fortsetter arbeidet med Sambandet 13. november 2026.
>
> ChatGPT har gjennomgått og godkjent planen for BMAD UX Finalize, men vi skal først sikre det ferdige mockarbeidet i Git.
>
> **Jeg godkjenner at F4- og F7-mockene og de tilhørende UX-kontrollhendelsene committes og pushes.**
>
> Repository: `IBE160-2026/G99-byfuglien-risoy-sonsteng`
> Branch: `ux/sebastian-ux-design`
> Forventet HEAD: `02cb630`
>
> ### 1. Kontroller før commit
>
> Bekreft:
> - Riktig branch og HEAD.
> - F1 og F2 er fortsatt uendret.
> - F4 inneholder de tre godkjente rettelsene.
> - F7 inneholder de to godkjente rettelsene: `:focus-visible` for skjemafelt og korrekt forklaring av forslag 9–15.
> - UX-memloggen inneholder kontrollhendelsene for F4 og F7.
> - DESIGN.md og EXPERIENCE.md har `status: draft`.
>
> Bare følgende tre filer skal inngå i commiten:
>
> 1. `_bmad-output/planning-artifacts/ux-designs/ux-G99-byfuglien-risoy-sonsteng-2026-11-02/.memlog.md`
> 2. `_bmad-output/planning-artifacts/ux-designs/ux-G99-byfuglien-risoy-sonsteng-2026-11-02/.working/key-f4-aktivitetsskjema.html`
> 3. `_bmad-output/planning-artifacts/ux-designs/ux-G99-byfuglien-risoy-sonsteng-2026-11-02/.working/key-f7-gjennomgang.html`
>
> Stopp hvis det finnes uventede endringer som kan påvirke commiten.
>
> ### 2. Commit og push
>
> - Stage kun de tre nevnte filene.
> - Kontroller staged diff, inkludert den nye F7-filen.
> - Kjør `git diff --cached --check`.
> - Opprett én commit med meldingen:
>
> `docs(ux): approve F4 and F7 key screen mockups`
>
> - Push til `origin/ux/sebastian-ux-design`.
>
> Ikke merge, rebase eller bytt branch.
>
> ### 3. Kontroller resultatet
>
> Rapporter:
> - Commit-hash.
> - Hvilke filer som ble committet.
> - At push var vellykket.
> - At lokal branch er synkronisert med origin.
> - At arbeidsområdet er rent.
>
> ### 4. Viktige begrensninger
>
> - Ikke start BMAD Finalize i denne runden.
> - Ikke flytt filer.
> - Ikke endre DESIGN.md eller EXPERIENCE.md.
> - Ikke endre PRD eller Product Brief.
> - Ikke gjør nye produktbeslutninger.
> - Ikke sett noe dokument til `status: final`.
> - Ikke løs OQ-7 på egen hånd.
> - Ikke opprett nye KI-logger eller sesjonslogger i denne runden; dagens samlede arbeid skal dokumenteres etter prosjektets regler før økten avsluttes.
>
> Rapporter resultatet og stopp for gjennomgang med ChatGPT.

</details>

<details>
<summary><strong>Prompt 7 – Dekningskontroll og flytting til mockups/ og wireframes/</strong></summary>

> Vi fortsetter arbeidet med Sambandet 13. november 2026.
>
> ChatGPT har gjennomgått og godkjent resultatet av forrige commit.
>
> Repository: `IBE160-2026/G99-byfuglien-risoy-sonsteng`
> Branch: `ux/sebastian-ux-design`
> Forventet HEAD: `be61164`
>
> **Oppgave: Utfør første avgrensede arbeidsrunde i eksisterende BMAD UX Finalize – dekningskontroll og organisering av godkjente UX-artefakter.**
>
> Ikke start en ny BMAD-workflow.
>
> ### 1. Gjennomfør dekningskontroll (Pass 1)
>
> Les gjeldende BMAD UX-skill og relevante seksjoner i DESIGN.md, EXPERIENCE.md, UX-memloggen og gjeldende skisser.
>
> Kontroller alle åtte flatene:
>
> - F1 Årsvisning – HTML-mock, wireframe og spine.
> - F2 Månedsvisning – HTML-mock, wireframe og spine.
> - F3 Aktivitetsdetaljer – wireframe og spine.
> - F4 Aktivitetsskjema – HTML-mock, wireframe og spine.
> - F5 Sletting – wireframe og spine.
> - F6 Opplasting og analyse – wireframe og spine.
> - F7 KI-gjennomgang – HTML-mock, wireframe og spine.
> - F8 Oppsummering og forkasting – wireframe og spine.
>
> Kontroller at de dokumenterte flytene, tilstandene, komponentene og referansene er tilstrekkelige til å forstå hver flate.
>
> F3, F5, F6 og F8 er foreløpig foreslått som `spine-only`. Dette er ikke et nytt formelt gruppevedtak.
>
> Dersom du finner manglende eller motstridende UX-beslutninger som hindrer forsvarlig dekning, STOPP før filflytting og rapporter dem.
>
> Ikke opprett nye HTML-mocker eller fyll hull med antakelser.
>
> ### 2. Organiser godkjente artefakter
>
> Dersom dekningskontrollen ikke avdekker blokkerende hull, godkjenner jeg følgende filorganisering:
>
> **Flytt fire HTML-mocker til `mockups/`:**
>
> - `key-f1-arsvisning.html`
> - `key-f2-manedsvisning.html`
> - `key-f4-aktivitetsskjema.html`
> - `key-f7-gjennomgang.html`
>
> **Flytt syv gjeldende Excalidraw-skisser med hver sin tilhørende `.forhandsvisning.png` til `wireframes/`:**
>
> - `flow-f1-arsvisning-2026-11-03`
> - `flow-f2-f3-manedsvisning-v3-2026-11-03`
> - `flow-f4-aktivitetsskjema-2026-11-09`
> - `flow-f5-sletting-2026-11-09`
> - `flow-f6-opplasting-analyse-2026-11-09`
> - `flow-f7-gjennomgang-v3-2026-11-03`
> - `flow-f8-oppsummering-forkasting-2026-11-03`
>
> Kontroller nøyaktige eksisterende filnavn før flytting.
>
> Bruk `git mv` for sporede filer slik at Git kan registrere flyttingene.
>
> Behold historiske skisseversjoner og `kombinert-retning-1.html` i `.working/`.
>
> Den historiske HTML-filen har gamle kategorier og skal ikke presenteres som en gjeldende UX-spesifikasjon.
>
> ### 3. Oppdater filreferanser
>
> Oppdater referanser i DESIGN.md og EXPERIENCE.md slik at de peker til de nye plasseringene.
>
> Legg inn lenker fra spinene til de fire godkjente HTML-mockene.
>
> Oppdater bare filstier i kommentarene i HTML-mockene når det er nødvendig.
>
> Viktig:
> - Ikke endre mockenes synlige innhold, HTML-struktur, CSS eller UX-regler.
> - Ikke endre selve Excalidraw-skissene eller PNG-innholdet.
> - Ikke endre historiske KI-logger, sesjonslogger eller tidligere memloggoppføringer.
> - Ikke destiller eller språkvask øvrig spine-innhold i denne runden.
> - DESIGN.md og EXPERIENCE.md skal fortsatt ha `status: draft`.
>
> ### 4. Dokumenter organiseringen
>
> Når flyttingen og referansekontrollen er fullført, før én kort kontrollhendelse (`event`) i UX-memloggen.
>
> Beskriv hva som ble flyttet, at de historiske filene ble bevart, og at referansene ble oppdatert.
>
> Ikke registrer den foreløpige `spine-only`-klassifiseringen som et formelt gruppevedtak.
>
> ### 5. Kvalitetskontroll
>
> Kontroller:
>
> 1. Fire HTML-mocker finnes i `mockups/`.
> 2. Syv `.excalidraw`-filer og syv tilhørende PNG-er finnes i `wireframes/`.
> 3. Ingen av de godkjente filene er mistet.
> 4. Alle oppdaterte filreferanser peker til eksisterende filer.
> 5. Ingen gjeldende referanser peker til gamle plasseringer ved en feil.
> 6. Historiske referanser i logger er bevart.
> 7. OQ-7 og OQ-8 er fortsatt dokumentert korrekt.
> 8. DESIGN.md og EXPERIENCE.md er fortsatt `draft`.
> 9. Git viser bare forventede endringer og flyttinger.
>
> Kjør `git diff --check`, kontroller LF-linjeskift og vis `git status`.
>
> ### 6. Begrensninger
>
> - Ikke ta nye produkt- eller arkitekturbeslutninger.
> - Ikke endre PRD eller Product Brief.
> - Ikke gjennomfør språkvask eller `bmad-review` ennå.
> - Ikke oppdater KI-logg, sesjonslogg eller issues.md nå.
> - Ikke sett noen UX-dokumenter til `final`.
> - Ikke commit eller push.
>
> ### 7. Rapporter og stopp
>
> Lever:
>
> 1. Dekningsmatrise for F1–F8, med eventuelle hull eller usikkerheter.
> 2. Oversikt over flyttede filer.
> 3. Oversikt over oppdaterte referanser.
> 4. Resultat av kvalitetskontroll.
> 5. Git-status.
> 6. Gjenstående beslutningspunkter før neste Finalize-runde.
>
> Stopp etter dette. Jeg skal gjennomgå resultatet med ChatGPT før vi fortsetter.

</details>

<details>
<summary><strong>Prompt 8 – Konsolidering av DESIGN.md og EXPERIENCE.md</strong></summary>

> Vi fortsetter BMAD UX Finalize-forberedelsene i Sambandet, 13. november 2026.
>
> ChatGPT har gjennomgått og godkjent rapporten fra dekningskontroll og filorganisering.
>
> Repository: `IBE160-2026/G99-byfuglien-risoy-sonsteng`
> Branch: `ux/sebastian-ux-design`
> Forventet HEAD: `be61164`
>
> **Oppgave: Gjennomfør én avgrenset konsolideringsrunde av DESIGN.md og EXPERIENCE.md.**
>
> Vi skal bare føre allerede godkjente UX-beslutninger og dokumenterte regler inn i spinene, samt rette utdaterte referanser og beskrivelser.
>
> ### 1. Bevar eksisterende arbeid
>
> Bekreft at:
> - Fire HTML-mocker ligger i `mockups/`.
> - Sju gjeldende Excalidraw-skisser og tilhørende PNG-er ligger i `wireframes/`.
> - De tidligere filflyttingene og memlog-hendelsen er bevart.
> - Begge spinene fortsatt har `status: draft`.
>
> Ikke reverser flyttinger eller gjenopprett filer i `.working/`.
>
> ### 2. Oppdater valgt kalenderår i F1
>
> Før inn gruppevedtaket fra 12. november 2026 i relevante seksjoner i DESIGN.md og EXPERIENCE.md.
>
> Vedtaket:
> - Valgt kalenderår har 2 px mørk, sterk kant.
> - Lys panelbakgrunn.
> - 44 px høyde.
> - 10 px hjørneavrunding.
> - Nøytral valgt-markering, tydelig forskjellig fra primærknappen.
> - Oransje brukes bare til tastaturfokus.
>
> Bruk eksisterende vedtak i memloggen og den godkjente F1-mocken som grunnlag.
>
> Oppdater bare relevante beskrivelser av valgt/aktiv-markering og periodenavigasjon. Ikke innfør nye navigasjonsregler.
>
> ### 3. Oppdater F4-tegntelleren
>
> Dokumenter den godkjente illustrasjonen:
> - Tom merknad: «0 tegn».
> - Merknad over grensen: «N tegn over grensen».
> - Teksten forkortes ikke automatisk.
> - En merknad over grensen er ugyldig og blokkerer lagring.
>
> Ikke fastsett noen maksimal tegngrense. OQ-8 er fortsatt åpen.
>
> Skill mellom formuleringene som brukes i mockene og tekniske krav som ennå ikke er avklart.
>
> ### 4. Rett utdaterte beskrivelser
>
> **Excalidraw:**
> Begge spinene har en utdatert merknad om at skissene ikke er åpnet eller gjennomgått i Excalidraw.
>
> Kontroller den dokumenterte gjennomgangen fra 11. november og oppdater formuleringen så den er faktisk riktig.
>
> Ikke fjern andre [VALIDERES]-markører som fortsatt gjelder tester som ikke er gjennomført.
>
> **F8-retur:**
> Oppdater Mermaid-navigasjonskartet slik at den allerede dokumenterte returen «Forkast uten å lagre → F1» er representert.
>
> Bruk den eksisterende returregeltabellen som fasit. Ikke innfør en ny navigasjonsregel.
>
> **F4 i Layout:**
> Kontroller at tabellen Layout i DESIGN.md har korrekt dekning av F4.
>
> Legg til eller korriger F4-raden ved behov, basert på gjeldende F4-skisse og godkjent HTML-mock. Ikke finn på en ny layoutbeskrivelse.
>
> ### 5. Presiser historisk designreferanse
>
> I DESIGN.md og EXPERIENCE.md:
>
> Presiser at `kombinert-retning-1.html` er en historisk arbeidsfil som kan brukes som referanse for palett og formspråk.
>
> Filen inneholder utdaterte kategorier («Kat. A–I») og er ikke styrende for gjeldende kategorier eller funksjonelle UX-regler.
>
> Behold filen i `.working/`. Ikke endre innholdet.
>
> ### 6. Kontroller konsistens og dekning
>
> Etter endringene:
>
> - Sammenlign DESIGN.md og EXPERIENCE.md med godkjente beslutninger i memloggen.
> - Kontroller at F1–F8 fortsatt er dekket.
> - Bekreft at F3, F5, F6 og F8 foreløpig står som spine-only, uten å registrere dette som et nytt gruppevedtak.
> - Kontroller alle endrede Markdown-lenker.
> - Behold OQ-7 som blokkerende for `status: final`.
> - Behold OQ-8 og øvrige utestede forhold som dokumenterte åpne punkter.
> - Ikke behandle historiske skisser som styrende ved konflikt med spinene.
>
> ### 7. Git- og kvalitetskontroll
>
> Kontroller både staged og unstaged endringer, siden `git mv` kan ha lagt filflyttinger i staging.
>
> Kjør:
> - `git status`
> - `git diff --check`
> - `git diff --cached --check`
> - Kontroll av LF-linjeskift.
>
> Kontroller at bare DESIGN.md og EXPERIENCE.md er ytterligere endret i denne arbeidsrunden.
>
> ### 8. Begrensninger
>
> - Ikke endre noen HTML-mocker.
> - Ikke endre Excalidraw- eller PNG-filer.
> - Ikke endre PRD eller Product Brief.
> - Ikke gjør nye produkt- eller arkitekturbeslutninger.
> - Ikke gjennomfør generell språkvask nå.
> - Ikke kjør `bmad-review` ennå.
> - Ikke endre tidligere memloggoppføringer.
> - Ikke lag nytt formelt gruppevedtak.
> - Ikke oppdater KI-logg, sesjonslogg eller issues.md i denne runden.
> - Ikke sett noen UX-dokumenter til `final`.
> - Ikke commit eller push.
>
> ### 9. Rapporter og stopp
>
> Rapporter:
> 1. Hvilke konkrete seksjoner som ble endret i DESIGN.md.
> 2. Hvilke konkrete seksjoner som ble endret i EXPERIENCE.md.
> 3. Hvilke godkjente beslutninger endringene bygger på.
> 4. Eventuelle motstridende beskrivelser eller manglende grunnlag.
> 5. Om alle lenker og dekningskrav fortsatt stemmer.
> 6. Git-status og resultater fra kontrollene.
>
> Stopp for gjennomgang med ChatGPT før neste Finalize-runde.

</details>

<details>
<summary><strong>Prompt 9 – Valgt kalenderår, memlogg-referanser og BMAD-review (read-only)</strong></summary>

> Vi fortsetter BMAD UX Finalize-forberedelsene i Sambandet, 13. november 2026.
>
> ChatGPT har gjennomgått rapporten fra konsolideringen av DESIGN.md og EXPERIENCE.md.
>
> Arbeidet er tilfredsstillende, men før neste endringsrunde trenger vi en målrettet kontroll av ett mulig motstridspunkt og en strukturert BMAD-review.
>
> Branch: `ux/sebastian-ux-design`
> Forventet HEAD: `be61164`
>
> **Denne runden er READ ONLY. Ikke endre filer.**
>
> ### 1. Undersøk valgt kalenderår i F1
>
> Sammenlign:
> - Den eksakte generelle regelen om tekstbåret valgt/aktiv-markering i DESIGN.md og EXPERIENCE.md.
> - Gruppevedtaket fra 12. november om alternativ B.
> - Den godkjente F1 HTML-mocken i `mockups/`.
>
> Avklar:
> 1. Om den generelle regelen faktisk krever synlig ordlyd «Valgt», eller om dette er et eksempel.
> 2. Om den allerede godkjente F1-utformingen kan beskrives korrekt uten å endre mocken.
> 3. Om det finnes en reell konflikt som krever nytt gruppevedtak.
>
> Vis korte, eksakte utdrag som underbygger vurderingen.
>
> Ikke endre F1 eller UX-spinene. Ikke finn på en ny regel.
>
> ### 2. Kontroller memlogg-referanser
>
> Tidligere rapporter oppga:
> - F4-godkjenning: oppføring 148.
> - F7-godkjenning: oppføring 149.
> - Filorganisering: oppføring 150.
>
> Den siste rapporten henviste også til oppføring 151 for F1-vedtaket og oppføring 148 for Excalidraw-kontrollen.
>
> Undersøk hvordan memloggen nummererer oppføringene.
>
> Rapporter de faktiske identifikatorene eller andre entydige referanser for:
> - Excalidraw-kontrollen 11. november.
> - Gruppevedtaket om valgt kalenderår 12. november.
> - F4- og F7-godkjenningen 13. november.
> - Filorganiseringen 13. november.
>
> Ikke endre tidligere oppføringer.
>
> ### 3. Kjør BMAD-kvalitetskontroll
>
> Les relevante instruksjoner for `bmad-review`.
>
> Gjennomfør review av DESIGN.md og EXPERIENCE.md med:
> - `structure`
> - `prose`
>
> Dette skal være en analyse, ikke automatisk revisjon.
>
> Dersom review-verktøyet må skrive til dokumentene for å kjøre, stopp og forklar dette først.
>
> Vurder særlig:
> - Struktur, sammenheng og navigasjon.
> - Konsistens mellom de to spinene.
> - Dekning av F1–F8.
> - Tydelige komponentregler, tilstander og returregler.
> - Formuleringer som er tvetydige eller motstridende.
> - Utdaterte beskrivelser.
> - Om de historiske arbeidsfilene er korrekt avgrenset.
> - OQ-7, OQ-8, `[VALIDERES]` og `[FORELØPIG]`.
>
> Ikke foreslå nye produktfunksjoner som løsning på dokumentasjonsproblemer.
>
> ### 4. Sorter funnene
>
> Lag en prioritert oversikt med tre kategorier:
>
> **A – Må rettes før Finalize**
> Faktiske motstrid, manglende dekning, ugyldige referanser eller lignende.
>
> **B – Språkvask og presisering**
> Forbedringer som ikke endrer vedtatte UX-regler.
>
> **C – Dokumenterte åpne avhengigheter**
> Punkter som skal beholdes åpne, for eksempel OQ-8 og testing som ikke er gjennomført.
>
> Marker særskilt hva som krever en beslutning fra prosjektgruppen.
>
> Ikke løs OQ-7.
>
> ### 5. Git-kontroll og stopp
>
> Kontroller at tidligere filflyttinger, memlogg og spine-endringer er bevart.
>
> Kjør `git status`, `git diff --check` og `git diff --cached --check`.
>
> Ikke:
> - Endre filer eller memlogg.
> - Oppdatere KI-logg, issues.md eller sesjonslogg.
> - Endre godkjente HTML-mocker eller wireframes.
> - Utføre commit eller push.
> - Sette DESIGN.md eller EXPERIENCE.md til `final`.
>
> Rapporter:
> 1. Konklusjonen om valgt kalenderår.
> 2. Korrekte memlogg-referanser.
> 3. Resultatet fra BMAD-review.
> 4. Prioriterte funn i A, B og C.
> 5. Hva som krever gruppebeslutning.
> 6. Git-status.
>
> Stopp for gjennomgang med ChatGPT.

</details>

<details>
<summary><strong>Prompt 10 – Navigasjonskart, typografi i F7, Layout og metadata</strong></summary>

> Vi fortsetter BMAD UX Finalize-forberedelsene i Sambandet, 13. november 2026.
>
> ChatGPT har gjennomgått rapporten fra `bmad-review` med lensene `structure` og `prose`.
>
> Vi skal nå rette de konkrete, dokumenterte avvikene. Vi skal ikke gjennomføre en generell språkvask eller ta nye produktbeslutninger.
>
> Branch: `ux/sebastian-ux-design`
> Forventet HEAD: `be61164`
>
> ### 1. Rett navigasjonskartet i EXPERIENCE.md
>
> BMAD-review fant at navigasjonskartet ikke samsvarer fullt med den godkjente Returregler-tabellen.
>
> Kontroller og rett:
> - F4 → F3 gjelder redigering, ikke opprettelse av ny aktivitet.
> - Retur ved opprettelse av ny aktivitet skal samsvare med eksisterende returregler for F1/F2.
> - F3 «Lukk» skal ha korrekt retur.
> - Manglende F6-returer skal representeres der Returregler-tabellen gir grunnlag.
>
> Bruk eksisterende Returregler-tabell som fasit.
>
> Ikke finn på nye navigasjonsregler. Dersom tabellen ikke gir tilstrekkelig grunnlag for en kant, rapporter dette i stedet for å gjette.
>
> Kontroller at Mermaid-syntaksen fortsatt er gyldig.
>
> ### 2. Rett typografien i F7 HTML-mocken
>
> Endre kun den aktuelle CSS-regelen for problemmerker i:
>
> `mockups/key-f7-gjennomgang.html`
>
> Problemmerker som viser status, inkludert «Må rettes», «Usikker» og kildeproblem, skal følge eksisterende regel om minimum 18 px.
>
> - Endre nødvendig skriftstørrelse fra 16 px til 18 px.
> - Behold farger, rammer, ordlyd og statusbetydning.
> - Ikke endre typografiregelen i DESIGN.md.
> - Ikke endre andre metadata som allerede følger gjeldende regler.
>
> Render tilstand A og B i headless Chrome ved 1366, 1440 og 1840 px.
>
> Kontroller særlig:
> - Alle problemmerker er lesbare.
> - Tekst kan brytes til nye linjer uten å bli klippet.
> - Ingen horisontal scrolling eller uønsket overlapp.
> - Alle forslag, felt, kildeutdrag og handlingsknapper er bevart.
>
> Dette er fortsatt en statisk mock. Ikke påstå at tastatur, skjermleser, projektor eller faktisk interaksjon er testet.
>
> ### 3. Fullfør Layout-tabellen i DESIGN.md
>
> Legg til dokumentert dekning for F3, F5, F6 og F8.
>
> Bruk eksisterende gjeldende wireframes og spine-beskrivelser.
>
> Hver rad skal:
> - Kort beskrive eksisterende layout.
> - Vise til riktig skisse i `wireframes/`.
> - Ikke innføre nye UX-beslutninger.
>
> F3, F5, F6 og F8 kan omtales som dekket av skisse og spine, men ikke registreres som formelt vedtatt `spine-only` før prosjektgruppen har bekreftet dette.
>
> ### 4. Oppdater dokumentmetadata
>
> DESIGN.md og EXPERIENCE.md er endret 13. november, men har fortsatt `updated: 2026-11-11`.
>
> Oppdater `updated` til `2026-11-13`, i samsvar med prosjektets eksisterende YAML-konvensjoner.
>
> Behold `status: draft`.
>
> ### 5. Behold øvrige forhold uendret
>
> Ikke:
> - Endre valgt kalenderår i F1.
> - Registrere noen ny tolkning av valgt kalenderår som gruppevedtak.
> - Endre andre godkjente mocker.
> - Endre Excalidraw-skisser eller PNG-er.
> - Gjennomføre generell språkvask av DESIGN.md og EXPERIENCE.md.
> - Gjennomføre flere review-lenser nå.
> - Løse OQ-7 eller OQ-8.
> - Fjerne [VALIDERES] eller [FORELØPIG] uten grunnlag.
> - Endre tidligere memloggoppføringer.
> - Oppdatere KI-logg, sesjonslogg eller issues.md.
> - Committe eller pushe.
>
> ### 6. Kvalitetskontroll
>
> Kontroller:
> 1. Navigasjonskartet samsvarer med Returregler.
> 2. F7-problemmerkene følger gjeldende 18 px-regel.
> 3. F1–F8 har korrekt dokumentert dekning i Layout.
> 4. Alle filreferanser fortsatt fungerer.
> 5. DESIGN.md og EXPERIENCE.md har `status: draft` og korrekt `updated`.
> 6. Tidligere filflyttinger og memlogg-endringer er bevart.
>
> Kjør `git status`, `git diff --check` og `git diff --cached --check`.
>
> Kontroller LF-linjeskift.
>
> ### 7. Rapporter og stopp
>
> Rapporter:
> - Nøyaktig hvilke navigasjonskanter som ble rettet.
> - Endringen av F7-problemmerkene og resultatet av visuell kontroll.
> - Nye rader i Layout-tabellen.
> - Eventuelle avvik eller manglende grunnlag.
> - Git-status.
>
> Ikke legg inn en ny memlogg-hendelse før vi har gjennomgått resultatet.
>
> Stopp for kontroll med ChatGPT.

</details>

<details>
<summary><strong>Prompt 11 – Fire gruppevedtak (151–154)</strong></summary>

> Vi fortsetter BMAD UX Finalize-forberedelsene i Sambandet, 13. november 2026.
>
> **Viktig: Sebastian har nå eksplisitt bekreftet følgende fire beslutninger på vegne av prosjektgruppen. De er formelle gruppevedtak og skal dokumenteres som dette – ikke som forslag eller kontrollhendelser.**
>
> Repository: `IBE160-2026/G99-byfuglien-risoy-sonsteng`
> Branch: `ux/sebastian-ux-design`
> Forventet HEAD: `be61164`
>
> Fortsett den eksisterende BMAD UX-workflowen. Ikke start en ny.
>
> ### 1. Registrer fire gruppevedtak i UX-memloggen
>
> Bruk prosjektets etablerte `memlog.py append` og korrekt type for gruppebeslutninger. Undersøk eksisterende format før du skriver.
>
> Registrer følgende vedtak datert 13. november 2026, med Sebastian som godkjenner på vegne av prosjektgruppen:
>
> **Vedtak 1 – F3 retur fra kalenderens rutenett**
>
> Når F3 Aktivitetsdetaljer åpnes fra kalenderens rutenett i F2, skal «Lukk» returnere til samme månedsvisning. Fokus skal tilbake til aktiviteten som åpnet modalen.
>
> Eksisterende vedtak om retur til dagsoversikten når F3 ble åpnet derfra, beholdes.
>
> **Vedtak 2 – F6 retur fra dokumentopplasting**
>
> Når brukeren velger «Lukk» i F6, returnerer løsningen til F1 eller F2, avhengig av hvor opplastingen ble startet. Fokus returnerer til «Last opp dokument».
>
> Ved feil, avvist fil eller ingen funn blir brukeren i den relevante F6-tilstanden til vedkommende selv velger en tilgjengelig handling. Det skal ikke skje automatisk retur.
>
> Vellykket analyse går videre til F7 etter den allerede dokumenterte flyten. Behold eksisterende regler for ny analyse, avvisning og feilbehandling.
>
> **Vedtak 3 – F1 markering av valgt kalenderår**
>
> Det godkjente F1-designet beholdes uendret.
>
> Årstallet, for eksempel «2026», sammen med vedtatt nøytral valgt-markering og `aria-current`, er tilstrekkelig for denne kalenderårvelgeren.
>
> Synlig tekst «Valgt:» er ikke påkrevd i F1. Dette er en presisering av tidligere vedtak om valgt/aktiv-markering, ikke en generell endring av alle komponenter.
>
> **Vedtak 4 – UX-leveransens mockdekning**
>
> F1, F2, F4 og F7 leveres med HTML-mock, wireframe og spine.
>
> F3, F5, F6 og F8 leveres uten egne HTML-mocker, men med gjeldende Excalidraw-skisser og beskrivelser i DESIGN.md og EXPERIENCE.md.
>
> Dette er nå et godkjent gruppevedtak om UX-leveransens dokumentasjonsdekning. Det innebærer ikke at flatene utelates fra implementasjonen.
>
> Sikre at alle nye memloggoppføringer har korrekt format og LF-linjeskift. Tidligere oppføringer skal ikke endres.
>
> ### 2. Oppdater EXPERIENCE.md
>
> Bruk gruppevedtakene og eksisterende UX-regler.
>
> **Returregler:**
> - Legg til eksplisitt F3-retur til F2 ved «Lukk» etter åpning fra rutenettet.
> - Behold F3-retur til dagsoversikt når F3 ble åpnet derfra.
> - Legg til F6-retur til F1 eller F2 ved «Lukk», med fokus på «Last opp dokument».
> - Presiser at feil, avvist fil og ingen funn ikke utløser automatisk retur fra F6.
> - Behold den allerede dokumenterte overgangen F6 → F7 etter vellykket analyse.
>
> **Navigasjonskart:**
> - Oppdater Mermaid-kartet så det samsvarer med Returregler-tabellen.
> - Vis nødvendige F3- og F6-returer.
> - Ikke lag separate kanter for hver feilsituasjon dersom det vil gi inntrykk av automatisk navigasjon.
> - Bruk eksisterende noder og tegnforklaring der dette passer.
> - Valider Mermaid-syntaks hvis verktøy for det er tilgjengelig. Skill mellom syntaksvalidering og manuell kontroll i rapporten.
>
> **Valgt/aktiv-markering:**
> - Presiser at den generelle regelen om tekstbåret valgt tilstand ikke krever ordet «Valgt» i F1.
> - Henvis til det nye gruppevedtaket.
> - Behold øvrige regler for valgt/aktiv-markering.
>
> **UX-dekning:**
> - Før inn det nye gruppevedtaket om hvilke flater som har HTML-mocker, og hvilke som er dekket av skisser og spiner.
> - Behold full dekning av F1–F8.
>
> ### 3. Oppdater DESIGN.md
>
> Oppdater bare relevante deler:
>
> - Presiser F1-tolkningen av valgt kalenderår der komponenten er beskrevet.
> - Oppdater eventuell tekst som fortsatt omtaler F3, F5, F6 og F8 som bare foreslått spine-only.
> - Sørg for at Layout-tabellen samsvarer med det nye gruppevedtaket.
> - Ikke endre typografi, farger, komponenter eller layout utover dette.
>
> ### 4. Kontroll av konsistens
>
> Kontroller at:
>
> 1. De fire gruppevedtakene er registrert korrekt i UX-memloggen.
> 2. DESIGN.md og EXPERIENCE.md gjengir vedtakene uten motstrid.
> 3. Returregler og Mermaid-kart samsvarer.
> 4. Den godkjente F1-mocken ikke er endret.
> 5. Ingen andre HTML-mocker er endret.
> 6. Alle åtte flater fortsatt er dokumentert.
> 7. Alle lenker peker til eksisterende filer.
> 8. OQ-7 fortsatt blokkerer `status: final`.
> 9. OQ-8 og reelle `[VALIDERES]`-punkter fortsatt står åpne.
>
> Oppdater `updated` i dokumentene bare hvis prosjektets konvensjon krever det. Behold `status: draft`.
>
> ### 5. Bevar alt tidligere arbeid
>
> Det ligger allerede ucommittede endringer fra Finalize-forberedelsene:
> - Flytting av mocker og wireframes.
> - Oppdaterte filreferanser.
> - Konsolidering av UX-spinene.
> - Rettet navigasjonskart.
> - 18 px problemmerker i F7.
> - Memloggoppføring om filorganiseringen.
>
> Alt dette skal bevares.
>
> Kontroller både staged og unstaged endringer.
>
> Kjør:
> - `git status`
> - `git diff --check`
> - `git diff --cached --check`
> - Kontroll av LF-linjeskift.
>
> ### 6. Begrensninger
>
> Ikke:
> - Endre PRD eller Product Brief.
> - Endre HTML-mocker eller Excalidraw-skisser.
> - Opprette nye UX-funksjoner.
> - Gjennomføre generell språkvask.
> - Kjøre ny BMAD-review.
> - Løse OQ-7 eller OQ-8.
> - Fjerne andre åpne spørsmål uten gruppevedtak.
> - Endre historiske memloggoppføringer.
> - Oppdatere KI-logg, sesjonslogg eller issues.md ennå.
> - Sette noen dokumenter til `status: final`.
> - Committe eller pushe.
>
> ### 7. Rapporter og stopp
>
> Rapporter:
> 1. De fire memloggoppføringene, inkludert deres faktiske ordenstall.
> 2. Endringene i EXPERIENCE.md.
> 3. Endringene i DESIGN.md.
> 4. Navigasjonskartet og kontrollen mot Returregler.
> 5. Eventuelle gjenværende motstridspunkter.
> 6. Resultatet av Git- og kvalitetskontroll.
>
> Stopp for gjennomgang med ChatGPT før videre arbeid.

</details>

<details>
<summary><strong>Prompt 12 – ChatGPT-vurdering, change-oppføring og plan for språkvask</strong></summary>

> ## Gruppevedtakene er innarbeidet – godkjent
>
> Basert på Claude Codes rapport vurderer jeg denne runden som godkjent. Alle fire gruppevedtakene fra 13. november er registrert, og de relevante UX-reglene er oppdatert uten å endre godkjente mocker eller skisser.
>
> | Kontroll                         | Resultat                   |
> | -------------------------------- | -------------------------- |
> | Gruppevedtak 151–154             | Registrert                 |
> | F3-retur til månedsvisningen     | Dokumentert                |
> | F6-retur til F1/F2               | Dokumentert                |
> | F1-markering av valgt kalenderår | Avklart                    |
> | Mockdekning F1–F8                | Formelt vedtatt            |
> | Returregler og navigasjonskart   | Samsvarer ifølge rapporten |
> | OQ-7                             | Fortsatt blokkerende       |
> | Dokumentstatus                   | `draft`                    |
>
> Det er også riktig at Claude Code ikke har registrert en egen `change`-oppføring ennå. Den bør vi føre før denne delen av Finalize-arbeidet avsluttes.
>
> ### Hva gjenstår?
>
> Vi har kommet til oppryddingsfasen. Jeg anbefaler følgende rekkefølge:
>
> 1. Dokumentere konsolideringen og rettelsene i memloggen.
> 2. Gjennomgå gjenstående språkvask og `[FORELØPIG]`-markører.
> 3. Godkjenne eventuelle tekstendringer før de gjennomføres.
> 4. Kontrollere og godkjenne KI-logg og sesjonslogg, deretter committe arbeidet.
> 5. Avklare OQ-7 før formell Finalize.
>
> Jeg vil ikke at Claude Code skal starte en omfattende omskriving av spinene nå. Først bør vi se nøyaktig hvilke tekstendringer som faktisk er nødvendige.
>
> ## Neste steg – memlogg og språkvaskplan
>
> Kopier denne prompten til Claude Code:
>
> Vi fortsetter BMAD UX Finalize-forberedelsene i Sambandet, 13. november 2026.
>
> ChatGPT har gjennomgått og godkjent innarbeidingen av de fire gruppevedtakene fra 13. november.
>
> Repository: `IBE160-2026/G99-byfuglien-risoy-sonsteng`\
> Branch: `ux/sebastian-ux-design`\
> Forventet HEAD: `be61164`
>
> **Oppgave: Dokumenter utført konsolideringsarbeid og lag en konkret plan for siste språkvask. Ikke gjennomfør språkvasken ennå.**
>
> ### 1. Før én change-oppføring i UX-memloggen
>
> Bruk etablert `memlog.py append` med riktig type for dokumentendringer (`change`). Kontroller eksisterende format først.
>
> Oppføringen skal kort oppsummere Finalize-forberedelsene 13. november:
>
> - Godkjente mocker og gjeldende wireframes er organisert i `mockups/` og `wireframes/`.
> - Referanser i DESIGN.md, EXPERIENCE.md og mockkommentarer er oppdatert.
> - Tidligere godkjent F1-markering, F4-tegntellere og øvrige dokumenterte UX-regler er konsolidert.
> - Navigasjonskartet er avstemt mot Returregler.
> - Nye gruppevedtak 151–154 er innarbeidet.
> - F7-problemmerker er korrigert til 18 px etter eksisterende typografiregel.
> - F1–F8 er dekket etter prosjektgruppens beslutning.
> - OQ-7 blokkerer fortsatt `status: final`.
> - OQ-8 og reelle valideringspunkter er fortsatt åpne.
> - Dokumentene har fortsatt `status: draft`.
>
> Dette er en `change`-oppføring, ikke et nytt gruppevedtak.
>
> Behold tidligere oppføringer uendret og sikre LF-linjeskift.
>
> ### 2. Gjennomgå gjenstående språkvask – READ ONLY
>
> Les DESIGN.md og EXPERIENCE.md, med resultatene fra siste BMAD-review som grunnlag.
>
> Finn alle gjenstående `[FORELØPIG]`-markører og de relevante tekstfunnene fra `prose`- og `structure`-reviewen.
>
> Lag en tabell med:
>
> 1. Dokument og seksjon.
> 2. Nåværende formulering.
> 3. Foreslått ny formulering.
> 4. Begrunnelse.
> 5. Om endringen er ren språkvask eller krever en beslutning.
>
> Prioriter:
>
> - Tydelighet og korrekt bokmål.
> - Konsistent terminologi.
> - Fjerning av faktisk utdatert ordlyd.
> - Tvetydige beskrivelser.
> - Overflødige gjentakelser.
>
> Behold engelske kanoniske BMAD-seksjonsnavn der workflowen krever dem.
>
> Ikke flytt eller slett større tekstblokker uten å begrunne hvorfor. Ikke gjennomfør alle review-anbefalingene automatisk.
>
> ### 3. Skill mellom tre typer funn
>
> **A – Kan språkvaskes uten nye beslutninger**
>
> Formuleringer der betydningen allerede er vedtatt og ikke endres.
>
> **B – Krever godkjenning fra Sebastian eller gruppen**
>
> Formuleringer som kan påvirke hvordan brukeren forstår eller bruker løsningen.
>
> **C – Må avvente OQ-7 eller andre åpne avhengigheter**
>
> Særlig ordlyd som gjelder aktivering av demo-modus eller oppstart uten API-nøkkel.
>
> Ikke løs punkter i kategori B eller C på egen hånd.
>
> ### 4. Gjennomfør sluttkontroll uten flere endringer
>
> Kontroller:
>
> - At memloggen har den nye `change`-oppføringen.
> - At de fire gruppevedtakene 151–154 fortsatt står uendret.
> - At alle mocker og skisser er bevart.
> - At begge spinene fortsatt er `draft`.
> - At OQ-7 er dokumentert som blokkerende.
> - At ingen `[VALIDERES]`-punkter er fjernet.
> - At ingen nye filer eller dokumentendringer har oppstått utover memloggen i denne runden.
>
> Kjør `git status`, `git diff --check` og `git diff --cached --check`.
>
> ### 5. Begrensninger
>
> - Ikke utfør selve språkvasken ennå.
> - Ikke endre DESIGN.md eller EXPERIENCE.md i denne runden.
> - Ikke endre mocker, skisser, PNG-er, PRD eller Product Brief.
> - Ikke start ny BMAD-workflow.
> - Ikke gjennomfør Finalize.
> - Ikke kjør nye review-lenser.
> - Ikke oppdater KI-logg, sesjonslogg eller issues.md ennå.
> - Ikke commit eller push.
>
> ### 6. Rapporter og stopp
>
> Lever:
>
> 1. Memloggoppføringens ordenstall og innhold.
> 2. En samlet tabell over foreslåtte språkendringer.
> 3. Klassifisering A, B eller C.
> 4. Eventuelle nye motstridspunkter.
> 5. Git-status.
>
> Stopp for gjennomgang med ChatGPT før tekstene endres.
>
> Når denne rapporten kommer, tar vi stilling til de konkrete formuleringene. Målet er å gjøre dokumentasjonen klar for formell Finalize uten å endre vedtatt UX-design.
>
> Vi lar OQ-7 stå åpen til arkitekturavklaringen foreligger.

</details>

<details>
<summary><strong>Prompt 13 – Gruppevedtak B1–B4 og språkvask A1–A12</strong></summary>

> Vi fortsetter BMAD UX Finalize-forberedelsene i Sambandet, 13. november 2026.
>
> **Sebastian har eksplisitt godkjent de fire brukerrettede formuleringene B1–B4 på vegne av prosjektgruppen. De er nå formelle gruppevedtak.**
>
> Repository: `IBE160-2026/G99-byfuglien-risoy-sonsteng`
> Branch: `ux/sebastian-ux-design`
> Forventet HEAD: `be61164`
>
> Fortsett den eksisterende BMAD UX-workflowen. Ikke start en ny.
>
> ## 1. Kontroller og bevar eksisterende arbeid
>
> Før du endrer noe, bekreft:
> - At arbeidsområdet inneholder de forventede, ucommittede Finalize-forberedelsene.
> - At fire HTML-mocker ligger i `mockups/`.
> - At syv gjeldende Excalidraw-skisser og syv tilhørende PNG-er ligger i `wireframes/`.
> - At UX-memloggen har 155 oppføringer, inkludert gruppevedtakene 151–154 og change-oppføringen 155.
> - At DESIGN.md og EXPERIENCE.md har `status: draft`.
> - At OQ-7 fortsatt blokkerer `status: final`.
>
> Bevar alle tidligere endringer, både staged og unstaged. Ikke kjør kommandoer som kan overskrive eller nullstille arbeidet.
>
> ## 2. Registrer godkjenningen av B1–B4
>
> Bruk prosjektets etablerte `memlog.py append` og korrekt format for `(decision by group)`.
>
> Registrer én samlet gruppebeslutning datert 13. november 2026, bekreftet av Sebastian på vegne av prosjektgruppen.
>
> Vedtaket gjelder disse fire formuleringene:
>
> **B1 – For lang merknad**
>
> «! Må rettes: Ugyldig – 120 tegn for mye. Kort ned teksten eller fjern merknaden. Teksten forkortes ikke automatisk.»
>
> 120 tegn er fortsatt et fiktivt eksempel. OQ-8 er ikke avklart, og ingen maksimal tegngrense fastsettes.
>
> **B2 – Usikker kategori**
>
> «? Kontroller: Usikker – sammenlign med kildeutdraget»
>
> **B3 – Sperret oppsummering**
>
> «Kan ikke gå til oppsummering ennå: 8 forslag er ikke behandlet. 1 godkjent forslag har felt som må rettes.»
>
> Tallene tilhører det eksisterende fiktive F7-eksempelet.
>
> **B4 – Feil ved lagring**
>
> «Valgene dine er beholdt. Prøv igjen.»
>
> Dette endrer ikke regler for lagring, feilbehandling eller bevaring av brukerens valg.
>
> Registrer vedtaket med nøyaktig ordlyd. Det er et gruppevedtak, ikke bare en kontrollhendelse.
>
> Ikke endre tidligere memloggoppføringer. Sikre LF-linjeskift.
>
> ## 3. Gjennomfør dokumentasjonsrettelsene A1–A12
>
> Endre bare relevante deler av DESIGN.md og EXPERIENCE.md.
>
> **A1 – Status**
> - Endre «Status: førsteutkast» til «Status: utkast» i begge dokumentene.
>
> **A2 – Statusmarkører**
> - Endre «godkjent av Sebastian, bindende» til «godkjent av Sebastian eller prosjektgruppen, bindende».
> - Behold øvrig betydning og alle statusmarkører.
>
> **A3 – PRD-status**
> - Kontroller PRD-ens faktiske oppdateringsdato i eksisterende filer eller dokumenthistorikk.
> - Oppdater datoreferansen bare hvis 11. november 2026 kan bekreftes.
> - Behold opplysningen om at den reviderte PRD-en ikke er validert på nytt.
> - Hvis datoen ikke kan bekreftes, behold teksten og rapporter usikkerheten.
>
> **A4 – Tom måned**
> - Bruk formuleringen:
>   «Etter M6-1 teller ikke aktiviteter som bare ligger i nabomånedens dager.»
>
> **A5 – Key Flows**
> - Endre «Edge case» til «Feilvei» i de tre relevante tabellene.
> - Behold kanoniske BMAD-seksjonsnavn.
>
> **A6 – Modal/dialog**
> - Endre «bekreftelser i F7/F8» til «forkastingsdialogen i F8 (over F7)».
>
> **A7 – F4 State Patterns**
> - Fjern den unødvendige gjentakelsen av den lange feilmeldingen.
> - Bruk en kort henvisning til riktig seksjon i Voice and Tone.
> - Ikke fjern informasjon om at feilen blokkerer lagring eller at teksten ikke forkortes automatisk.
>
> **A8 – DESIGN › Felt med etikett**
> - Behold visuelle og typografiske krav.
> - Henvis til EXPERIENCE.md for ordlyden i tegnteller og feilmeldinger.
> - Ikke fjern krav som bare finnes i DESIGN.md.
>
> **A9 – Årshjulsirkel**
> - Behold sorteringsregler og krav til tilgjengelige navn samlet i EXPERIENCE.md.
> - La DESIGN.md beskrive utseende og henvise tydelig til EXPERIENCE.md for atferd.
> - Bevar samtlige normative krav og vedtaksreferanser.
> - Kontroller før og etter at ingen regler er mistet eller fått endret betydning.
>
> **A10 – Åpne spørsmål**
> - Del eksisterende oversikt i «Åpne» og «Avklart».
> - Flytt avklarte punkter til riktig undertabell.
> - Behold alle rader, vedtaksreferanser og dokumenterte avhengigheter.
> - OQ-7 skal fortsatt stå som blokkerende.
> - OQ-8, OQ-2 og kategorifarger skal ikke fremstilles som avklart.
>
> **A11 – Lenker**
> - Legg inn korte, relevante lenker til godkjente HTML-mocker ved komponent- og tilstandsbeskrivelser for F1, F2, F4 og F7.
> - Unngå unødvendig gjentakelse.
> - Kontroller at relative stier fungerer.
>
> **A12 – Historiske kategoriplassholdere**
> - Fjern den overflødige setningen i DESIGN.md › Kategorimerke om at kategoriene erstatter «Kat. A … Kat. I».
> - Behold den historiske sporbarheten i memloggen og eksisterende avviksbeskrivelse.
>
> Dette er dokumentasjonsarbeid. Ikke innfør nye UX-regler eller produktfunksjoner.
>
> ## 4. Oppdater godkjent brukerrettet tekst B1–B4
>
> Bruk nøyaktig ordlyd fra gruppevedtaket i punkt 2.
>
> **B1:**
> - Oppdater relevant eksempel i EXPERIENCE.md › Voice and Tone.
> - Oppdater den tilsvarende feilmeldingen i `mockups/key-f4-aktivitetsskjema.html`.
> - Behold de andre feilmeldingene, de fire valideringsfeilene og hele merknadsteksten.
>
> **B2:**
> - Oppdater EXPERIENCE.md › Voice and Tone.
> - Oppdater den usikre kategorimeldingen i begge tilstandene i `mockups/key-f7-gjennomgang.html`.
>
> **B3:**
> - Oppdater EXPERIENCE.md › Voice and Tone.
> - Oppdater årsaksteksten ved «Gå til oppsummering» i begge tilstandene i F7-mocken.
> - Behold sperringene og telleren.
>
> **B4:**
> - Oppdater relevant ordlyd i EXPERIENCE.md og eventuell eksisterende F8-tekst i spine-dokumentasjonen.
> - Dersom den samme teksten finnes i en gjeldende HTML-mock, oppdater den der også.
> - Ikke rediger Excalidraw-skisser eller konstruer en ny F8-mock.
>
> Sørg for at ordlyden er konsekvent mellom UX-spinene og de aktuelle HTML-mockene.
>
> ## 5. Behandle B5–B8 og [FORELØPIG]
>
> **B5:**
> - De ni øvrige eksempeltekstene er godkjent uendret gjennom denne språkvasken. Ikke skriv dem om.
>
> **B6:**
> - Fjern [FORELØPIG]-markøren som gjelder Voice and Tone-eksemplene B1–B5, når det er kontrollert at alle disse formuleringene er konsistente.
> - Ikke fjern andre markører som gjelder uavklarte forhold.
>
> **B7:**
> - Oppdater raden om mikrotekst i EXPERIENCE.md › Åpne spørsmål, slik at den viser at B1–B5 er avklart gjennom gruppevedtak 13. november.
> - Behold eventuelle uavklarte deler av samme punkt synlige og åpne.
> - Ikke marker demo-modus-teksten som vedtatt.
>
> **B8:**
> - Kontroller at alle godkjente brukerrettede formuleringer er oppdatert i relevante mocker.
> - F1 og F2 skal ikke endres med mindre en eksakt, godkjent tekstforekomst gjør det nødvendig. Rapporter i så fall behovet i stedet for å endre dem.
>
> ## 6. La OQ-7 og åpne punkter stå
>
> Ikke endre:
>
> - C1: «DEMO-MODUS – forhåndsdefinerte forslag, ingen språkmodell».
> - C2: Teksten om at demo-modus finnes for støttede testdokumenter.
> - OQ-7 eller beslutninger om aktivering av demo-modus.
> - OQ-8 eller tekniske grenseverdier.
> - OQ-2 og produktnavn.
> - [ÅPENT] kategorifarger.
> - Reelle [VALIDERES]-punkter.
> - Gjeldende regler for lagring, avvisning, analyse og navigasjon.
>
> DESIGN.md og EXPERIENCE.md skal fortsatt ha `status: draft`.
>
> ## 7. Visuell kontroll av F4 og F7
>
> Render begge tilstander i hver mock i headless Chrome ved:
>
> - 1366 px
> - 1440 px
> - 1840 px
>
> Kontroller:
> 1. At B1 vises korrekt i F4.
> 2. At B2 og B3 vises korrekt i begge F7-tilstandene.
> 3. At B4 er oppdatert der den faktisk forekommer, uten å konstruere nye flater.
> 4. At ingen tekst klippes, overlapper eller skaper horisontal scrolling.
> 5. At F4 fortsatt har fire valideringsfeil.
> 6. At F7 fortsatt har to blokkerende feltfeil, én usikker kategori og to sperrede handlinger.
> 7. At alle ni kategoriene, eksisterende eksempeldata og kildeutdrag er bevart.
> 8. At fokusmarkering og typografiregelen på 18 px er bevart.
>
> Dette er kontroll av statiske mocker. Ikke påstå at faktisk tastaturbruk, skjermleser, projektor eller interaksjon er testet.
>
> ## 8. Dokument- og Git-kontroll
>
> Kontroller:
> - At alle A1–A12 er utført eller har begrunnet avvik.
> - At B1–B4 samsvarer nøyaktig med gruppevedtaket.
> - At ingen normative UX-regler er mistet under A7–A10.
> - At F1–F8 fortsatt har vedtatt dokumentasjonsdekning.
> - At alle relative lenker peker til eksisterende filer.
> - At samtlige tidligere Finalize-forberedelser og gruppevedtak er bevart.
> - At ingen historiske memloggoppføringer er endret.
> - At alle endrede tekstfiler har LF.
>
> Kontroller både staged og unstaged endringer.
>
> Kjør:
> - `git status`
> - `git diff --check`
> - `git diff --cached --check`
>
> Rapporter eventuelle problemer i stedet for å gjøre nye, ikke-godkjente endringer.
>
> ## 9. Begrensninger
>
> Ikke:
> - Endre Excalidraw-skisser eller PNG-er.
> - Endre PRD eller Product Brief.
> - Lage nye mocker.
> - Kjøre ny BMAD-workflow.
> - Kjøre nye review-lenser.
> - Løse OQ-7 eller OQ-8.
> - Gjennomføre formell BMAD Finalize.
> - Sette dokumenter til `status: final`.
> - Oppdatere KI-logg, sesjonslogg eller issues.md ennå.
> - Committe eller pushe.
>
> ## 10. Rapporter og stopp
>
> Lever en strukturert sluttrapport med:
>
> 1. Den nye gruppebeslutningens faktiske ordenstall i memloggen.
> 2. Status for A1–A12.
> 3. Status for B1–B8.
> 4. Hvilke [FORELØPIG]-markører som er fjernet, og hvilke som står igjen.
> 5. Resultatet av visuell kontroll ved 1366, 1440 og 1840 px.
> 6. Eventuelle avvik, uavklarte formuleringer eller motstridende regler.
> 7. Git-status og diff-kontroller.
>
> Stopp etter rapporten. Jeg skal gjennomgå resultatet med ChatGPT før videre arbeid.

</details>

<details>
<summary><strong>Prompt 14 – Sluttkontroll og logger (denne loggen)</strong></summary>

> Vi fortsetter arbeidet med Sambandet, 13. november 2026.
>
> ChatGPT har gjennomgått rapporten fra siste språkvaskrunde. Arbeidet er godkjent med én mindre kontroll som gjenstår før commit.
>
> Repository: `IBE160-2026/G99-byfuglien-risoy-sonsteng`
> Branch: `ux/sebastian-ux-design`
> Forventet HEAD: `be61164`
>
> **Oppgave: Gjennomfør sluttkontroll av Finalize-forberedelsene og klargjør KI-logg, sesjonslogg og issues.md for godkjenning.**
>
> Dette er IKKE formell BMAD UX Finalize.
>
> ### 1. Kontroller tabellen Åpne spørsmål i EXPERIENCE.md
>
> Forrige rapport oppga:
> - 22 opprinnelige rader.
> - 15 åpne rader etter omorganiseringen.
> - 10 avklarte rader etter omorganiseringen.
> - Totalt 25 rader.
>
> Undersøk:
> 1. Hvordan de 22 opprinnelige radene ble til 25.
> 2. Hvilke opprinnelige rader som ble delt opp.
> 3. Om noen punkter er duplisert, forsvunnet eller feilklassifisert.
> 4. Om OQ-7, OQ-8, OQ-2, øvrig mikrotekst og andre uavklarte spørsmål fortsatt er korrekt dokumentert.
>
> Rapporter en kort forklaring på differansen.
>
> Ikke endre UX-dokumentene dersom tallene kan forklares og innholdet er korrekt. Ved reelle feil: rapporter funnet og stopp før dokumentendring.
>
> ### 2. Gjennomfør samlet teknisk dokumentkontroll
>
> Kontroller de nåværende filene og arbeidsområdet, inkludert staged og unstaged endringer.
>
> Bekreft:
> - Fire godkjente HTML-mocker finnes i `mockups/`.
> - Syv gjeldende Excalidraw-skisser og syv tilhørende PNG-er finnes i `wireframes/`.
> - Historiske arbeidsfiler er bevart.
> - DESIGN.md og EXPERIENCE.md dekker F1–F8.
> - Returregler og navigasjonskart samsvarer.
> - Alle fire gruppevedtak 151–154 er innarbeidet.
> - Gruppevedtak 156 om mikrotekst er innarbeidet.
> - Memloggoppføring 155 om konsolideringen er bevart.
> - Alle relative filreferanser fungerer.
> - F4 og F7 inneholder godkjent ordlyd.
> - OQ-7 fortsatt blokkerer `status: final`.
> - OQ-8, reelle [VALIDERES]-punkter og resterende [FORELØPIG]-punkter er korrekt dokumentert.
> - DESIGN.md og EXPERIENCE.md fortsatt har `status: draft`.
>
> Kontroller Mermaid-syntaks med tilgjengelig verktøy hvis mulig. Dersom formell validering ikke er tilgjengelig, rapporter begrensningen. Ikke installer nye verktøy uten godkjenning.
>
> Ikke kjør nye BMAD-review-lenser.
>
> ### 3. Opprett KI-logg for 13. november
>
> Følg CLAUDE.md, AGENTS.md og prosjektets etablerte KI-loggformat.
>
> Dokumenter dagens faktiske bruk av Claude Code og ChatGPT, herunder:
> - Oppstart og read-only-kontroll.
> - F4-rettelser og godkjenning.
> - Utarbeidelse, kontroll og godkjenning av F7.
> - Commit `be61164` som allerede er pushet.
> - Dekningskontroll og flytting av mocker og wireframes.
> - Konsolidering av DESIGN.md og EXPERIENCE.md.
> - BMAD-review med structure og prose.
> - Korrigering av navigasjonskart og typografi.
> - Gruppevedtakene 151–154.
> - Språkvask A1–A12 og B1–B8.
> - Gruppevedtak 156.
> - Hva som er testet, og hva som ikke er testet.
> - Åpne avhengigheter, særlig OQ-7.
>
> Følg eksisterende praksis for å dokumentere de eksakte Claude Code-promptene, dersom de kreves av prosjektet.
>
> Ikke konstruer manglende prompttekst, tester eller godkjenninger.
>
> Marker KI-loggen som utkast til gjennomgang. Ikke registrer at den er godkjent ennå.
>
> ### 4. Oppdater eksisterende sesjonslogg
>
> Bruk eksisterende sesjonslogg for UX-arbeidet.
>
> Dokumenter kort:
> - Dagens arbeidsoppgaver og resultater.
> - Godkjente beslutninger og kontrollhendelser.
> - Endringer i filstruktur og UX-spiner.
> - Gjennomførte kontroller.
> - Gjenstående oppgaver før formell Finalize.
>
> Bevar tidligere logginnhold.
>
> ### 5. Oppdater issues.md
>
> Kontroller eksisterende punkter opp mot dagens faktiske status.
>
> - Marker ferdige F4- og F7-oppgaver som ferdige etter prosjektets konvensjon.
> - Marker fullført organisering, konsolidering og språkvask korrekt.
> - Behold OQ-7 som åpen og blokkerende for UX Finalize.
> - Behold OQ-8 og utestede forhold korrekt dokumentert.
> - Rett den tidligere inkonsistensen om KI-loggen fra 12. november: Den var godkjent, mens enkelte loggtekster omtalte den som utkast. Kontroller dokumentasjonen før status endres.
> - Legg til en tydelig oppgave om godkjenning av KI-logg og sesjonslogg for 13. november før neste commit.
>
> Ikke marker hele UX-workflowen som ferdig.
>
> ### 6. Kvalitetskontroll
>
> Kjør:
> - `git status`
> - `git diff --check`
> - `git diff --cached --check`
>
> Kontroller LF-linjeskift i alle nye og endrede tekstfiler.
>
> Kontroller at:
> - Tidligere staged filflyttinger er bevart.
> - Ingen godkjente skisser eller mocker er overskrevet.
> - Ingen uventede filer er endret.
> - Ingen historiske memloggoppføringer er endret.
> - Ingen filer har fått `status: final`.
>
> ### 7. Begrensninger
>
> Ikke:
> - Endre DESIGN.md eller EXPERIENCE.md utover å rapportere eventuelle feil.
> - Endre HTML-mocker, Excalidraw-skisser eller PNG-er.
> - Endre PRD eller Product Brief.
> - Registrere nye gruppevedtak.
> - Løse OQ-7 eller OQ-8.
> - Gjennomføre formell BMAD UX Finalize.
> - Committe eller pushe.
> - Markere dagens KI-logg eller sesjonslogg som godkjent uten eksplisitt gjennomgang.
>
> ### 8. Rapporter og stopp
>
> Lever:
> 1. Forklaringen på 22 versus 25 rader i Åpne spørsmål.
> 2. Resultatet av samlet dokumentkontroll.
> 3. Hvor KI-loggen er opprettet, og hva den dekker.
> 4. Hva som er oppdatert i sesjonsloggen.
> 5. Hvilke punkter som er oppdatert i issues.md.
> 6. Eventuelle gjenstående avvik.
> 7. Git-status med oversikt over alle endrede og nye filer.
>
> Stopp for gjennomgang med ChatGPT. Ikke utfør commit eller push.

</details>

## Hva KI leverte

- **Oppstart (prompt 1):** kontroll av branch, HEAD, logger og arbeidsmappe. Ingen filer endret.
- **F4 Aktivitetsskjema (prompt 2–3):** tegnteller A «0 tegn», tegnteller B «120 tegn over grensen», tre faktiske mellomrom i Ansvarsområde (␣-illustrasjonen og CSS-regelen fjernet), oppdaterte kommentarer og tilstandsnotater. Kontrollhendelse i memloggen (oppføring 148).
- **F7 Gjennomgang (prompt 3–5):** ny mock `key-f7-gjennomgang.html` etter gjeldende skisse v3: A oversikt synlig, B oversikt skjult; blokkerende feltfeil, usikker kategori, kildeutdrag med status, sperret «Godkjenn» og «Gå til oppsummering» med årsak. Rettet etter ChatGPT-gjennomgang: `:focus-visible` for skjemafelt og tekst om at forslag 9–15 ikke er vist. Demo-modus-merket er utelatt (OQ-7). Kontrollhendelse i memloggen (oppføring 149).
- **Plan for Finalize (prompt 5):** read-only plan med beslutningspunkter.
- **Commit og push (prompt 6):** `be61164` (`docs(ux): approve F4 and F7 key screen mockups`) med memloggen, F4 og F7, pushet til `origin/ux/sebastian-ux-design`.
- **Organisering (prompt 7):** dekningskontroll F1–F8; fire mocker flyttet til `mockups/` og sju skisser med PNG til `wireframes/` med `git mv` (SHA-256 uendret); referanser i spinene og stier i mockkommentarene oppdatert; lenker fra spinene til mockene; event i memloggen (oppføring 150).
- **Konsolidering (prompt 8):** valgt kalenderår i F1 (gruppevedtak 12. november), tellerformuleringer fra F4, rettet Excalidraw-merknad, kanten «Forkast uten å lagre → F1», F4-rad i Layout, `kombinert-retning-1.html` presisert som historisk arbeidsfil.
- **Kontroll og review (prompt 9):** vurdering av valgt kalenderår, korrigering av memlogg-referanser (to tall i tidligere rapporter var linjenumre, ikke ordenstall), og BMAD-review med `structure` og `prose`, sortert i A/B/C. Ingen filer endret.
- **Rettelser (prompt 10):** navigasjonskartet avstemt mot Returregler, problemmerkene i F7 endret fra 16 til 18 px, F3/F5/F6/F8-rader i Layout, `updated: 2026-11-13` i begge spinene.
- **Gruppevedtak (prompt 11):** oppføring 151–154 (F3-retur, F6-retur, valgt kalenderår i F1, mockdekning) og innarbeiding i begge spinene.
- **Change-oppføring og språkvaskplan (prompt 12):** oppføring 155 og tabell med forslag A1–A12, B1–B8, C1–C2.
- **Språkvask (prompt 13):** gruppevedtak 156 om B1–B4; A1–A12 gjennomført; B1 i F4-mocken og B2/B3 i F7-mocken; [FORELØPIG]-markøren for eksemplene i Voice and Tone fjernet; tabellen Åpne spørsmål delt i «Åpne» og «Avklart».
- **Sluttkontroll og logger (prompt 14):** denne loggen, ny seksjon i sesjonsloggen og oppdatert `issues.md`.

## Hva vi endret og hvorfor

- **F4:** rettelsene ble foreslått av ChatGPT 12. november og godkjent av Sebastian (prompt 2–3).
- **F7, tilstand B:** skissen har ingen egen tilstand der bare godkjenningen er sperret; B følger skissen (oversikten skjult), og sperren vises i begge tilstandene. Dette ble rapportert som avvik (prompt 3).
- **F7, fokus og forslag 9–15:** ChatGPT fant at skjemafeltene manglet synlig tastaturfokus, og at teksten om forslag 9–15 var uklar (prompt 4).
- **Memlogg-referanser:** Claude Code oppga i to rapporter linjenumre som om de var ordenstall; dette ble rettet i prompt 9. Ingen filer inneholdt de feilaktige tallene.
- **Navigasjonskart:** Claude Code la ikke inn F3- og F6-returer som ikke hadde grunnlag i Returregler-tabellen (prompt 10). Gruppevedtak 151 og 152 ga grunnlaget, og kantene ble lagt inn i prompt 11.
- **Typografi i F7:** problemmerkene i den godkjente mocken brøt regelen om minst 18 px for status; mocken ble rettet, ikke regelen (prompt 10).
- **Valgt kalenderår:** mulig motstrid mellom regelen om tekstbåret markering og F1-mocken ble avklart med gruppevedtak 153, uten endring i mocken (prompt 11).
- **Språkvask:** bare godkjente formuleringer ble endret (prompt 13). Demo-modus-teksten (C1, C2) og øvrig mikrotekst fra skissene står fortsatt åpne.
- **Beholdt:** ingen Excalidraw-skisser, PNG-er, PRD eller Product Brief ble endret. F1- og F2-mocken fikk bare nye stier i kommentarene. Ingen nye produktbeslutninger ble tatt av KI.

## Testing

Det ble ikke testet noen fungerende applikasjon. Kontrollene gjaldt statiske HTML-mocker uten JavaScript og Markdown-dokumenter. Dette ble faktisk kjørt:

- **Visuell kontroll i headless Chrome (Claude Code):** F4 og F7 ble rendret ved 1366, 1440 og 1840 px etter hver endring (prompt 2, 3, 4, 10 og 13). PNG-ene ble lagret i scratchpad utenfor repoet.
- **Måling i nettleseren:** midlertidige skript i kopier utenfor repoet målte horisontal scroll, klipping, overlapp, antall feilmeldinger, `aria-invalid`, sperrede knapper, skriftstørrelse på problemmerkene og at merkene får plass i forslagsraden.
- **Programmatisk fokus:** i F7 ble et tekstfelt og et tekstområde gitt fokus med skript; begge fikk `:focus-visible` med 3 px oransje ring, 3 px avstand og hvit offset (prompt 4). Dette er ikke en tastaturtest.
- **Filflytting:** SHA-256 før og etter `git mv` var identisk for alle 18 filene (prompt 7).
- **Referanser:** alle relative lenker i DESIGN.md og EXPERIENCE.md og alle stier i mockkommentarene peker til filer som finnes.
- **Navigasjonskart:** ingen Mermaid-validator (`mmdc`) var tilgjengelig, så syntaksen er **ikke formelt validert**. En manuell strukturkontroll (header, kantformat og nodedefinisjoner) fant ingen avvik.
- **Tabellen Åpne spørsmål:** radene ble sammenlignet ordrett med versjonen i HEAD: 22 rader flyttet uendret, raden om mikrotekst erstattet av tre rader (23 − 1 + 3 = 25), ingen duplikater.
- **`git diff --check` og `git diff --cached --check`:** exit 0 etter hver runde. LF ble kontrollert i alle endrede tekstfiler (`memlog.py` skriver CRLF og ble konvertert til LF etter hver skriving).
- **ChatGPT (ifølge promptene):** rendret F7 A og B i Chromium ved 1366, 1440 og 1840 px (prompt 4).

**Ikke testet:** projektor, tastatur, skjermleser og faktisk interaksjon. Klassifiseringstesten med 25–30 fiktive aktiviteter er ikke gjennomført.

**Åpne avhengigheter:** OQ-7 (aktivering av demo-modus, oppstart uten API-nøkkel, gjenkjenning av testdokumenter) blokkerer `status: final`. OQ-8 (tegngrense, tidsgrense, dokumentstørrelse, nettlesere) og OQ-2 (produktnavn) står åpne, i tillegg til [VALIDERES]-punktene og ordlyden om demo-modus.
