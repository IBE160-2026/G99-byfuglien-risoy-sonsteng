# 2026-11-01 — BMAD-validering og revisjon av PRD

- **Deltakere:** Lars Tellef Risøy
- **KI-verktøy:** Claude Code med modellen Claude Opus 5.5 (`claude-opus-5-5`) og BMAD-skill `bmad-prd` (Validate). To underagenter (general-purpose) gjennomførte selve valideringen. ChatGPT (OpenAI) ble brukt til å formulere og kvalitetssikre promptene til Claude Code.
- **Kontrollert av:** Lars Tellef Risøy

## Oppgave

Validere den ferdigstilte PRD-en med BMADs Validate-workflow etter at Product Brief
ble forkortet 2026-11-01, og avgjøre om PRD-en er klar for UX Design. Deretter
skulle gruppens beslutninger om funnene innarbeides i PRD-en og
beslutningshistorikken (`.memlog.md`), og PRD-fasen avsluttes med commit og push.
Økten gikk over 1.–2. november, med et brudd i tilkoblingen og en omstart av PC-en
underveis.

## Prompt (ordrett)

Promptene er gjengitt ordrett og i rekkefølge. Hver prompt er sammenleggbar.
Claude Codes svar mellom promptene er ikke tatt med. Prompt 7 er bevisst
forkortet: innledningen er gjengitt ordrett, og resten er erstattet med `[...]`.
Alle andre prompter er gjengitt i sin helhet. To meldinger som ikke gjaldt
oppgaven, er utelatt: en tilkoblingstest («test») og et spørsmål om innliming
med Ctrl+V.

<details>
<summary><strong>Prompt 1 – Start av bmad-prd</strong> (2026-11-01)</summary>

> /bmad-prd

</details>

<details>
<summary><strong>Prompt 2 – Validate PRD</strong> (2026-11-01)</summary>

> Kjør **Validate PRD** på vår eksisterende `prd.md` etter BMAD-metodens offisielle valideringsworkflow.
>
> Bruk nyeste `product-brief.md`, `CLAUDE.md` og relevant beslutningshistorikk som kontekst.
>
> Vurder spesielt:
> - Samsvar mellom Product Brief og PRD, inkludert IN/OUT scope.
> - Fullstendighet, intern konsistens, sporbarhet og testbarhet.
> - Om produktbeslutninger er tilstrekkelig avklart, eller feilaktig utsatt til UX/Architecture.
> - Om dokumentet er klart for neste BMAD-fase.
>
> Følg BMADs egne valideringskriterier. Rapporter faktiske avvik med alvorlighetsgrad, dokumentreferanse og minimal anbefalt rettelse.
>
> **Ikke endre noen prosjektfiler uten min godkjenning.** Avslutt med en tydelig vurdering av om PRD-en er klar for UX Design.

</details>

<details>
<summary><strong>Prompt 3 – Fortsett etter brutt tilkobling</strong> (2026-11-01)</summary>

> Tilkoblingen ble brutt etter at begge bakgrunnsagentene fullførte PRD-valideringen.
>
> Fortsett fra der du stoppet. Undersøk først om resultatene fra begge agentene og eventuelle rapporter i scratchpad fortsatt er tilgjengelige.
>
> Gjenbruk eksisterende resultater og fullfør BMAD Validate PRD med én samlet rapport som viser funn, alvorlighetsgrad, anbefalte rettelser og om PRD-en er klar for UX Design.
>
> Ikke start valideringen på nytt dersom resultatene kan gjenopprettes. Ikke endre noen prosjektfiler uten min godkjenning.

</details>

<details>
<summary><strong>Prompt 4 – Kopier rapportene til docs/</strong> (2026-11-01)</summary>

> Kopier de fire fullførte PRD-valideringsrapportene fra scratchpad til en egnet undermappe under `docs/`, uten å overskrive eksisterende filer. Behold originalrapportenes innhold uendret.
>
> Vis meg hvilke filer som er opprettet og `git status -sb`.
>
> Ikke endre `prd.md`, `product-brief.md`, `.memlog.md` eller andre eksisterende prosjektfiler. Ikke commit eller push ennå.
>
> Vi skal først vurdere valideringsfunnene og ta nødvendige produktbeslutninger.

</details>

<details>
<summary><strong>Prompt 5 – Innarbeid gruppens beslutninger i PRD-en</strong> (2026-11-01)</summary>

