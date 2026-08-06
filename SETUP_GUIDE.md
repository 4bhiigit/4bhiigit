# Setup Guide

Everything you need to put the profile README live, plus how to customize it later.

---

## 1. Folder Structure

GitHub renders a profile README when it lives in a repository with the **exact same name as your username**. Create (or reuse) a repo called `4bhiigit`, and lay it out like this:

```
4bhiigit/
├── README.md                          → the profile page itself
└── .github/
    └── workflows/
        ├── snake.yml                  → generates the animated contribution snake
        └── metrics.yml                → generates the daily metrics panel (optional)
```

That's it — no other files are required. Everything else (stats cards, typing animation, icons) is loaded live from external image services referenced inside `README.md`, so there's nothing to build or deploy on your side.

---

## 2. Assets Used

Every visual element is a **live, dynamically generated image** — nothing is a static file you need to upload, and nothing goes stale, since each one re-renders on every page load.

| Element | Service | Maintained by |
|---|---|---|
| Hero banner & footer wave | capsule-render | [kyechan99/capsule-render](https://github.com/kyechan99/capsule-render) |
| Typing animation | readme-typing-svg | [DenverCoder1/readme-typing-svg](https://github.com/DenverCoder1/readme-typing-svg) |
| Tech stack icons | skillicons.dev | [tandpfun/skill-icons](https://github.com/tandpfun/skill-icons) |
| Featured skill badges | shields.io | [badges/shields](https://github.com/badges/shields) |
| Project cards | github-readme-stats (pin API) | [anuraghazra/github-readme-stats](https://github.com/anuraghazra/github-readme-stats) |
| GitHub stats & top languages | github-readme-stats | same as above |
| Streak stats | github-readme-streak-stats | [DenverCoder1/github-readme-streak-stats](https://github.com/DenverCoder1/github-readme-streak-stats) |
| Activity graph | github-readme-activity-graph | [Ashutosh00710/github-readme-activity-graph](https://github.com/Ashutosh00710/github-readme-activity-graph) |
| Trophies | github-profile-trophy | [ryo-ma/github-profile-trophy](https://github.com/ryo-ma/github-profile-trophy) |
| Profile view counter | komarev | [komarev.com/ghpvc](https://komarev.com/ghpvc/) |
| Snake animation (optional) | Platane/snk | [Platane/snk](https://github.com/Platane/snk) |
| Metrics panel (optional) | lowlighter/metrics | [lowlighter/metrics](https://github.com/lowlighter/metrics) |

All of these are free, open-source, and actively maintained at the time of writing. If any single one ever goes down, only that one image breaks — the rest of the page is unaffected.

---

## 3. Installation Notes

1. Create a public repository named exactly `4bhiigit` (must match your GitHub username).
2. Add `README.md` at the root.
3. Commit — GitHub will immediately start rendering it on your profile page.
4. Optionally add the two workflow files under `.github/workflows/` (see section 5 below) for the animated snake and the daily metrics panel.

No build step, no dependencies, no local dev server needed — it's pure Markdown/HTML rendered by GitHub itself.

---

## 4. Customization Guide

**Swap the accent color.** Every image URL in the README uses the same gold hex, `D4AF37`, and the same background, `0D1117`. Find-and-replace either value across the file to re-theme the whole page in one pass.

**Update project cards.** The "Featured Projects" section pulls live data by `repo=` name in the `github-readme-stats` pin URLs — if you pin different repositories on your profile, just swap the `repo=` value and the linked repo name; the card content (stars, language, description) updates automatically.

**Add certifications/achievements.** The "Highlights" section is intentionally left as a short, honest summary rather than invented awards. Once you've earned specific certifications or competition results, add them as a plain bullet list under that heading.

**Rewrite the Learning Journey.** That section reflects a reasonable roadmap for your stated interests — edit the three columns freely as your goals change.

**Typing animation phrases.** Edit the `lines=` parameter in the `readme-typing-svg` URL (semicolon-separated, spaces as `+`).

---

## 5. GitHub Actions Setup

### Snake animation (`snake.yml`)
- Place at `.github/workflows/snake.yml` in your `4bhiigit` repo.
- No secrets needed — it uses the default `GITHUB_TOKEN`.
- On first run it creates an `output` branch containing the generated SVGs.
- To display the snake in your README, add this once the first run completes:
  ```markdown
  ![Snake animation](https://raw.githubusercontent.com/4bhiigit/4bhiigit/output/github-contribution-grid-snake-dark.svg)
  ```

### Metrics panel (`metrics.yml`) — optional
- Place at `.github/workflows/metrics.yml`.
- Requires a **Personal Access Token** with `repo` and `read:user` scopes, saved as a repository secret named `METRICS_TOKEN` (Settings → Secrets and variables → Actions). The default `GITHUB_TOKEN` doesn't have enough scope for some metrics plugins.
- Once it runs, embed the result with:
  ```markdown
  ![Metrics](./metrics.svg)
  ```

Both workflows run on a schedule (the "daily refresh" / "auto update" behavior) and can also be triggered manually from the **Actions** tab.

---

## 6. Image Credits

All dynamic images are generated on request by the third-party open-source services listed in section 2, using your public GitHub data. No images were downloaded, copied, or hosted — every URL in the README calls the originating service directly, so credit and control stay with those projects.
