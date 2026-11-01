# Underlag för integritetspolicyn – TextTV Touch

Det här är underlaget för varje påstående i [integritetspolicyn](../../texttv-touch/privacy/index.md). Uppdatera underlaget i samma PR som policyn, och granska appens kod igen innan du gör det.

**Senast granskat:** 2026-11-01, `acjmattsson/texttv-touch` (`main`).

## URL:er i App Store Connect

| Apple-fält | URL |
|---|---|
| Privacy Policy URL | `https://acjmattsson.github.io/texttv-touch/privacy/` |
| Support URL | `https://acjmattsson.github.io/texttv-touch/support/` |
| Marketing URL (valfri) | `https://acjmattsson.github.io/texttv-touch/` |

## Vad appen gör

| Område | Fakta | Källa i appen |
|---|---|---|
| Nätverk | Enda anropet: `GET https://www.svt.se/text-tv/api/{sidnummer}`. Inga egna headers. | `src/services/svtTextApi.ts` |
| Lokal lagring | `AppSettings` (`inputPosition`, `theme`, `favorites`) i AsyncStorage, nyckel `texttv_settings`. | `src/store/settingsContext.tsx` |
| Cache | Sidor i minnet (`Map`), max 10 min, försvinner när appen stängs. | `src/store/pageCache.ts` |
| WebView | Lokalt byggd HTML (`baseUrl: ''`), laddar inga externa resurser. | `src/components/PageCardWebKit.tsx` |
| Tredjepart | Inga SDK:er för analys, annonser, kraschrapporter, konton eller push. | `package.json` |

## Support och personuppgiftsansvar

| | |
|---|---|
| Personuppgiftsansvarig | Alexander Mattsson (privatperson) |
| E-post | `acjmattsson+texttv@gmail.com` (Gmail plus-alias, filtreras per app) |
| Publik kanal | GitHub-ärenden via mallarna i `.github/ISSUE_TEMPLATE/` |
| Rättslig grund för support-e-post | Berättigat intresse (GDPR art. 6.1 f): att kunna svara |
| Lagring av mejl | Tills ärendet är avslutat, senast 12 månader |

## App Privacy i App Store Connect

**Data Not Collected.** Appen samlar inte in data. Anropen till SVT är nödvändiga för funktionen och beskrivs i policyn. Support via e-post eller GitHub sker utanför appen och omfattas inte av märkningen.

## Granska igen när

appen får analys, kraschrapportering, konton, push-notiser, nya nätverksanrop eller ny lokal lagring, eller när en Expo-tjänst som kan samla in data slås på (se ADR-0005 i `acjmattsson/texttv-touch`).
