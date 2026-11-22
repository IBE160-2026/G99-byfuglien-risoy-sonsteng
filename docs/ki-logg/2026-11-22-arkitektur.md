# 2026-11-22 — Arkitektur: BMAD Architecture (Coaching path) og Reviewer Gate

> **Status:** Utkastet ble laget av Claude Code ved slutten av økten. Elias Wahlquist Sønsteng har kontrollert og godkjent loggen 22. november 2026 (se `CLAUDE.md` og `docs/ki-logg/README.md`).

- **Deltakere:** Elias Wahlquist Sønsteng (arkitekturansvarlig)
- **KI-verktøy:**
  - Claude Code med modellen Claude Opus 5.5 (`claude-opus-5-5`), kjørt i en skysesjon i Claude-appen med en lesekopi av repoet, og i en Remote Control-sesjon på Elias' Mac for alle endringer i arbeidskopien (branch, memlogg, commit og push). Claude Code fulgte BMAD-skillen `bmad-architecture` (Coaching path) og skrev memlogg-oppføringene med `_bmad/scripts/memlog.py` via `uv`. Reviewer Gate ble kjørt med fem underagenter i skyen: rubric-gjennomgang, versjonskontroll mot npm, motstanderpar (adversarial unit pairs) og `bmad-review` med lensene `adversarial` og `edge-case-hunter`. Lensene `structure` og `prose` ble ikke kjørt, fordi spinen er et kortfattet byggegrunnlag og ikke prosa.
  - ChatGPT (OpenAI) som sparringspartner og kontroll. Ifølge promptene gikk Elias gjennom rapportene med ChatGPT før han ga tilbakemelding, og flere av promptene er formulert med ChatGPT. ChatGPT gjorde ingen endringer i repositoryet.
  - Elias tok alle beslutningene. De er merket som godkjent av Elias og ventende på gruppevedtak i spinen og memloggen; gruppen har ikke behandlet dem ennå.
- **Kontrollert av:** Elias Wahlquist Sønsteng (godkjent 22. november 2026)

## Oppgave

Økten startet arkitekturfasen for Sambandet. Målet var å avklare systemgrenser, lagring og aktivitetsmodell, KI-leverandør (OQ-6), demo-modus (OQ-7, som blokkerer UX Finalize), teknologistack, grenseverdier (OQ-8) og teststrategi, én beslutning om gangen, og samle dem i et arkitekturdokument (`ARCHITECTURE-SPINE.md`) med beslutningshistorikk i `.memlog.md`. Dokumentet skulle deretter gjennom BMAD Reviewer Gate før commit. PRD-en var frosset, og UX-dokumentene ble ikke endret.

## Prompt (ordrett)

Loggen gjengir alle 13 promptene i kronologisk rekkefølge. Bare prompt 8 er forkortet med `[...]`: de sju memlogg-kommandoene er kuttet, fordi teksten deres står ordrett i `.memlog.md`. Claude Codes svar og Remote Control-instruksjonene er ikke tatt med.

| Nr. | Prompt |
|---|---|
| 1 | Kartlegging og plan (read-only) |
| 2 | Start av Coaching path, punkt 1: Hovedgrenser |
| 3 | Punkt 1 godkjent, punkt 2: Datalagring og aktivitetsmodell |
| 4 | Punkt 2 godkjent, punkt 3: OQ-6 |
| 5 | Punkt 3 godkjent, punkt 4: OQ-7 |
| 6 | Punkt 4 godkjent, notat til Sebastian |
| 7 | Notatet godkjent, memlogg og punkt 5: Teknologistack |
| 8 | Opprett branch og memlogg på Mac-en |
| 9 | Memlogg-commit og valg av stack (S1), punkt 6: OQ-8 |
| 10 | OQ-8 godkjent, punkt 7: Teststrategi og lokal kjøring |
| 11 | Punkt 7 godkjent, skriv arkitekturdokumentet |
| 12 | Tre tillegg godkjent, kjør Reviewer Gate |
| 13 | Reviewer Gate-regler godkjent, memlogg og logger før commit |

<details>
<summary><strong>Prompt 1 – Kartlegging og plan (read-only)</strong></summary>

