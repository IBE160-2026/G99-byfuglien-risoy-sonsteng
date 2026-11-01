# 2026-11-01 — Validering, presisering og forkorting av Product Brief

- **Deltakere:** Risøy
- **KI-verktøy:** Claude Code med modellen Claude Opus 5.5 (`claude-opus-5-5`). Valideringen brukte BMAD-agenten Mary (Business Analyst) og `bmad-product-brief` i Validate-modus. Forkortingen brukte BMAD-veiledningen i `bmad-product-brief` som grunnlag.
- **Kontrollert av:** Risøy

## Oppgave

Kvalitetssikre Product Brief før UX-fasen, uten å starte Analysis-fasen på nytt,
og forkorte den mot faglærers veiledende omfang uten å endre produktet. Arbeidet
foregikk i to økter samme dag:

1. **Validering og presisering:** En uavhengig BMAD-validering av briefen mot fem
   kontroller: traceability, measurability, explicit exclusions, provenance og
   consistency. Deretter en begrenset oppdatering med de sju tekstendringene
   Risøy godkjente, fulgt av en konsistenskontroll mot den ferdige PRD-en.
   Endringene ble committet i `0d4517e`.
2. **Redaksjonell forkorting:** Briefen hadde 1 146 ord og fylte rett under fire
   A4-sider, mens veiledende omfang er omtrent 1–2 sider. Målet var omtrent 2,5
   sider med samme innhold, scope og minst like høy presisjon.

**Bevisst avvik fra README:** Begge øktene står i denne fila, selv om README sier
én fil per økt, fordi de utgjør én sammenhengende validerings- og
forkortingsprosess. Øktene er skilt i hver seksjon.

## Prompt (ordrett)

Promptene er gjengitt i rekkefølge. Første økt startet med kommandoen
`/bmad-agent-analyst`, og andre økt startet etter `/clear`.

**Kilder:** Prompt 3–8 er kopiert fra samtalen i andre økt. Prompt 1–2 er bevart
slik de sto i utkastet til denne loggen fra første økt. Samtalen fra første økt
var ikke tilgjengelig da loggen ble ferdigstilt, så de er ikke kontrollert mot
den på nytt.

<details>
<summary><strong>Prompt 1 – Validering av Product Brief</strong></summary>

> Jeg ønsker å gjennomføre en uavhengig validering av vår eksisterende Product Brief før vi går videre til UX-fasen.
>
> **Oppdrag:**
> Bruk BMAD v6 sin offisielle Product Brief-workflow med **Validate intent**. Du skal opptre som Mary, Business Analyst.
>
> Les følgende:
> - `docs/product-brief.md`
> - `CLAUDE.md`
> - Relevant prosjektkonfigurasjon og BMAD-instruksjoner.
>
> **Viktig kontekst:**
> - Product Brief er allerede utarbeidet.
> - PRD er ferdigstilt og validert.
> - Vi ønsker nå en kvalitetssjekk av Product Brief, ikke å starte Analysis-fasen på nytt.
>
> **Gjennomfør valideringen med særlig vekt på:**
>
> 1. **Traceability:** Kan hver MVP-funksjon spores til et tydelig brukerbehov eller mål?
> 2. **Measurability:** Er suksesskriteriene tilstrekkelig testbare på Product Brief-nivå, uten å kreve detaljer som hører hjemme i PRD?
> 3. **Explicit exclusions:** Er det tydelig hva som ikke skal inngå i første versjon?
> 4. **Provenance:** Er faktiske observasjoner, antakelser og påstander om eksisterende løsninger tilstrekkelig underbygget?
> 5. **Consistency:** Er problem, løsning, scope, tekniske begrensninger og visjon innbyrdes konsistente?
>
> Vurder også om eventuelle vesentlige risikoer eller uavklarte spørsmål mangler.
>
> **Arbeidsregler:**
> - Ikke rediger noen filer.
> - Ikke opprett nye dokumenter eller valideringsrapporter i repoet.
> - Ikke gjennomfør commit eller push.
> - Ikke foreslå endringer bare for å gjøre dokumentet lengre eller mer omfattende.
> - Skill tydelig mellom faktiske mangler, anbefalte forbedringer og valgfrie tillegg.
> - Ta hensyn til at Product Brief skal være et overordnet dokument, mens FR, NFR og detaljerte acceptance criteria hører hjemme i PRD og senere utviklingsarbeid.
> - Ikke bruk tidligere samtaler eller våre foreslåtte endringer som fasit.
>
> **Ønsket resultat:**
>
> Gi meg en strukturert vurdering av hver av de fem kvalitetskontrollene, med konkrete henvisninger til Product Brief.
>
> For hvert eventuelle funn skal du oppgi:
> - Hvilken seksjon det gjelder.
> - Hva som er problemet.
> - Hvorfor det er et problem etter BMAD.
> - Om endringen er nødvendig, anbefalt eller valgfri.
> - Et konkret forbedringsforslag der det er relevant.
>
> Avslutt med en samlet vurdering av om Product Brief kan beholdes slik den er, om mindre endringer anbefales, eller om vesentlig revisjon er nødvendig.
>
> **Stopp etter vurderingen og vent på mine beslutninger.**

</details>

<details>
<summary><strong>Prompt 2 – Begrenset oppdatering</strong></summary>

