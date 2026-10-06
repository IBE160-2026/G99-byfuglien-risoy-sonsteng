# Tilbakemelding på product brief

| | |
|---|---|
| **Gruppe** | G99 – G99-byfuglien-risoy-sonsteng |
| **Product brief** | `_bmad-output/planning-artifacts/product-brief.md` (commit `fbcdb19`) |
| **Tilbakemelding fra** | Faglærer i IBE160 (utarbeidet med KI-støtte) |
| **Dato** | 2026-10-06 |

## Samlet vurdering

- **Bør revideres før dere går videre.** Rett punktene markert «Endre» før dere lager PRD og arkitektur.

**Det som er bra:**

1. Problemet er reelt og kommer tydelig fra egen erfaring: ledere i Forsvaret (troppsjef, kompanisjef, seksjonssjef) som bruker tid på å lete i lokale, skrivebeskyttede Excel-ark og dokumenter i stedet for å lede og planlegge.
2. Prinsippet om at brukeren skal kontrollere, endre, godkjenne eller avvise KI-generert informasjon før den går inn i planen, er et godt og ansvarlig designvalg.
3. «OUT»-listen er fornuftig: integrasjoner, sanntidssamarbeid, KI-basert prioritering og avansert analyse er holdt utenfor første versjon.

**De viktigste endringene:**

1. Briefen er for abstrakt til at PRD og stories kan bygges på den. Det er uklart hva «planleggingsinformasjon» konkret er (aktiviteter, frister, ressurser, personell?), og hvordan visningen fra overordnet nivå til uke- og dagsnivå ser ut. Beskriv én konkret kjerneflyt i 3–5 steg og et konkret eksempel, f.eks. en troppsjef som legger inn en ordre og får aktivitetene inn i en ukeplan.
2. Suksesskriteriene kan ikke testes. «Mindre tid», «brukes som primært verktøy», «aktiv bruk i møter» og «presise nok» er forretningsmål. Skriv funksjonelle kriterier av typen «brukeren kan …» med forventet resultat.
3. Repoet er offentlig, og KI-delen sender dokumenter til en ekstern språkmodell. Ekte ordre, direktiver og instrukser fra Forsvaret må ikke brukes – heller ikke ugraderte interne dokumenter. Skriv inn i briefen at all utvikling og testing skjer med fiktive dokumenter.

## Vanskelighetsgrad og gjennomførbarhet

### Vurdert vanskelighetsgrad

- **Middels**

**Sammenlignbart med:** En kombinasjon av 6) To-do-liste med smarte etiketter (enkel) og dokumentuttrekket i 2) AI CV- og søknadsassistent (middels). Planlegging med aktiviteter og frister er CRUD, men KI-uttrekk fra dokumenter med godkjenning, flere detaljnivåer i visningen og et felles planbilde gjør det middels. Det kan bli vanskelig hvis «felles planbilde på tvers av roller og nivåer» betyr flere brukere og tilgangsstyring.

**Begrunnelse:**

| Faktor | Nivå (lav / middels / høy) | Kommentar |
|---|---|---|
| Domenelogikk – hvor mange og hvor kompliserte regler og beregninger må stemme? | Middels | Aktiviteter med tid, varighet og nivå (år, måned, uke, dag), og overgang mellom nivåer. Reglene er ikke beskrevet. |
| Datamodell – antall entiteter og relasjoner mellom dem | Middels | Plan, aktivitet, kategori, kildedokument og KI-forslag med status (foreslått, godkjent, avvist). Eventuelt enhet og rolle. |
| Brukere, roller og innlogging | Middels–høy | «Felles planbilde på tvers av roller og nivåer» tilsier flere brukere og roller, men avansert flerbrukersamarbeid er «OUT». Dette må avklares. |
| KI-funksjonalitet i appen, f.eks. kall til språkmodell, prompts i koden og håndtering av usikre svar | Middels | Uttrekk, strukturering og kategorisering av innhold fra dokumenter, med godkjenning. Avgrenset og godt plassert. |
| Integrasjoner og eksterne tjenester, f.eks. API-er, betaling og e-post | Middels | Språkmodell-API. Andre integrasjoner er riktig holdt utenfor. |
| Sanntid, samtidighet eller flere brukere som påvirker hverandre | Middels | Et delt planbilde betyr at flere kan endre samme plan. Sanntid er «OUT», men samtidige endringer må likevel håndteres hvis flere brukere er med. |
| Filhåndtering, f.eks. opplasting, PDF-lesing og eksport | Middels | Opplasting og tekstuttrekk fra ordre og direktiver (Word/PDF). |
| Sikkerhet og personvern | Høy | Militære planleggingsdata er sensitive. I et studentprosjekt med offentlig repo og ekstern språkmodell må alt være fiktivt. |