> Vi har nå gjennomgått BMAD Validate PRD-resultatene og tatt produktbeslutninger i gruppen.
>
> Oppgaven din er å oppdatere den eksisterende `prd.md` med **minimale, målrettede og konsistente endringer**, slik at PRD-en blir klar for UX Design.
>
> Dette er en kontrollert revisjon, ikke en ny PRD-workflow.
>
> ## 1. Les prosjektgrunnlaget
>
> Les først:
>
> - `CLAUDE.md`
> - gjeldende `prd.md`
> - nyeste `product-brief.md`
> - relevant `.memlog.md`
> - rapportene i `docs/prd-validering/2026-11-01/`
>
> Bruk prosjektets eksisterende struktur, begreper og krav-ID-er.
>
> Product Brief er godkjent og skal ikke endres. De tidligere valideringsrapportene skal bevares uendret.
>
> ## 2. Implementer følgende beslutninger
>
> ### H1 – Frister
>
> En tydelig frist med én dato skal behandles som en éndagsaktivitet.
>
> Startdato og sluttdato settes til samme dato når dokumentet tydelig beskriver en frist.
>
> Dette er et unntak fra regelen om at KI ikke skal anta éndagsvarighet bare fordi én dato er oppgitt.
>
> Dersom datoen er ufullstendig eller tvetydig, gjelder reglene i M1.
>
> Presiser relevante deler av Glossary, FR-17, User Journeys og eventuelle testbare konsekvenser.
>
> Ikke opprett en egen datatype for frister.
>
> ### H4 – Lesbarhet i årshjulet
>
> FR-13 skal stille et konkret, testbart krav om at alle aktiviteter kan finnes og åpnes selv om mange aktiviteter ligger i samme måned.
>
> Legg inn et akseptansescenario med 20 aktiviteter i én måned.
>
> Det er tillatt at årsvisningen sammenfatter aktiviteter eller angir at flere finnes, men ingen aktivitet skal være utilgjengelig.
>
> Den visuelle løsningen bestemmes i UX-workflowen.
>
> Ikke lås PRD-en til en bestemt knapp, indikator, popup eller layout.
>
> ### M1 – Ufullstendige datoer
>
> KI kan tolke årstall og datoer ut fra dokumentkontekst når det finnes tilstrekkelig grunnlag.
>
> Ved tvetydighet skal usikkerheten markeres tydelig.
>
> Når det ikke finnes forsvarlig grunnlag for en konkret dato, markeres feltet som manglende og må kompletteres av brukeren.
>
> En ukeangivelse uten konkret dag skal ikke automatisk gjøres om til en bestemt dato.
>
> Ikke anta at dokumentet gjelder kalenderåret som vises i årshjulet.
>
> Ta hensyn til at aktiviteter legitimt kan tilhøre et annet kalenderår.
>
> ### M2 og M3 – Dokumentgjennomgang og samlet lagring
>
> Dette er den viktigste endringen.
>
> Vi går bort fra umiddelbar lagring ved godkjenning av hvert aktivitetsforslag.
>
> Ny regel:
>
> 1. Brukeren laster opp ett dokument og får aktivitetsforslag.
> 2. Brukeren kan kontrollere, redigere, komplettere, godkjenne eller avvise forslagene individuelt.
> 3. Disse valgene er midlertidige under gjennomgangen.
> 4. Alle forslag må være godkjent eller avvist før gjennomgangen kan fullføres.
> 5. Brukeren må eksplisitt velge å fullføre og lagre.
> 6. Først da lagres alle godkjente aktiviteter samlet i planen.
> 7. Dersom gjennomgangen forkastes, lukkes eller avbrytes før fullføring, lagres ingen aktiviteter fra denne gjennomgangen.
> 8. Dersom applikasjonen lukkes, krasjer eller lastes på nytt før fullføring, går gjennomgangen tapt, og planen forblir uendret.
> 9. Brukeren kan ikke starte analyse av et nytt dokument mens en annen dokumentgjennomgang er aktiv.
> 10. Gjeldende gjennomgang må enten fullføres og lagres eller forkastes før en ny analyse kan starte.
>
> Selve lagringsoperasjonen skal være atomisk: enten lagres alle godkjente aktiviteter, eller ingen. En lagringsfeil må ikke føre til delvis lagring eller en uriktig melding om at lagringen var vellykket.
>
> Brukeren skal kunne forkaste en ufullstendig gjennomgang. UX avgjør hvordan denne handlingen og eventuelle bekreftelser presenteres.
>
> Det skal ikke implementeres automatisk duplikatkontroll i v1. En ny analyse av samme dokument kan generere forslag som allerede finnes i planen. Denne konsekvensen skal være tydelig for brukeren, mens UX bestemmer hvordan informasjonen presenteres.
>
> Oppdater alle berørte deler av PRD-en, spesielt:
>
> - UJ-1 og relevante edge cases
> - Glossary
> - FR-7
> - FR-15
> - FR-16 ved behov
> - FR-21 til FR-26
> - NFR-1
> - MVP Scope
> - eventuelle kryssreferanser og success metrics
>
> Undersøk også andre steder som omtaler umiddelbar lagring eller delvis fullført gjennomgang.
>
> Behold muligheten til å navigere mellom gjennomgangen og årshjulet innenfor samme aktive økt, uten å miste midlertidige valg. Dette skal ikke regnes som å avslutte gjennomgangen, og det skal fortsatt ikke være mulig å starte en ny dokumentanalyse før den første er avsluttet.
>
> Ikke bestem konkret navigasjon eller knappelayout. Det tilhører UX.
>
> ### M4 – Kategoriliste
>
> De konkrete kategoriene skal fortsatt bestemmes i UX-workflowen.
>
> Behold OQ-3.
>
> Presiser eventuelt at UX også skal vurdere behovet for en generell restkategori.
>
> Ikke definer kategorilisten nå, og ikke endre dagens prinsipp om at kategorier må velges fra en fast liste.
>
> ### M5 – Demo-modus
>
> Ved feil i analyse med språkmodellen skal brukeren få en forståelig feilmelding og informasjon om at demo-modus finnes for støttede testdokumenter.
>
> Det skal ikke skje automatisk overgang til demo-modus.
>
> Hvordan informasjon og valg presenteres, avgjøres i UX.
>
> Behold skillet mellom faktisk KI-analyse og forhåndsdefinerte demoresultater.
>
> ### H2 – Testbarhet av KI-atferd
>
> Presiser skillet mellom:
>
> **Deterministiske applikasjonskrav:**
> - validering av obligatoriske felt
> - håndtering av manglende og ugyldige verdier
> - kategoriliste
> - datoregel
> - kildeutdragverifisering
> - eksplisitt fullføring og atomisk lagring
> - korrekt håndtering av språkmodellens strukturerte svar
>
> **KI-kvalitet:**
> - om relevante aktiviteter blir identifisert
> - om datoer tolkes riktig
> - om forslag er korrekte
> - hvordan usikker informasjon identifiseres
>
> Det første skal kunne testes med tydelige, reproducerbare tester.
>
> Det andre skal evalueres mot fasit i SM-3, med dokumentasjon av variasjon og begrensninger.
>
> Ikke innfør en kunstig prosentgrense for KI-kvalitet.
>
> Behold relevante krav til språkmodellens ønskede atferd i FR-17, men ikke formuler probabilistisk modellkvalitet som om applikasjonen kan garantere feilfri KI.
>
> ### H3 – MVP-ferdigkriterier
>
> Presiser SM-1 og SM-2 slik at:
>
> - alle tre sentrale User Journeys kan gjennomføres fra start til slutt
> - alle funksjonelle krav innenfor MVP scope skal være implementert og verifisert
> - gjeldende Constraints og Non-Functional Requirements skal etterprøves etter sine relevante kriterier
> - testplanen fastsetter testmetoder, testdata, prosedyrer og testdybde, men kan ikke redusere hvilke MVP-krav som gjelder
> - feil, avvik og eventuelle begrensninger dokumenteres
>
> Ikke utvid MVP-scope.
>
> ## 3. Bevar PRD-ens struktur
>
> Behold:
>
> - eksisterende seksjonsstruktur
> - eksisterende krav-ID-er
> - de tre User Journeys
> - gjeldende produktvisjon
> - Product Brief sitt IN/OUT scope
> - eksisterende terminologi
> - relevante åpne spørsmål til UX, Architecture og testplan
>
> Ikke legg til nye funksjoner med mindre de følger direkte av beslutningene ovenfor.
>
> Hvis nye krav-ID-er er nødvendige, begrunn hvorfor før de opprettes. Foretrekk å oppdatere eksisterende krav.
>
> ## 4. Konsistenskontroll
>
> Etter redigering skal du gjennomgå hele PRD-en på nytt.
>
> Kontroller særlig:
>
> - ingen formuleringer om umiddelbar permanent lagring av enkeltforslag
> - ingen mulighet for delvis lagring ved avbrutt gjennomgang
> - ingen motsetning mellom FR-23, FR-25, FR-26 og NFR-1
> - ingen motsigelser mellom User Journeys og Features
> - korrekt behandling av frister og ufullstendige datoer
> - samsvar mellom Glossary og krav
> - korrekte FR- og seksjonsreferanser
> - ingen utilsiktede endringer i MVP-scope
> - ingen nye produktbeslutninger som burde tas av gruppen
>
> Bruk valideringsrapportene som kontrollgrunnlag, men ikke rett alle de 34 opprinnelige funnene automatisk. Denne oppgaven gjelder de beslutningene gruppen faktisk har tatt.
>
> Hvis du identifiserer en ny, vesentlig produktbeslutning, rapporter den i stedet for å bestemme på egen hånd.
>
> ## 5. Resultat og godkjenning
>
> Når redigeringen er fullført:
>
> 1. Vis `git status -sb`.
> 2. Vis `git diff --check`.
> 3. Vis `git diff -- prd.md`.
> 4. Oppsummer hvilke seksjoner og krav som er endret, og hvorfor.
> 5. Bekreft at Product Brief og de fire valideringsrapportene er uendret.
> 6. Oppgi eventuelle åpne problemstillinger som fortsatt må behandles før UX.
> 7. Gi en vurdering: Ready for UX – YES / NO, med begrunnelse.
>
> Ikke commit eller push.
>
> Ikke endre `product-brief.md`, tidligere valideringsrapporter eller andre eksisterende prosjektfiler.
>
> Oppdater bare `prd.md` på dette stadiet.
>
> Vent på min eksplisitte godkjenning før commit, push eller ytterligere filendringer.
>
> Målet er en presis, konsistent og ferdig PRD – ikke et lengre dokument enn nødvendig.