> Vi skal nå gjennomføre en begrenset oppdatering av Product Briefen etter en uavhengig validering med Mary, Business Analyst, i BMAD v6.
>
> Vi har gjennomgått samtlige funn og tatt konkrete beslutninger om hvilke endringer som skal gjennomføres.
>
> **Oppdraget er å implementere kun de sju godkjente tekstendringene, kontrollere konsistens mot PRD og dokumentere arbeidet i KI-loggen.**
>
> ## 1. Forberedelse
>
> Les:
> - `AGENTS.md` og relevante prosjektinstruksjoner.
> - `_bmad-output/planning-artifacts/product-brief.md`.
> - Den ferdige PRD-en i planning-artifacts.
> - Eksisterende instruksjoner for KI-loggføring.
>
> Bruk eksisterende BMAD-struktur og gjeldende filer. Ikke opprett en ny Product Brief.
>
> Kontroller først `git status -sb`, slik at eventuelle eksisterende endringer ikke overskrives.
>
> ## 2. Godkjente endringer
>
> ### Endring 1 – Section 2: The Problem
>
> Legg til følgende setning på et naturlig sted i problembeskrivelsen:
>
> «Problemforståelsen bygger på gruppemedlemmenes samlede erfaringer og observasjoner fra over ett års tjeneste som troppssjefer i Forsvaret.»
>
> Ikke endre resten av problembeskrivelsen.
>
> ### Endring 2 – Section 4: What Makes This Different
>
> Erstatt setningen som hevder at eksisterende planleggingsverktøy ofte krever manuell overføring av informasjon, med:
>
> «I den aktuelle planleggingsprosessen må informasjon fra ordre og dokumenter ofte bearbeides og overføres manuelt til aktivitetsplanen.»
>
> Behold resten av seksjonen, inkludert beskrivelsen av løsningens særpreg.
>
> Formålet er å beskrive den observerte arbeidsprosessen uten å fremsette udokumenterte påstander om konkurrentenes funksjonalitet.
>
> ### Endring 3 – Section 6: User outcome
>
> Legg til følgende suksesskriterium:
>
> «I brukertest kan brukeren finne ut når en aktivitet skjer og hvem som har ansvaret, uten å åpne andre filer.»
>
> Behold eksisterende suksesskriterier.
>
> ### Endring 4 – Section 6: Business / mission
>
> Behold eksisterende beskrivelse av sammenligningen mellom Excel og applikasjonen.
>
> Legg til:
>
> «Løsningen regnes som mer effektiv dersom oppgaven tar kortere tid uten flere feil sammenlignet med en forhåndsdefinert fasit.»
>
> ### Endring 5 – Section 7: IN 2 – Aktivitetshåndtering
>
> Legg til følgende presisering:
>
> «Frister registreres som aktiviteter.»
>
> Dette skal ikke innføre en separat fristfunksjon eller utvide eksisterende scope.
>
> ### Endring 6 – Section 7: IN 5 – Brukerkontroll og lagring
>
> Legg til:
>
> «Brukeren skal kunne kontrollere forslagene mot tilgjengelige kildeutdrag fra dokumentet.»
>
> Dette skal være en presisering av eksisterende brukerkontroll, ikke en ny funksjon.
>
> ### Endring 7 – Section 7: OUT – First version
>
> Legg til følgende avgrensning:
>
> «Operativ bruk med ekte dokumenter. Første versjon demonstrerer konseptet med fiktive data.»
>
> Ikke endre eksisterende sikkerhetskrav i Section 8.
>
> ## 3. Hva skal ikke endres?
>
> Vi har eksplisitt besluttet følgende:
>
> - Ingen ny Risks & Assumptions-seksjon.
> - Ingen nye krav til Excel-import, eksport eller utskrift.
> - Ingen endring av demo-modus i Section 8.
> - Ingen endring av produktvisjonen.
> - Ingen endring av produktnavn.
> - Ingen innføring av nye prosentmål eller detaljerte NFR.
> - Ingen implementering av ny funksjonalitet.
> - Ingen øvrige endringer fra Marys valideringsrapport.
>
> Ikke benytt oppdraget til generell omskriving, språkvask eller omstrukturering av dokumentet.
>
> ## 4. Konsistenskontroll mot PRD
>
> Etter at endringene er gjennomført, les relevante deler av den ferdige PRD-en.
>
> Kontroller særlig:
>
> 1. At frister kan håndteres innenfor den eksisterende aktivitetsmodellen.
> 2. At brukeren kan kontrollere KI-forslag mot tilgjengelige kildeutdrag.
> 3. At presiseringen om operativ bruk og fiktive data ikke motsier PRD.
> 4. At de to nye suksesskriteriene er forenlige med PRD-ens eksisterende success metrics og teststrategi.
> 5. At endringene ikke introduserer nye funksjonskrav eller utvider MVP.
>
> Hvis en endring avdekker motstrid eller en vesentlig mangel i PRD, skal du rapportere dette.
>
> **Ikke rediger PRD-en uten særskilt godkjenning.**
>
> ## 5. KI-logg og prosessdokumentasjon
>
> Følg eksisterende instruksjoner i `AGENTS.md`, `CLAUDE.md` dersom den finnes, og KI-loggens README.
>
> Dokumenter den faktiske arbeidsøkten med:
> - Formålet med oppdateringen.
> - At endringene bygger på en uavhengig BMAD-validering og påfølgende menneskelige beslutninger.
> - Hvilke endringer som ble godkjent.
> - At gruppen bevisst avviste andre forslag for å unngå unødvendig scope-utvidelse og detaljering.
> - Hvilke kontroller som ble gjennomført.
> - Eventuelle avvik som ble oppdaget.
>
> Følg eksisterende loggformat. Ikke finn opp en ny mal.
>
> ## 6. Avsluttende kontroll
>
> Når arbeidet er ferdig:
>
> 1. Vis `git diff` for Product Briefen.
> 2. Vis hvilke filer som er endret.
> 3. Oppsummer resultatet av konsistenskontrollen mot PRD.
> 4. Kontroller at ingen ikke-godkjente endringer er gjennomført.
> 5. Vis `git status -sb`.
>
> **Viktig:**
>
> - Ikke gjennomfør commit.
> - Ikke gjennomfør push.
> - Ikke endre andre planleggingsdokumenter.
> - Ikke overskriv eksisterende ucommittede endringer.
> - Stopp etter kontrollen og vent på min godkjenning.
>
> Målet er en presis og minimal oppdatering av Product Briefen, med full sporbarhet og uten unødvendig endring av den allerede ferdigstilte PRD-en.

