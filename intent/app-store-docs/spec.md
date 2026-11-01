# Spec: App Store-dokumentation för TextTV Touch

## URL:er (stabila, anges i App Store Connect)

| Apple-fält | URL |
|---|---|
| Privacy Policy URL | `https://acjmattsson.github.io/texttv-touch/privacy/` |
| Support URL | `https://acjmattsson.github.io/texttv-touch/support/` |
| Marketing URL (valfri) | `https://acjmattsson.github.io/texttv-touch/` |

## Underlag för integritetspolicyn

Granskat i `acjmattsson/texttv-touch` (`main`, 2026-11-01):

| Område | Fakta | Källa |
|---|---|---|
| Nätverk | Enda anropet: `GET https://www.svt.se/text-tv/api/{sidnummer}`. Inga egna headers. | `src/services/svtTextApi.ts` |
| Lokal lagring | `AppSettings` (`inputPosition`, `theme`, `favorites`) i AsyncStorage, nyckel `texttv_settings`. | `src/store/settingsContext.tsx` |
| Cache | Sidor i minnet (`Map`), max 10 min, försvinner när appen stängs. | `src/store/pageCache.ts` |
| WebView | Lokalt byggd HTML (`baseUrl: ''`), laddar inga externa resurser. | `src/components/PageCardWebKit.tsx` |
| Tredjepart | Inga SDK:er för analys, annonser, kraschrapporter, konton eller push. | `package.json` |

**Slutsats för App Store Connect (App Privacy):** *Data Not Collected.* Utvecklaren samlar inte in data. Anropen till SVT är nödvändiga för funktionen och beskrivs i policyn.

**Måste granskas igen** när appen får analys, kraschrapportering, konton, push-notiser eller nya nätverksanrop.

## Krav på varje policysida

- "Senast uppdaterad" med datum.
- Länk till sidans ändringshistorik på GitHub.
- Kontaktväg.

## Jekyll

- Tema: `jekyll-theme-primer` (GitHubs standard), `lang: sv`.
- `exclude`: `README.md`, `CLAUDE.md`, `docs/`, `intent/`.
