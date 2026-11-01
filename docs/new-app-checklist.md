# Checklist: adding a new app

Use this when an app gets its pages on the site. The rules behind each step are in [ADR-0001](adr/0001-one-public-docs-repo-for-all-apps.md), [ADR-0002](adr/0002-lightweight-process-for-docs-repo.md) and [ADR-0003](adr/0003-english-as-default-language.md).

Replace `<app>` with the app's slug (lowercase, hyphens, e.g. `texttv-touch`). The slug becomes part of URLs that never change, so choose it carefully.

## 1. Before writing anything

- [ ] The app record exists in App Store Connect, so the name is reserved.
- [ ] Decide the app's user-facing language. English is the default; anything else is an exception per ADR-0003.
- [ ] Review the app's code for everything that touches user data:
  - network requests (which hosts, what is sent)
  - local storage (what is stored, where)
  - third-party SDKs and services (analytics, crash reporting, ads, accounts, push, Game Center, iCloud, etc.)
  - Expo/EAS services that can collect data

## 2. Privacy basis (internal, English)

- [ ] Create `docs/<app>/privacy-basis.md`, using [`docs/texttv-touch/privacy-basis.md`](texttv-touch/privacy-basis.md) as the template:
  - the date and branch the code was reviewed on
  - the App Store Connect URLs
  - one row per fact, with the source file in the app
  - support contact, data controller, legal basis and retention
  - the App Privacy label this leads to
  - what should trigger a new review

## 3. Pages (in the app's language)

- [ ] `<app>/index.md`: product page with links to the policy and support page, and a "back to all apps" link.
- [ ] `<app>/privacy/index.md`: privacy policy. Every claim must be backed by the privacy basis. It must include:
  - a "last updated" date and a link to the file's change history on GitHub
  - what the app stores and sends, and what it does not do
  - how support contacts are handled, users' rights and the data controller
- [ ] `<app>/support/index.md`: support page with:
  - the email alias (`acjmattsson+<short-name>@gmail.com`)
  - a link to the issue forms, and a warning that issues are public
  - an FAQ

## 4. Support channels

- [ ] Gmail: create a filter for `to:acjmattsson+<short-name>@gmail.com` (label, and optionally skip the inbox).
- [ ] Issue forms in `.github/ISSUE_TEMPLATE/`, using the TextTV Touch forms as the template:
  - `<app>-bug.yml` and `<app>-question.yml`
  - title prefix `[<App name>] `
  - the public-issue warning and the required privacy checkbox
- [ ] Check that the contact link in `.github/ISSUE_TEMPLATE/config.yml` still fits.

## 5. Site and repository

- [ ] If the language isn't English: add a `defaults` entry with `lang` for `<app>` in `_config.yml`.
- [ ] Add the app to the language table in ADR-0003 (a table row is an update, not a new decision).
- [ ] Add the app to the landing page (`index.md`) and to the table in `README.md`.
- [ ] Open a PR with a clear description that links to the privacy basis.

## 6. After merge

- [ ] The pages are live at `https://acjmattsson.github.io/<app>/`, `/privacy/` and `/support/`.
- [ ] View the page source and check that `<html lang>` is correct.
- [ ] The new issue forms show up under "New issue".
- [ ] Send a test email to the alias and check that the filter catches it.
- [ ] Enter the URLs in App Store Connect:
  - Privacy Policy URL: `https://acjmattsson.github.io/<app>/privacy/`
  - Support URL: `https://acjmattsson.github.io/<app>/support/`
  - Marketing URL (optional): `https://acjmattsson.github.io/<app>/`
- [ ] Fill in App Privacy in App Store Connect so that it matches the privacy basis.

## When an existing app changes

When an app gains a new network request, storage, SDK or service:

- [ ] Review the code again and update `docs/<app>/privacy-basis.md`.
- [ ] Update the policy and its "last updated" date in the same PR.
- [ ] Update App Privacy in App Store Connect **before** the new version is submitted.