</details>

<details>
<summary><strong>Prompt 3 – Forslag til forkortet Product Brief</strong></summary>

> Vi skal nå gjennomføre en redaksjonell optimalisering av vår ferdigstilte Product Brief etter BMAD v6.
>
> Product Briefen er validert, kvalitetssikret og committet til origin/main i commit `0d4517ed7b1f68dd2a80335adf0467b9c661767a`.
>
> Den inneholder 1 146 ord og fyller rett under fire A4-sider. Faglærers veiledende omfang er omtrent 1–2 sider. Vi ønsker å redusere dokumentet til omkring **2,5 A4-sider**, samtidig som vi bevarer faglig kvalitet og nødvendige detaljer.
>
> **Viktigste prinsipp: Skriv mer konsist, ikke bare mindre.**
>
> Søk aktivt etter formuleringer som kan dekke flere relevante forhold med færre ord, men uten å introdusere tvetydighet, upresise krav eller tap av betydning.
>
> ## 1. Les grunnlaget
>
> Les:
> - `AGENTS.md` og relevante prosjektinstruksjoner.
> - `_bmad-output/planning-artifacts/product-brief.md`.
> - Ferdig PRD for å forstå hvilke detaljer som allerede er presisert der.
>
> Bruk BMAD v6 sine prinsipper for Product Brief og riktig detaljeringsnivå.
>
> ## 2. Oppdrag
>
> Utarbeid et forslag til en forkortet Product Brief.
>
> Mål:
> - Omtrent 2,5 A4-sider ved tilsvarende formatering som nå.
> - Foreløpig ordmål 800–900 ord, men ikke som absolutt grense.
> - Bevar den nåværende strukturen med seksjonene 1–9.
> - Bevar produktets identitet, problemforståelse, kjerneflyt, målgruppe, suksesskriterier, scope, sikkerhetsforutsetninger og visjon.
> - Bevar alle sju presiseringene som ble godkjent etter Marys validering.
> - Ikke introduser ny funksjonalitet, nye krav eller nye antakelser.
>
> ## 3. Redaksjonelle prinsipper
>
> Prioriter følgende:
>
> **A. Fjern gjentakelser**
>
> Undersøk særlig overlapping mellom:
> - Executive Summary og The Problem.
> - The Problem og Who This Serves.
> - The Solution og Scope IN.
> - Success Criteria og Security & Testing.
>
> Behold informasjonen der den har størst verdi, men sørg for at hver seksjon fortsatt oppfyller sin funksjon.
>
> **B. Konsolider formuleringer**
>
> Identifiser setninger som kan kombineres til én kortere, mer presis formulering.
>
> En sammenslåing skal bare gjennomføres dersom alle opprinnelige betydningselementer bevares.
>
> **C. Bevar entydighet**
>
> Ikke forenkle krav eller avgrensninger slik at de kan tolkes på flere måter.
>
> Bevar spesielt:
> - De fem MVP-kapabilitetene.
> - Hvilke dokumentformater som støttes.
> - At usikker informasjon markeres.
> - Eksplisitt brukergodkjenning.
> - Kildeutdrag.
> - Datalagring.
> - At frister håndteres som aktiviteter.
> - Avgrensning mot operativ bruk med ekte dokumenter.
> - Mock/demo-modus.
> - Skillet mellom V1 og langsiktig visjon.
>
> **D. Riktig detaljeringsnivå**
>
> Product Brief skal forklare hva som skal bygges, hvorfor, for hvem, innenfor hvilke rammer og hvordan vi vurderer suksess.
>
> Ikke gjør den til en PRD med detaljerte FR, NFR eller acceptance criteria.
>
> ## 4. Leveranse – kun forslag
>
> Presenter:
>
> 1. Hele den foreslåtte, forkortede Product Briefen i Markdown.
> 2. Ordtelling før og etter, samt prosentvis reduksjon.
> 3. Et estimat på antall A4-sider, tydelig merket som estimat dersom dokumentet ikke faktisk er rendret.
> 4. En kort oversikt over hvilke seksjoner som er forkortet mest, og hvorfor.
> 5. Eventuelle formuleringer hvor forkortingen kan medføre tap av presisjon eller betydning.
>
> Gjennomfør også en kontroll mot den eksisterende PRD-en for å sikre at forslaget ikke endrer produktets innhold eller scope.
>
> **Viktig:**
> - Ikke rediger filer.
> - Ikke opprett nye dokumenter.
> - Ikke oppdater KI-loggen ennå.
> - Ikke gjennomfør commit eller push.
> - Ikke endre PRD-en.
> - Ikke slett eksisterende tekst uten å kunne begrunne hvorfor informasjonen enten er bevart annet sted eller ikke er nødvendig på Product Brief-nivå.
>
> Stopp etter å ha presentert forslaget. Jeg skal gjennomgå og godkjenne teksten før den eventuelt implementeres.