> Sambandet – oppstart av BMAD Architecture
> Vi skal starte arkitekturfasen for gruppeprosjektet Sambandet i IBE160 Programmering med KI ved Høgskolen i Molde.
> Du skal fungere som teknisk arkitekturveileder i Claude Code og hjelpe meg å gjennomføre BMAD Architecture systematisk, med én avgrenset oppgave om gangen.
> Vi bruker VS Code, GitHub og Claude Code. Svar på norsk bokmål, men behold etablerte tekniske fagbegreper på engelsk.
> Viktig: Vi skal fortsette det eksisterende prosjektet, ikke etablere et nytt produkt. Produktkrav og UX-beslutninger skal legges til grunn for arkitekturen.
> 1. Prosjektinformasjon
> Repository:
> IBE160-2026/G99-byfuglien-risoy-sonsteng
> Prosjekt: Sambandet.
> Sambandet er en planleggingsapplikasjon for ledere og planleggingsteam, med operative ledere i Forsvaret som første målgruppe.
> Løsningen skal:
>
> * Samle aktiviteter i et visuelt årshjul, med månedsvisning og aktivitetsdetaljer.
> * Tillate manuell opprettelse, redigering og sletting av aktiviteter.
> * La brukeren laste opp eksisterende dokumenter.
> * Bruke KI til å hente ut forslag til aktiviteter.
> * La brukeren kontrollere, korrigere, godkjenne eller avvise forslag før de lagres.
> * Ha en demo-modus der kjerneflyten kan demonstreres uten API-nøkkel og uten betalt KI.
>
> Dette er en kort introduksjon, ikke en fullstendig kravspesifikasjon. PRD er styrende for produktkravene.
> 2. Status ved overlevering
> Product Brief og PRD er ferdigstilt.
> UX-fasen er gjennomført frem til Finalize-forberedelsene. UX-ansvarlig har ferdigstilt:
>
> * DESIGN.md og EXPERIENCE.md, begge med status: draft.
> * Dokumentasjon for F1–F8.
> * Syv Excalidraw-skisser og tilhørende forhåndsvisninger.
> * Fire godkjente HTML-nøkkelmocker for F1, F2, F4 og F7.
> * UX-beslutninger og dokumentasjon i eksisterende memlogg.
> * BMAD-review og språkvask.
>
> Siste bekreftede UX-commit:
> 9a0c3e8a666ec38b8b8f8a0afaa7d29392c636ff
> Branch:
> ux/sebastian-ux-design
> Denne branchen var ren og synkronisert med origin ved overleveringen.
> Ikke endre UX-branchen eller UX-dokumentene uten avtale med UX-ansvarlig.
> Arkitekturen skal utvikles i eget arbeidsløp og egen branch etter at vi har kontrollert Git-status og blitt enige om branchstrategien.
> 3. Første oppgave – READ ONLY
> Start med å kartlegge prosjektet.
> Ikke opprett eller endre filer i denne runden.
> A. Kontroller Git og utviklingsmiljø
> Undersøk:
>
> 1. Hvilket repository og hvilken lokal mappe vi arbeider i.
> 2. Aktiv branch og HEAD.
> 3. Om arbeidsområdet er rent.
> 4. Om lokal branch og origin er synkronisert.
> 5. Om det finnes nye commits på origin/main.
> 6. Om min GitHub-konto har nødvendige rettigheter.
> 7. Hvilke verktøy og BMAD-skills som er tilgjengelige.
>
> Du kan kjøre git fetch --prune origin, men ikke merge, pull, rebase eller endre branch ennå.
> Hvis det finnes ucommittede endringer eller uventede avvik, stopp og rapporter.
> Ikke vis API-nøkler, tokens eller andre hemmeligheter.
> B. Les prosjektinstruksjonene
> Finn og les:
>
> * CLAUDE.md
> * AGENTS.md
> * Relevante README-filer.
> * docs/ki-logg/README.md
> * Instruksjoner for sesjonslogg og issues.md.
> * Tilgjengelige BMAD Architecture-instruksjoner og workflow-skills.
>
> Kontroller faktisk BMAD-versjon og hvilke arbeidsflyter som finnes. Ikke anta at et bestemt kommandonavn er riktig.
> C. Les eksisterende prosjektgrunnlag
> Finn og gjennomgå:
>
> 8. Product Brief.
> 9. Gjeldende PRD.
> 10. PRD-validering og relevante tilbakemeldinger.
> 11. DESIGN.md.
> 12. EXPERIENCE.md.
> 13. UX-memloggen og sentrale gruppevedtak.
> 14. Eksisterende prosjektlogg og åpne spørsmål.
> 15. Eventuelle arkitekturdokumenter som faktisk tilhører Sambandet.
>
> UX-dokumentasjonen finnes på origin/ux/sebastian-ux-design.
> Les den uten å bytte branch eller endre arbeidsområdet, for eksempel med git show, dersom den ikke finnes i den aktive arbeidskopien.
> Kontroller om main og UX-branchen har ulikt dokumentinnhold. Ikke velg en eldre versjon uten å rapportere forskjellen.
> Vær spesielt oppmerksom på at det tidligere er observert en architecture/technology.md på main som gjelder prosjektet pytagoras-website-v2. Den skal ikke behandles som en vedtatt arkitektur for Sambandet.
> 4. Kartlegg arkitekturarbeidet
> Med PRD og UX som grunnlag, identifiser hvilke tekniske områder arkitekturen må avklare.
> Undersøk særlig:
>
> * Frontend og visning av kalender og årshjul.
> * Backend og applikasjonslogikk.
> * Datalagring og aktivitetsmodellen.
> * Dokumentopplasting, validering og tekstuttrekk.
> * Integrasjon med språkmodell og håndtering av API-nøkler.
> * KI-forslag, kildeutdrag og godkjenningsflyt.
> * Demo-modus med forhåndsdefinerte forslag.
> * Feilhåndtering, personvern og sikkerhet.
> * Testbarhet, etterprøvbarhet og lokal kjøring.
>
> Målet er en enkel, gjennomførbar og vedlikeholdbar arkitektur som dekker PRD. Unngå overengineering.
> Ikke velg teknologistack ennå. Presenter først hvilke beslutninger BMAD Architecture krever, og hvilke føringer prosjektet allerede har.
> 5. Særlig viktig: OQ-7
> UX-ansvarlig har overlevert OQ-7 til arkitekturen fordi dette blokkerer formell UX Finalize.
> Tre tekniske spørsmål gjenstår:
> A – Hvordan aktiveres demo-modus?
>
> * Eksplisitt ved oppstart, eksempelvis med miljøvariabel eller startskript?
> * Automatisk når API-nøkkel mangler?
> * Andre alternativer må begrunnes opp mot eksisterende krav.
>
> B – Hva skjer uten API-nøkkel i vanlig modus?
>
> * Starter applikasjonen normalt, mens dokumentanalyse gir en tydelig feilmelding?
> * Eller er dokumentopplasting deaktivert med forklaring allerede fra oppstart?
>
> C – Hvordan gjenkjennes støttede testdokumenter?
>
> * Hash av filinnhold?
> * Hash av normalisert tekstinnhold?
> * Hvordan sikrer vi at vilkårlige dokumenter ikke får feilaktige forhåndsdefinerte KI-forslag?
>
> Relevante krav omfatter særlig PRD FR-18, FR-20, FR-30, C-3, C-4, C-5 og NFR-10.
> Foreløpig anbefaling fra UX-gjennomgangen er eksplisitt aktivering ved oppstart, normal oppstart uten API-nøkkel og innholdskontroll for testdokumenter.
> Dette er anbefalinger, ikke gruppevedtak.
> Arkitekturansvarlig skal undersøke konsekvensene før gruppen tar beslutningene.
> Undersøk også OQ-6 og OQ-8 og hvordan de henger sammen med arkitekturen. Vurder særlig lagring av aktiviteter i demo-modus uten å fastsette ny funksjonalitet.
> 6. Planlegg BMAD Architecture
> Etter kartleggingen ønsker jeg en konkret plan for hvordan vi skal gjennomføre arkitekturarbeidet.
> Planen skal inneholde:
>
> 16. Hvilken BMAD Architecture-workflow vi skal bruke.
> 17. Hvilke eksisterende dokumenter den krever som input.
> 18. Anbefalt egen Git-branch og utgangspunkt for branchen.
> 19. Hvilke arkitekturbeslutninger som må tas, og i hvilken rekkefølge.
> 20. Hvordan OQ-7 bør avklares og overleveres til UX-ansvarlig.
> 21. Hvilke arkitekturartefakter vi skal produsere.
> 22. Hvordan beslutninger, KI-bruk og endringer skal dokumenteres.
> 23. Hvor kontroll- og godkjenningspunktene bør ligge.
>
> Prioriter korte, kontrollerbare arbeidsrunder. Jeg ønsker å gjennomgå og forstå viktige beslutninger før du går videre.
> 7. Begrensninger
> I denne første runden skal du IKKE:
>
> * Starte BMAD Architecture.
> * Opprette ny branch.
> * Opprette eller endre filer.
> * Endre PRD, Product Brief eller UX-dokumenter.
> * Bestemme teknologistack.
> * Registrere nye produkt- eller gruppevedtak.
> * Installere verktøy.
> * Committe eller pushe.
> * Merge eller rebase branches.
> * Starte implementering.
>
> 8. Rapporter og stopp
> Lever en oversikt med:
>
> 24. Git-status og tilgjengelig utviklingsmiljø.
> 25. Dokumenter og prosjektinstruksjoner som er lest.
> 26. Gjeldende produkt- og UX-grunnlag.
> 27. Åpne arkitekturspørsmål, inkludert OQ-6, OQ-7 og OQ-8.
> 28. Anbefalt branchstrategi.
> 29. Trinnvis plan for BMAD Architecture.
> 30. Eventuelle avvik eller risikoer før vi starter.
>
> Stopp etter rapporten.
> Jeg vil gjennomgå resultatet med ChatGPT før vi oppretter arkitekturbranchen og starter selve workflowen.
>
>
>
> Jeg skal lage arkitektur. Gi meg en liste over hva jeg skal gjøre og få meg på veien.

