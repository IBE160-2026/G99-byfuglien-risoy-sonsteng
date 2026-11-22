# 2026-11-09 — UX: visuell retning, F4–F6 og første utkast av DESIGN.md og EXPERIENCE.md

- **Deltakere:** Sebastian Byfuglien
- **KI-verktøy:**
  - Claude Code med modellen Claude Opus 5.5 (`claude-opus-5-5`) og BMAD-skill `bmad-ux` (fortsatt kjøring, Coaching path). Claude Code brukte underagenter (general-purpose) til å tegne wireframes og til å skrive førsteutkastet av DESIGN.md og EXPERIENCE.md. Alt underagentene leverte, ble kontrollert av Claude Code før det ble lagt fram.
  - ChatGPT (OpenAI) som uavhengig kontrollagent og rådgiver, jf. `prompts/chatgpt-kontrollagent.md`. Ifølge promptene gikk Sebastian gjennom Claude Codes rapporter, forslag og utkast med ChatGPT før han tok stilling. ChatGPT gjorde ingen endringer i repositoryet og kontrollerte ikke prosjektfilene direkte.
  - Sebastian Byfuglien tok alle beslutningene.
- **Kontrollert av:** Sebastian Byfuglien

## Oppgave

Økten fortsatte den eksisterende BMAD UX-kjøringen etter noen dagers opphold.
Først skulle prosjektstatusen kontrolleres, og UX-arbeidet som bare fantes
lokalt, skulle committes og pushes. Deretter skulle den visuelle retningen
avsluttes, F4–F6 og tastaturmodellen beskrives, og første fullstendige utkast
av DESIGN.md og EXPERIENCE.md skrives og kvalitetssikres. Dokumentene skal ha
`status: draft` til OQ-3 og andre avhengigheter er avklart.

## Avvik i loggføring: 3. og 4. november 2026

UX-øktene 3. og 4. november ble ikke KI-logget mens de var ferske, og de har
heller ingen sesjonslogg. Det er ikke laget logger for disse dagene i
ettertid, i tråd med `docs/ki-logg/README.md`.

- **Dette er dokumentert:**
  - Arbeidet og beslutningene står i UX-memloggen
    `_bmad-output/planning-artifacts/ux-designs/ux-G99-byfuglien-risoy-sonsteng-2026-11-02/.memlog.md`,
    oppføring 39–91. Oppføringene er datert i teksten: beslutninger 3. november,
    gjenbruk av fargetemaer 4. november.
  - Resultatene ligger i `.working/` i samme mappe: wireframes v1–v3 for F1, F2/F3,
    F7 og F8, designretninger og fargetemaer. De ble committet 9. november i
    `5769b3a`, `cd014a9` og `0903def`.
- **Dette er ikke gjengitt:** promptene fra 3. og 4. november og ChatGPT-dialogen
  fra de dagene.
- **Kan ikke bekreftes ut fra repoet:** nøyaktige tidspunkter og hvor lenge øktene varte.

## Prompt (ordrett, med dokumenterte unntak)

Prompter sendt til Claude Code 9. november, med dokumenterte unntak. Promptene
er gjengitt i rekkefølge og med uendret tekst, bortsett fra de to unntakene som
er beskrevet under. Hver prompt er sammenleggbar. Claude Codes svar mellom
promptene er ikke tatt med, og promptene til ChatGPT og ChatGPTs svar er ikke
gjengitt.

Én del er bevisst kuttet med `[...]`: Meldingen i prompt 1 inneholdt to like
kopier av en prompt om å kombinere fargetemaene før kontrollprompten. Sebastian
skrev selv i kontrollprompten at prompten om fargetemaene ikke var sendt, og
Claude Code gjennomførte den ikke. Den første kopien er gjengitt, og den andre
er erstattet med `[...]`.

Prompt 12 ble kuttet av før den var ferdig skrevet, og står slik den kom inn.

Utkastet dokumenterer arbeidet fram til og med prompt 12. Godkjenning av denne
KI-loggen og de nye commitene for 9. november er ikke gjennomført ennå og står
derfor ikke i loggen.

<details>
<summary><strong>Prompt 1 – Oppstartskontroll etter opphold</strong></summary>