</details>

<details>
<summary><strong>Prompt 4 – Korrigering av utkastet på 928 ord</strong></summary>

> Jeg har gjennomgått forslaget til forkortet Product Brief på 928 ord.
>
> Forslaget er et godt utgangspunkt, men før vi godkjenner det ønsker jeg en siste redaksjonell forbedring.
>
> Ta utgangspunkt i det forkortede utkastet, ikke den opprinnelige versjonen.
>
> Gjennomfør følgende i det foreslåtte utkastet:
>
> 1. **Section 2:** Forbedre lesbarheten i den lange problembeskrivelsen. Bevar samtlige betydningselementer, men unngå en lang setning med mange sideordnede ledd.
>
> 2. **Section 3:** Kontroller at kjerneflyten fortsatt er entydig når det gjelder KI-genererte aktivitetsforslag, brukerkontroll og godkjenning.
>
> 3. **Section 6:** Gjør det eksplisitt at tidsbruken måles og sammenlignes mellom Excel og applikasjonen. Behold kriteriet om kortere tid uten flere feil.
>
> 4. **Section 7 – IN 4:** Erstatt «de samme feltene» med en kort, selvstendig formulering som tydelig beskriver hvilke aktivitetsopplysninger KI skal foreslå. Unngå unødvendige gjentakelser.
>
> 5. **Section 7 – OUT:** Behold den opprinnelige betydningen av avgrensningene. KI-basert prioritering og beslutningstaking skal være utelatt, og prediksjon, konfliktanalyse, optimalisering og beslutningsstøtte skal være utelatt uavhengig av teknologi.
>
> 6. **Section 8:** Bruk tydelig og forpliktende språk («skal») for sentrale sikkerhetskrav og krav til demo-modus.
>
> Kontroller også at de sju tidligere godkjente presiseringene fortsatt er ivaretatt.
>
> **Mål:** En mer konsis Product Brief med samme innhold, samme scope og minst like høy presisjon som den opprinnelige versjonen.
>
> Ikke gjør teksten lengre enn nødvendig. Foretrekk korte, tydelige setninger fremfor komplekse formuleringer med mange innskutte ledd.
>
> Presenter hele det reviderte utkastet, ny ordtelling og et estimat på sidelengde.
>
> Ikke rediger filer, PRD eller KI-logg. Ikke gjennomfør commit eller push. Stopp for godkjenning.

</details>

<details>
<summary><strong>Prompt 5 – Optimalisering av IN og OUT</strong></summary>

> Vi ønsker å undersøke om Product Briefen kan forkortes ytterligere, særlig gjennom en mer effektiv utforming av Section 7 – Scope (IN og OUT).
>
> Ta utgangspunkt i det siste reviderte utkastet på 980 ord, som foreløpig bare ligger i scratchpad. Sammenlign med den committede Product Briefen og den ferdige PRD-en.
>
> **Mål:**
>
> Reduser tekstmengden ytterligere uten å miste informasjon, endre MVP eller svekke presisjonen. Vi ønsker å nærme oss 2,5 A4-sider, men sidetallet skal ikke prioriteres foran kvalitet.
>
> ## 1. Optimaliser IN
>
> Behold de fem hovedkapabilitetene, men undersøk om beskrivelsene kan gjøres kortere.
>
> Vurder spesielt:
> - Om formuleringer kan dekke flere egenskaper samtidig.
> - Om gjentakelser mellom IN-punktene kan fjernes gjennom presise henvisninger.
> - Om alle nødvendige funksjoner fortsatt er entydig definert.
> - Om viktige avgrensninger kan fremgå tydeligere av IN, slik at de ikke trenger å gjentas i OUT.
>
> Behold skillet mellom årsvisning, månedsvisning med ukeinndeling og egne uke-/dagsvisninger.
>
> ## 2. Optimaliser OUT
>
> Gjennomgå hvert eksisterende OUT-punkt kritisk.
>
> Undersøk:
> - Hvilke punkter som kan slås sammen i naturlige kategorier.
> - Hvilke avgrensninger som allerede følger entydig av IN, og derfor eventuelt kan utelates.
> - Om noen punkter er unødvendig detaljerte på Product Brief-nivå.
> - Om bredere formuleringer kan dekke flere avgrensninger uten å bli tvetydige.
>
> Ikke behold et OUT-punkt bare fordi det finnes i originalen. Vurder hvilken funksjon det faktisk har.
>
> Samtidig skal bevisste og viktige avgrensninger fortsatt fremgå, særlig flerbruker, integrasjoner, Task Manager, avanserte KI-funksjoner og operativ bruk med ekte dokumenter.
>
> ## 3. Kontroller betydningen
>
> For hver sammenslåing eller fjerning skal du vurdere:
>
> 1. Er den opprinnelige betydningen fullstendig bevart?
> 2. Kan formuleringen misforstås?
> 3. Er avgrensningen fortsatt tydelig for en leser som bare har Product Briefen?
> 4. Samsvarer formuleringen med den ferdige PRD-en?
> 5. Er dette faktisk en forbedring, eller bare færre ord?
>
> Vær spesielt oppmerksom på at alle aktiviteter har start- og sluttdato, også éndagsaktiviteter og frister, der datoene er like.
>
> Ikke innfør nye funksjoner, krav eller antakelser.
>
> ## 4. Leveranse
>
> Presenter:
>
> - Et fullstendig forslag til revidert IN og OUT.
> - Antall ord før og etter for hver av de to delene.
> - En oversikt over hvilke punkter som er slått sammen eller fjernet, og hvorfor dette er forsvarlig.
> - Eventuelle presisjonsproblemer eller avvik fra PRD-en.
> - Estimert totalt ordantall for Product Briefen dersom forslaget tas i bruk.
> - Din vurdering av om det finnes ytterligere realistiske muligheter for forkorting.
>
> **Viktig:**
>
> Ikke rediger noen prosjektfiler, PRD eller KI-logg. Ikke gjennomfør commit eller push.
>
> Ikke gjennomfør generell omskriving av de andre seksjonene.
>
> Stopp etter å ha presentert forslaget, slik at vi kan vurdere og godkjenne det før implementering.

