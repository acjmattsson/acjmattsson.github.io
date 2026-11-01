# ADR-0002: A lighter process for the documentation repository

- **Status:** Accepted
- **Date:** 2026-11-01
- **Decision maker:** Alexander Mattsson (product owner)
- **Related:** [ADR-0001](0001-one-public-docs-repo-for-all-apps.md)
- **Translated** from Swedish to English on 2026-11-01 per [ADR-0003](0003-english-as-default-language.md). The decision is unchanged.

## Context

The app repositories follow Anthropic's AI-native SDLC: every change gets `intent.md` → `spec.md` → `plan.md` before the code is written. That process was carried over here for the first two changes.

Here, the text is the deliverable itself. The plan and the result end up being nearly the same thing, and the PR description and commit history already explain why a change is made. The part that actually proved useful was the basis for the privacy policy: which code in the app each claim in the policy relies on.

## Decision

1. **No `intent/` folder** in this repository. The existing intent, spec and plan files are removed. They remain in the Git history.
2. **A living basis document per app** in `docs/<app>/privacy-basis.md`. It shows which code each claim in the policy relies on, and when that code was last reviewed. The basis is updated in the same PR as the policy.
3. **Structure and rules** for the repository are still recorded as ADRs in `docs/adr/`.
4. **Everything else** (FAQ, wording, issue templates, typos) is done through a PR with a clear description.

This amends point 8 of ADR-0001: `intent/` is no longer among the excluded folders.

## Consequences

- **+** Less overhead for text changes.
- **+** The basis for each policy is collected in one place per app instead of being spread across several spec files.
- **−** A departure from the process used in the app repositories. It is deliberate and applies only to this repository.
