# 2026-11-04 — Competitive Research om produktets særpreg

- **Deltakere:** Lars Tellef Risøy
- **KI-verktøy:** Claude Code med modellen Claude Opus 5.5 (`claude-opus-5-5`) og BMAD-skillene `bmad-help`, `bmad-deep-recon` (type `competitive`, Run) og `bmad-review` (linsene structure og prose). Tolv underagenter (general-purpose) ble brukt: seks til nettsøk i to runder, tre til kritisk motgjennomgang («red team»), én til semantisk sitatkontroll og to til språk- og strukturgjennomgang. ChatGPT (OpenAI) ble brukt til kritisk vurdering av Claude Codes resultater, utforming av promptene og planlegging av videre arbeid.
- **Kontrollert av:** <fylles inn av gruppemedlemmet som har godkjent loggen>

## Oppgave

Kartlegge om særpreget i Product Brief §4 og PRD §1 er tilstrekkelig underbygget
mot eksisterende løsninger, uten å starte planleggingen på nytt. Product Brief og
PRD var ferdigstilt, og UX var påbegynt av et annet gruppemedlem. Undersøkelsen
skulle dekke interaktive årshjul, KI-basert uttrekk av aktiviteter og frister fra
dokumenter, Microsoft 365 (Copilot og Planner) og løsninger som kombinerer
dokumentanalyse, menneskelig godkjenning og visuell planlegging. Resultatet
skulle deretter komprimeres til en beslutningsorientert rapport på 3–5 sider.

## Prompt (ordrett)

Promptene er gjengitt ordrett og i rekkefølge. Claude Codes svar mellom
promptene er ikke tatt med.

<details>
<summary><strong>Prompt 1 – Forberedelse og anbefalt workflow</strong> (2026-11-04)</summary>

> Vi skal nå gjennomføre Competitive Research som et avgrenset supplement til analysefasen i IBE160-prosjektet.
>
> **Kontekst**
>
> Product Brief og PRD er ferdigstilt, kontrollert og godkjent. PRD har status `final`. UX-workflowen er påbegynt av et annet gruppemedlem.
>
> Vi ønsker å undersøke om produktets påståtte særpreg er tilstrekkelig underbygget, uten å starte planleggingsprosessen på nytt.
>
> **Oppgave**
>
> 1. Kontroller først Git-status, lokale endringer og upushede commits. Hent siste endringer fra origin og gjennomfør trygg fast-forward dersom mulig. Ved konflikt eller risiko for å overskrive arbeid skal du stoppe og rapportere.
> 2. Les `CLAUDE.md`, gjeldende Product Brief, PRD og relevant eksisterende research.
> 3. Bruk `bmad-help` eller tilsvarende i installert BMAD-versjon for å identifisere riktig Competitive Research-workflow.
> 4. Undersøk om tilsvarende research allerede finnes i prosjektet, slik at vi unngår duplisering.
> 5. Presenter kort hvordan du anbefaler å gjennomføre en målrettet Competitive Research med vekt på:
>    - eksisterende interaktive årshjul
>    - KI-basert uttrekk av aktiviteter og frister fra dokumenter
>    - Microsoft 365, Copilot, Planner og relevante konkurrerende løsninger
>    - løsninger som kombinerer dokumentanalyse, menneskelig godkjenning og visuell planlegging
>    - hvorvidt vårt påståtte konkurransefortrinn faktisk skiller seg fra eksisterende produkter
>
> **Rammer**
>
> - Følg den installerte BMAD-metodikken.
> - Skill dokumenterte produktfunksjoner fra antakelser og markedsføringspåstander.
> - Ikke endre Product Brief, PRD, UX eller andre godkjente planleggingsdokumenter.
> - Ikke opprett research-rapport eller nye prosjektfiler ennå.
> - Ikke start UX, architecture eller implementering.
> - Respekter eksisterende KI-loggstruktur.
> - Ingen commit eller push i denne omgang.
>
> **Resultat**
>
> Presenter anbefalt BMAD-workflow, eventuelle eksisterende research-artefakter og foreslått avgrensning. Stopp deretter for godkjenning før researchen gjennomføres.