</details>

<details>
<summary><strong>Prompt 6 – Implementering og formatering</strong></summary>

> Vi godkjenner det siste forkortingsforslaget på 967 ord, inkludert den reviderte IN- og OUT-listen.
>
> Gjennomfør følgende:
>
> **1. Oppdater Product Brief**
>
> - Ta utgangspunkt i det reviderte utkastet på 980 ord.
> - Implementer det siste godkjente IN/OUT-forslaget slik at dokumentet blir omtrent 967 ord.
> - Behold alle ni seksjoner, de fem MVP-kapabilitetene og de sju tidligere godkjente presiseringene.
> - Ikke endre produktets funksjonalitet, scope eller betydningen av kravene.
> - Kontroller at resultatet fortsatt samsvarer med PRD.
>
> **2. Vurder formatering og sidelengde**
>
> Når teksten er oppdatert, undersøk hvordan Product Briefen kan presenteres på omtrent 2,5 A4-sider.
>
> Bruk følgende prinsipper:
> - A4-format og normale, profesjonelle marger.
> - Lesbar skriftstørrelse, helst 11 punkt.
> - Kompakt, men ryddig avstand mellom overskrifter og avsnitt.
> - Tydelig visuell forskjell mellom hovedseksjoner og underpunkter.
> - IN- og OUT-listene skal fortsatt være lette å lese.
> - Ikke press teksten sammen med svært liten skrift eller unaturlig liten linjeavstand.
>
> Undersøk om sideantallet først og fremst påvirkes av Markdown-rendering, overskriftsavstander, listeavstander eller marger.
>
> Dersom det er praktisk mulig, lag en midlertidig A4-forhåndsvisning utenfor repoet, slik at sidetallet kan måles i stedet for bare å estimeres.
>
> Ikke opprett nye permanente filer i repoet.
>
> **3. Rapporter resultatet**
>
> Vis:
> - Endelig ordtelling.
> - `git diff` for Product Brief.
> - Resultatet av konsistenskontrollen mot PRD.
> - Faktisk sidetall dersom dokumentet er rendret, ellers et tydelig estimat.
> - Anbefalte formateringsinnstillinger.
> - Om omtrent 2,5 sider er realistisk uten å redusere lesbarheten.
>
> Ikke gjennomfør ytterligere tekstforkorting uten godkjenning.
>
> **4. Avgrensninger**
>
> - Ikke endre PRD.
> - Ikke endre eller fullfør KI-loggen ennå.
> - La det eksisterende KI-loggutkastet i `docs/ki-logg/` være urørt.
> - Ikke gjennomfør commit eller push.
>
> Stopp etter kontrollen og vent på min godkjenning.

</details>

<details>
<summary><strong>Prompt 7 – Kontroll av PDF-forhåndsvisning</strong></summary>

> Jeg godkjenner den oppdaterte Product Briefen på 967 ord.
>
> Den redaksjonelle forkortingen er ferdig, og ingen ytterligere tekstendringer skal gjennomføres.
>
> Før commit ønsker jeg at du:
>
> 1. Kontrollerer PDF-forhåndsvisningen side for side, særlig overskrifter, IN-/OUT-lister og sideskift.
> 2. Bekrefter at den anbefalte formateringen gir et lesbart og profesjonelt resultat.
> 3. Beholder Product Briefen og PRD-en uendret.
> 4. Kontrollerer at `git diff --check` fortsatt er uten feil.
> 5. Viser `git status -sb`.
>
> Ikke gjennomfør commit eller push ennå.
>
> Vi skal deretter ferdigstille KI-loggen for valideringen og forkortingen, før vi committer dokumentasjonen.

</details>

<details>
<summary><strong>Prompt 8 – Ferdigstilling av KI-logg</strong></summary>

