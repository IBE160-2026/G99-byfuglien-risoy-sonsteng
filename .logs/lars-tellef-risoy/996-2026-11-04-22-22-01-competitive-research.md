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
