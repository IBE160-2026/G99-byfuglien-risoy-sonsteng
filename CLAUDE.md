# CLAUDE.md

Se [AGENTS.md](AGENTS.md) for instruksjoner til KI-agenter som jobber i dette
repoet. Innholdet gjelder likt for Claude Code.

## KI-logg

Etter en økt som endrer kode: foreslå en loggoppføring etter malen i
[docs/ki-logg/README.md](docs/ki-logg/README.md). Vis utkastet til brukeren og
lagre det først når et gruppemedlem har kontrollert og godkjent det. Ikke lag
oppføringer om tidligere økter, og ikke beskriv tester som ikke er kjørt.

## Sesjonslogg

Når en oppgave eller økt avsluttes, før sluttoppsummeringen, bruk `sesjonslogg`-skillen: dokumenter Oppgave + Plan + Resultat + åpne punkter i `.logs/<bruker>/`, og før åpne punkter i `.logs/<bruker>/issues.md`. Skillen committer loggfila lokalt; push gjør du selv. Gruppens egne regler for commit og språk gjelder foran dette.