**Hva vanskelighetsgraden betyr for dere:**

- _Middels:_ Et godt balansert valg. Pass på at kjerneflyten blir ferdig og stabil før dere legger til mer. Her betyr det: registrere aktiviteter, se dem på minst to detaljnivåer, og hente aktiviteter ut av ett fiktivt dokument med godkjenning. Flere brukere og deling kan komme etterpå.

### Gjennomførbarhet med BMAD og Claude Code

Dere skal planlegge med BMAD (product brief → PRD → arkitektur → epics og stories) og implementere med Claude Code. Vurderingen under tar hensyn til at det må være tid til hele denne flyten, og til testing, retting og README til slutt.

| Spørsmål | Vurdering (OK / risiko / stor risiko) | Kommentar |
|---|---|---|
| **Tid og omfang** – kan v1 realistisk bli ferdig og stabil i løpet av semesteret, med tid til flere iterasjoner? | Risiko | Tre funksjonsområder i «IN» er overkommelig for tre personer, men omfanget er så løst beskrevet at det kan vokse ukontrollert. Ingen PRD ennå. |
| **BMAD-flyten** – er briefen konkret nok til at PRD, arkitektur og stories kan lages uten store hull, og blir det overkommelig mange stories? | Stor risiko | Uten konkrete datatyper, skjermbilder og en kjerneflyt må PRD-en finne opp produktet. Det gir svak sporbarhet fra brief til kode. |
| **Egnet for Claude Code** – bruker løsningen en vanlig, godt dokumentert teknologistakk som Claude Code håndterer godt, eller krever den nisjeteknologi, spesialmaskinvare eller mye manuell konfigurasjon? | OK | En webapp med database, kalender-/tidslinjevisning og LLM-kall er godt dokumentert. |
| **Kontroll på KI-ens arbeid** – kan gruppen selv avgjøre om koden gjør det riktige? Krever domenet kunnskap gruppen ikke har, f.eks. avanserte beregninger eller fagregler, så er det vanskelig å kvalitetssikre. | OK | Dere kjenner domenet og kan vurdere om uttrekket fra en ordre er riktig. Lag fiktive ordre med en fasit over hvilke aktiviteter som skal hentes ut. |
| **Testbarhet** – finnes det tydelige regler og forventede resultater som tester kan skrives mot? | Risiko | Når datamodellen og kjerneflyten er beskrevet, kan registrering, nivåvisning og godkjenning testes godt. I dag mangler grunnlaget. |
| **Kjørbar for sensor** – kan appen kjøres lokalt etter README, uten gruppens nøkler, betalte kontoer eller egen infrastruktur? | Risiko | Ikke omtalt. Planlegg lokal kjøring med fiktive eksempeldokumenter og demomodus for KI-uttrekket. |
| **Avhengigheter og kostnader** – krever løsningen betalte API-er, f.eks. språkmodeller, og finnes det en plan for kostnad, testmodus eller mock-data? | Risiko | Språkmodell er ikke valgt, og kostnad og testmodus er ikke nevnt. |

**Konklusjon om gjennomførbarhet:**

- **Gjennomførbart med justert omfang.** Se forslagene under.

**Forslag til justering av omfang eller vanskelighetsgrad:**

1. Definer v1 som én bruker (eller ett planleggingsteam uten roller) som registrerer aktiviteter med dato, varighet og kategori, ser dem i en års-/månedsoversikt og en uke-/dagsvisning, og laster opp ett fiktivt dokument der KI foreslår aktiviteter som brukeren godkjenner eller avviser.
2. Flytt «felles planbilde på tvers av roller og nivåer» til et senere trinn, eller definer det helt konkret (f.eks. to roller med lesetilgang og skrivetilgang).
3. Lag 3–4 fiktive ordre/direktiver med fasit som brukes både i tester og i README-demoen.

## Hvorfor product brief er viktig for mappen

Product brief er utgangspunktet for PRD, arkitektur, stories og til slutt koden. Del 1 av mappen vurderes blant annet på om sensor kan følge en sporbar vei fra plan til ferdig app. Den vurderes også på om appen gjør det dere har beskrevet, om den er testet, om den er godt designet, og om den kan kjøres etter README. Et uklart, for stort eller for lite brief gjør alt dette vanskeligere senere. Det er mye enklere å rette nå enn sent i semesteret.

## 1. Gjennomgang av briefens deler