</details>

<details>
<summary><strong>Prompt 2 – Godkjenning av plan og gjennomføring</strong> (2026-11-04)</summary>

> Jeg godkjenner den foreslåtte Competitive Research-planen, med følgende beslutninger og presiseringer.
>
> **Innstillinger**
> - Workflow: `bmad-deep-recon`, type `competitive`.
> - Mode: Run.
> - Rapportspråk: norsk bokmål.
> - Preset: standard, med 3 parallelle underagenter.
> - Validation: high, inkludert kritisk motgjennomgang av hovedkonklusjonene.
> - Output: Markdown. Ikke generer HTML-oppsummering.
>
> **Presiseringer til undersøkelsen**
>
> 1. Undersøk ikke bare om konkurrenter tilbyr enkeltfunksjonene, men om de tilbyr en tilsvarende samlet arbeidsflyt: dokumentopplasting, KI-genererte aktivitetsforslag, individuell brukerkontroll mot kildeutdrag, eksplisitt godkjenning og interaktivt årshjul.
>
> 2. Skill mellom funksjonalitet som finnes direkte i ett produkt, funksjonalitet som kan oppnås gjennom integrasjoner/konfigurasjon, og funksjonalitet som krever egenutvikling.
>
> 3. Vurder særskilt om eksisterende Microsoft 365-verktøy kan dekke behovet tilstrekkelig godt, selv om de ikke fungerer nøyaktig som vår løsning.
>
> 4. Skill tydelig mellom dokumenterte funksjoner, leverandørpåstander, antakelser og funksjoner det ikke er funnet bevis for. Ikke konkluder med at en funksjon ikke eksisterer bare fordi den ikke ble funnet. Bruk daterte og etterprøvbare kilder, med uavhengig bekreftelse der det er mulig.
>
> 5. Vurder særpreget mot den faktiske MVP-en i Product Brief og PRD, ikke mot fremtidige funksjoner utenfor scope.
>
> **Gjennomføring**
>
> Kjør den godkjente BMAD-workflowen og opprett research-artefaktene i den etablerte BMAD-strukturen.
>
> Respekter pågående UX-arbeid. Ikke endre Product Brief, PRD, UX, arkitektur eller andre godkjente planleggingsdokumenter.
>
> Følg eksisterende rutiner for KI-logg og beslutningshistorikk uten unødvendig dobbeltlogging.
>
> Når rapporten er ferdig, presenter hovedfunnene, hvilke kilder som støtter dem, vesentlige usikkerheter og din vurdering av om påstanden om særpreg holder.
>
> Stopp deretter for min kontroll og godkjenning.
>
> **Ikke commit eller push ennå.**

</details>

<details>
<summary><strong>Prompt 3 – Komprimering av rapporten</strong> (2026-11-04)</summary>

