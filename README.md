# Raven Action

> Enterprise AI coding discipline — GitHub Action implementation.
> Part of the [Raven platform](https://github.com/giggsoinc/raven-core). MIT License.
> Built by [Giggso Inc](https://github.com/giggsoinc).

*Platform-agnostic enforcement. Works with Claude Code, OpenAI Codex, or any AI coding agent.*

---

## What It Does

Raven Action runs on every PR — regardless of what AI agent wrote the code:
- CVE scan all imports
- Secret detection in changed files
- Manifest validation
- Audit log written on every run
- Posts visible status: ✅ cleared / 🔴 blocked / ⚠️ did not run

---

## Install

Add to `.github/workflows/raven.yml` in your repo:

```yaml
name: Raven Discipline Check
on: [pull_request]

jobs:
  raven:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: giggsoinc/raven-action@main
        with:
          openai-api-key: ${{ secrets.OPENAI_API_KEY }}
          manifest-path: .raven/manifest.json
```

---

## Works With

| AI Coding Agent | How |
|---|---|
| Claude Code | Adds CI layer on top of pre-commit hooks |
| OpenAI Codex | Primary enforcement layer for PR gates |
| GitHub Copilot | Catches what behavioral instructions miss |
| Any agent / human | Platform-agnostic — runs on every PR regardless |

---

## Status Check

Every PR gets a visible status check:

```
✅ raven/discipline-check — passed
🔴 raven/discipline-check — blocked (CVE: requests 2.6.0 CVSS 9.8)
⚠️ raven/discipline-check — did not run (manifest missing)
```

---

## License

MIT — [Giggso Inc](https://github.com/giggsoinc)