</details>

<details>
<summary><strong>Prompt 6 – D1 og beslutningshistorikk</strong> (2026-11-02)</summary>

> Vi har gjenopprettet Claude Code-samtalen etter omstart av PC-en.
>
> Den tidligere PRD-revisjonen er gjennomført, men vi har ennå ikke ferdigstilt siste gruppebeslutning D1 og oppdateringen av beslutningshistorikken.
>
> Fortsett med den siste avtalte oppgaven:
>
> 1. Innarbeid D1: Brukeren kan endre, redigere og omgjøre både godkjente og avviste aktivitetsforslag frem til eksplisitt «Fullfør og lagre».
> 2. Oppdater `.memlog.md` med gruppebeslutningene fra 2026-11-01 og D1, uten å overskrive tidligere beslutningshistorikk.
> 3. Korriger utdatert omtale av gjeldende Product Brief i PRD §4.5 og §8.2.
> 4. Gjennomfør konsistenskontroll og kontroller `git diff --check`.
> 5. Vis en kort oppsummering, `git status -sb` og diff for filene som er endret.
>
> Les gjeldende filer først, og kontroller hva som allerede er utført, slik at du ikke gjentar eksisterende endringer.
>
> Ikke endre Product Brief eller valideringsrapportene. Ikke commit eller push. Vent på min godkjenning.

