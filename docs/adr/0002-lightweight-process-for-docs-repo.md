# ADR-0002: Lättare arbetssätt för dokumentationsrepot

- **Status:** Accepterad
- **Datum:** 2026-11-01
- **Beslutsfattare:** Alexander Mattsson (produktägare)
- **Relaterat:** [ADR-0001](0001-one-public-docs-repo-for-all-apps.md)

## Kontext

Apprepona följer Anthropics AI-native SDLC: varje förändring får `intent.md` → `spec.md` → `plan.md` innan koden skrivs. Det arbetssättet togs med hit i de två första förändringarna.

Här är texten själva leveransen. Plan och resultat blir nästan samma sak, och PR-beskrivningen och commit-historiken förklarar redan varför en ändring görs. Den del som faktiskt gjorde nytta var underlaget för integritetspolicyn: vilken kod i appen varje påstående i policyn bygger på.

## Beslut

1. **Ingen `intent/`-mapp** i det här repot. Befintliga intent-, spec- och planfiler tas bort. De finns kvar i git-historiken.
2. **Ett levande underlag per app** i `docs/<app>/privacy-basis.md`. Det visar vilken kod varje påstående i policyn bygger på, och när koden senast granskades. Underlaget uppdateras i samma PR som policyn.
3. **Struktur och regler** för repot dokumenteras fortfarande som ADR i `docs/adr/`.
4. **Allt annat** (FAQ, formuleringar, ärendemallar, stavfel) görs med en PR och en tydlig beskrivning.

Det här ändrar ADR-0001 punkt 8: `intent/` finns inte längre bland de undantagna mapparna.

## Konsekvenser

- **+** Mindre administration för textändringar.
- **+** Underlaget för policyn samlas på ett ställe per app i stället för att spridas över flera spec-filer.
- **−** Avsteg från arbetssättet i apprepona. Det är medvetet och gäller bara det här repot.
