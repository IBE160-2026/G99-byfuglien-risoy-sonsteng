# PRD: validering og revisjon

## 2026-11-02 kl. 19:03 — Lars Tellef Risøy

### Oppgave
Validere den ferdigstilte PRD-en med BMAD Validate etter forkortingen av Product Brief, innarbeide gruppens beslutninger om funnene og avslutte PRD-fasen med commit og push, slik at UX Design kan starte fra et felles grunnlag. Økten startet 2026-11-01 og ble fullført 2026-11-02 etter omstart.

### Plan
- `bmad-prd` Validate med to underagenter: én for BMAD-rubrikken og én for kontroll mot brief og memlog. Deretter én samlet rapport.
- Rapportene kopieres uendret til `docs/prd-validering/2026-11-01/`.
- Gruppens beslutninger H1, H4, M1–M5, H2, H3 og deretter D1 innarbeides i PRD-en, og `.memlog.md` oppdateres.
- Kontroll før commit. Detaljer og prompter står i [KI-loggen](../../docs/ki-logg/2026-11-01-prd-validering.md).

### Resultat
- **Validering:** Karakter Fair, med 0 critical, 4 high, 23 medium og 7 low. Rapportene ligger i `docs/prd-validering/2026-11-01/`.
- **PRD:** `prd.md` er revidert etter gruppens beslutninger. Lagringen skjer nå samlet og atomisk ved «Fullfør og lagre» i stedet for umiddelbart ved hver godkjenning. Det er lagt inn regler for frister og ufullstendige datoer, og FR-13 har fått et akseptansescenario med 20 aktiviteter. FR-17 er delt i deterministiske krav og KI-kvalitet, og MVP-kriteriene i SM-1 og SM-2 er presisert. D1 gjør godkjente og avviste forslag omgjørbare fram til fullføring. Det er ikke opprettet nye krav-ID-er.
- **Product Brief-omtale:** §4.5 og §8.2 punkt 1 og 4 er rettet. OQ-1 er kontrollert og beholdt, fordi den daterte konstateringen fortsatt stemmer.
- **`.memlog.md`:** 15 nye oppføringer er lagt til, inkludert en override som delvis erstatter A20 og A21. Eldre historikk er uendret. Filen er konvertert tilbake til LF etter at `memlog.py` skrev CRLF.
- **Kontroller:** `git diff --check` fant ingenting. Product Brief er uendret, og rapportene er byte-identiske med originalene.
- **Status:** PRD-fasen er avsluttet. UX Design er ikke startet.

### Åpne punkter
- UX (OQ-3): innholdet i kategorilisten, inkludert restkategori og eventuell egen kategori for frister.
- UX (OQ-4, OQ-5): lesbarhet i årsvisningen og utforming av gjennomgang, fullføring, forkasting, navigasjon, informasjon om demo-modus ved feil og om mulige duplikater.
- Arkitektur (OQ-6–OQ-8): valg av språkmodell, aktivering av demo-modus, lagringsløsning, tidsgrense, dokumentstørrelse og nettlesere.
- Testplan (OQ-9, OQ-10): har verken eier eller workflow, og må foreligge før stories.
- Valideringsfunn som gruppen ikke har behandlet, står fortsatt åpne i `docs/prd-validering/2026-11-01/validation-report.md`. Eksempler er eiere for OQ-er (M10), merknadsgrensen (M11), delte uker i månedsvisningen (M6) og briefens nye suksesskriterier i SM-1 og SM-4 (M12).
