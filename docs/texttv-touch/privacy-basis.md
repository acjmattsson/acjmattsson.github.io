# Privacy policy basis – TextTV Touch

This document is the basis for every claim in the [privacy policy](../../texttv-touch/privacy/index.md). Update it in the same PR as the policy, and review the app's code again before doing so.

The policy itself is in Swedish, because the app is Swedish only ([ADR-0003](../adr/0003-english-as-default-language.md)).

**Last reviewed:** 2026-11-01, `acjmattsson/texttv-touch` (`main`).

## URLs in App Store Connect

| Apple field | URL |
|---|---|
| Privacy Policy URL | `https://acjmattsson.github.io/texttv-touch/privacy/` |
| Support URL | `https://acjmattsson.github.io/texttv-touch/support/` |
| Marketing URL (optional) | `https://acjmattsson.github.io/texttv-touch/` |

## What the app does

| Area | Facts | Source in the app |
|---|---|---|
| Network | Only request: `GET https://www.svt.se/text-tv/api/{page number}`. No custom headers. | `src/services/svtTextApi.ts` |
| Local storage | `AppSettings` (`inputPosition`, `theme`, `favorites`) in AsyncStorage, key `texttv_settings`. | `src/store/settingsContext.tsx` |
| Cache | Pages in memory (`Map`), max 10 min, gone when the app closes. | `src/store/pageCache.ts` |
| WebView | Locally built HTML (`baseUrl: ''`), loads no external resources. | `src/components/PageCardWebKit.tsx` |
| Third parties | No SDKs for analytics, ads, crash reporting, accounts or push. | `package.json` |

## Support and data controller

| | |
|---|---|
| Data controller | Alexander Mattsson (private individual) |
| Email | `acjmattsson+texttv@gmail.com` (Gmail plus alias, filtered per app) |
| Public channel | GitHub issues through the forms in `.github/ISSUE_TEMPLATE/` |
| Legal basis for support email | Legitimate interest (GDPR Art. 6(1)(f)): being able to reply |
| Email retention | Until the matter is closed, at most 12 months |

## App Privacy in App Store Connect

**Data Not Collected.** The app collects no data. The requests to SVT are necessary for the app to work and are described in the policy. Support by email or on GitHub happens outside the app and is not covered by the label.

## Review again when

the app gets analytics, crash reporting, accounts, push notifications, new network requests or new local storage, or when an Expo service that can collect data is turned on (see ADR-0005 in `acjmattsson/texttv-touch`).