> Vi fortsetter eksisterende BMAD UX-kjøring i Coaching path på norsk bokmål. Ikke opprett ny arbeidsmappe, ikke endre PRD, ikke commit og ikke push.
>
> Bruk eksisterende arbeidsmappe:
> _bmad-output/planning-artifacts/ux-designs/ux-G99-byfuglien-risoy-sonsteng-2026-11-02/
>
> ## Nye beslutninger som skal dokumenteres i eksisterende UX-memlogg
> 1. Vi velger hovedretningen fra **tema 1 – Kjølig og luftig** som visuell grunnretning.
> 2. Vi vil bruke **fargetokener fra tema 2 – Presis monokrom** som utgangspunkt.
> 3. **Panelfargen fra tema 1 beholdes**.
> 4. **Fokusfargen skal være oransje**.
> 5. Inspirasjonen fra **apple.com, polestar.no og langsikt.no** beholdes som faglig referanse:
>    - Apple: luft, tydelig hierarki, én primærhandling per flate
>    - Polestar: presis struktur, hårfine skillelinjer, nøktern layout
>    - Langsikt: tydelige metadata og redaksjonelt hierarki
> 6. OQ-3 skal fortsatt stå åpen.
>
> ## Oppgave
> Gjør bare nødvendige justeringer i de visuelle arbeidsfilene i `.working/`, basert på beslutningene over.
>
> ### Konkret:
> - Oppdater den valgte retningen slik at den blir en **kombinert retning**:
>   - formspråk og uttrykk fra tema 1
>   - semantiske fargetokener fra tema 2
>   - panelfarge fra tema 1
>   - oransje fokusfarge
> - Ikke lag flere parallelle alternativer med mindre du oppdager en reell motstrid.
> - Rett mindre visuelle inkonsistenser hvis nødvendig.
> - Behold løsningen lys, profesjonell, enkel og egnet for PC og projektor.
> - Kategorier og status skal fortsatt kunne skilles uten farge alene.
>
> ## Leveranse
> 1. Oppdater eksisterende UX-memlogg med beslutningene.
> 2. Lag én oppdatert arbeidsfil i `.working/` som viser den kombinerte retningen, med tilhørende forhåndsvisning hvis workflowen allerede bruker det.
> 3. Presenter:
>    - hvilke filer som ble oppdatert eller opprettet
>    - hvilke fargetokener som nå foreslås brukt
>    - hvordan tema 1 + tema 2 faktisk er kombinert
>    - hvilke visuelle beslutninger som fortsatt gjenstår før DESIGN.md kan ferdigstilles
>
> Ikke skriv ut DESIGN.md eller EXPERIENCE.md ennå.
> Stopp etter at den oppdaterte kombinerte retningen er presentert.
>
> [...]
>
> Vi fortsetter IBE160-prosjektet Sambandet etter noen dagers opphold.
>
> Før vi gjør noe nytt arbeid, ønsker jeg en grundig, men kortfattet oppstartskontroll.
>
> **Viktig kontekst:**
> - Vi arbeider i den eksisterende BMAD UX-kjøringen.
> - Branch: `ux/sebastian-ux-design`.
> - UX-arbeidsmappe: `_bmad-output/planning-artifacts/ux-designs/ux-G99-byfuglien-risoy-sonsteng-2026-11-02/`.
> - Siste rapporterte UX-memlogg hadde 91 oppføringer.
> - Siste kjente lokale commit var `72a9abd`.
> - Den siste prompten om å kombinere fargetemaene ble IKKE sendt eller gjennomført før oppholdet.
>
> **Gjennomfør følgende kontroll:**
>
> 1. Les `CLAUDE.md`, `AGENTS.md` og relevante BMAD-instruksjoner.
>
> 2. Kontroller Git-status:
>    - Gjeldende branch.
>    - Siste commits.
>    - Sporede endringer og filer som ikke spores.
>    - Om det finnes uventede endringer.
>    - Om arbeidsområdet inneholder arbeid som ikke er committet.
>
> 3. Kjør `git fetch origin` og undersøk om det har kommet nye endringer fra gruppen. Ikke kjør pull, merge, rebase eller checkout.
>
> 4. Kontroller eksisterende BMAD UX-kjøring:
>    - At riktig arbeidsmappe finnes.
>    - At UX-memloggen er intakt.
>    - Antall oppføringer og siste dokumenterte beslutninger.
>    - Status for DESIGN.md og EXPERIENCE.md.
>    - Status for åpne UX-punkter, særlig OQ-3.
>
> 5. Kontroller eksisterende arbeidsfiler i `.working/`, inkludert wireframes og fargetemaene. Ikke overskriv noe.
>
> 6. Kontroller om følgende siste brukerbeslutning allerede er dokumentert:
>    - Formspråk fra tema 1 – Kjølig og luftig.
>    - Fargetokens fra tema 2 – Presis monokrom.
>    - Panelfarge fra tema 1.
>    - Oransje fokusfarge.
>
>    Denne beslutningen ble godkjent i ChatGPT, men prompten om å dokumentere den ble ikke sendt til Claude Code. Behandle den som godkjent, men ikke nødvendigvis registrert i prosjektet.
>
> 7. Undersøk om det finnes endringer i PRD, Product Brief eller prosjektinstruksjoner som påvirker videre UX-arbeid.
>
> **Rapporter til slutt:**
> - Er prosjektet i orden?
> - Er noe endret siden sist?
> - Finnes det ucommittet arbeid som må ivaretas?
> - Hvor stoppet BMAD UX-prosessen?
> - Hva er neste konkrete steg for å fortsette der vi slapp?
>
> **Begrensninger:**
>
> Dette er kun en kontroll.
>
> Ikke endre, opprett, slett eller overskriv filer.
> Ikke bruk git reset, git clean eller git restore.
> Ikke start en ny BMAD-kjøring.
> Ikke commit eller push.
> Ikke dokumenter nye UX-beslutninger ennå.
>
> Stopp etter statusrapporten. Jeg vil kvalitetssikre den med ChatGPT før vi fortsetter.

</details>

<details>
<summary><strong>Prompt 2 – Forbered lokale commits</strong></summary>

> Oppstartskontrollen 2026-11-09 er gjennomgått og godkjent.
>
> Vi fortsetter eksisterende BMAD UX-kjøring på `ux/sebastian-ux-design`.
>
> Før vi gjør flere designendringer, ønsker jeg å sikre UX-arbeidet som foreløpig bare finnes lokalt.
>
> **Oppgave: Forbered lokale Git-commits**
>
> 1. Kontroller gjeldende Git-status og bekreft at vi står på riktig branch.
> 2. Gjennomgå de 53 ucommittede oppføringene i UX-memloggen og de 24 filene i `.working/`.
> 3. Skill mellom:
>    - viktige UX-kilder, som Excalidraw-filer og designarbeidsfiler
>    - genererte PNG-forhåndsvisninger
>    - eventuelle midlertidige, overflødige eller dupliserte filer
> 4. Kontroller prosjektets Git- og dokumentasjonsregler før du foreslår hvilke filer som bør committes.
> 5. Les de oppdaterte KI-loggreglene direkte fra `origin/main` uten å merge eller endre branchen.
> 6. Foreslå en ryddig commit-plan som sikrer relevant UX-arbeid, med nøyaktige filnavn og norske commit-meldinger.
>
> **Om manglende logger fra 3. og 4. november:**
>
> Ikke opprett etterdaterte logger eller rekonstruer ordrette prompter på usikkert grunnlag.
>
> Presenter kort hvordan mangelen kan dokumenteres åpent og i samsvar med de nye reglene. Skill mellom dokumentert historikk og informasjon som ikke kan bekreftes.
>
> **Viktig:**
>
> - Ikke slett, overskriv eller flytt filer.
> - Ikke opprett nye UX-arbeidsmapper.
> - Ikke gjennomfør commits ennå.
> - Ikke push.
> - Ikke merge eller rebase fra main.
> - Ikke gjør flere UX- eller designendringer.
>
> Stopp etter commit-planen og en kort anbefaling om dokumentasjonsavviket. Jeg skal godkjenne planen før gjennomføring.

</details>

<details>
<summary><strong>Prompt 3 – Gjennomfør tre lokale commits</strong></summary>