</details>

<details>
<summary><strong>Prompt 7 – Avslutt PRD-fasen med commit og push</strong> (2026-11-02)</summary>

> Vi har nå gjennomgått og godkjent den siste PRD-revisjonen, inkludert D1 og oppdateringen av `.memlog.md`.
>
> Gruppen bekrefter også regelen du utledet i FR-22: Dersom et godkjent aktivitetsforslag redigeres, må alle obligatoriske felt fortsatt være gyldige ved fullføring. Ellers skal fullføring blokkeres.
>
> **Oppgaven er nå å avslutte PRD-fasen, ferdigstille prosessdokumentasjonen og gjennomføre commit og push til `origin/main`.**
>
> [...]

</details>

<details>
<summary><strong>Prompt 8 – Metadata til KI-loggen og PRD-dato</strong> (2026-11-02)</summary>

> Vi har nå avklart de tre opplysningene til KI-loggen:
>
> - **Deltakere:** Lars Tellef Risøy
> - **Kontrollert av:** Lars Tellef Risøy
> - **KI-verktøy:** Ja, ChatGPT ble brukt til å formulere og kvalitetssikre promptene til Claude Code.
>
> Gjennomfør følgende:
>
> 1. Fyll inn disse opplysningene i KI-loggutkastet.
> 2. Vis **hele KI-loggutkastet**, inkludert alle seksjoner og promptene slik de er dokumentert. Ikke bare oppsummer innholdet.
> 3. Korriger metadataene i `prd.md` fra `updated: 2026-11-01` til `updated: 2026-11-02`, siden siste PRD-endring ble gjort 2. november.
> 4. Kjør `git diff --check` og vis `git status -sb`.
> 5. Bekreft at ingen andre endringer er gjort.
>
> **Viktig:** Opplysningen om hvem som kontrollerer loggen er ikke i seg selv en endelig godkjenning. Jeg skal først lese og kontrollere hele utkastet.
>
> Ikke commit eller push. Ikke lagre KI-loggen permanent i repoet før jeg eksplisitt har godkjent innholdet.
>
> Vent på min tilbakemelding.

