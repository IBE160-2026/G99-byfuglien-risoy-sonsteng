# Tilbakemelding på PRD

| | |
|---|---|
| **Gruppe** | G99 – G99-byfuglien-risoy-sonsteng |
| **PRD vurdert** | `_bmad-output/planning-artifacts/prds/prd-G99-byfuglien-risoy-sonsteng-2026-10-19/prd.md` (status `final`, sist endret 2026-11-05, commit 9bea0ea) |
| **Dato** | 2026-11-12 |
| **Type** | Formativ tilbakemelding, ikke karakter |

## 1. Samlet inntrykk

Dette er en sterk PRD med egen tese: KI foreslår, brukeren kontrollerer mot kildeutdrag og godkjenner, og ingenting havner i planen uten eksplisitt fullføring. Kravene er konkrete nok til å bli testtilfeller, og KI-delen er behandlet ærlig. Risikoen er størrelse og mangel på prioritering. PRD-en har 30 FR-er, ca. 9 400 ord og en detaljrikdom som kan bli tung å bygge og teste for en gruppe på tre. Kategorilisten, som mange krav hviler på, er heller ikke bestemt ennå.

## 2. Dette fungerer godt

- **KI-kontroll og testing er tenkt gjennom.** FR-17 skiller mellom det applikasjonen gjør deterministisk («testes reproduserbart med kontrollerte svar») og det språkmodellen bare kan instrueres til («evalueres mot fasit i SM-3, ikke som bestått eller ikke bestått»). Sammen med demo-modus (FR-18), egenverifisering av kildeutdrag (FR-28) og NFR-9 om ubetrodd innhold er dette det emnet ber om.
- **Testbare konsekvenser med faktiske tall.** FR-10 oppgir ISO-ukenummer som kan sjekkes direkte (29.12.2025 = uke 1, 31.12.2026 = uke 53), og FR-13 har et akseptansescenario med 20 aktiviteter i én måned. Jeg har kontrollert ukenumrene, og de stemmer.
- **Ærlig avgrensning.** §7 skiller «utenfor v1, men del av visjonen» fra «ikke planlagt». C-1 til C-8 følger opp briefen-tilbakemeldingen (fiktive data, nøkler utenfor Git, lokal kjøring), og P-1 sier åpent at problemet ikke er undersøkt med brukere.

## 3. Oversikt per dimensjon

| Dimensjon | Vurdering | Kort begrunnelse |
|---|---|---|
| Beslutningsklarhet | sterk | Valg står som beslutninger med begrunnelse (§8.2 punkt 6, «Gruppebeslutning 2026-11-01»), og de åpne spørsmålene er reelle og har eier. |
| Substans | sterk | Én persona som styrer alle valg, produktspesifikke NFR-er med «Etterprøving», ingen boilerplate. |
| Strategisk sammenheng | sterk | Tesen (kontrollert KI-uttrekk) går igjen i FR-er, SM-er og counter-metrics. |
| Testbarhet | sterk | Nesten alle FR-er har «Consequences (testable)». Svakest er SM-ene (se 4.4). |
| Scope og avgrensning | god | Non-goals er tydelige, men det mangler prioritering innenfor MVP. |
| Brukbarhet for neste fase | god | ID-ene er sammenhengende, men PRD-en er lang og har noen løse tråder (se 4.5 og kap. 5). |
| Formtilpasning | god | UJ med navngitt hovedperson passer. Formen er tyngre enn en enkeltbrukerapp trenger. |

## 4. Viktigste forbedringer

### 4.1 Ingen prioritering innenfor MVP
- **Alvorlighet:** høy
- **Hvor:** §8.1 In Scope, «Detaljerte krav står i §4–§6»
- **Problem og hvorfor det betyr noe:** Alle 30 FR-er, 10 NFR-er og 8 constraints er MVP, og SM-2 krever at alle er implementert og verifisert. Går tiden tynt, vet ingen hva som kuttes først. Epics og stories får ingen rekkefølge å bygge på.
- **Forslag:** Legg til en kort «skjæreliste» i §8.1. Eksempel: *Kjerne (må med): FR-1–FR-11, FR-15–FR-17, FR-21–FR-26, FR-18. Kan forenkles hvis tiden knapper: FR-13 (sammenfatning ved mange aktiviteter), FR-12 (gråtone-krav), FR-28 (verifisering, FR-27 viser da utdraget uten status).* Dere velger selv hva som står hvor, men rekkefølgen bør være skrevet ned.

### 4.2 Kategorilisten blokkerer, men er skjøvet til UX
- **Alvorlighet:** høy
- **Hvor:** §3 «Innholdet fastsettes i UX-workflowen», OQ-3 «Må avklares før implementering av … analyse og demo-modus»
- **Problem og hvorfor det betyr noe:** FR-1, FR-12, FR-17, FR-18 og SM-3 avhenger av listen. Den er et domenevalg og ikke et UX-valg, og fasit for testdokumentene kan ikke lages uten den. Statusen er `final` selv om dette står åpent.
- **Forslag:** Sett en foreløpig liste i PRD-en nå, f.eks. *Øvelse, Utdanning, Frist, Møte, Kontroll/inspeksjon, Vedlikehold, Annet*, og la UX bare bestemme utseendet. Avgjør samtidig om «Annet» finnes (OQ-3 spør om dette).

