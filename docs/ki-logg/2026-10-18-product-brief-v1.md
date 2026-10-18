# 2026-10-18 — Product Brief v1.0

- **Deltakere:** Risøy, Byfuglien, Sønsteng
- **KI-verktøy:** Claude Code med modellen Claude Opus 5.5 (`claude-opus-5-5`)
- **Kontrollert av:** Risøy

## Oppgave

Ferdigstille Product Brief for den reviderte prosjektideen «KI-assistert
interaktivt årshjul» (`_bmad-output/planning-artifacts/product-brief.md`) som
v1.0, slik at PRD, arkitektur og stories kan bygges på den.

Økten hadde fire deler:

1. Rette Markdown-formateringen i den reviderte briefen uten å endre faglig
   innhold.
2. Vurdere briefen punkt for punkt mot faglærers tilbakemelding
   (`_bmad-output/planning-artifacts/tilbakemelding-product-brief.md`, commit
   `4969122`). Tilbakemeldingen gjaldt den forrige versjonen av briefen
   (commit `fbcdb19`).
3. Legge inn de tekstendringene gruppen godkjente etter vurderingen.
4. Committe og publisere v1.0 med faglærers tilbakemelding bevart i
   historikken.

Selve innholdsrevisjonen fra «Sambandet» til «KI-assistert interaktivt
årshjul» lå allerede som ucommittet endring i arbeidskopien da
formateringsoppgaven startet. Den ble ikke skrevet av Claude i denne økten.

## Prompt (ordrett)

Promptene er gjengitt ordrett og i rekkefølge, slik de ble skrevet i økten.

### Prompt 1

> Finn den eksisterende Product Brief-filen i prosjektet og vis meg den fullstendige filstien.
>
> Ikke gjør noen endringer ennå.

### Prompt 2

> Oppgave:
> 1. Les hele dokumentet.
> 2. Rett Markdown-overskrifter til korrekt H1-, H2- og H3-hierarki.
> 3. Nummerer Vision som seksjon 8.
> 4. Rett listeformateringen under Scope, inkludert punktet om ukevisning.
> 5. Fjern unødvendige mellomrom og tomme linjer.
> 6. Behold alle formuleringer, krav, avgrensninger og suksesskriterier uendret.
>
> Etterpå:
> - Vis git diff for product-brief.md.
> - Kontroller at ingen andre filer er endret av deg.
> - Vis git status -sb.
> - Oppsummer kort hvilke formateringsendringer du har gjort.
>
> Ikke gjennomfør commit eller push. Vent på min godkjenning.

### Prompt 3

> Gjør en siste kontroll av _bmad-output/planning-artifacts/product-brief.md.
>
> 1. Kontroller at "The Problem" er en H3-underseksjon under "1. Executive Summary".
> 2. Kontroller at User outcome, Behavior, Quality og Business / mission er fire separate avsnitt med fet kategorioverskrift.
> 3. Rett eventuelle Markdown-formateringsfeil uten å endre faglig innhold.
> 4. Kontroller at hvert hovedpunkt i IN- og OUT-scope forekommer nøyaktig én gang i den ferdige filen.
> 5. Vis de relevante delene av dokumentet og git status -sb.
>
> Ikke gjennomfør commit eller push ennå.

### Prompt 4

> Vi skal nå ferdigstille Product Brief v1.0.
>
> 1. Legg til manglende punktum i de to OUT-scope-punktene om flerbrukerfunksjonalitet og ukevisning.
> 2. Kontroller at bare _bmad-output/planning-artifacts/product-brief.md er endret.
> 3. Kontroller at dokumentet inneholder den reviderte prosjektideen "KI-assistert interaktivt årshjul", med 5 IN-scope-punkter og 9 OUT-scope-punkter.
> 4. Vis en kort oppsummering av endringene sammenlignet med forrige commit.
> 5. Commit kun product-brief.md med meldingen:
>    "Finalize Product Brief v1.0 – AI-assisted annual wheel"
> 6. Push til origin/main.
> 7. Vis resultatet fra push og git status -sb etterpå.
>
> Ikke inkluder andre filer i committen.