</details>

<details>
<summary><strong>Prompt 9 – Korrektur av KI-loggutkastet</strong> (2026-11-02)</summary>

> Jeg har gjennomgått KI-loggutkastet. Innholdet er i hovedsak godkjent, men noen tekstlige feil må korrigeres før endelig godkjenning.
>
> Gjør følgende minimale rettelser:
>
> 1. Kontroller hele utkastet for utilsiktet avkortede setninger, overskrifter og punktlister. Jeg har blant annet funnet `- ka`, `- Pr`, `.memlo` og `**D1** (`. Gjenopprett disse fra den faktiske samtalehistorikken eller tilgjengelige kilder. Ikke gjett manglende tekst.
> 2. Skill mellom bevisst forkortede prompter med `[...]` og utilsiktet avkortet tekst. Behold tillatte forkortelser, men gjør dem konsekvente og tydelige.
> 3. Inkluder prompt 8 og dokumenter at den førte til utfylling av KI-loggmetadata og endring av `updated` i PRD til 2026-11-02.
> 4. Kontroller at dokumentasjonen av D1 inkluderer at godkjente og avviste forslag kan redigeres og omgjøres frem til fullføring, og at obligatoriske felt fortsatt må være gyldige ved fullføring.
> 5. Kontroller at datoer, verktøybruk, valideringsresultater og utførte tester stemmer med faktisk historikk.
>
> Behold følgende metadata:
> - Deltakere: Lars Tellef Risøy
> - Kontrollert av: Lars Tellef Risøy
> - KI-verktøy: Claude Code og ChatGPT
>
> Vis deretter den korrigerte KI-loggen i sin helhet. Dersom den er for lang for ett svar, vis den i tydelig nummererte deler uten å kutte setninger.
>
> Ikke endre andre prosjektfiler. Ikke lagre KI-loggen permanent i repoet. Ikke commit eller push før jeg eksplisitt har godkjent den korrigerte versjonen.

</details>

## Hva KI leverte

**Validering (prompt 2–3).** Claude Code kjørte `bmad-prd` med Validate-intent.
To underagenter vurderte PRD-en hver for seg. Den ene brukte BMADs
kvalitetsrubrikk med sju dimensjoner. Den andre sammenlignet PRD-en med nyeste
Product Brief og `.memlog.md` og testet samspillet mellom kravene. Claude Code
kontrollerte funnene mot kildetekstene og laget én samlet rapport:

- **Karakter:** Fair, fordi BMADs regel gir Fair ved ethvert high-funn.
- **Funn:** 0 critical, 4 high, 23 medium og 7 low.
- **Vurdering:** Ikke klar for UX før sju punkter var avgjort.

Ved sammenstillingen endret Claude Code to av agentenes vurderinger:

- **H1 (frister):** Agenten mente KI-loggen fra 2026-11-01 motsa PRD-en. Claude Code mente at loggen bevisst skiller lagrede frister fra KI-tolkning, og omtalte funnet som en manglende beslutning. Alvorlighetsgraden ble beholdt som high.
- **M13 (testdeltakere):** Funnet ble nedgradert fra high til medium, fordi memlog viser at SM-1 var et bevisst valg.

