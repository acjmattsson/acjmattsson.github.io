# acjmattsson.github.io

Public documentation (GitHub Pages, Jekyll) for acjmattsson's apps on the App Store. Structure and rules: [ADR-0001](docs/adr/0001-one-public-docs-repo-for-all-apps.md).

## Rules

1. One folder per app with a stable slug: `<app>/index.md`, `<app>/privacy/index.md`, `<app>/support/index.md`. Adding an app: follow [docs/new-app-checklist.md](docs/new-app-checklist.md).
2. **URLs never change.** They are entered in App Store Connect.
3. A policy describes only what the app actually does. Review the app's code (network, storage, SDKs) before a policy is written or changed, and update the basis in `docs/<app>/privacy-basis.md` in the same PR.
4. Every policy has a "last updated" date and a link to its change history. The date is updated on every content change.
5. **Language per [ADR-0003](docs/adr/0003-english-as-default-language.md):** everything in English, including internal documents, even though we talk in Swedish. Exception: user-facing content for TextTV Touch (pages, policy, support, issue templates) is Swedish only (`defaults` in `_config.yml`).
6. No `intent/` folder here ([ADR-0002](docs/adr/0002-lightweight-process-for-docs-repo.md)). Structure and rules go in ADRs in `docs/adr/`. Other changes: a PR with a clear description.
7. `docs/`, `README.md` and `CLAUDE.md` are not published (`exclude` in `_config.yml`).