| Del av brief | Status | Kommentar |
|---|---|---|
| Executive Summary – er det klart hva appen er, og hvilket problem den løser? | Juster | Problemet er klart, men hva appen konkret er (en kalender, en tidslinje, et årshjul, en tavle?) går ikke fram. |
| The Problem – er problemet konkret, med reelle situasjoner og brukere? | OK | Konkrete roller og situasjoner (leting etter dokumenter i møter, gjeninntasting mellom Excel-ark). |
| The Solution – beskriver løsningen brukeropplevelsen, ikke bare teknologi? | Endre | Beskriver ønsket effekt («raskere informasjonsflyt, bedre situasjonsforståelse»), ikke hva brukeren gjør og ser. Beskriv kjerneflyten og de viktigste skjermbildene. |
| What Makes This Different – er vurderingen ærlig og realistisk? | Juster | Excel og årshjul er nevnt, men ikke vanlige planleggingsverktøy (f.eks. Planner, Trello, Teams-kalender eller verktøy Forsvaret allerede bruker). Si hvorfor de ikke dekker behovet. |
| Who This Serves – er primærbrukerne tydelige, og vet vi hva de trenger? | Juster | «En leder eller et planleggingsteam» er bredt. Velg én primærbruker, f.eks. en troppsjef, og beskriv en typisk uke. |
| Success Criteria – kan kriteriene faktisk sjekkes eller testes? | Endre | Alle fire områdene er forretnings- eller atferdsmål. Legg til funksjonelle, testbare kriterier. |
| Scope – er det klart hva som er med i første versjon, og hva som ikke er det? | Juster | «OUT» er tydelig, men «IN» er så generelt formulert at det kan romme nesten hva som helst. Konkretiser datatyper, visninger og dokumentformat. |
| Vision – henger visjonen sammen med resten uten å blåse opp omfanget? | OK | Nøktern og konsistent med problemet. |

## 2. Utgangspunkt for del 1 av mappen

Punktene følger kriteriene i sensorveiledningen for del 1. Vektene i parentes viser hvor mye hvert kriterium teller i del 1.

| Kriterium i del 1 | Hva briefen bør legge til rette for | Status | Kommentar |
|---|---|---|---|
| **1. Prosess og KI-styring** (30 %) | Brief som er presis nok til at PRD og stories kan bygges direkte på den, slik at krav kan spores fra brief til kode. | Endre | Repoet har god struktur (AGENTS.md, KI-logg-mal, ryddige commits), men briefen er for abstrakt til at krav kan spores til stories. Konkretiser før PRD. |
| **2. Funksjonalitet og omfang** (20 %) | Realistisk omfang for gruppen og semesteret: en tydelig kjerneflyt som kan bli ferdig og stabil, og nok innhold til å vise reell funksjonalitet. | Juster | Tre funksjonsområder er et rimelig omfang, men kjerneflyten må beskrives. |
| **3. Kvalitetssikring og testing** (15 %) | Suksesskriterier og funksjoner som er konkrete nok til å bli testtilfeller. | Endre | Skriv funksjonelle kriterier og lag fiktive dokumenter med fasit for KI-uttrekket. |
| **4. Design og brukeropplevelse** (10 %) | Tydelige brukere og brukssituasjoner som designet kan bygges rundt, gjerne med de viktigste skjermbildene eller flytene skissert. | Juster | Visuell oversikt på flere nivåer er kjernen, men ingen skisser eller beskrivelser av visningene finnes. Lag enkle wireframes. |
| **5. Kodekvalitet og arkitektur** (10 %) | Teknologivalg som er begrunnet og ikke mer komplekse enn appen trenger. | Juster | Teknologi er ikke valgt. Hold v1 til én database og én bruker/rolle, og begrunn valgene i arkitekturen. |
| **6. README og kjørbarhet** (10 %) | Løsning som andre kan kjøre lokalt uten betalte kontoer, og uten tilgang til gruppens egne tjenester og nøkler. | Juster | Planlegg lokal kjøring med fiktive eksempeldata og demomodus for KI. |
| **7. Ryddighet i repoet** (5 %) | En plan for hvor hemmeligheter, testdata og dokumentasjon skal ligge. | Endre | Skriv eksplisitt at bare fiktive dokumenter brukes, at ingen dokumenter fra Forsvaret legges i repoet eller sendes til språkmodellen, og at nøkler ligger i `.env` utenfor Git. |

## 3. Neste steg for gruppen

1. Beskriv én konkret kjerneflyt og de viktigste skjermbildene, med et eksempel fra en tenkt troppsjefs planlegging, og konkretiser hva en «aktivitet» består av.
2. Skriv om suksesskriteriene til testbare «brukeren kan …»-krav, og avklar om v1 har én eller flere brukere.
3. Legg til en kort seksjon om datasikkerhet (kun fiktive data, ingen ekte dokumenter til språkmodellen), velg språkmodell og demomodus, og gå deretter videre til PRD.

Oppdater product brief i repoet når dere har gjort endringene, slik at historikken viser hvordan planen utviklet seg. Det er en del av prosessen sensor ser etter.