Rapportene ble først lagt i en midlertidig mappe, fordi brukeren ikke hadde gitt
lov til å endre prosjektfiler. I prompt 4 ble de kopiert uendret til
`docs/prd-validering/2026-11-01/`:

- `validation-report.html`
- `validation-report.md`
- `review-rubric.md`
- `review-brief-og-beslutninger.md`

**Revisjon av PRD-en (prompt 5).** Claude Code gjorde gruppens beslutninger om til
endringer i `prd.md`. Det ble ikke opprettet nye FR-, NFR-, C-, SM- eller OQ-ID-er.
Det nye er edge cases i UJ-1 (E6a og E9–E11) og Glossary-begrepene Frist,
Ubehandlet aktivitetsforslag, Fullføring og Forkasting av gjennomgang. Claude
Code meldte at D1 var en uavklart produktbeslutning, og listet regler som var
utledet av beslutningene, slik at gruppen kunne ta stilling til dem.

**D1 og beslutningshistorikk (prompt 6).** Claude Code tok D1 inn i UJ-1,
Glossary, §4.4, FR-22–FR-24 og §8.2. Utdatert omtale av briefen i §4.5 og §8.2
punkt 1 og 4 ble rettet. Med BMADs `memlog.py` ble 13 oppføringer lagt til i
`.memlog.md`. Skriptet skrev filen med CRLF-linjeskift, og Claude Code
konverterte den tilbake til LF i tråd med `.gitattributes`.

**Avslutning (prompt 7).** Claude Code kontrollerte OQ-1 og fant ikke behov for
endring (se under). Claude Code la til to memlog-oppføringer: gruppens bekreftelse
av FR-22-regelen og avslutningen av PRD-fasen. Claude Code skrev også sesjonsloggen
og oppdaterte `issues.md`, laget utkast til denne oppføringen og gjennomførte
kontrollene før commit. Commit og push ble ikke gjennomført, fordi KI-loggen
etter `CLAUDE.md` og `docs/ki-logg/README.md` først måtte kontrolleres og
godkjennes av et gruppemedlem.

**Metadata og PRD-dato (prompt 8).** Claude Code fylte inn deltaker, kontrollør
og bruken av ChatGPT i dette utkastet, og endret `updated` i frontmatter til
`prd.md` fra 2026-11-01 til 2026-11-02.

**Korrektur (prompt 9).** Brukeren meldte om avkortet tekst i utkastet
(`- ka`, `- Pr`, `.memlo` og `**D1** (`). Claude Code søkte gjennom fila og fant
ingen avkortede linjer. Teksten sto hel (`- kategoriliste`,
`- Product Brief sitt IN/OUT scope`, `.memlog.md` og `**D1** (prompt 6)`), så
avkortingen må ha oppstått da teksten ble vist. Claude Code la deretter til
prompt 8 og 9, beskrev forkortingen av prompt 7 og presiserte D1 og
memlog-oppføringene.

## Hva vi endret og hvorfor

**Gruppens beslutninger etter valideringen** (prompt 5):

- **H1:** En tydelig frist med én dato registreres som éndagsaktivitet. Frist er ingen egen datatype.
- **H4:** FR-13 får et akseptansescenario med 20 aktiviteter i én måned. Alle aktiviteter skal kunne finnes og åpnes, men årsvisningen kan sammenfatte.
- **M1:** KI kan tolke årstall og dato ut fra dokumentkonteksten, og markerer tvetydighet som usikker. Uten forsvarlig grunnlag, og ved uke uten dag, blir feltet manglende. KI antar ikke at dokumentet gjelder kalenderåret som vises.
- **M2/M3:** Valgene i gjennomgangen er midlertidige. Alle forslag må være godkjent eller avvist før eksplisitt «Fullfør og lagre». Da lagres de godkjente samlet og atomisk. Ny analyse er sperret mens en gjennomgang er aktiv, og det er ingen duplikatkontroll i v1.
- **M4:** Kategorilisten avgjøres fortsatt i UX (OQ-3), som også skal vurdere en restkategori.
- **M5:** Ved feil i analysen får brukeren informasjon om demo-modus. Det skjer ingen automatisk overgang til demo-modus.
- **H2:** FR-17 er delt i deterministiske applikasjonskrav og ønsket modellatferd. Modellatferden evalueres i SM-3, uten prosentgrense.
- **H3:** SM-1 og SM-2 krever alle tre UJ-er og alle MVP-krav. Testplanen kan ikke redusere kravene.