> Vi har nå godkjent den endelige Product Briefen på 967 ord, inkludert den redaksjonelle forkortingen og kontrollen av A4-formatering.
>
> Vi skal ferdigstille KI-loggen før commit og push.
>
> **1. Oppdater eksisterende KI-logg**
>
> Fil:
> `docs/ki-logg/2026-11-01-product-brief-validering.md`
>
> Fyll inn:
> - Deltakere: Risøy
> - Kontrollert av: Risøy
>
> Behold eksisterende loggstruktur og følg instruksjonene i `CLAUDE.md`, `AGENTS.md` og KI-loggens README.
>
> **2. Dokumenter hele arbeidsprosessen**
>
> Loggen skal dekke:
>
> - Uavhengig validering med Mary, Business Analyst.
> - De fem kvalitetskontrollene fra BMAD.
> - Kritisk vurdering av Marys funn, inkludert hvilke forslag som ble godkjent og avvist.
> - De sju godkjente presiseringene.
> - Konsistenskontroll mot PRD.
> - Commit `0d4517e`, som inneholder presiseringene.
> - Redaksjonell forkorting fra 1 146 til 967 ord (15,6 %).
> - Hvordan IN og OUT ble komprimert uten å endre MVP.
> - Testing av ulike A4-formateringer og kontroll av lesbarhet og sideskift.
> - Endelig resultat: omtrent 2,5 sider med anbefalt formatering.
>
> **3. Dokumenter KI-bruken**
>
> Ta med de faktiske promptene fra begge arbeidsøktene, i tråd med eksisterende KI-loggmal.
>
> Ikke finn på manglende prompter eller rekonstruer dem som ordrette hvis de ikke er tilgjengelige.
>
> Hvis du ikke har tilgang til alle tidligere prompts, oppgi dette tydelig og bevar det som faktisk finnes.
>
> Beskriv hvordan gruppemedlemmet vurderte og korrigerte KI-forslag fremfor å akseptere dem ukritisk.
>
> **4. Dokumenter videreføringspunkter**
>
> - UX: Vurdere om frister skal ha egen kategori.
> - Testplan: Frister som éndagsaktiviteter med lik start- og sluttdato.
> - Testplan: Bruker skal kunne finne tidspunkt og ansvarsområde uten å åpne andre filer.
> - Testplan: Risikoer knyttet til fiktive dokumenter, datotolkning og feilaktig brukergodkjenning.
>
> **5. Sluttkontroll**
>
> - Kontroller at KI-loggen er fullstendig og faktuelt korrekt.
> - Kontroller at Product Briefen fortsatt inneholder 967 ord.
> - Kontroller at PRD-en er urørt.
> - Kjør `git diff --check`.
> - Vis `git status -sb`.
> - Vis hvilke filer som skal inngå i commit.
>
> Ikke gjør flere endringer i Product Brief eller PRD.
>
> **Ikke gjennomfør commit eller push ennå.**
>
> Presenter den ferdige KI-loggen for min godkjenning, og stopp der.

</details>

## Hva KI leverte

**Første økt**

- **Validering (prompt 1):** En vurdering av de fem kontrollene, gitt bare i
  samtalen, uten egen rapportfil. Konklusjonen var at mindre endringer ble
  anbefalt. Funnene var tre nødvendige (frister, kilde til problemforståelsen,
  ikke operativ bruk), seks anbefalte og fem valgfrie. Den fullstendige
  vurderingen er ikke bevart, så denne oppsummeringen bygger på utkastet fra
  første økt.
- **Oppdatering (prompt 2):** De sju godkjente tekstendringene i
  `_bmad-output/planning-artifacts/product-brief.md`.
- **Konsistenskontroll:** En gjennomgang av de berørte delene av PRD-en.
- **Logg:** Utkast til denne loggen.

**Andre økt**

- **Forkortingsforslag (prompt 3):** Et utkast på 928 ord med ordtelling,
  sideestimat, oversikt over kutt, risiko for presisjonstap og kontroll mot
  PRD-en. KI påpekte at sidemålet på 2,5 sider ikke ble nådd.
- **Revidert utkast (prompt 4):** 980 ord etter Risøys korrigeringer.
- **Nytt IN og OUT (prompt 5):** Et forslag som ga 967 ord totalt. KI vurderte
  gevinsten som liten og anbefalte å avslutte forkortingen og heller justere
  formateringen.
- **Implementering og formatering (prompt 6):** Godkjent tekst i
  `_bmad-output/planning-artifacts/product-brief.md`, målte A4-forhåndsvisninger
  utenfor repoet, anbefalte formateringsinnstillinger og kontroll mot PRD-en.
- **Sidekontroll (prompt 7):** Gjennomgang av PDF-forhåndsvisningen side for side.
- **Logg (prompt 8):** Oppdatering av denne loggen.

## Hva vi endret og hvorfor

### Validering og presisering

Endringene bygger på valideringen og Risøys påfølgende beslutninger. Risøy
vurderte alle funnene og fastsatte den endelige ordlyden i tekstendringene. Flere
av formuleringene bygger på forslag fra valideringen. De sju endringene ble
committet i `0d4517e` (`docs: valider og presiser product brief`).

**Godkjent og lagt inn:**

1. **§2 The Problem:** Problemforståelsen er knyttet til gruppemedlemmenes
   erfaring som troppssjefer. Opplysningen om erfaringen er oppgitt av Risøy i
   prompt 2.
2. **§4 What Makes This Different:** Påstanden om at alternativene ofte krever
   manuell overføring er erstattet med en beskrivelse av den observerte
   arbeidsprosessen. Slik unngår briefen udokumenterte påstander om
   konkurrentenes funksjonalitet. Hele setningen ble byttet ut, også leddet
   «Disse dekker ulike planleggingsbehov».
