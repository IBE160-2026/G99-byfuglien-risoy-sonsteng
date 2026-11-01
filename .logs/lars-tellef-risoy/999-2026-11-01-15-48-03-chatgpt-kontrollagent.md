# ChatGPT-kontrollagent

## 2026-11-01 kl. 15:48 — Lars Tellef Risøy

### Oppgave
Etablere masterprompten for en separat ChatGPT-kontrollagent som et versjonskontrollert dokument, uten at den blir en del av Claude Codes operative instruksjoner, og dokumentere dette i KI-loggen.

### Plan
- Vurdere plassering mot repoets struktur. `docs/` er BMADs `project_knowledge`, så filen ble lagt i `prompts/` i roten.
- Opprette masterprompten og KI-loggen etter godkjenning av utkastet.
- Kontrollere, committe og pushe etter separat godkjenning.
- Da push ble avvist: kontrollere de to nye commitene på `origin/main`, rebase og pushe uten force.

### Resultat
- Commit `07d3af6` legger til `prompts/chatgpt-kontrollagent.md` og `docs/ki-logg/2026-11-01-chatgpt-kontrollagent.md`.
- Commitene `813e31e` og `c5f412f` fra Bård Pettersen ble kontrollert før rebase: `himolde.no`-adresse, GitHub-konto med admin-tilgang til repoet og samme commiter i andre IBE160-grupperepoer. Commitene er usignerte. Ingen konflikt med KI-loggen eller masterprompten, som berører andre filer.
- Sesjonsloggen dokumenterer økten i tillegg til KI-loggen, som fortsatt følger `docs/ki-logg/README.md`.
- Verifisert: alle 14 hovedoverskrifter finnes, linjeskift er LF, whitespace-kontrollene er uten feil, og mønstersøk fant ingen hemmeligheter i masterprompten.
- Bevisst utelatt fra masterpromptfilen: privat ChatGPT-lenke, plassholder og eget versjonsnummer. `CLAUDE.md`, `AGENTS.md` og BMAD-konfigurasjonen ble ikke endret i denne økten.

### Åpne punkter
- Masterprompten er ikke maskinelt sammenlignet med originalen i ChatGPT-dialogen. Bare de 14 hovedoverskriftene er kontrollert med søk.
