# ADR-0001: Ett publikt dokumentationsrepo för alla appar

- **Status:** Accepterad
- **Datum:** 2026-11-01
- **Beslutsfattare:** acjmattsson (produktägare)

## Kontext

Apple kräver att varje app i App Store länkar till en **integritetspolicy** (Privacy Policy URL) och en **supportsida** (Support URL). En marknadsförings-URL är valfri. Fler appar är på väg (TextTV Touch, Boxsplosion), och alla behöver samma sorts sidor.

Apparnas kod ligger i privata repon. GitHub Pages från privata repon kräver betald plan, och koden ska inte bli publik bara för att policyn ska kunna publiceras.

## Beslut

1. **Ett publikt repo, `acjmattsson/acjmattsson.github.io`**, för all publik dokumentation om alla appar. Det publiceras som GitHub-användarsida på `https://acjmattsson.github.io/`.
2. **En mapp per app** med stabil slug (gemener, bindestreck): `texttv-touch/`, `boxsplosion/`.
3. **Fast struktur per app:**
   ```
   <app>/index.md           # Produktsida (kan användas som marknadsförings-URL)
   <app>/privacy/index.md   # Privacy Policy URL
   <app>/support/index.md   # Support URL
   ```
   `index.md` i en mapp ger URL:er som slutar på `/privacy/` och lämnar plats för t.ex. `privacy/en/` senare.
4. **Egen integritetspolicy per app.** Apple granskar policyn mot vad just den appen gör. Hellre lite duplicerad text än en delad policy som blir fel för någon app.
5. **URL:er ändras aldrig** när de väl angetts i App Store Connect. Flyttas en sida lämnas en omdirigering kvar.
6. **Transparens via Git.** Repot är publikt med flit: varje ändring av en policy syns i historiken. Varje policy visar "Senast uppdaterad" och länkar till sin egen ändringshistorik.
7. **Svenska** är grundspråket. Engelska läggs till som `<sida>/en/` om en app säljs utanför Sverige.
8. Beslut om sajten dokumenteras som ADR i `docs/adr/` i det här repot. `docs/`, `intent/`, `README.md` och `CLAUDE.md` publiceras inte på sajten (`exclude` i `_config.yml`) men är läsbara på GitHub.

## Konsekvenser

- **+** En plats att underhålla, ett enhetligt utseende och korta URL:er.
- **+** Policyändringar är spårbara för vem som helst.
- **+** Appkoden förblir privat.
- **−** Användarsidan (`acjmattsson.github.io`) är unik per konto. Roten används nu av app-dokumentationen. En personlig sida får i så fall dela utrymme med den.
- **−** Byte till egen domän i framtiden kräver nya URL:er i App Store Connect för alla appar (eller omdirigeringar).

## Alternativ som valdes bort

- **Repo per app** (`texttv-touch-site` m.fl.): fler repon att underhålla, längre URL:er, inget gemensamt utseende.
- **Repo med namnet `apps`**: fungerar, men ger ett extra led i varje URL (`/apps/texttv-touch/…`) utan vinst.
- **Publicera från apprepona**: kräver att koden blir publik eller betald plan.
