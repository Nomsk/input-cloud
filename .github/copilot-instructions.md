# Copilot instructions for contributors and AI agents

Purpose: Help AI coding agents and contributors become productive quickly in this repository.

- **Big Picture:** This repository is a minimal static web project (single entry point: `index.html` in the repository root). There is no build system, package manifest, or test harness detected. Changes typically modify `index.html` (markup, inline CSS, or inline JS) or add assets alongside it.

- **Key files:**
  - `index.html` — single source of truth for the site. Inspect it before making changes; external CDN links (scripts/styles) may control behavior.

- **How to run / preview locally (Windows PowerShell):**
  - If you have Python available (quickest):

    ```pwsh
    cd <repo-root>
    python -m http.server 8000
    Start-Process http://localhost:8000
    ```

  - Or install VS Code "Live Server" and use its "Go Live" command to preview changes.

- **Edit guidance / patterns observed:**
  - Keep changes scoped to `index.html` unless adding clearly-named assets (e.g. `assets/`, `images/`).
  - Prefer conservative edits: update or add only the markup or script needed for a single behavior. Small, focused PRs are easiest to review.
  - If modifying embedded scripts, prefer adding new functions rather than rewriting large blocks inline.

- **Search & merge guidance for AI:**
  - No existing `.github/copilot-instructions.md` or README was found — create or update the file at `.github/copilot-instructions.md` with concise, actionable items (this file).
  - When merging with an existing file: preserve any project-specific guidance; prefer the repo's explicit commands (e.g. if there is a `package.json` later, prefer its `scripts` values for run/test commands).

- **PR checklist for AI-generated changes:**
  - Produce a concise PR description explaining the intent and manual verification steps.
  - Include a screenshot or short video/GIF for UI changes where visual appearance matters.
  - Provide steps to preview changes locally (copy the exact `python -m http.server`/Live Server steps above).
  - If adding external dependencies, include the exact CDN URL and purpose in the PR body.

- **Testing / verification:**
  - Manual verification: open `http://localhost:8000` and exercise interactive parts in major browsers.
  - No automated tests were discovered; do not add test claims to PRs unless you also add a test harness and CI.

- **Project-specific conventions:**
  - Single-file primary artifact — assume global changes are visible site-wide.
  - No opinionated linting or formatter config detected; follow common HTML/CSS/JS best practices and keep diffs small.

- **Integration points & external services:**
  - Inspect `index.html` for external script/style tags or API endpoints before editing. Document any changes to external integrations in PRs.

- **When to ask a human:**
  - If a requested change touches authentication, production API keys, or third-party billing/configuration — stop and ask.
  - If asked to enable a global feature flag (example: "Enable Claude Haiku 4.5 for all clients") — ask: where are feature flags stored? (repo, CI, or external admin console?). Do not modify secrets or deployment systems without explicit instructions and credentials.

- **Examples from this repo:**
  - Primary change example: to add a new script, add a `<script src="/assets/new-feature.js"></script>` near the end of `index.html` and include a short PR body showing manual steps to verify the feature.

If anything in this file is unclear or you want additional details (for example, CI commands or where to store feature flags), tell me which area to expand and whether you want me to preview a PR with the requested change.
