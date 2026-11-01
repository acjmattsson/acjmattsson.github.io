# ADR-0001: One public documentation repository for all apps

- **Status:** Accepted. Point 7 is superseded by [ADR-0003](0003-english-as-default-language.md); point 8 is amended by [ADR-0002](0002-lightweight-process-for-docs-repo.md).
- **Date:** 2026-11-01
- **Decision maker:** acjmattsson (product owner)
- **Translated** from Swedish to English on 2026-11-01 per ADR-0003. The decision is unchanged.

## Context

Apple requires every app on the App Store to link to a **privacy policy** (Privacy Policy URL) and a **support page** (Support URL). A marketing URL is optional. More apps are on the way (TextTV Touch, Boxsplosion), and they all need the same kinds of pages.

The apps' source code lives in private repositories. GitHub Pages from a private repository requires a paid plan, and the code should not become public just so that the policy can be published.

## Decision

1. **One public repository, `acjmattsson/acjmattsson.github.io`**, for all public documentation about all apps. It is published as the GitHub user site at `https://acjmattsson.github.io/`.
2. **One folder per app** with a stable slug (lowercase, hyphens): `texttv-touch/`, `boxsplosion/`.
3. **Fixed structure per app:**
   ```
   <app>/index.md           # Product page (can be used as the marketing URL)
   <app>/privacy/index.md   # Privacy Policy URL
   <app>/support/index.md   # Support URL
   ```
   `index.md` inside a folder gives URLs ending in `/privacy/` and leaves room for, for example, `privacy/en/` later.
4. **A separate privacy policy per app.** Apple reviews the policy against what that particular app does. A little duplicated text is better than a shared policy that turns out wrong for one of the apps.
5. **URLs never change** once they have been entered in App Store Connect. If a page moves, a redirect is left behind.
6. **Transparency through Git.** The repository is public on purpose: every change to a policy is visible in its history. Each policy shows a "last updated" date and links to its own change history.
7. **Swedish** is the base language. English is added as `<page>/en/` if an app is sold outside Sweden. *(Superseded by ADR-0003.)*
8. Decisions about the site are recorded as ADRs in `docs/adr/` in this repository. `docs/`, `intent/`, `README.md` and `CLAUDE.md` are not published on the site (`exclude` in `_config.yml`) but can be read on GitHub.

## Consequences

- **+** One place to maintain, a consistent look and short URLs.
- **+** Policy changes can be traced by anyone.
- **+** The app code stays private.
- **−** The user site (`acjmattsson.github.io`) is unique per account. Its root is now used by the app documentation, so a personal site would have to share the space.
- **−** Moving to a custom domain later requires new URLs in App Store Connect for every app (or redirects).

## Alternatives considered

- **One repository per app** (`texttv-touch-site` and so on): more repositories to maintain, longer URLs, no shared look.
- **A repository named `apps`**: works, but adds a segment to every URL (`/apps/texttv-touch/…`) for no benefit.
- **Publishing from the app repositories**: requires the code to become public, or a paid plan.
