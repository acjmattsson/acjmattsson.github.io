# ADR-0003: Engelska som standardspråk

- **Status:** Accepterad
- **Datum:** 2026-11-01
- **Beslutsfattare:** Alexander Mattsson (produktägare)
- **Relaterat:** ersätter punkt 7 i [ADR-0001](0001-one-public-docs-repo-for-all-apps.md)

## Kontext

ADR-0001 gjorde svenska till grundspråk. Men alla appar riktar sig inte bara till Sverige. TextTV Touch bygger på SVT Text och är enbart svensk, medan till exempel ett spel kan ha användare var som helst. Repot och sajten är dessutom den publika kontaktytan mot alla användare, och de gemensamma delarna (startsida, README, repobeskrivning) behöver fungera för alla.

## Beslut

1. **Engelska är standardspråket** för allt publikt innehåll om inget annat anges: sidor, ärendemallar, README och sajtens gemensamma delar.
2. **En app kan ha ett annat språk.** Det anges i appens rad i tabellen nedan och i `_config.yml` (`defaults` med `lang` för appens sökväg), så att sidornas `<html lang>` blir rätt.
3. **Fler språk för en app** läggs till som `<sida>/<språkkod>/`, t.ex. `privacy/sv/`. Befintliga URL:er ändras inte (ADR-0001, punkt 5).
4. **Repobeskrivningen på GitHub** är tvåspråkig (engelska och svenska), eftersom TextTV Touchs användare är svenska.
5. **Interna dokument** (`CLAUDE.md`, ADR:er, `docs/`) skrivs på svenska. Git-meddelanden skrivs på engelska.

| App | Språk |
|---|---|
| TextTV Touch | Svenska (enbart) |
| Boxsplosion | Engelska |

## Konsekvenser

- **+** Nya appar och de gemensamma sidorna når fler användare.
- **+** Sidornas språk är korrekt märkt för skärmläsare och sökmotorer.
- **−** Sajten blandar språk: startsidan är på engelska, och TextTV Touchs sidor är på svenska.