3. **§6 User outcome:** Nytt kriterium om å finne når en aktivitet skjer og hvem
   som har ansvaret, uten å åpne andre filer.
4. **§6 Business / mission:** Ny betingelse for når løsningen regnes som mer
   effektiv.
5. **§7 IN 2:** Frister registreres som aktiviteter. Dette er ingen egen
   fristfunksjon.
6. **§7 IN 5:** Forslagene kan kontrolleres mot tilgjengelige kildeutdrag. Dette
   presiserer eksisterende brukerkontroll.
7. **§7 OUT:** Operativ bruk med ekte dokumenter er utenfor første versjon.

**Avvist av Risøy**, for å unngå unødvendig scope-utvidelse og detaljering:

- Egen seksjon for risikoer og antakelser.
- Krav eller avgrensning om Excel-import, eksport og utskrift.
- Endring av demo-modus i §8.
- Endring av produktvisjonen og produktnavnet.
- Nye prosentmål og detaljerte NFR-er.
- Øvrige forslag fra valideringen.

**Avvik og merknader:**

- Prompt 1 oppga `docs/product-brief.md`, som ikke finnes. Valideringen brukte
  `_bmad-output/planning-artifacts/product-brief.md`, som `AGENTS.md` peker til.
- Konsistenskontrollen fant ingen motstrid mot PRD-en. Den fant tre forhold som
  ikke krever endring nå:
  - En frist med bare én dato kan få sluttdato markert som manglende etter
    UJ-1 E6, med mindre dokumentet tydelig beskriver en éndagsaktivitet. Brukeren
    fyller da inn datoen.
  - SM-1 nevner ikke oppgaven fra det nye User outcome-kriteriet eksplisitt.
    Oppgaven kan tas inn i testplanen (OQ-9, OQ-10).
  - PRD §4.5 og §8.2 omtaler kildeutdrag som tillegg og endring fra briefen,
    mens briefen nå nevner kildeutdrag. PRD-en er ikke endret.

### Redaksjonell forkorting

Briefen ble forkortet fra 1 146 til 967 ord, en reduksjon på 15,6 %. Tellingene er
gjort med `wc -w`, inkludert overskrifter og listetegn. Alle ni seksjoner, de fem
MVP-kapabilitetene og de sju presiseringene er beholdt.

| Trinn | Hele briefen | IN | OUT |
|---|---|---|---|
| Committet (`0d4517e`) | 1 146 | 170 | 115 |
| KI-forslag etter prompt 3 | 928 | – | – |
| Etter Risøys korrigeringer (prompt 4) | 980 | 145 | 110 |
| Godkjent etter prompt 5 | 967 | 144 | 98 |

**Slik vurderte og korrigerte Risøy KI-forslagene:**

- **Presisjon foran ordmål:** Risøy godtok ikke utkastet på 928 ord som det var,
  men ba om seks korrigeringer (prompt 4). Teksten ble da 52 ord lengre, og Risøy
  beholdt presisjonen. Flere av punktene var risikoer KI hadde pekt på, mens Risøy
  avgjorde at de skulle rettes:
  - Tidsbruken i Excel-sammenligningen ble gjort eksplisitt.
  - «De samme feltene» ble erstattet med feltene selv.
  - «KI-basert» ble avgrenset, slik at prediksjon, konfliktanalyse, optimalisering
    og beslutningsstøtte er utelatt uavhengig av teknologi.
  - «Skal» ble brukt i sikkerhetskravene og kravene til demo-modus.
- **Lesbarhet og entydighet:** Risøy ba om kortere setninger i §2 og en kontroll av
  at kjerneflyten i §3 er entydig. §3 sier nå at bare godkjente forslag lagres som
  aktiviteter.
- **Scope:** Risøy ba KI vurdere hvert OUT-punkt kritisk og teste hver endring mot
  fem spørsmål, blant annet om den faktisk var en forbedring (prompt 5).
- **Formatering:** KI hadde estimert sidetallet. Risøy ba om en måling på A4 og satte
  krav til lesbarhet (prompt 6), og kontrollen side for side kom i prompt 7.

**Utover listen i prompt 4:** KI satte også tilbake «skal» i §6 og IN 2, 4 og 5,
pluss originalens betydning i to OUT-punkter. Dette ble vist tydelig i forslaget,
og Risøy godkjente senere teksten.

**Slik ble IN og OUT komprimert uten å endre MVP:**

- **OUT gikk fra 10 til 8 punkter:** Konsentriske ringer, ukevisning og omfattende
  tilpasning ble samlet i ett punkt. Ingen avgrensninger ble fjernet.
- **Uke- og dagsvisning:** «Egne uke- og dagsvisninger» skiller dem fra
  ukeinndelingen i månedsvisningen. Dagsvisning står ikke i committet OUT, men
  følger av §9 og PRD §7, så scope er uendret.
- **Beholdt selv om de delvis følger av IN:** OCR, ringer, ukevisning og tilpasning,
  fordi PRD-en viser til dem som «fra Product Brief, OUT». Automatiske endringer
  ble også beholdt, fordi IN 5 bare dekker at aktiviteter legges inn.
- **To KI-punkter:** Beholdt atskilt, slik at det er klart hva «KI-basert» gjelder.
- **IN:** Bare små kutt. Hver aktivitet skal fortsatt ha sluttdato, og det står
  uttrykkelig i IN 2. KI testet «feltene i punkt 2» i IN 4, men forkastet det fordi
  det sparte bare 2 ord og gjorde punktet avhengig av IN 2.