### Prompt 5

> Jeg velger alternativ 2.
>
> Les tilbakemeldingsfilen som ligger i den nye commiten på origin/main.
>
> Sammenlign tilbakemeldingene med vår nåværende Product Brief v1.0 og vurder punkt for punkt:
> 1. Hva tilbakemeldingen innebærer.
> 2. Om den allerede er ivaretatt.
> 3. Om det er behov for ytterligere endringer.
>
> Ikke endre filer, gjennomfør rebase, merge eller push ennå. Vis vurderingen først.

### Prompt 6

> Vi har vurdert anbefalingene dine og besluttet følgende:
>
> 1. The Solution: Foreslå en nummerert kjerneflyt med fem steg og et kort, konkret eksempel med en fiktiv øvingsordre. Behold manuell aktivitetshåndtering.
>
> 2. Who This Serves: Legg til én kort setning som beskriver troppssjefens typiske arbeid med ordre, ukeplaner og møter.
>
> 3. Rett skrivefeilen «troppsjefer» til «troppssjefer».
>
> 4. Behold Quality under Success Criteria uendret. Konkrete måltall og akseptansekriterier fastsettes senere i PRD og testplanen.
>
> Ikke endre andre seksjoner eller utvid MVP-scope.
>
> Vis meg de konkrete tekstforslagene før du endrer filen.
>
> Ikke gjennomfør commit, rebase, merge eller push ennå.

### Prompt 7

> Jeg godkjenner tekstforslagene med følgende justeringer:
>
> 1. The Solution:
> - Bruk den foreslåtte nummererte kjerneflyten med fem steg.
> - Behold det fiktive eksempelet «Øvelse Testfjell».
> - Ikke oppgi et bestemt antall KI-genererte aktiviteter i eksempelet.
> - Behold muligheten for manuell aktivitetshåndtering.
>
> 2. Who This Serves:
> - Legg inn den foreslåtte setningen om troppssjefens typiske arbeidsuke.
> - Unngå at planleggingsmøter omtales unødvendig to ganger.
>
> 3. Rett skrivefeilen «troppsjefer» til «troppssjefer».
>
> 4. Behold Quality under Success Criteria uendret.
>
> Gjennomfør kun disse endringene i:
> _bmad-output/planning-artifacts/product-brief.md
>
> Kontroller at Scope og øvrig faglig innhold er uendret.
>
> Vis git diff og git status -sb etterpå.
>
> Ikke gjennomfør commit, rebase, merge eller push ennå.

### Prompt 8

> Product Brief v1.0 er nå godkjent.
>
> Gjennomfør følgende i denne rekkefølgen:
>
> 1. Kontroller at bare _bmad-output/planning-artifacts/product-brief.md har ucommittede endringer.
> 2. Legg kun denne filen til staging.
> 3. Bruk git commit --amend for å inkludere de siste endringene i den eksisterende lokale Product Brief-commiten. Behold commit-meldingen:
> "Finalize Product Brief v1.0 – AI-assisted annual wheel"
> 4. Hent siste endringer fra origin og gjennomfør en kontrollert rebase av lokal main mot origin/main.
> 5. Kontroller at faglærers tilbakemeldingsfil er bevart, og at Product Brief inneholder de siste godkjente endringene.
> 6. Dersom rebase fullføres uten konflikter, push til origin/main.
> 7. Vis:
> - Ny commit-ID
> - Resultatet fra push
> - git status -sb
> - Hvilke filer den nye Product Brief-commiten inneholder
>
> Ikke bruk force push. Ved konflikt eller uventede endringer skal du stoppe og forklare situasjonen før du fortsetter.

### Prompt 9

Prompten under ble brukt for å lage denne loggoppføringen.