> Jeg har gjennomgått commit-planen med ChatGPT og godkjenner den med én endring:
>
> **Alle 12 PNG-forhåndsvisningene skal committes.**
>
> Begrunnelsen er at vi ønsker å bevare hele UX-utviklingen, og at PNG-filene gjør skissene tilgjengelige uten Excalidraw. Den ekstra filstørrelsen er akseptabel.
>
> **Gjennomfør følgende tre lokale commits på `ux/sebastian-ux-design`:**
>
> **Commit 1 – UX-memlogg**
> - Bare eksisterende `.memlog.md`.
>
> Commit-melding:
> `docs: før UX-beslutninger fra Discovery inn i memloggen`
>
> **Commit 2 – Wireframes**
> - Alle 8 `.excalidraw`-filene i `.working/`.
> - Alle 8 tilhørende PNG-forhåndsvisningene.
>
> Commit-melding:
> `docs: legg til foreløpige wireframes for F1, F2/F3, F7 og F8`
>
> **Commit 3 – Designretninger og fargetemaer**
> - De 3 `direction-*.html`-filene.
> - `color-themes-lys-1.html`.
> - De 4 tilhørende PNG-forhåndsvisningene.
>
> Commit-melding:
> `docs: legg til foreløpige designretninger og fargetemaer`
>
> **Kontroller:**
> 1. At vi står på riktig branch.
> 2. At bare de godkjente filene stages i hver commit.
> 3. At `git show --stat HEAD` viser riktig innhold etter hver commit.
> 4. At alle 24 arbeidsfilene og memloggen er bevart i Git.
> 5. At arbeidsområdet er rent etterpå.
> 6. At `main` fortsatt er uendret.
>
> Bruk prosjektets etablerte regler for commit-meldinger og medforfatterskap.
>
> **Om loggføringen:**
>
> Vi følger anbefalingen om å dokumentere avviket fra 3. og 4. november åpent i KI-loggen for 9. november, med henvisning til memloggen og arbeidsfilene. Ikke opprett etterdaterte KI-logger eller rekonstruer usikre opplysninger.
>
> Denne loggen skal utarbeides og godkjennes separat før den committes. Ikke opprett eller commit den som del av de tre commitene over.
>
> **Begrensninger:**
> - Ikke push.
> - Ikke merge eller rebase.
> - Ikke endre PRD, DESIGN.md eller EXPERIENCE.md.
> - Ikke gjør flere UX-endringer ennå.
> - Ikke slett noen filer.
>
> Stopp etter de tre commitene og rapporter Git-status, commit-hasher og eventuelle avvik.

</details>

<details>
<summary><strong>Prompt 4 – Push av UX-branchen</strong></summary>

> Jeg godkjenner at de seks lokale commitene på `ux/sebastian-ux-design` pushes til GitHub.
>
> **Gjør følgende:**
>
> 1. Kontroller at gjeldende branch er `ux/sebastian-ux-design`.
> 2. Kontroller at arbeidsområdet er rent, og at siste commit er `0903def`.
> 3. Bekreft at `origin` peker til riktig GitHub-repository for IBE160-prosjektet.
> 4. Kontroller at branchen ikke allerede finnes på `origin`.
> 5. Push kun denne branchen med:
>    `git push -u origin ux/sebastian-ux-design`
> 6. Verifiser etterpå at:
>    - `origin/ux/sebastian-ux-design` peker til samme commit som den lokale branchen.
>    - Branchen har korrekt upstream.
>    - Arbeidsområdet fortsatt er rent.
>    - `main` og `origin/main` ikke er endret av operasjonen.
>
> **Begrensninger:**
>
> - Ikke bruk force push.
> - Ikke opprett pull request.
> - Ikke merge eller rebase.
> - Ikke push til `main`.
> - Ikke endre prosjektfiler.
> - Ikke start nytt UX-arbeid ennå.
>
> Rapporter resultatet, inkludert commit-hash, upstream og eventuelle feil.
>
> Stopp etter verifiseringen.

</details>

<details>
<summary><strong>Prompt 5 – Kombinert visuell retning</strong></summary>

> Pushen er gjennomført og verifisert. Vi fortsetter UX-arbeidet.
>
> Fortsett eksisterende `/bmad-ux`-kjøring i Coaching path på norsk bokmål, på branchen `ux/sebastian-ux-design`.
>
> **Godkjent designbeslutning**
>
> Jeg velger følgende kombinasjon:
>
> 1. Formspråk og generell utforming fra tema 1 – «Kjølig og luftig».
> 2. Grunnleggende fargetokens fra tema 2 – «Presis monokrom».
> 3. Panelfargen fra tema 1 skal beholdes.
> 4. Fokusfargen skal være oransje.
>
> Dette er godkjente føringer, men den eksakte oransjen og den endelige tokenpaletten skal fortsatt vurderes.
>
> Designretning A betyr «Lys, strukturert planleggingsverktøy». Dette er allerede bekreftet, ikke en ny antakelse.
>
> **Oppgave**
>
> 1. Les eksisterende UX-memlogg og fargetemaarbeidet i `.working/`.
> 2. Dokumenter den godkjente kombinasjonen i memloggen med tydelig skille mellom vedtatte føringer og åpne detaljvalg.
> 3. Lag én samlet visuell forhåndsvisning av den kombinerte retningen.
> 4. Vis hvordan kombinasjonen fungerer på F1 (årshjul), F2/F3 (måned og aktivitetsdetaljer) og F7 (KI-gjennomgang).
> 5. Presenter hvilke eksisterende fargetokens fra tema 2 som beholdes, hvilke som må overstyres av tema 1, og hvilke nye tokens den oransje fokusfargen krever.
> 6. Foreslå en egnet oransje fokusfarge med hex-verdi og kontroller kontrast og tilgjengelighet. Skill mellom kontrastberegninger og faktisk projektortesting.
> 7. Rapporter eventuelle reelle problemer før vi godkjenner den endelige paletten.
>
> **Designprinsipper**
>
> Behold inspirasjonen fra Apple, Polestar og Langsikt.
>
> Prioriter tydelig typografi, gode mellomrom, lesbarhet på projektor og enkel navigasjon.
>
> Oransje skal brukes som fokusmarkering, ikke automatisk som kategori- eller feilkode. Fokus må være tydelig også for tastaturbrukere.
>
> OQ-3 forblir åpen. Kategoriene bruker fortsatt plassholdere.
>
> **Begrensninger**
>
> - Ikke fastsett endelig fargepalett eller typografi uten min godkjenning.
> - Ikke endre godkjente brukerflyter.
> - Ikke opprett en ny UX-kjøring.
> - Ikke endre PRD, DESIGN.md eller EXPERIENCE.md.
> - Ikke start implementering.
> - Ikke commit eller push.
>
> Lagre den kombinerte forhåndsvisningen i eksisterende `.working/`.
>
> Stopp etter dokumentasjon og presentasjon av resultatet, slik at jeg kan gjennomgå det sammen med ChatGPT.

</details>

<details>
<summary><strong>Prompt 6 – Palett godkjent; typografi og komponenter</strong></summary>