</details>

<details>
<summary><strong>Prompt 2 – Start av Coaching path, punkt 1: Hovedgrenser</strong></summary>

> Vi skal nå gjennomføre BMAD Architecture (Coaching path) for prosjektet **Sambandet** i branch `arch/elias-architecture`. Svar på norsk bokmål, men behold etablerte tekniske fagbegreper på engelsk.
>
> ### Kontekst og premisser som allerede er avklart:
> 1. **Branch og grunnlag:** Branchen er opprettet fra `origin/ux/sebastian-ux-design` (med `origin/main` merget inn) slik at vi bygger på nyeste PRD (11.11) og UX-grunnlaget (`DESIGN.md`, `EXPERIENCE.md`, F1–F8 og HTML-mockups).
> 2. **Skjæreliste og ansvarsfordeling:**
>    - **Jeg (Arkitektur):** Eier arkitekturdokumentasjonen og avklarer systemgrenser, lagring/datamodell, KI-integrasjon, demo-modus, teknologistack, OQ-6, OQ-7, OQ-8 og teststrategi.
>    - **UX-ansvarlig (Sebastian):** Eier `DESIGN.md`, `EXPERIENCE.md` og UX-skisser/mockups. Vi skal **ikke** endre UX-filer i dette arbeidet.
>    - **PRD:** Produktkravene er frosset. Endringer i krav krever eget gruppevedtak.
>    - **Gamle filer:** Ignorer `architecture/technology.md` fra `main` (den tilhører et annet prosjekt, *pytagoras-website-v2*).
> 3. **Arbeidsmetode (VIKTIG):**
>    - Jobb stegvis med **én avgrenset beslutning om gangen**.
>    - **Skill tydelig mellom forslag og vedtak:** Presenter alternativer, anbefaling og konsekvenser, og **stopp** for å la meg godkjenne eller ta saken til gruppen før du dokumenterer noe som vedtatt eller går videre til neste punkt.
>    - Følg prosjektets regler i `CLAUDE.md`, `AGENTS.md` og `docs/ki-logg/README.md`.
>
> ### Rekkefølge på arkitekturbeslutningene vi skal gjennomgå:
> 1. Hovedgrenser (System Boundaries: nettleser vs. lokal server, håndtering av API-nøkler)
> 2. Datalagring og aktivitetsmodell
> 3. OQ-6 (avklaringer knyttet til lagring/demo-flyt)
> 4. OQ-7 (aktivering av demo-modus, oppstart uten API-nøkkel og gjenkjenning av testdokumenter – dette blokkerer UX Finalize og skal overleveres til Sebastian så snart vi har vedtatt det)
> 5. Teknologistack (enkel, vedlikeholdbar og uten overengineering)
> 6. OQ-8 (konkrete verdier og grenser)
> 7. Teststrategi og lokal kjøring
>
> ### Din første oppgave nå:
> Bekreft kort at du har lest gjeldende PRD (11.11), `DESIGN.md`, `EXPERIENCE.md` og prosjektinstruksjonene (`CLAUDE.md` / `AGENTS.md`), og legg deretter frem **kun punkt 1: Hovedgrenser (System Boundaries)** med konkrete alternativer, anbefaling og konsekvenser. Stopp etter dette og vent på min tilbakemelding.

