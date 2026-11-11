# Competitive Research om produktets særpreg

## 2026-11-04 kl. 22:22 — Lars Tellef Risøy

### Oppgave
Undersøke om særpreget i Product Brief §4 og PRD §1 er tilstrekkelig underbygget mot eksisterende løsninger, uten å starte planleggingen på nytt. Resultatet skulle komprimeres til en beslutningsorientert rapport og committes sammen med KI-loggen.

### Plan
- `bmad-help` identifiserte `bmad-deep-recon` med type `competitive` (Run). Innstillingene var preset standard, validation high med kritisk motgjennomgang, og bare Markdown.
- Tre spor (årshjul, Microsoft 365, KI-uttrekk med menneskelig kontroll) i to runder. Deretter kritisk motgjennomgang av K1–K3, semantisk sitatkontroll og språkgjennomgang.
- Rapporten ble komprimert til 3–5 sider, med korte vurderinger av kostnad og tilgjengelighet og av militær tilpasning. Til slutt en kontroll før commit.
- Detaljer og prompter står i [KI-loggen](../../docs/ki-logg/2026-11-04-competitive-research.md). Beslutningshistorikken står i [`.memlog.md`](../../_bmad-output/planning-artifacts/research/competitive-aarshjul-ki-uttrekk-saerpreg-2026-11-04/.memlog.md).

### Resultat
- **Rapport:** [`research.md`](../../_bmad-output/planning-artifacts/research/competitive-aarshjul-ki-uttrekk-saerpreg-2026-11-04/research.md), ca. 2 500 ord og 32 kilder. Underlaget ligger i `digests/` (10 filer).
- **Konklusjon:** Særpreget holder bare delvis og bør snevres inn til sporbar kontroll av hvert KI-forslag mot verifiserte kildeutdrag før det legges inn i årshjulet. Plandisc og Microsoft Planner Agent er de nærmeste alternativene. Kostnad og tilgjengelighet har verdi for demonstrasjon, men er ikke et markedsfortrinn. Militær tilpasning er relevant, men et tynt særpreg alene.
- **Kontroller:** Den mekaniske sitatkontrollen er bestått. Den semantiske sitatkontrollen fant 11 avvik, som er rettet. Sluttkontrollen rettet feilnummererte kilder ([4]–[8]) og presiserte at kategori bare kan ha feltstatus manglende eller usikker. Påstandsregisteret har 10 verifiserte og 17 uverifiserte påstander.
- **Ikke endret:** Product Brief, PRD og UX. Ingen produkter er prøvd i praksis.
- **Commit:** Research-artefaktene, KI-loggen og denne sesjonsloggen ligger i én samlet commit, pushet til `origin/main`.

### Åpne punkter
- Gruppebeslutning: Skal særpreget i Product Brief §4 og PRD §1 snevres inn som anbefalt, med Plandisc og Planner Agent nevnt som alternativer? Det vil i så fall gjøres via `bmad-product-brief` eller `bmad-prd` i oppdateringsmodus.
- Testplan: Mål om kontrollen virker. Det gjelder om brukerne oppdager bevisst innlagte feil, andelen verifiserte kildeutdrag og om «usikker» treffer de faktiske feilene (jf. M14).
- Valgfritt: Prøv Plandisc AI Import og Planner Agent med et fiktivt testdokument for å verifisere de viktigste leverandørpåstandene.
- Kontroller raskt aldrende påstander på nytt. Det statlige KI-pålegget om Copilot og Microsofts retning kontrolleres i desember 2026. Funksjonspåstandene om Plandisc, Microsoft og Clio kontrolleres senest i februar 2027, og uansett før særpreget brukes i en endelig rapport.

## 2026-11-05 kl. 19:32 — Lars Tellef Risøy

### Oppgave
Presisere særpreget i Product Brief §4 og PRD §1 ut fra Competitive Research. Revisjonen skulle være minimal, uten nye krav, endret scope eller endrede funksjonskrav.

### Plan
- Claude Code foreslo ny ordlyd, vist ved siden av eksisterende tekst. Gruppen valgte en kortere ordlyd, som ble satt inn ordrett.
- Før commit ble én presisering lagt inn i PRD §1. Ordlyden ble endret fra «verifiserte kildeutdrag» til «kildeutdrag som applikasjonen verifiserer», fordi FR-27–FR-29 tillater forslag med manglende eller ikke-verifiserte kildeutdrag.
- Detaljer og prompter står i [KI-loggen](../../docs/ki-logg/2026-11-05-saerpreg-brief-prd.md).

### Resultat
- **Product Brief §4:** Plandisc og Microsoft Planner Agent er nevnt med forbehold. Særpreget er nå den samlede arbeidsflyten fra ordre til årshjul, med kildeutdrag som applikasjonen verifiserer, og godkjenning av hvert forslag.
- **PRD §1, tredje avsnitt:** har tilsvarende ordlyd. Status er fortsatt `final`, og `updated` er satt til 2026-11-05. To linjer er lagt til i PRD-ens `.memlog.md`: beslutningen og presiseringen.
- Det er ikke innført nye krav og ingen endringer i scope, UX eller arkitektur. Punktet om særpreg i `issues.md` er lukket.

### Åpne punkter
- Si fra til gruppemedlemmet som jobber med UX om den nye formuleringen av særpreget. UX-kravene er ikke endret.