> Vi skal nå ferdigstille Competitive Research før vi vurderer eventuelle justeringer i Product Brief og PRD.
>
> **Oppgave**
>
> Revider `research.md` til en konsis, beslutningsorientert rapport på omtrent 3–5 sider, med hovedvekt på det som faktisk er relevant for produktets særpreg og vår MVP.
>
> Behold den gjennomførte researchen som grunnlag. Ikke start en ny omfattende undersøkelse.
>
> **Prioriter følgende innhold:**
>
> 1. Kort formål og metode, inkludert kildekritikk.
> 2. De viktigste konkurrentene, særlig Plandisc, Microsoft Planner Agent og Clio.
> 3. En kompakt sammenligningsmatrise mot vår faktiske MVP.
> 4. Hva som reelt skiller løsningen vår fra eksisterende alternativer.
> 5. Vesentlige usikkerheter, motargumenter og konsekvenser for prosjektet.
> 6. Utvalgte, etterprøvbare kilder.
>
> **Vurder også to supplerende differensieringsfaktorer:**
>
> - **Kostnad og tilgjengelighet:** Vurder verdien av at applikasjonen kan kjøres lokalt og demonstreres uten betalt KI-tilgang. Skill tydelig mellom gratis demo-modus og ordinær KI-analyse som kan medføre API-kostnader. Ikke påstå at hele løsningen er gratis.
> - **Militær tilpasning:** Vurder om målretting mot troppssjefer, militær terminologi, ordrebasert planlegging, aktivitetskategorier og ukehenvisninger gir et relevant særpreg. Skill mellom funksjonalitet som allerede er spesifisert, tilpasninger som bare er mulige, og fordeler som må dokumenteres gjennom testing.
>
> Disse to vurderingene skal være korte og hovedsakelig bygge på eksisterende prosjektkrav og research. Ikke utvid undersøkelsen til en omfattende pris- eller domenestudie.
>
> **Kvalitetskrav**
>
> - Skill mellom dokumenterte funn, leverandørpåstander og antakelser.
> - Ikke presenter manglende funn som bevis for unikhet.
> - Ikke påstå at løsningen er dokumentert bedre enn konkurrentene.
> - Behold relevante kilder med etterprøvbare henvisninger.
> - Kontroller at hovedkonklusjonene er konsistente med kildegrunnlaget og tidligere red-team-funn.
> - Unngå unødvendige gjentakelser og tekniske detaljer som allerede finnes i `digests/`.
>
> Behold `digests/` og `.memlog.md` som underlagsmateriale og prosessdokumentasjon.
>
> **Avgrensning**
>
> Ikke endre Product Brief, PRD, UX eller andre godkjente planleggingsdokumenter. Ikke utvid MVP-scope.
>
> Ikke opprett nye prosjektleveranser utover nødvendige oppdateringer av research-artefaktene og eventuell KI-logg etter eksisterende rutiner.
>
> **Når arbeidet er ferdig**
>
> Presenter kort:
> - Hva som ble komprimert eller endret.
> - Den endelige vurderingen av produktets særpreg.
> - Om kostnad/tilgjengelighet og militær tilpasning tilfører reell verdi.
> - Eventuelle funn som kan begrunne senere justeringer i Product Brief eller PRD.
> - Hvilke filer som er endret, og Git-status.
>
> Stopp deretter for kontroll og godkjenning. Ikke commit eller push ennå.

</details>

<details>
<summary><strong>Prompt 4 – Siste kontroll før commit</strong> (2026-11-04)</summary>

> Den komprimerte Competitive Research-rapporten er faglig godkjent.
>
> Før commit ønsker jeg en siste, begrenset kontroll:
>
> 1. Les den faktiske `research.md` og kontroller at den ikke inneholder doble overskrifter, gjentatte avsnitt eller rester fra omskrivingen.
> 2. Kontroller at alle kildehenvisninger i den komprimerte rapporten peker til korrekte oppføringer i den endelige kildelisten.
> 3. Kontroller at beskrivelsene av feltstatus samsvarer med PRD, inkludert at kategorifeltet ikke har status «ugyldig».
> 4. Kontroller eksisterende KI-loggrutiner i `CLAUDE.md` og `docs/ki-logg/README.md`, og klargjør nødvendig loggføring uten dobbeltlogging.
> 5. Vis hvilke filer som er endret eller opprettet, og gjeldende Git-status.
>
> Rett eventuelle mindre feil direkte. Ikke gjennomfør ny research, og ikke endre Product Brief, PRD eller UX.
>
> Stopp før commit og push. Presenter bare eventuelle kontrollfunn og en kort bekreftelse på at researchen er klar til å committes.

</details>

<details>
<summary><strong>Prompt 5 – Godkjenning av KI-logg før commit</strong> (2026-11-04)</summary>