> Vi fortsetter den eksisterende BMAD UX-kjøringen i Coaching path på norsk bokmål.
>
> Jeg godkjenner den kombinerte fargepaletten og formspråket som designgrunnlag for Sambandet.
>
> **1. Godkjent visuell retning**
>
> - Designretning A: Lyst, strukturert planleggingsverktøy.
> - Formspråk fra tema 1 «Kjølig og luftig».
> - Fargetokens fra tema 2 «Presis monokrom».
> - Panelfarge fra tema 1: `#F3F5F8`.
> - Bakgrunn: `#FFFFFF`.
> - Primærhandling: `#0B0B0B` med hvit tekst.
> - Oransje fokusfarge: `#C75000`.
> - Øvrige semantiske fargetokens beholdes fra tema 2, slik de er dokumentert i den kombinerte forhåndsvisningen.
> - Inspirasjonen fra Apple, Polestar og Langsikt beholdes.
>
> **2. Presiseringer**
>
> - Oransje brukes utelukkende til fokusmarkering, ikke til valgt element, kategorier eller feilmeldinger.
> - Valgt måned og aktivt forslag skal ha en tydelig, nøytral markering som er forskjellig fra tastaturfokus og blokkerende feltfeil.
> - Behold den lyse panelfargen og avrundede hjørner.
> - Bruk diskrete kantlinjer der paneler trenger tydeligere avgrensning. Ikke stol på skygger alene.
> - Behold god kontrast og tydelig typografisk hierarki.
> - Kontroller lesbarhet på vanlig PC og projektor under senere UX-validering.
> - Kategorienes endelige identitet avventer OQ-3.
>
> **3. Dokumentasjon**
>
> Før beslutningene inn i eksisterende UX-memlogg med relevante referanser.
>
> Skill tydelig mellom:
> - godkjente designbeslutninger
> - detaljer som fortsatt må spesifiseres
> - validering som gjenstår
>
> Ikke merk projektorlesbarhet som testet eller godkjent.
>
> **4. Fortsett UX-workflowen**
>
> Bruk den installerte BMAD UX-workflowen til å identifisere neste nødvendige steg mot DESIGN.md og EXPERIENCE.md.
>
> Jeg ønsker nå å arbeide med:
> - typografisk hierarki og skriftstørrelser
> - komponentprinsipper
> - tilgjengelighet og tastaturnavigasjon
> - resterende nødvendige UX-avklaringer før Finalize
>
> Presenter et konkret og begrenset forslag til typografi og komponentprinsipper som passer den godkjente designretningen.
>
> Prioriter PC, projektor og lesbarhet. Unngå nye funksjoner og unødvendige designalternativer.
>
> Ikke fastsett nye detaljer uten min godkjenning.
>
> **Begrensninger**
>
> - Ikke start implementering.
> - Ikke opprett en ny UX-arbeidsmappe.
> - Ikke endre PRD-en.
> - Ikke ferdigstill DESIGN.md eller EXPERIENCE.md ennå.
> - Ikke commit eller push.
>
> Stopp etter at beslutningene er dokumentert og neste konkrete designforslag er presentert.

</details>

<details>
<summary><strong>Prompt 7 – A–D godkjent; F4, F5 og F6</strong></summary>

> Vi fortsetter den eksisterende BMAD UX-kjøringen i Coaching path på norsk bokmål.
>
> Jeg godkjenner forslagene A–D om typografi, avstander, komponentprinsipper og tastaturnavigasjon, med følgende justeringer.
>
> **1. Typografi**
> - Bruk systemfonter, tabulære tall og de foreslåtte typografiske nivåene.
> - Bruk skriftvektene 400, 600 og 700.
> - Minst 16 px tekst som hovedregel, og minst 18 px på informasjon som er viktig for status og handling.
> - Størrelsene er et designgrunnlag, ikke dokumentasjon på faktisk projektorlesbarhet.
>
> **2. Avstander og komponenter**
> - Bruk det foreslåtte 8 px-avstandssystemet.
> - Behold formspråket med luftige flater, avrundede hjørner og minst 44 px høye klikkflater.
> - Behold tidligere godkjente fargetokens og komponentprinsipper.
> - Paneler skal ha tydelige kantlinjer når det er nødvendig for å skille dem fra bakgrunnen.
>
> **3. Valgt måned og aktivt forslag**
> - Ikke bruk en helsvart sektor for valgt måned.
> - Marker valgt måned nøytralt, for eksempel med tydelig mørk kant og svak bakgrunn.
> - Vis også tekst som «Valgt: Mars 2026».
> - Marker aktivt forslag i F7 nøytralt, med tydelig indikator og tekst.
> - Oransje `#C75000` brukes bare til tastaturfokus, ikke til valgt eller aktiv tilstand.
>
> **4. Forkasting**
> - I bekreftelsesdialogen skal «Fortsett gjennomgangen» være det trygge, fremhevede standardvalget.
> - «Forkast uten å lagre» skal være tydelig tilgjengelig, men ikke fremheves som standardhandlingen.
>
> **5. Tastaturnavigasjon**
> - Behold hovedprinsippene fra forslaget.
> - I årshjulet flytter piltastene fokus mellom månedene uten å åpne eller endre visningen.
> - Enter eller mellomrom åpner månedsvisningen for fokusert måned.
> - Modalene skal håndtere fokus korrekt. Ved lukking går fokus tilbake til elementet som åpnet modalen.
> - Hvis F3 åpnes fra en dagsoversikt, beholdes dagsoversikten og samme måned ved lukking.
>
> **Dokumentasjon**
>
> Før disse godkjente beslutningene inn i eksisterende UX-memlogg med relevante PRD- og tilgjengelighetsreferanser.
>
> Skill mellom vedtatte designregler og forhold som krever testing på PC eller projektor.
>
> **Neste UX-oppgave: F4, F5 og F6**
>
> Bruk gjeldende PRD, UX-memlogg og godkjente brukerflyter som grunnlag.
>
> Utarbeid et samlet forslag til atferd, skjermtilstander og enkle wireframes for:
>
> - F4: Manuell opprettelse og redigering av aktivitet, inkludert feltvalidering, lagring, avbryt og retur til riktig visning.
> - F5: Bekreftelse ved sletting av aktivitet, inkludert retur til riktig måned eller dagsoversikt.
> - F6: Dokumentopplasting og analyse, inkludert filkontroll, behandling, fremdrift, ingen funn, feil og demo-modus.
>
> Bruk fiktive data. Behold tidligere godkjente beslutninger og ikke innfør nye funksjoner uten grunnlag i PRD-en.
>
> Lag foreløpige wireframes i eksisterende `.working/`. Bruk godkjent designgrunnlag, men ikke lås nye produktbeslutninger.
>
> Presenter F4–F6 samlet, med:
> 1. De foreslåtte brukerflytene og tilstandene.
> 2. Hva som allerede er bestemt.
> 3. Eventuelle reelle avklaringer jeg må ta.
> 4. Hvordan skissene støtter PRD-kravene.
>
> Ikke opprett en ny BMAD-kjøring.
> Ikke endre PRD, DESIGN.md eller EXPERIENCE.md ennå.
> Ikke start implementering.
> Ikke commit eller push.
>
> Stopp etter at wireframene og vurderingene er presentert.

</details>

<details>
<summary><strong>Prompt 8 – Avklaringer for F4, F5 og F6</strong></summary>