> Vi skal nå dokumentere arbeidsøkten der vi ferdigstilte Product Brief v1.0.
>
> Les først docs/ki-logg/README.md og følg den eksisterende malen.
>
> Oppgave:
> 1. Opprett KI-loggen:
>    docs/ki-logg/2026-10-18-product-brief-v1.md
>
> 2. Dokumenter:
>    - Oppgaven og formålet med arbeidsøkten.
>    - Hvilket KI-verktøy som ble benyttet.
>    - Promptene som faktisk ble brukt.
>    - Hva Claude leverte.
>    - Hvilke forslag vi godkjente, endret eller avviste, og hvorfor.
>    - Hvordan resultatet ble kontrollert.
>    - Relevant Git-historikk, inkludert commit 70b359b.
>
> 3. Gjengi promptene ordrett der fullstendig tekst er tilgjengelig i samtalehistorikken. Ikke presenter forkortede eller rekonstruerte prompts som ordrette. Dersom en prompt ikke kan gjenfinnes fullstendig, merk den tydelig som et utdrag.
>
> 4. Fremhev spesielt:
>    - Revisjonen etter faglærers tilbakemelding.
>    - At vi konkretiserte brukerflyten i fem steg.
>    - At vi la inn et fiktivt eksempel.
>    - At vi avviste å fastsette et vilkårlig kvalitetsmål før PRD og testplan.
>    - At endringene ble kvalitetssikret før commit og push.
>
> 5. Ikke finn på opplysninger om deltakere, tester eller beslutninger. Bruk plassholdere der informasjon mangler.
>
> 6. Kontroller at loggen følger malen og at opplysningene stemmer med den faktiske arbeidsøkten.
>
> Vis meg hele loggen og git status -sb.
>
> Ikke gjennomfør commit eller push ennå. Vent på min godkjenning.

## Hva KI leverte

Alle endringene gjaldt `_bmad-output/planning-artifacts/product-brief.md`.

- **Filsøk (prompt 1):** Fant briefen og skilte den fra BMAD-malen og et
  referansedokument som også har «brief» i filnavnet.
- **Formatering (prompt 2 og 3):**
  - Seksjonene ble nummerert H2-overskrifter, og Vision ble «8. Vision».
  - «The Problem» ble H3 under «1. Executive Summary».
  - Under Scope ble IN og OUT H3-overskrifter. IN fikk en nummerert liste, og
    OUT fikk `-`-lister. Ukevisning-punktet fikk punkttegn.
  - Tab-innrykkede `•`-punkter under Scope og Security & Testing ble
    `-`-lister. Endringen i Security & Testing gikk ut over prompt 2, og Claude
    sa ifra om det.
  - Kategoriene i Success Criteria ble fire separate avsnitt med fet skrift.
  - Avsnitt som Markdown ville slått sammen, fikk tom linje mellom seg.
  - Overflødige tomme linjer, tab og mellomrom på slutten av linjer ble fjernet.
- **Punktum (prompt 4):** Lagt til i OUT-punktene om flerbrukerfunksjonalitet
  og ukevisning.
- **Vurdering mot tilbakemeldingen (prompt 5):** En tabell som går gjennom
  faglærers tilbakemelding punkt for punkt. Konklusjonen var at det meste var
  ivaretatt i den reviderte briefen. Det som gjensto:
  - kjerneflyt i nummererte steg og et konkret eksempel
  - en typisk uke for primærbrukeren
  - en grense for kvaliteten på KI-uttrekket
  - en skrivefeil
- **Tekstforslag (prompt 6), lagt inn etter godkjenning (prompt 7):**
  - **The Solution:** En kjerneflyt i fem steg: last opp dokument → få
    aktivitetsforslag → kontroller forslagene → legg inn i planen → få
    oversikt. I tillegg et fiktivt eksempel med en øvingsordre for «Øvelse
    Testfjell».
  - **Who This Serves:** En ny setning om troppssjefens typiske uke.
  - **Executive Summary:** «troppsjefer» rettet til «troppssjefer».
- **Git (prompt 4 og 8):** Commit, amend, fetch, rebase og push. Detaljene står
  under «Testing».

## Hva vi endret og hvorfor

**Revisjon etter faglærers tilbakemelding.** Faglærer mente den forrige briefen
var for abstrakt, at suksesskriteriene ikke kunne testes, og at bruk av
fiktive data måtte stå eksplisitt. Første push (prompt 4) ble avvist fordi
tilbakemeldingen var pushet til origin i mellomtiden. Gruppen valgte da å lese
og vurdere tilbakemeldingen før briefen ble publisert som v1.0 (prompt 5,
«alternativ 2»). Alternativet var å rebase og pushe med en gang.