</details>

<details>
<summary><strong>Prompt 3 – Punkt 1 godkjent, punkt 2: Datalagring og aktivitetsmodell</strong></summary>

> Vi går videre med følgende tilbakemelding på Punkt 1 (Hovedgrenser):
>
> 1. **Alternativ B (Nettleser-UI og én lokal server):** Godkjent som arkitekturretning (jeg tar med de overordnede arkitekturbeslutningene til samlet godkjenning i gruppen, men du kan føre Alternativ B inn i arkitekturgrunnlaget nå).
> 2. **Tekstuttrekk på serveren:** Enig. Å samle tekstuttrekk, normalisering, kildeverifisering (FR-28) og KI-kall på serveren gir en ren, testbar pipeline og gjør det enkelt å slette dokument og tekst rett etter analysen (FR-16).
> 3. **Gjennomgang i nettleserens minne:** Enig. Det oppfyller FR-26 direkte og gjør «Fullfør og lagre» til en tydelig atomisk operasjon (NFR-1).
>
> Jeg pusher `arch/elias-architecture` til GitHub nå.
>
> Gå videre til **punkt 2: Datalagring og aktivitetsmodell**. Legg frem alternativer, anbefaling og konsekvenser, og stopp for min tilbakemelding.

</details>

<details>
<summary><strong>Prompt 4 – Punkt 2 godkjent, punkt 3: OQ-6</strong></summary>