> Vi fortsetter eksisterende BMAD UX-kjøring i Coaching path på norsk bokmål.
>
> Jeg godkjenner anbefalingene for F4, F5 og F6, med presiseringene nedenfor.
>
> **1. F4 – Opprettelse og redigering**
>
> Jeg godkjenner F4-1, F4-2, F4-3 og F4-5:
>
> - F4 skal være en modal.
> - Ved redigering erstatter F4 aktivitetsdetaljene i F3. Det skal ikke åpnes modaler oppå hverandre.
> - «Lagre» skal kunne aktiveres selv om skjemaet er ufullstendig. Ved ugyldige verdier vises en feiloppsummering, feil ved feltene og fokus på første relevante feil.
> - Etter opprettelse returnerer brukeren til visningen vedkommende startet fra, med tydelig tilbakemelding og hensiktsmessig tilbakeføring av tastaturfokus.
> - Etter redigering går brukeren tilbake til F3.
>
> **F4-4 – Ulagrede endringer:**
>
> - Hvis brukeren velger «Avbryt» eller Esc uten å ha endret noe, lukkes skjemaet direkte.
> - Hvis det finnes ulagrede endringer, skal brukeren bekrefte at endringene forkastes.
> - Det trygge standardvalget er å fortsette redigeringen.
> - Ikke forkast skjemadata ved et utilsiktet tastetrykk.
>
> **2. F5 – Sletting**
>
> Jeg godkjenner F5-1 og F5-3, med justering av F5-2:
>
> - Sletting krever bekreftelse.
> - «Avbryt» er det trygge, visuelt fremhevede standardvalget.
> - Når F3 ble åpnet fra en dagsoversikt, returnerer brukeren etter sletting til den oppdaterte dagsoversikten hvis det fortsatt finnes aktiviteter der.
> - Hvis dagen blir tom, går brukeren tilbake til månedsvisningen.
> - Etter vellykket sletting annonseres bekreftelsen til skjermleser.
> - Tastaturfokus flyttes til et relevant, varig element i den gjenværende visningen, ikke til en midlertidig melding.
>
> **3. F6 – Dokumentopplasting og analyse**
>
> Jeg godkjenner F6-1, F6-2, F6-3 og F6-5:
>
> - F6 vises som modal.
> - Vis en tydelig påminnelse om at bare fiktive dokumenter skal brukes.
> - Kontroller filformat og filstørrelse ved filvalg.
> - Avvis skannede PDF-er når tekstinnholdet er kontrollert etter at analysen er startet.
> - Ved analysefeil er «Prøv igjen» primærhandling og «Lukk» sekundærhandling.
> - Behold tidligere godkjente regler for demo-modus, ingen funn, feilhåndtering og sperret opplasting under aktiv gjennomgang.
>
> **F6-4 – Langvarig analyse:**
>
> Dette punktet er ikke endelig avgjort.
>
> Kontroller den eksakte ordlyden i gjeldende PRD om analyse, avbrudd, tidsavbrudd og feilhåndtering.
>
> Presenter én anbefalt løsning som hindrer at brukeren blir låst i en modal på ubestemt tid, uten å innføre unødvendig ny funksjonalitet.
>
> Ikke legg til en ny kanselleringsfunksjon eller endre PRD-en uten godkjenning.
>
> **4. Dokumentasjon og kontroll**
>
> 1. Før de godkjente beslutningene inn i eksisterende UX-memlogg med relevante PRD-referanser.
> 2. Behold F6-4 som åpent punkt inntil kravkontrollen er gjennomgått.
> 3. Rett den inkonsekvente arbeidstittelen i F6-wireframen.
> 4. Oppdater bare de aktuelle foreløpige wireframene dersom beslutningene krever det.
> 5. Skill mellom godkjente regler, åpne valg og validering som gjenstår.
>
> **5. Videre mot Finalize**
>
> Når dette er gjort, gi en kort og konkret vurdering av hva som fortsatt må avklares før DESIGN.md og EXPERIENCE.md kan utarbeides.
>
> Ikke start en ny Discovery-runde.
>
> Ikke utvid MVP, endre PRD-en eller ta nye produktbeslutninger på mine vegne.
>
> Ikke start implementering, commit eller push.
>
> Stopp etter dokumentasjon, kontroll av F6-4 og en kort fremdriftsvurdering.

</details>

<details>
<summary><strong>Prompt 9 – F6-4 og øvrige avklaringer; skriv DESIGN.md og EXPERIENCE.md</strong></summary>

> Vi fortsetter eksisterende BMAD UX-kjøring i Coaching path på norsk bokmål.
>
> Jeg godkjenner de siste anbefalingene for F6-4 og de resterende UX-avklaringene.
>
> **1. F6-4 – Langvarig dokumentanalyse**
>
> - Analysemodulen forblir åpen mens analysen pågår.
> - Brukeren kan ikke lukke den med Esc under aktiv analyse.
> - En faktisk håndhevet tidsgrense skal avslutte analyser som ikke gir svar, i tråd med NFR-3.
> - Tidsgrensen bestemmes i arkitekturen (OQ-8).
> - Ved tidsavbrudd behandles analysen som feilet, med «Prøv igjen» og «Lukk».
> - Ikke vis en uavklart plassholder som `[tidsgrense]` i brukergrensesnittet.
> - Ikke innfør egen avbrytfunksjon i MVP.
>
> **2. Øvrige godkjente UX-beslutninger**
>
> - OQ-3 forblir åpen til gruppen har godkjent kategorilisten. UX-spesifikasjonene kan utarbeides med tydelig merkede plassholdere.
> - `DESIGN.md` og `EXPERIENCE.md` skal ikke få `status: final` før OQ-3 og andre nødvendige avhengigheter er avklart.
> - Overgangen mellom år og måned skal være et direkte visningsbytte uten zoom-animasjon, med tydelig overskrift og korrekt tastaturfokus.
> - Tone og stemme: klart, profesjonelt bokmål. Meldinger skal forklare hva som skjedde, hvorfor noe eventuelt er sperret, og hva brukeren kan gjøre. Bruk begrepene fra PRD konsekvent.
> - En nyopprettet aktivitet skal ikke få ekstra visuell markering i kalenderen. Vis en tydelig lagringsbekreftelse og eventuell lenke dersom aktiviteten ligger utenfor perioden som vises.
> - Etter opprettelse returneres tastaturfokus til «Ny aktivitet» eller et tilsvarende varig element i visningen brukeren startet fra.
> - Ved feil under sletting beholdes aktiviteten. Feilen vises i slette-dialogen, med mulighet for å prøve igjen eller avbryte.
>
> **3. Dokumentasjon**
>
> Før de godkjente beslutningene inn i eksisterende UX-memlogg med relevante PRD-referanser. Behold tidligere oppføringer som historikk.
>
> **4. Utarbeid UX-spesifikasjonene**
>
> Fortsett den installerte BMAD UX-workflowen og bruk gjeldende PRD, Product Brief, UX-memlogg og godkjente wireframes som grunnlag.
>
> Utarbeid første fullstendige utkast til:
>
> - `DESIGN.md`: fargetokens, typografi, avstander, hjørner, komponenter, visuell struktur, fokus og tilgjengelighet.
> - `EXPERIENCE.md`: informasjonsarkitektur, brukerreiser, nøkkelflyter, skjermflatene F1–F8, tilstander, navigasjon, validering og feilhåndtering.
>
> Følg strukturen og kravene i den installerte BMAD UX-workflowen, inkludert relevante Key Flows, Component Patterns og Accessibility Floor.
>
> Viktige føringer:
> - Behold begge dokumentene med `status: draft`.
> - Dokumenter kun vedtatte beslutninger som bindende.
> - Merk OQ-3, M11-a og avhengigheter til arkitekturen tydelig.
> - Skill mellom godkjent design, foreløpige forslag og validering som gjenstår.
> - Ikke finn på kategorinavn, tekniske løsninger eller nye produktkrav.
> - Bruk eksisterende UX-arbeidsmappe. Ikke start ny kjøring.
>
> **5. Kvalitetskontroll**
>
> Kontroller utkastene mot gjeldende PRD og memloggen.
>
> Rapporter:
> 1. Hvilke deler av DESIGN.md og EXPERIENCE.md som er utarbeidet.
> 2. Eventuelle mangler, motstridende krav eller åpne avhengigheter.
> 3. Om alle brukerreiser, skjermflater og sentrale tilstander er dekket.
> 4. Hva som gjenstår før dokumentene kan ferdigstilles.
>
> Ikke endre PRD-en uten godkjenning.
>
> Ikke start implementering.
> Ikke commit eller push.
>
> Stopp etter at de to utkastene er skrevet og kvalitetssikret. Jeg skal gjennomgå resultatet med ChatGPT før vi går videre.