**Godkjent:**

- Formateringen fra prompt 2 og 3, inkludert listene i Security & Testing.
- **Brukerflyten ble konkretisert i fem steg** under The Solution, slik
  faglærer ba om. Setningen om manuell opprettelse, redigering og sletting av
  aktiviteter ble beholdt.
- **Det fiktive eksempelet «Øvelse Testfjell»** ble lagt inn. Det viser
  kjerneflyten med en oppdiktet øvingsordre og bruker bare funksjoner som
  allerede er IN-scope.
- Rettelsen «troppsjefer» → «troppssjefer».

**Endret av gruppen:**

- Eksempelet skulle ikke oppgi et bestemt antall KI-genererte aktiviteter.
  Claude hadde foreslått «tre aktiviteter», og det ble endret til «aktiviteter
  basert på ordren».
- Setningen om typisk uke skulle ikke nevne planleggingsmøter to ganger, så den
  korte varianten ble brukt: «I en typisk uke mottar troppssjefen ordre fra
  overordnet ledd og omsetter dem til ukeplaner for troppen.»

**Avvist:**

- Claude anbefalte en konkret grense for kvaliteten på KI-uttrekket under
  Quality. **Gruppen avviste å fastsette et kvalitetsmål nå**, fordi måltall og
  akseptansekriterier skal fastsettes i PRD og testplan. Quality ble stående
  uendret.
- Andre seksjoner ble ikke endret, og MVP-scope ble ikke utvidet.

**Fremgangsmåte:** Tekstforslagene ble vist før filen ble endret, og hvert steg
ventet på godkjenning før commit, rebase og push.

## Testing

Ingen automatiske tester ble kjørt, for økten endret bare dokumentasjon.
Endringene ble kvalitetssikret med disse kontrollene før commit og push:

- **Uendret tekst etter formatering:** Teksten ble sammenlignet linje for linje
  før og etter, med Markdown-tegn og tomme linjer fjernet. Bare overskriftsnivå,
  fet skrift og tomme linjer var endret.
- **Formatsjekk:** Ingen tab, mellomrom på slutten av linjer eller doble tomme
  linjer. Overskriftshierarkiet ble listet og gått gjennom.
- **Scope:** Hvert av de 14 hovedpunktene forekom nøyaktig én gang. Det var 5
  under IN og 9 under OUT.
- **Godkjente tekstendringer:** Seksjonene The Problem, 3, 5 (inkludert
  Quality), 6, 7 og 8 ble sammenlignet med en kopi fra før endringen og var
  uendret.
- **Før commit:** `git status --porcelain` viste at bare `product-brief.md` var
  endret, og bare den filen ble staget.
- **Etter rebase:**
  - Tilbakemeldingsfilen var bevart og identisk med versjonen i `4969122`.
  - Product Brief i commiten var identisk med den godkjente versjonen.
- **Push:** Uten force. Etter push var `git status -sb` lik
  `## main...origin/main`.

**Git-historikk fra økten:**

1. `9f31c6f` «Finalize Product Brief v1.0 – AI-assisted annual wheel» ble
   committet lokalt (prompt 4).
2. Push ble avvist med `! [rejected] main -> main (fetch first)`, fordi origin
   hadde fått `4969122` «Legg til tilbakemelding på product brief».
3. De godkjente tekstendringene ble lagt inn i den lokale committen med
   `git commit --amend --no-edit`, som ga `5f83b27`. Committen var ikke pushet.
4. `git fetch` og `git rebase origin/main` gikk uten konflikter, og den nye
   commiten fikk ID `70b359b`.
5. `git push origin main` ga `4969122..70b359b  main -> main`.

Historikken på origin/main er nå: `fbcdb19` → `4bb4dbc` → `4969122`
(faglærers tilbakemelding) → `70b359b` (Product Brief v1.0).
`70b359b` inneholder bare `_bmad-output/planning-artifacts/product-brief.md`
(57 linjer lagt til, 33 fjernet).