**Endret lagringsmodell.** M2/M3 erstatter umiddelbar lagring ved hver
godkjenning med samlet, atomisk lagring ved fullføring. De tidligere
beslutningene A20 og A21 er derfor delvis erstattet. Dette står som en override i
`.memlog.md` og som revidert i PRD §11.2.

**D1** (prompt 6): Godkjente og avviste aktivitetsforslag kan redigeres og
omgjøres fram til «Fullfør og lagre». Et godkjent forslag som redigeres, må
fortsatt ha gyldige obligatoriske felt ved fullføring, ellers blokkeres
fullføringen. Denne delen av regelen ble utledet av Claude Code og bekreftet av
gruppen i prompt 7 (FR-22).

**KI-forslag som gruppen godkjente:**

- **FR-22-regelen:** Claude Code utledet at et godkjent forslag som redigeres, fortsatt må oppfylle FR-2, ellers blokkeres fullføringen. Gruppen bekreftet regelen uttrykkelig i prompt 7.
- **Øvrige regler:** Claude Code meldte disse som utledet, og de inngikk i revisjonen gruppen godkjente i prompt 7:
  - en gjennomgang kan fullføres selv om alle forslagene er avvist
  - ved lagringsfeil forblir gjennomgangen aktiv
  - datoer vises med årstall under gjennomgangen
  - tekst i årsvisningen skal ikke overlappe slik at den blir uleselig
  - OQ-3 spør også om frister trenger egen kategori

**Ikke endret:**

- **Øvrige valideringsfunn:** De ble ikke rettet, fordi gruppen ba om bare å innarbeide beslutningene sine (prompt 5).
- **Product Brief:** Uendret.
- **OQ-1:** Teksten er en datert konstatering fra 2026-10-22. Den stemmer fortsatt: brief-gjennomgangen fant ingen motstrid etter forkortingen, og briefen gjentar ikke detaljene i §8.2.

## Testing

Dokumentarbeid, så ingen programvare er testet. Disse kontrollene ble faktisk
kjørt:

- **Git-formatering:** `git diff --check` uten funn etter revisjonen (prompt 5), etter D1 (prompt 6), i kontrollen før commit (prompt 7) og etter datoendringen (prompt 8).
- **Product Brief:** `git diff --quiet` bekreftet at den er uendret.
- **Valideringsrapportene:** `cmp` bekreftet at de fire rapportene i `docs/prd-validering/2026-11-01/` er byte-identiske med originalene.
- **Beslutningshistorikk:** Linje 5–168 i `.memlog.md` ble sammenlignet med en kopi tatt før oppdateringen og var uendret. En telling viste 0 CR-bytes i `prd.md` og `.memlog.md` etter konverteringen.
- **Søk etter utdatert tekst:** `grep` fant ingen rester av umiddelbar lagring, bekreftelse av forkasting ved ny opplasting eller utdatert omtale av briefen.
- **ID-kontinuitet:** FR-1–30, NFR-1–10, C-1–8, SM-1–4, OQ-1–10 og P-1–5 er sammenhengende og unike.
- **ISO-ukenumre:** Eksemplene i FR-10 ble regnet på nytt av begge underagentene og stemte.
- **Hemmeligheter:** Et `grep`-søk etter API-nøkler og andre hemmeligheter i filene som skal committes, ga ingen treff (prompt 7).
- **Avkortet tekst:** Et `grep`- og `awk`-søk i utkastet fant ingen avkortede linjer, og fila ble kontrollert for gyldig UTF-8 (prompt 9).

**Ikke gjennomført:** Ny BMAD-validering etter revisjonen, og gjennomlesing av
PRD-en i gjengitt form (HTML eller PDF).

**Kjente begrensninger:**

- Rapportene inneholder henvisninger til den midlertidige mappen og uttalelser om at repoet ikke var endret. Det stemte da rapportene ble skrevet, og innholdet er bevart uendret.
- `_bmad/bmm/config.yaml` angir engelsk som kommunikasjonsspråk, men økten og rapportene er på norsk etter brukerens prompter.