> Vi går videre med følgende tilbakemelding på Punkt 2 (Datalagring og aktivitetsmodell):
>
> 1. **Lagring – Velger A2 (Én JSON-fil som serveren eier):** Godkjent. Atomisk skriving via midlertidig fil (NFR-1), `schemaVersion`, lesbar fil for testing og regelen om å aldri overskrive en skadet fil er en veldig ren løsning. Å samle dette i én lagringsmodul gjør også valget reversibelt.
> 2. **Aktivitetsmodellen og feltene:** Enig i feltene (`id`, `tittel`, `ansvarsomrade`, `startdato`, `sluttdato`, `kategori`, `merknader`), samt at KI-opprinnelse/kildeutdrag ikke lagres permanent og at uke/måned beregnes ved visning. Dobbeltsjekk at feltnavn og eventuelle valgfrie felt matcher `DESIGN.md` og UX-mockups, og ta med merknaden om samtidige faner i README-planen.
> 3. **Datoformat:** Enig i ren `ÅÅÅÅ-MM-DD` uten tidssone for å unngå tidssone-forskyvninger.
> 4. **Kategori:** Enig i å lagre kategori som en fast bokstavkode fra én felles definert liste.
>
> Gå videre til **punkt 3: OQ-6**. Legg frem alternativer, anbefaling og konsekvenser, og stopp for min tilbakemelding.

</details>

<details>
<summary><strong>Prompt 5 – Punkt 3 godkjent, punkt 4: OQ-7</strong></summary>

> Vi går videre med følgende beslutning på Punkt 3 (OQ-6):
>
> 1. **Leverandør:** Vi velger **Alternativ A (Anthropic)** (tas med til samlet godkjenning i gruppen, men føres inn i arkitekturgrunnlaget nå).
> 2. **Modellvalg:** Enig i at konkret modellnavn (f.eks. Haiku eller Sonnet) settes via miljøvariabel og avgjøres etter en kort sammenligningstest i punkt 5–6.
> 3. **Regel 1–6:** Godkjent i sin helhet, inkludert versjonerte prompt-filer i `prompts/`, felles svarskjema der applikasjonen setter «ugyldig», og total tidsgrense inkludert nye forsøk.
>
> Gå videre til **punkt 4: OQ-7** (aktivering av demo-modus, oppstart uten API-nøkkel, gjenkjenning av testdokumenter og lagring i demo-modus). Legg frem alternativer, anbefaling og konsekvenser, og stopp for min tilbakemelding.

</details>

<details>
<summary><strong>Prompt 6 – Punkt 4 godkjent, notat til Sebastian</strong></summary>

> Vi går videre med følgende beslutning på Punkt 4 (OQ-7):
>
> 1. **A1, B1, C2 og D1 er godkjent** (tas med til samlet godkjenning i gruppen, men føres inn som vedtatt arkitekturretning nå).
>    - **Merknad:** Sørg for at API-kontrakten mellom frontend og server inkluderer at serveren opplyser om `demoMode` ved oppstart (f.eks. via et enkelt oppstarts-/helse-endepunkt), slik at nettleseren vet når demo-merket skal vises.
> 2. **Notat til Sebastian:** Ja, skriv et kort, presist overleveringsnotat til Sebastian nå som oppsummerer A1, B1, C2 og D1, inkludert hvordan nettleseren får vite at `demoMode` er aktivt ved oppstart, og hvilke tre mikrotekster/justeringer han trenger for å fullføre UX Finalize.
>
> Stopp etter at du har vist utkastet til notatet til Sebastian, før vi går videre til **punkt 5: Teknologistack**.

</details>

<details>
<summary><strong>Prompt 7 – Notatet godkjent, memlogg og punkt 5: Teknologistack</strong></summary>

> Notatet til Sebastian er godkjent – jeg sender det over til ham nå.
>
> Loggfør OQ-7-vedtaket i memloggen i tråd med prosjektets rutiner, og gå deretter videre til **punkt 5: Teknologistack**. Legg frem alternativer, anbefaling (enkel, vedlikeholdbar og uten overengineering) og konsekvenser, og stopp for min tilbakemelding.

</details>

<details>
<summary><strong>Prompt 8 – Opprett branch og memlogg på Mac-en</strong></summary>

> Ja, kjør dette i `/Users/eliassonsteng/G99-byfuglien-risoy-sonsteng`, men **ikke** lag branch fra `main` – den nyeste PRD-en (11.11) og UX-grunnlaget ligger på `origin/ux/sebastian-ux-design`.
>
> Gjør følgende i nøyaktig denne rekkefølgen:
>
> 1. Hent siste endringer og opprett riktig arkitekturbranch:
>    - `git fetch --prune origin`
>    - `git switch -c arch/elias-architecture origin/ux/sebastian-ux-design`
>    - `git merge origin/main`
>    - `git push -u origin arch/elias-architecture`
>    *(Stopp og si fra hvis det oppstår en merge-konflikt eller feil.)*
>
> 2. Når du står på `arch/elias-architecture`, kjør memlogg-oppsettet **én enkelt gang** (ikke duplikatet):
>    ```bash
>    W=_bmad-output/planning-artifacts/architecture/architecture-G99-byfuglien-risoy-sonsteng-2026-11-22
>    [...]
>    ```