**Avvik og merknader:**

- Ordmålet på 800–900 ble ikke nådd. Risøy godkjente 967 ord.
- Omtrent 2,5 sider nås gjennom formatering, ikke tekstkutt alene. I den anbefalte
  profilen utgjør forkortingen ca. 0,3 side.
- Formateringen ligger ikke i repoet. `product-brief.md` er ren Markdown, så andre
  visninger, for eksempel på GitHub, kan gi et annet sidetall.
- Konsistenskontrollen fant ingen motstrid mot PRD-en og ingen endring av MVP.
  Merknadene fra første økt om SM-1 og kildeutdrag i PRD §4.5 og §8.2 gjelder
  fortsatt. PRD-en er ikke endret.
- PRD-ens `.memlog.md` ble ikke lest i andre økt.

### Videreføringspunkter

- **UX:** Vurdere om frister skal ha egen kategori.
- **Testplan:** Frister og datoer, der lagrede aktiviteter og KI-tolkning holdes
  atskilt:
  - **Lagrede aktiviteter:** Alle lagrede aktiviteter har start- og sluttdato.
    Datoene er like for éndagsaktiviteter og frister. For frister er dette Risøys
    presisering. PRD-en sier det ikke uttrykkelig.
  - **KI-tolkning:** Angir et dokument bare én dato, skal KI ikke automatisk anta
    at aktiviteten varer én dag uten tilstrekkelig grunnlag (UJ-1 E6). Manglende
    eller usikker informasjon håndteres gjennom brukerkontrollen.
- **Testplan:** Bruker skal kunne finne tidspunkt og ansvarsområde uten å åpne
  andre filer.
- **Testplan:** Risikoer knyttet til fiktive dokumenter, datotolkning og feilaktig
  brukergodkjenning.

## Testing

Ingen kode ble skrevet, så ingen programtester ble kjørt. Brukertest og
Excel-sammenligning er ikke gjennomført, fordi applikasjonen ikke er bygget.

**Første økt, dokumentkontroller:**

- `git status -sb` før endringene: arbeidskopien var ren.
- `git diff --word-diff`: bare de sju godkjente tekstendringene i briefen.
- `git diff --numstat`: 7 linjer lagt til og 6 fjernet, bare i briefen.
- `git diff --check`: ingen whitespace-feil.
- `git ls-files --eol`: linjeskift er LF.
- `git diff --stat` for PRD-mappen: ingen endringer.
- Manuell gjennomlesing av PRD-ens relevante deler mot de sju endringene.

**Andre økt, dokumentkontroller:**

- `wc -w`: briefen har 967 ord.
- Strengsøk: alle sju presiseringene står ordrett i briefen.
- `git diff --numstat`: 29 linjer lagt til og 33 fjernet i briefen.
- `git diff --check`: ingen whitespace-feil.
- `git ls-files --eol`: linjeskift er LF.
- `git diff --quiet` for PRD-mappen: ingen endringer.
- Manuell gjennomlesing av hele PRD-en mot forslagene. Henvisningene i PRD-en til
  briefens seksjoner, IN 3–4 og OUT er fortsatt gyldige.

**Andre økt, A4-formatering:**

20 profiler ble rendret som A4-PDF med Microsoft Edge i headless-modus, utenfor
repoet. Fyllgraden er innholdshøyden delt på høyden til én A4-side.

| Profil (A = luftig utgangspunkt satt opp av KI) | Sider for 967 ord |
|---|---|
| A: Arial 12 pt, linjeavstand 1,5, marger 25,4 mm, store overskrifter | 3,75 |
| A med linjeavstand 1,15 | 3,13 |
| A med 11 pt | 3,36 |
| A med kompakte overskrifter | 3,43 |
| A med marger 20 mm | 3,50 |
| A med kompakt avstand i avsnitt og lister | 3,57 |
| A med Calibri | 3,60 |
| **Anbefalt:** Calibri 11 pt, linjeavstand 1,3, marger 25 mm, kompakt avstand | **2,47** |

Linjeavstand og skriftstørrelse påvirket sidetallet mest, deretter overskrifter og
marger. Avstand i avsnitt og lister påvirket det minst.

**Anbefalte innstillinger:** A4, 25 mm marger, Calibri 11 pt, CSS-linjeavstand 1,3,
tittel 16 pt, seksjonsoverskrifter 13 pt med 12 pt over og 4 pt under,
underoverskrifter 11,5 pt, 6 pt etter avsnitt, 3 pt mellom listepunkter og 18 pt
innrykk.

**Andre økt, kontroll av lesbarhet og sideskift:**

PDF-en med anbefalt formatering ble gjort om til sidebilder og kontrollert side for
side.

- **Resultat:** 3 fysiske sider, der tredje side er omtrent halvfull, altså omtrent
  2,5 sider.
- **Lesbarhet:** Overskriftshierarki, marger og lister er ryddige, og æ, ø, å,
  tankestrek og punkttegn vises riktig.
- **Sideskift:** Ingen overskrift står alene nederst på en side. §5 deles over
  side 1–2, og OUT deles mellom punkter over side 2–3. Dette ble vurdert som
  akseptabelt.

**Ikke testet:** Word og andre renderere. Word beregner linjeavstand annerledes, så
sidetall og sideskift kan avvike. Formateringen som ga «rett under fire sider», var
ikke kjent og ble ikke gjenskapt nøyaktig.