> Jeg godkjenner den ferdige Competitive Research-rapporten og sluttkontrollen.
>
> Før vi committer, ønsker jeg å godkjenne KI-loggen i samsvar med rutinene i CLAUDE.md og docs/ki-logg/README.md.
>
> Vis meg det komplette utkastet til `2026-11-04-competitive-research.md`, slik at jeg kan kontrollere at KI-bruken, de viktigste promptene, beslutningene og kontrollfunnene er korrekt dokumentert.
>
> Ikke endre researchrapporten eller andre prosjektfiler.
>
> Ikke opprett KI-loggfilen i repoet, og ikke commit eller push før jeg har godkjent utkastet.
>
> Når KI-loggen er godkjent, skal vi samle research-artefaktene og KI-loggen i en kontrollert commit og push til origin/main. Unngå separate eller automatiske commits fra sesjonsloggingen uten at disse er avklart på forhånd.

</details>

<details>
<summary><strong>Prompt 6 – Godkjent KI-logg, commit og push</strong> (2026-11-04)</summary>

> Jeg godkjenner KI-loggen med følgende justeringer før commit:
>
> 1. **KI-verktøy:** Legg til ChatGPT. Det ble brukt til kritisk vurdering av Claude Codes resultater, utforming av promptene og planlegging av videre arbeid.
>
> 2. **Personlig refleksjon:** Legg til følgende korte avsnitt i KI-loggen:
>
>    *Competitive Research ble gjennomført etter at Product Brief og PRD var ferdigstilt, altså senere enn det som normalt ville vært naturlig i BMAD-prosessen. Etter nye innspill fra forelesningen vurderte vi det likevel som hensiktsmessig å gå tilbake og undersøke eksisterende løsninger. Dette ga oss et bedre grunnlag for å vurdere produktets særpreg og viste verdien av å revurdere tidligere beslutninger når vi får ny kunnskap.*
>
> 3. **Godkjenning:** Behold «Kontrollert av» som et felt for gruppemedlemmet som faktisk har godkjent loggen. Ikke finn på et navn.
>
> 4. **Sesjonslogg:** Ta relevant oppdatering av `.logs/lars-tellef-risoy/issues.md` med i samme commit. Unngå separat automatisk commit.
>
> **Gjennomføring**
>
> - Opprett den godkjente KI-loggen i `docs/ki-logg/2026-11-04-competitive-research.md`.
> - Kontroller at kun research-artefaktene, KI-loggen og relevant sesjonslogg inngår.
> - Commit og push til `origin/main`.
> - Vis commit-ID, hvilke filer som inngikk, push-resultatet og `git status -sb`.
>
> Ikke endre Product Brief, PRD eller UX ennå.

</details>

## Hva KI leverte

- **Forberedelse:** Claude Code kontrollerte Git, leste CLAUDE.md, AGENTS.md, Product Brief, PRD og tidligere logger, og fant ingen eksisterende research. Med `bmad-help` ble `bmad-deep-recon` med type `competitive` identifisert som riktig workflow. Claude Code foreslo en plan med tre spor (årshjul, Microsoft 365, KI-uttrekk med menneskelig kontroll).
- **Gjennomføring:**
  - To runder med nettsøk i tre spor.
  - Tre skeptikere angrep hver sin hovedkonklusjon (K1–K3). Alle tre konkluderte med «må nyanseres», ingen med «faller», og konklusjonene ble snevret inn tilsvarende.
  - En semantisk sitatkontroll av den første, lange rapporten fant 11 avvik mellom tekst og kilde, og ordlyden ble rettet.
  - En språk- og strukturgjennomgang ga forslag. De fleste ble innarbeidet. Ikke innarbeidet: like kolonner i alle tabellene og ensartet datoformat.
- **Komprimering:** Rapporten ble skrevet om fra ca. 6 500 til ca. 2 500 ord. Kostnad og tilgjengelighet og militær tilpasning ble vurdert ut fra eksisterende PRD-krav og funn, uten ny research. Den lange arbeidsversjonen er ikke lagt i repoet. Grunnlaget for den ligger i `digests/` og `.memlog.md`.
- **Resultat:** Mappa `_bmad-output/planning-artifacts/research/competitive-aarshjul-ki-uttrekk-saerpreg-2026-11-04/` med:
  - `research.md`: rapporten, komprimert til ca. 2 500 ord pluss 32 utvalgte kilder
  - `.memlog.md`: beslutningshistorikk og påstandsregister
  - `digests/`: notater fra søkerundene, motgjennomgangen og sitatkontrollen