### 4.3 Obligatorisk ansvarsområde er en uavklart avveining
- **Alvorlighet:** medium
- **Hvor:** §3 «Obligatoriske felt», FR-2, UJ-1 steg 3 («mangler ansvarsområde (manglende)»)
- **Problem og hvorfor det betyr noe:** Ordrer nevner ofte ikke hvem som har ansvaret. Da blir mange forslag *manglende* og må fylles inn for hånd, og det kan spise opp gevinsten (dere nevner selv «Kontrollarbeid» som counter-metric). Valget er ikke begrunnet som en avveining.
- **Forslag:** Skriv det som beslutning: «Ansvarsområde er obligatorisk fordi UJ-3 skal svare på hvem som har ansvaret. Prisen er at brukeren fyller inn feltet ved forslag uten ansvarlig.» Alternativ: tillat verdien «Ikke angitt». Mål andelen i SM-3.

### 4.4 Suksessmålene har ingen terskler
- **Alvorlighet:** medium
- **Hvor:** SM-2 «Alle funksjonelle krav … er implementert», SM-3 «Det settes ingen prosentgrense», SM-4 uten mål
- **Problem og hvorfor det betyr noe:** SM-2 er i praksis «vi er ferdige». SM-3 og SM-4 sier hva som måles, men ikke hva som regnes som et godt nok resultat. Uten forventning blir resultatene vanskelige å tolke og vurdere.
- **Forslag:** Legg til hypoteser, ikke krav. Eksempel for SM-4: *«Vi forventer at planleggingsoppgaven tar kortere tid i applikasjonen enn i Excel, uten flere feil mot fasit. Er det motsatt, rapporterer vi det og analyserer hvorfor.»* Tilsvarende for SM-3: *«Vi forventer at brukeren må rette høyst ett felt i hvert forslag i et flertall av tilfellene.»*

### 4.5 Lengde og dobbeltføring
- **Alvorlighet:** medium
- **Hvor:** UJ-1 «Capabilities (blir FR-er)» og E1–E11, mot FR-15–FR-30
- **Problem og hvorfor det betyr noe:** Samme regel står i brukerreisen, i en capability-liste og i FR-en, f.eks. kategori, éndagsaktivitet og datotolkning (E6, E6a og FR-17). Det gir fare for at kopiene glir fra hverandre, og lesere må lese tre steder.
- **Forslag:** Behold én fullstendig versjon, i FR-ens Consequences. La UJ-1 vise hovedflyten og noen få edge cases, og la capability-listene være korte lenker (→ FR-nn). Det kan gjøre PRD-en rundt en tredjedel kortere uten å miste innhold.

## 5. Mekaniske funn

- **ID-er:** FR-1–30, NFR-1–10, C-1–8, SM-1–4, OQ-1–10 og P-1–5 er sammenhengende, og krysshenvisningene jeg sjekket løser seg. (lav)
- **§11.2 henviser til A1–A33** (A4, A9, A20 osv.), som ikke står noe sted i PRD-en. De finnes bare i `.memlog.md`. En leser av PRD-en kan ikke følge dem. Fjern listen eller flytt den dit. (lav)
- **OQ-1** er «Avklart» og står likevel under åpne spørsmål. Fjern den eller flytt den til beslutninger. (lav)
- **UJ-1 steg 1** sier «.docx-format», men FR-15 og Glossary tillater også tekstbasert PDF. (lav)
- **Ingen personopplysninger eller hemmeligheter** funnet.

## 6. Før dere går videre

**Må avklares før UX, arkitektur og epics:**
- Kategorilisten (4.2).
- Rekkefølge og skjæreliste (4.1).
- Om ansvarsområde er obligatorisk (4.3).

**Kan vente:**
- Produktnavn (OQ-2).
- Valg av språkmodell, lagringsløsning, tidsgrenser (OQ-6–OQ-8, i arkitekturen).
- Testmengder (OQ-9, OQ-10, i testplanen).

**Oppfølging av briefen-tilbakemeldingen: ja.** Kjerneflyten er beskrevet konkret (UJ-1), suksesskriteriene er gjort om til testbare krav, og C-1/C-4 dekker fiktive data og nøkler. Valgene om én bruker og demo-modus er også fulgt opp. Skisser av skjermbilder gjenstår, og de hører hjemme i UX-arbeidet.

## 7. Refleksjonsspørsmål

1. Reglene for ufullstendige datoer (E6a, FR-17) er detaljerte. Hvilke av dem kom fra KI-forslag, og hvilke bestemte dere selv ut fra hvordan ordrer faktisk ser ut? Hvordan sjekket dere at reglene er fornuftige?
2. Dere endret i november fra umiddelbar lagring til samlet lagring ved fullføring (§8.2 punkt 6). Hvordan sikret dere at endringen ble gjennomført konsekvent i alle 30 FR-ene og tre brukerreiser, og hva sa KI-en om valget?

_Vurdert mot kvalitetsrubrikken i bmad-prd. Dette er veiledning, ikke sensur._