</details>

<details>
<summary><strong>Prompt 10 – Kontroll- og oppryddingsrunde før Finalize</strong></summary>

> Vi fortsetter den eksisterende BMAD UX-kjøringen i Coaching path på norsk bokmål.
>
> Jeg har gjennomgått statusrapporten for DESIGN.md og EXPERIENCE.md med ChatGPT og godkjenner en avgrenset kontroll- og oppryddingsrunde før Finalize.
>
> **1. Godkjent beslutning – én aktiv modal**
>
> Vi skal ha én aktiv modal om gangen.
>
> Når brukeren velger «Slett» fra F3:
> - Innholdet i F3-modalen erstattes av slettebekreftelsen.
> - «Avbryt» fører tilbake til F3 med samme aktivitet.
> - Bekreftet sletting fører tilbake til riktig månedsvisning eller dagsoversikt, etter tidligere godkjente regler.
> - Fokus håndteres korrekt uten stablede modaler eller konkurrerende fokusfeller.
>
> Behold tilsvarende tidligere godkjent prinsipp for redigering fra F3 til F4.
>
> **2. Valgt måned**
>
> Når brukeren returnerer fra månedsvisningen til årshjulet, skal sist besøkte måned være nøytralt markert.
>
> Vis for eksempel «Valgt: Mars 2026».
>
> Oransje `#C75000` brukes utelukkende til tastaturfokus, ikke til valgt måned.
>
> **3. Rett dokumentasjonsfeil**
>
> - Kontroller og rett ugyldig YAML i frontmatter i DESIGN.md og EXPERIENCE.md, uten å endre betydningen av kildehenvisningene.
> - Kontroller at dokumentene fortsatt følger den installerte BMAD UX-workflowens forventede format.
> - Rett F8-wireframen slik at «Fortsett gjennomgangen» er det trygge, fremhevede standardvalget.
> - Rett de to mindre uklarhetene i UJ-1 og UJ-2 som ble rapportert.
> - Kontroller at UX-dokumentene og relevante wireframes beskriver samme modalatferd.
>
> Dokumenter de nye godkjente beslutningene i eksisterende UX-memlogg. Behold tidligere oppføringer som historikk.
>
> **4. Gjennomgå de 13 foreløpige detaljene**
>
> Finn de 13 konkrete UX-detaljene som fortsatt krever beslutning.
>
> Presenter dem i én kort tabell med:
> - punkt og referanse
> - hva som er uavklart
> - din anbefaling
> - eventuell konsekvens for PRD, tilgjengelighet eller brukerflyt
>
> Skill mellom reelle produktbeslutninger og rene presentasjonsdetaljer.
>
> Ikke godkjenn eller fastsett disse detaljene på mine vegne. Jeg vil gjennomgå dem samlet med ChatGPT.
>
> **5. Kontroll før Finalize**
>
> Kontroller kort:
> - At DESIGN.md og EXPERIENCE.md fortsatt har `status: draft`.
> - At alle F1–F8 og UJ-1–UJ-3 fortsatt er dekket.
> - At OQ-3, M11-a og arkitekturavhengighetene er synlig dokumentert.
> - At oppdateringene på `origin/main` er kjent, uten at du automatisk merger eller rebaser.
> - At eventuelle gjenværende feil som blokkerer Finalize, identifiseres tydelig.
>
> **Begrensninger**
>
> Ikke start ny BMAD-kjøring.
> Ikke endre PRD.
> Ikke innfør nye funksjoner.
> Ikke fastsett de 13 foreløpige detaljene uten godkjenning.
> Ikke sett DESIGN.md eller EXPERIENCE.md til `final`.
> Ikke start implementering.
> Ikke commit eller push.
>
> Stopp etter oppryddingen, kvalitetskontrollen og beslutningstabellen.

</details>

<details>
<summary><strong>Prompt 11 – De 13 detaljene, dagsoversikt og feil ved sletting</strong></summary>