- **Siste kontroll før commit:**
  - Kildene [4]–[8] hadde fått nye numre ved komprimeringen, selv om rapporten sier at numrene er beholdt. Numrene er rettet tilbake til arbeidsversjonens, så de samsvarer med `.memlog.md`: [7] PlanIt, [8] Orbit, [10] Plandisc-integrasjoner, [11] Planner Agent-support, [12] GA-kunngjøring.
  - Det er presisert at kategori bare kan ha status manglende eller usikker, i samsvar med PRD.
  - Nummereringen av avsnitt og merkingen av lesegrunnlag er gjort konsekvent.
- **Hovedkonklusjon:**
  - Påstanden om særpreg holder bare delvis og bør snevres inn. Den foreslåtte formuleringen er sporbar kontroll av hvert KI-forslag mot verifiserte kildeutdrag før det legges inn i årshjulet. Plandisc og Microsoft Planner Agent er de nærmeste alternativene.
  - Kostnad og tilgjengelighet har verdi for demonstrasjon og evaluering gjennom demo-modus, men er ikke et markedsfortrinn. Ordinær analyse kan gi API-kostnader.
  - Militær tilpasning er relevant for posisjoneringen, men et tynt særpreg alene, og må vises gjennom testing.

## Hva vi endret og hvorfor

- **Ved planen:** Vi fastsatte innstillingene og la til fem presiseringer: samlet arbeidsflyt, leveringsnivå, Microsoft 365 som «godt nok»-alternativ, skillet mellom bevistyper og MVP som målestokk. Formålet var at undersøkelsen skulle teste påstanden mot den faktiske v1-flyten.
- **Etter første rapport:** Rapporten var for lang. Vi ba om en komprimert, beslutningsorientert versjon og to supplerende vurderinger: kostnad og tilgjengelighet, og militær tilpasning. Disse skulle bygge på eksisterende krav og funn, uten ny research.
- **Før commit:** Vi ba om en siste kontroll av struktur, kildehenvisninger og samsvar med PRD for feltstatus. Kontrollen avdekket feilnummereringen av kildene, som deretter ble rettet.
- **KI-loggen:** Vi kontrollerte utkastet og la til ChatGPT under KI-verktøy og en personlig refleksjon. Feltet «Kontrollert av» ble stående for gruppemedlemmet som faktisk godkjenner loggen.
- **Ikke endret:** Product Brief, PRD og UX. Om særpreget skal formuleres om, er en egen gruppebeslutning.

## Testing

Ingen kode er skrevet, så det finnes ingen programvaretester.

- **Mekanisk sitatkontroll** med `recon_kit.py citations`: ingen henvisninger uten rad i kildetabellen og ingen kilder uten henvisning, både før og etter komprimeringen og etter den siste kontrollen. Kontrollen fanget ikke feilnummereringen av [4]–[8], fordi markørene og radene stemte overens med hverandre. Feilen ble funnet ved manuell sammenligning med `.memlog.md`.
- **Påstandsregisteret** er talt med `recon_kit.py tally`: 10 verifiserte og 17 uverifiserte påstander.
- **Ferskheten** til påstandene er beregnet med `recon_kit.py staleness`.
- **Semantisk sitatkontroll** ved en egen underagent: 11 avvik, rettet.
- **Ikke gjort:** Ingen av konkurrentproduktene er prøvd i praksis.

## Refleksjon

Competitive Research ble gjennomført etter at Product Brief og PRD var
ferdigstilt, altså senere enn det som normalt ville vært naturlig i
BMAD-prosessen. Etter nye innspill fra forelesningen vurderte vi det likevel som
hensiktsmessig å gå tilbake og undersøke eksisterende løsninger. Dette ga oss et
bedre grunnlag for å vurdere produktets særpreg og viste verdien av å revurdere
tidligere beslutninger når vi får ny kunnskap.
