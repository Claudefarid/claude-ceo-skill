# Contributing to CEO Assistant

Thank you for helping improve the CEO Assistant skill. Contributions are welcome across all areas — new domains, integration guides, benchmark data, and bug fixes.

---

## Ways to contribute

### 1. Report a broken integration
If an MCP package name is wrong or a setup command fails, open an issue using the **Bug Report** template. Include the exact error message and which tool you were trying to connect.

### 2. Add a new business domain
Each domain lives in `references/`. To add a domain:
1. Create `references/<domain>.md` following the structure of an existing file (e.g. `references/finance.md`)
2. Add a routing entry to the routing table in `SKILL.md`
3. Add example prompts to `references/prompts.md`
4. Open a PR with a short description of what the domain covers

### 3. Improve benchmark data
Benchmarks live in `references/benchmarks.md`. If you have accurate data for a region or industry not yet covered, add it with a source reference.

### 4. Add an integration guide
Integration setup guides live in `references/connect.md`. To add a new tool:
1. Verify the npm package exists (`npm info <package-name> version`)
2. Add the step-by-step bash setup commands
3. Add the integration data-pull logic to `references/integrations.md`
4. Wire it into the relevant domain reference file

### 5. Share your use case
Open a GitHub Discussion under **Show and Tell** — describe how you use the skill and what prompts work well. This helps new users and informs future improvements.

---

## Pull request guidelines

- Keep PRs focused — one change per PR
- Test your integration commands before submitting
- Follow the existing file structure and tone (professional, no hype language, no emojis)
- Update `CHANGELOG.md` with your change under `[Unreleased]`

---

## Benchmark data standards

When adding benchmarks:
- Specify the source (industry report, aggregated public data, your own dataset)
- Specify the date range the data covers
- Mark regional benchmarks clearly (do not mix US and global data)
- Use ranges rather than single figures where variance is high

---

## Code of conduct

- Be direct and constructive in reviews
- No personal attacks
- Disagreements about approach belong in the issue, not in PR comments on code

---

## Questions?

Open a GitHub Discussion under **Q&A**.