> Vi fortsetter den eksisterende BMAD UX-kjøringen i Coaching path på norsk bokmål.
>
> Jeg godkjenner anbefalingene for de 13 foreløpige UX-detaljene, med justeringene nedenfor, samt de to nye avklaringene om dagsoversikt og feil ved sletting.
>
> **1. Godkjente detaljer**
>
> - F4/F6: Ved åpning av skjema får «Tittel» eller «Velg fil» innledende fokus.
> - F4: Ved lagringsfeil vises en feilmelding øverst i modalen, med tilgjengelig fokushåndtering.
> - F4: Feiloppsummeringen inneholder lenker som flytter fokus til tilhørende felt.
> - Dialoger: Det trygge standardvalget plasseres konsekvent først eller til venstre. Destruktive handlinger plasseres til høyre.
> - Valgt/aktiv: Bruk 2 px kant i `#0B0B0B`, panelbakgrunn `#F3F5F8` og en tydelig tekstindikator. Dette skal senere testes mot feltfeilmarkering.
> - F6: Ved for stor fil vises «Dokumentet er for stort til å behandles. Velg et mindre dokument.» Den konkrete grensen avhenger av OQ-8.
> - Dra-og-slipp inngår ikke i v1.
> - Øvrig mikrotekst fra skissene beholdes som foreløpig tekst og språkvaskes før ferdigstilling.
> - Datoformat: `dd.mm.åååå`, med både tastaturinntasting og datovelger.
> - F7: Valget om å skjule forslagsoversikten beholdes i den aktive gjennomgangen, uten krav om lagring på tvers av gjennomganger.
> - Øvrige visuelle detaljer i skissene brukes som utgangspunkt, men regnes ikke som ferdig validert.
>
> **2. Justering – meldingsstripe**
>
> Meldinger skal ikke forsvinne automatisk ved neste brukerhandling.
>
> De skal forbli synlige til brukeren lukker dem, eller til meldingen ikke lenger er relevant.
>
> Viktig tilbakemelding skal også være tilgjengelig for skjermlesere.
>
> **3. Justering – utilgjengelige kontroller**
>
> Ikke innfør en generell regel om at alle utilgjengelige kontroller skal kunne få tastaturfokus.
>
> Viktige sperrede handlinger skal være synlige med en forståelig forklaring.
>
> Vurder per komponent om vanlig `disabled` eller `aria-disabled` er mest hensiktsmessig. Dersom `aria-disabled` brukes, må aktivering faktisk hindres.
>
> Forklaringen skal være tilgjengelig med tastatur og skjermleser uansett løsning.
>
> **4. Dagsoversikten**
>
> Dagsoversikten er en utvidbar liste i månedsvisningen, ikke en modal.
>
> - «+N flere» åpner listen.
> - Listen viser alle aktiviteter for den aktuelle dagen.
> - F3 kan åpnes som modal fra dagsoversikten.
> - Ved lukking av F3 returnerer brukeren til samme dagsoversikt og måned.
> - Dagsoversikten skal ikke ha en egen modal fokusfelle.
> - Esc kan lukke dagsoversikten med riktig tilbakeføring av fokus.
>
> **5. F5 – feil ved sletting**
>
> - Ved mislykket sletting beholdes aktiviteten og slette-dialogen.
> - Feilmeldingen vises tydelig og annonseres til skjermleser.
> - «Prøv igjen» er primærhandling i feiltilstanden.
> - «Avbryt» er fortsatt tilgjengelig.
> - Ingen automatisk gjentakelse av sletteforsøket.
> - I den opprinnelige bekreftelsesdialogen forblir «Avbryt» det trygge, fremhevede standardvalget.
>
> **6. Dokumentasjon og kvalitetskontroll**
>
> 1. Før beslutningene inn i eksisterende UX-memlogg med relevante PRD-referanser.
> 2. Oppdater DESIGN.md og EXPERIENCE.md slik at de samsvarer med beslutningene.
> 3. Oppdater bare wireframes der tidligere fremstilling nå er feil.
> 4. Behold `status: draft` i begge UX-dokumentene.
> 5. Behold OQ-3, M11-a og arkitekturavhengighetene synlig dokumentert.
> 6. Kontroller at de 13 punktene ikke lenger står som uavklarte beslutninger. Behold eventuelle nødvendige testforbehold.
> 7. Rapporter kort hva som fortsatt blokkerer Finalize.
>
> Ikke opprett ny BMAD-kjøring.
> Ikke endre PRD.
> Ikke innfør nye funksjoner.
> Ikke start implementering.
> Ikke commit eller push.
>
> Stopp etter dokumentasjonen og kvalitetskontrollen.

</details>

<details>
<summary><strong>Prompt 12 – KI-logg, øktlogg og klargjøring for commit</strong> (prompten var avkuttet)</summary>

> Vi fortsetter i samme prosjekt og på eksisterende branch `ux/sebastian-ux-design`.
>
> UX-beslutningene er nå konsolidert. Før vi fortsetter BMAD Finalize, skal vi sikre at dagens arbeid er korrekt dokumentert og klart for commit.
>
> **1. Kontroller prosjektets loggregler**
>
> Les gjeldende `docs/ki-logg/README.md` og den oppdaterte versjonen på `origin/main`, uten å merge eller rebase.
>
> Kontroller også relevante instrukser i CLAUDE.md og AGENTS.md.
>
> **2. Opprett KI-logg for 9. november 2026**
>
> Dokumenter dagens faktiske KI-assisterte arbeid med UX:
> - beslutninger, wireframes og forhåndsvisninger
> - utvikling av DESIGN.md og EXPERIENCE.md
> - gjennomganger, korrigeringer og kvalitetskontroll
> - hvilke KI-verktøy som ble brukt og hvordan arbeidet ble kontrollert
>
> Bruk faktiske tilgjengelige samtaler, promptopplysninger, Git-endringer og memlogg som kilder.
>
> Skill tydelig mellom hva Claude Code har utført, hva ChatGPT har vurdert, og hva jeg har godkjent.
>
> Ikke dikt opp manglende prompts, tester eller hendelser.
>
> **3. Dokumenter loggavviket fra 3. og 4. november**
>
> Ta inn en kort, tydelig merknad i loggen for 9. november om at KI-loggføringen ikke ble gjort fortløpende disse dagene.
>
> Vis til den eksisterende UX-memloggen og arbeidsfilene som dokumenterer arbeidet.
>
> Ikke opprett tilbakedaterte logger som gir inntrykk av at de ble skrevet 3. eller 4. november.
>
> **4. Oppdater relevant øktlogg**
>
> Følg prosjektets etablerte praksis. Hold KI-logg, øktlogg og UX-memlogg adskilt, og unngå unødvendig duplisering.
>
> **5. Klargjør Git-kontrollpunkt**
>
> Kontroller:
> - `git status`
> - hvilke filer som er endret eller opprettet
> - at DESIGN.md og EXPERIENCE.md fortsatt har `status: draft`
> - at OQ-3, M11-a, OQ-7 og OQ-8 fortsatt er dokumentert som åpne avhengigheter
> - at ingen hemmeligheter eller reelle militære data er inkludert
> - at filer i `.working/` som inngår i arbeidet, ikke blir glemt
>
> Foreslå en ryddig commit-inndeling med konkrete commit-meldinger.
>
> **Viktig:**
> - Ikke endre produktbeslutninger eller PRD.
> - Ikke start en ny BMAD-kjøring.
> - Ikke merge eller rebase fra origin/main.
> - Ikke sett UX-dokumentene til final.
> - Ikke commit eller push ennå.
>
> Stopp og vis:
> 1. Hvilke logger du opp

</details>

## Hva KI leverte

Detaljene om hver beslutning står i UX-memloggen (oppføring 92–132) og
gjentas ikke her.

**Claude Code utførte:**

- **Oppstartskontroll (prompt 1):**
  - Kontrollerte Git-status, kjørte `git fetch` og fant 4 nye commits fra gruppen på `origin/main`, uten merge.
  - Fant at PRD og brief har fått ny formulering av særpreget (bare ordlyd) og nye regler for KI-logg.
  - Bekreftet at UX-memloggen var intakt, og at beslutningen om å kombinere fargetemaene ikke var registrert.