</details>

<details>
<summary><strong>Prompt 9 – Memlogg-commit og valg av stack (S1), punkt 6: OQ-8</strong></summary>

> Ja, commit og push memloggen nå med meldingen:
> `docs(arkitektur): start memlogg med beslutninger for punkt 1–4`
>
> Her er svarene på Punkt 5 (Teknologistack):
> 1. **Valg av stack:** Vi velger **S1 (TypeScript i hele løsningen)** med React + Vite (`client/`), Node-server (`server/`), delt validering/skjema (`shared/`), `prompts/`, `testdata/` og `data/` (gitignored).
> 2. **Språkkompetanse i gruppen:** Vi har erfaring med JavaScript/TypeScript (og grunnleggende webutvikling), så felles TypeScript på frontend og backend gir minst friksjon og enklest oppstart for sensor (`npm install` og `npm run demo`).
>    - **Merknad:** Bruk et minimalt og velkjent HTTP-rammeverk på serveren (f.eks. Express) og et rent JS/TS PDF-bibliotek uten eksterne systembinærfiler på Mac/Windows.
>
> Loggfør stack-beslutningen i memloggen, verifiser og lås anbefalte pakkeversjoner, og legg deretter frem **kun Punkt 6: OQ-8** (konkrete verdier og grenser) med alternativer, anbefaling og konsekvenser. Stopp og vent på min tilbakemelding.

</details>

<details>
<summary><strong>Prompt 10 – OQ-8 godkjent, punkt 7: Teststrategi og lokal kjøring</strong></summary>

> Jeg godkjenner alle verdiene for Punkt 6 (OQ-8):
> - **Tidsgrense for analyse:** 120 sekunder totalt (inkludert nye forsøk) – veldig fornuftig med tanke på at vi planlegger å teste Claude Opus.
> - **Dokumentstørrelse:** Maks 10 MB per fil og maks 100 000 tegn etter uttrekk.
> - **Merknader:** Maks 5 000 Unicode-tegn (inkl. grensetest på 5 000 vs. 5 001 tegn og oppdatering av telleren i F4 hos Sebastian).
> - **Nettlesere:** Edge og Chrome som primære nettlesere (med stikkprøver i Firefox og Safari).
>
> Loggfør stack-beslutningen (S1) og OQ-8 i memloggen, og gå deretter videre til **punkt 7: Teststrategi og lokal kjøring**. Legg frem alternativer, anbefaling og konsekvenser, og stopp for min tilbakemelding.

</details>

<details>
<summary><strong>Prompt 11 – Punkt 7 godkjent, skriv arkitekturdokumentet</strong></summary>

> Jeg har bekreftet memlogg-committen i den lokale tråden nå.
>
> Tilbakemelding på Punkt 7 (Teststrategi og lokal kjøring):
> 1. **A1, A2, A4 og A5:** Godkjent. God dekning på enhetstester (inkl. ISO-uker), integrasjonstester med falsk KI-leverandør, `npm run eval` for modellvalg/SM-3 og enkel GitHub Actions CI.
> 2. **A3 (Playwright):** Vi beholder Playwright som et valgfritt «bør»-punkt hvis vi får tid, og bruker en enkel manuell sjekkliste for tastatur og fokus slik at vi ikke overengineerer testriggen.
> 3. **Skriptene:** Godkjent (`npm run demo` på `127.0.0.1:3000`, `npm start`, `npm run dev`, `npm test`, `npm run typecheck` og `npm run eval`).
> 4. **`--demo`-flagg (justering av OQ-7 A1):** Veldig bra fanget opp – støtte for både `--demo`-flagg i npm-skriptet og miljøvariabelen `DEMO_MODE=true` sikrer at oppstart fungerer likt på både Mac og Windows.
>
> Loggfør stack (S1), OQ-8 og Punkt 7 i memloggen, og skriv deretter selve **arkitekturdokumentet** i tråd med BMAD Architecture-malen og prosjektets struktur. Stopp før Reviewer Gate slik at jeg kan gå gjennom utkastet.

</details>

<details>
<summary><strong>Prompt 12 – Tre tillegg godkjent, kjør Reviewer Gate</strong></summary>

