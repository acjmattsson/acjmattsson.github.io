# ADR-0003: English as the default language

- **Status:** Accepted
- **Date:** 2026-11-01
- **Decision maker:** Alexander Mattsson (product owner)
- **Related:** supersedes point 7 of [ADR-0001](0001-one-public-docs-repo-for-all-apps.md)

## Context

ADR-0001 made Swedish the base language. But not every app is aimed only at Sweden. TextTV Touch is built on SVT Text and is Swedish only, while a game, for example, can have users anywhere. The repository and the site are also the public point of contact for all users, so the shared parts (landing page, README, repository description) need to work for everyone.

The repository is public so that anyone can follow what is done and why. That is easiest when its history and internal documents are in one language.

## Decision

1. **Everything in this repository is in English** unless stated otherwise: pages, issue templates, README, the shared parts of the site, and internal documents (`CLAUDE.md`, ADRs, `docs/`). This holds even though the product owner and Claude talk in Swedish. Commit messages and PRs are in English, as before.
2. **An app can have its user-facing content in another language.** This applies to the app's pages, privacy policy, support page and issue templates. It is listed in the table below and set in `_config.yml` (`defaults` with `lang` for the app's path), so that the pages get the correct `<html lang>`. The app's internal documents (e.g. `docs/<app>/privacy-basis.md`) are still in English.
3. **More languages for an app** are added as `<page>/<language-code>/`, for example `privacy/en/`. Existing URLs do not change (ADR-0001, point 5).
4. **The repository description on GitHub** is bilingual (English and Swedish), because TextTV Touch's users are Swedish.
5. ADR-0001 and ADR-0002 were written in Swedish and have been translated without changing the decisions.

| App | User-facing language |
|---|---|
| TextTV Touch | Swedish (only) |
| Boxsplosion | English (only) |

## Consequences

- **+** New apps and the shared pages reach more users.
- **+** Anyone following the history reads it in one language.
- **+** Page languages are marked correctly for screen readers and search engines.
- **−** The site mixes languages: the landing page is in English and TextTV Touch's pages are in Swedish.