- **Git (prompt 2–4):**
  - Laget en commit-plan.
  - Laget tre lokale commits: `5769b3a` (memlogg), `cd014a9` (8 wireframes og 8 PNG-er) og `0903def` (4 HTML-filer og 4 PNG-er).
  - Pushet `ux/sebastian-ux-design` med upstream, uten force. `main` ble ikke rørt.
- **Visuell retning (prompt 5–6):**
  - Laget `.working/kombinert-retning-1.html` og en PNG.
  - Sammenlignet åtte oransjetoner og foreslo `#C75000`.
  - Regnet ut kontrast med WCAG-formelen og anslo projektorverdier med et CSS-filter.
  - Pekte på problemer: panel mot bakgrunn har bare 1,09:1, og markeringen for «valgt» ligner rammen for feil.
  - Foreslo typografi, avstand, komponenter og en tastaturmodell (A–D).
- **F4–F6 (prompt 7–9):**
  - Underagentene lagde wireframes for F4, F5 og F6, og Claude Code oppdaterte dem etter beslutningene.
  - Claude Code rettet arbeidstittelen og fjernet plassholderen `[tidsgrense]` fra F6, og kontrollerte F6-4 mot ordlyden i NFR-3 og NFR-5.
- **DESIGN.md og EXPERIENCE.md (prompt 9):**
  - En underagent skrev førsteutkastene etter workflowens oppskrift.
  - Claude Code kontrollerte dem mot PRD-en og memloggen.
- **Opprydding (prompt 10–11):**
  - Rettet frontmatter (ugyldig YAML i `sources`).
  - Oppdaterte modalatferd, valgt måned og de små feilene i UJ-1 og UJ-2.
  - Rettet skissene for F5 og F8.
  - Presenterte de 13 foreløpige detaljene med anbefalinger.
  - Oppdaterte begge dokumentene etter Sebastians vedtak.
- **Memlogg:** Førte alle beslutningene inn i UX-memloggen med `memlog.py` og konverterte linjeskift til LF etter hver skriving.

**ChatGPT vurderte**, ifølge promptene:
- oppstartskontrollen
- commit-planen
- forslagene og vurderingene som ble lagt fram
- statusrapporten for DESIGN.md og EXPERIENCE.md
- de 13 foreløpige detaljene

ChatGPT ble også brukt til å formulere promptene.

**Sebastian godkjente:**
- **Git:** de tre commitene, med alle 12 PNG-ene, og pushen
- **Visuelt:** den kombinerte paletten med `#C75000` som fokusfarge
- **A–D**, med justeringer
- **F4–F6 og F6-4**
- **Øvrige UX-avklaringer:**
  - én aktiv modal
  - valgt måned
  - de 13 detaljene, med justeringer for meldingsstripe og sperrede kontroller
  - dagsoversikten som en liste som ikke er en modal
  - feil ved sletting
- **Status:** at DESIGN.md og EXPERIENCE.md skal ha `status: draft` til OQ-3 er avklart

## Hva vi endret og hvorfor

- **Vedtatt og skrevet inn som bindende** i DESIGN.md, EXPERIENCE.md og memloggen. Forslagene fra Claude Code som Sebastian endret:
  - **Valgt måned:** Ikke en helsvart sektor, men nøytral markering med 2 px kant, panelbakgrunn og tekst.
  - **Lagre i F4:** Kan alltid trykkes. Bekreftelse ved endringer som ikke er lagret, ble lagt til (F4-4), selv om Claude Code anbefalte å droppe den.
  - **Fokus etter sletting:** Flyttes til et varig element, ikke til den midlertidige meldingen.
  - **F6-4:** Esc er sperret under analyse, og ingen plassholder skal vises i grensesnittet.
  - **Modaler:** Prinsippet om én aktiv modal ble gjort generelt.
  - **Meldingsstripe:** Forsvinner ikke ved neste handling.
  - **Sperrede kontroller:** Ingen generell fokusregel. Valget gjøres for hver komponent.
- **Fortsatt foreløpig:**
  - mikrotekst fra skissene, som språkvaskes før ferdigstilling
  - ordlyden på demo-merket
- **Utgangspunkt, ikke validert:** demping bak modaler, rammer og kanter, demo-merket, fremdriftsindikatoren og kolonnebreddene i F7.
- **Fortsatt åpent:**
  - OQ-3 (kategoriliste) hos gruppen
  - M11-a, en mulig konflikt med ordlyden i FR-2 og FR-23, hos gruppen
  - OQ-7 og OQ-8 i arkitekturen
- **Ikke endret:**
  - PRD-en
  - Product Brief
  - `main`
  - PRD-oppdateringen på `origin/main`, som ikke er hentet inn i UX-branchen

## Testing

Det er ikke testet noen programvare. Disse kontrollene ble faktisk kjørt:

- **Git:**
  - `git status`, `git fetch origin` og `git rev-list --left-right` mot `origin/main`
  - `git show --stat` etter hver commit
  - sjekksum av arbeidsfiler før og etter
  - `git ls-remote` og `rev-parse` etter push
- **Wireframes:**
  - JSON-validering av alle `.excalidraw`-filer: `index` på to tegn, unike og i rekkefølge, unike id-er og tillatte farger. Claude Code kontrollerte dette selv. Underagentene rapporterte i tillegg en egen kontroll av at innholdet holder seg innenfor rammene.
- **PNG-forhåndsvisninger:**
  - Laget med Claude Codes lokale SVG-renderer og Chrome uten nettverk, og sett gjennom av Claude Code. De er *ikke* tegnet av Excalidraw selv.
- **Kontrast:**
  - Alle 42 par på fargetemasiden ble regnet ut på nytt, og alle stemte.
  - Parene for den kombinerte retningen og oransjekandidatene ble regnet ut etter WCAG 2.1.
  - Projektortallene er anslag med et CSS-filter, ikke målinger.
- **Dokumentene:**
  - Det er kontrollert med `grep` at alle krav-ID-er finnes i PRD-en.
  - Det er funnet ingen kategorinavn som er diktet opp, ingen plassholdere i grensesnittekst, og ingen merkinger igjen for avklarte punkter.
  - Begge filene har `status: draft` og LF-linjeskift.
  - Frontmatter er skannet for risikable YAML-verdier. Det er ikke gjort full parsing, fordi det ikke finnes noe YAML-bibliotek, og ingenting er installert.
- **Hemmeligheter:** `grep` etter API-nøkler, tokens og passord i nye og endrede filer ga ingen treff.

**Ikke gjennomført:**
- åpning av `.excalidraw`-filene i Excalidraw
- testing på ekte projektor
- testing med tastatur og skjermleser
- full YAML-parsing
- ny BMAD-validering av PRD-en eller av UX-dokumentene