> Jeg har lastet ned arkitekturdokumentet og lagt det i `_bmad-output/planning-artifacts/architecture/architecture-G99-byfuglien-risoy-sonsteng-2026-11-22/`.
>
> De tre tilleggene dine er godkjent:
> 1. Standardisert API-feilformat `{ code, message }` med melding på norsk.
> 2. Norske domenefelt uten æ/ø/å i datamodell/API og engelsk på øvrige tekniske navn.
> 3. Styling basert på CSS-tokens fra `DESIGN.md` uten ekstra komponentbibliotek (ta det gjerne med som en eksplisitt AD for frontend-styling i tillegg til evt. detaljutsatte punkter).
>
> Kjør **Reviewer Gate** (og `bmad-review`) på arkitekturdokumentet nå, og rapporter eventuelle funn før vi oppdaterer KI-logg, sesjonslogg og committer.

</details>

<details>
<summary><strong>Prompt 13 – Reviewer Gate-regler godkjent, memlogg og logger før commit</strong></summary>

> Jeg godkjenner alle de åtte reglene (1–8) og endringene fra Reviewer Gate, og jeg har erstattet arkitekturdokumentet med den reviderte versjonen i run-mappen på Macen.
>
> Før vi avslutter:
> 1. Kontroller `git status -sb` og `git log -1` på Macen slik at vi verifiserer om memlogg-committen og oppføringene for S1, OQ-8 og Punkt 7 er på plass (og legg dem inn dersom de mangler).
> 2. Oppdater memloggen med resultatet fra Reviewer Gate og de 8 nye reglene (AD-16, AD-17 m.fl.).
> 3. Oppdater KI-logg (`docs/ki-logg/`) og sesjonslogg i tråd med `CLAUDE.md` og `AGENTS.md` (ta særlig med funnene fra Reviewer Gate som eksempel på kritisk gjennomgang og korrigering).
> 4. Vis meg utkastet til KI-loggen og hvilke filer som er endret før vi gjør siste commit og push på `arch/elias-architecture`.

</details>

## Hva KI leverte

- **Kartlegging (prompt 1):** read-only-rapport om Git-status, BMAD-versjon (6.12.0, skillen heter `bmad-architecture`), dokumentgrunnlag og forskjeller mellom `main` og UX-branchen. Rapporten fant at nyeste PRD (11.11) bare lå på `ux/sebastian-ux-design`, og at `architecture/technology.md` på `main` gjelder et annet prosjekt. Den foreslo også en plan for arkitekturarbeidet. Ingen filer ble endret.
- **Punkt 1–7 (prompt 2–11):** for hvert punkt alternativer, anbefaling og konsekvenser, med stopp for godkjenning. Vedtakene: lokal klient–server med nøkkelen på serveren (punkt 1), én JSON-fil og aktivitetsmodell med sju felt (punkt 2), Anthropic med modell via miljøvariabel (OQ-6), eksplisitt demo-modus, normal oppstart uten nøkkel og SHA-256 av normalisert tekst (OQ-7), TypeScript med React, Vite, Express og delt `shared/` (S1), grenseverdiene i OQ-8 og teststrategien i punkt 7. Pakkeversjonene ble kontrollert mot npm-registeret.
- **Overleveringsnotat til Sebastian (prompt 6):** kort notat om OQ-7 med tre justeringer for UX Finalize. Elias godkjente og sendte det.
- **Branch og memlogg (prompt 8, 9, 13):** `arch/elias-architecture` ble opprettet fra `origin/ux/sebastian-ux-design`, `origin/main` ble merget inn uten konflikt (`75c3c37`), og branchen ble pushet. `.memlog.md` ble opprettet med 12 oppføringer: oppstart, sju beslutninger, overleveringsnotatet, resultatet fra Reviewer Gate og de åtte nye reglene.
- **Arkitekturdokumentet (prompt 11–12):** `ARCHITECTURE-SPINE.md` etter BMAD-malen, med AD-1 til AD-15, konvensjoner, stack, strukturskisse, API-tabell, kapabilitetskart og utsatte punkter. AD-15 (styling med CSS-tokens fra `DESIGN.md`, uten komponentbibliotek) ble lagt til etter Elias' ønske.
- **Reviewer Gate (prompt 12):** fem uavhengige gjennomganger. Rubric-gjennomgangen ga dommen «kan godkjennes med endringer» med to høye funn. Motstanderparene fant at enheter som skulle snakke sammen, ikke hadde en felles kontrakt. Versjonskontrollen installerte hele stacken i et tomt testprosjekt på Node 24 og prøvde de tekniske påstandene. Rapportene ligger i `reviews/`. Claude Code rettet de klare funnene og la frem de nye reglene for Elias.

## Hva vi endret og hvorfor

Reviewer Gate er det tydeligste eksempelet i økten på at KI-forslaget ikke ble godtatt som det var. Førsteutkastet til spinen hadde feil som ville ha stoppet appen eller gitt ulik oppførsel i klient og server:

