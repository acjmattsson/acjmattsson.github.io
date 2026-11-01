# acjmattsson.github.io

Publik dokumentation (GitHub Pages, Jekyll) för acjmattssons appar i App Store. Struktur och regler: [ADR-0001](docs/adr/0001-one-public-docs-repo-for-all-apps.md).

## Regler

1. En mapp per app med stabil slug: `<app>/index.md`, `<app>/privacy/index.md`, `<app>/support/index.md`.
2. **URL:er ändras aldrig.** De står i App Store Connect.
3. En policy beskriver bara det appen faktiskt gör. Granska appens kod (nätverk, lagring, SDK:er) innan en policy skrivs eller ändras, och skriv underlaget i `spec.md`.
4. Varje policy har "Senast uppdaterad" och länk till sin ändringshistorik. Datumet uppdateras vid varje innehållsändring.
5. Sidtexter på svenska. Git-meddelanden (commit, PR) på engelska.
6. Varje förändring får `intent.md` → `spec.md` → `plan.md` i `intent/<förändring>/`. Arkitekturbeslut som ADR i `docs/adr/`.
7. `docs/`, `intent/`, `README.md` och `CLAUDE.md` publiceras inte (`exclude` i `_config.yml`).