- **Oppstart uten `.env`:** utkastet brukte `node --env-file=.env`, som avslutter med feil når filen mangler. Det ville ha stoppet `npm start` for sensor. Rettet til `--env-file-if-exists`, og `npm run demo` leser aldri `.env`.
- **Express-grenser:** Express godtar bare 100 kB JSON som standard. Utkastet tok det for gitt at større kropper gikk gjennom. Nå står grensene eksplisitt: rå opplasting 10 MB og JSON 1 MB.
- **Tidsfrist og nye forsøk:** Anthropic-SDK-en prøver selv to ganger på nytt og har 10 minutters timeout. Det kunne sprenge 120-sekundersfristen (OQ-8). Nå gjelder `maxRetries: 0`, høyst ett eget nytt forsøk ved nettverksfeil, 429 eller 5xx, og ett `AbortSignal` for hele fristen.
- **Filnavn med æøå:** `fetch` avviser header-tegn over U+00FF, så filnavnet sendes nå `encodeURIComponent`-kodet.
- **Express 5-ruter:** `*` er ikke gyldig i Express 5. SPA-fallback bruker `/{*splat}`.
- **Felles kontrakter:** demo-fasit og Anthropic-svar hadde ikke samme form, og én feil verdi kunne forkaste hele analysen. Det førte til AD-16 (råskjema og behandlet skjema). Klient og server kunne sende ulike kropper, noe som førte til AD-17 (alle former i `shared/api.ts`, feilformat `{ code, message, details? }`).
- **Kanttilfeller:** en skadet planfil gir `STORE_CORRUPT` og blir aldri overskrevet, tomme kildeutdrag forkastes, et kuttet modellsvar gir `ANALYSIS_FAILED`, og Node 26 er tatt med fordi den nå er aktiv LTS.

Gjennomgangen ga også åtte nye regler som gikk ut over det Elias allerede hadde vedtatt. Claude Code la dem frem som forslag i stedet for å føre dem inn som vedtatt, og Elias godkjente alle åtte (prompt 13): Host-sjekk mot DNS rebinding, én analyse om gangen (`ANALYSIS_BUSY`), Node 24 eller 26, AD-16 og AD-17, `valider()` som eneste kilde til feltstatus, fast liste med 14 feilkoder, `prompts/analyse/` som egen mappe og ingen idempotensnøkkel i v1.

Andre endringer underveis:
- **Branch fra riktig grunnlag:** Claude Code fant at `main` hadde en eldre PRD, og anbefalte branch fra UX-branchen med `main` merget inn. Elias fulgte anbefalingen (prompt 8).
- **`--demo`-flagg:** Claude Code fant i punkt 7 at `DEMO_MODE=true` i et npm-skript ikke virker likt på Windows uten ekstra pakker. OQ-7 A1 ble justert til å støtte både flagget og miljøvariabelen (prompt 11).
- **Tillegg Elias godkjente (prompt 12):** standardisert feilformat, norske domenefelt uten æøå og AD-15 for styling.
- **Beholdt:** PRD, Product Brief og UX-dokumentene ble ikke endret. Ingen beslutning er ført inn som gruppevedtak. Spinen har `status: draft` til gruppen har behandlet den.

## Testing

Det finnes ingen kode ennå, så ingen applikasjon ble testet. Dette ble faktisk kjørt:

- **Versjoner:** alle pakkeversjoner i stacken ble kontrollert mot npm-registeret 22. november 2026.
- **Prøveinstallasjon (Reviewer Gate):** hele stacken ble installert i et tomt testprosjekt på Node 24.22.3 i skyen. Påstandene i spinen ble prøvd der, blant annet `--env-file` mot `--env-file-if-exists`, Express' standardgrense, SDK-ens standardverdier for nye forsøk og timeout, Express 5-rutemønsteret og `fetch` med æøå i header. Testprosjektet ligger ikke i repoet.
- **Lint:** `lint_spine.py` fra `bmad-architecture` ga 0 funn på den reviderte spinen.
- **Memlogg:** oppføringene ble kontrollert for duplikater, HTML-entiteter og linjeskift (bare LF) på Mac-en.
- **Hash og lint på Mac-en:** spinen i run-mappen ble kontrollert mot SHA-256 av versjonen fra skyen (`6a226938…`) og lintet på nytt med 0 funn før commit.

**Ikke testet:** ingen kode er skrevet eller kjørt. Modellvalget (`npm run eval`) og grenseverdiene er ikke målt. Mermaid-diagrammene er ikke validert med et verktøy.

**Åpne avhengigheter:** alle beslutningene venter på samlet gruppevedtak. Sebastian må legge 5 000 tegn inn i telleren i F4 og fullføre UX Finalize etter OQ-7-notatet. Konkret modell velges etter `npm run eval`. Se memloggen og sesjonsloggen for detaljer.
