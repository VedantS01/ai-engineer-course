# AI Lead — Six-Month Tracker

A self-hosted, single-file daily tracker for the journey from strong programmer to AI lead. 24 weeks · 168 days · ~360 hours.

## What this is

`index.html` is a complete, self-contained webpage. No build step, no dependencies, no server. Open it locally or host it on GitHub Pages — both work.

It contains:
- The full daily curriculum (24 weeks × 7 days)
- 39 curated resource links (videos, blog posts, docs, repos)
- Progress tracking via `localStorage`
- JSON export/import so you can sync between devices via your repo
- A "today" highlight once you set a start date

---

## Deploy on GitHub Pages (5 minutes)

Replace `<you>` with your GitHub username throughout.

### 1. Create the repo

```bash
# from anywhere on your machine
mkdir ai-lead-tracker && cd ai-lead-tracker
git init
```

Drop `index.html` and this `README.md` into the folder.

```bash
git add .
git commit -m "Initial: tracker page"
```

### 2. Push to GitHub

Create a new empty repo on github.com (call it `ai-lead-tracker`), then:

```bash
git branch -M main
git remote add origin https://github.com/<you>/ai-lead-tracker.git
git push -u origin main
```

### 3. Enable Pages

On the GitHub repo page → **Settings** → **Pages** → under "Build and deployment", set:

- Source: **Deploy from a branch**
- Branch: **main** / folder: **/ (root)**

Hit save. Wait ~30 seconds.

Your tracker is now live at:

```
https://<you>.github.io/ai-lead-tracker/
```

Bookmark this. Open it daily.

---

## How to use it

1. **Set your start date** in the top controls. This activates the "today" highlight and the day-on-plan counter.
2. **Click any day card** to expand it — see the tasks and resource links.
3. **Click the empty box** on the left of a day to mark it complete. Don't mark complete unless you actually did the work; you're the only person you'd be cheating.
4. **Use "Go to today"** to jump back to the current day after browsing.

### Daily routine (≈2 hrs)

- 60 min: hands-on (the project for that week)
- 30 min: focused learning (the day's reading/video)
- 30 min: exploration / debugging / writing notes

### Weekly rhythm

Saturday is consolidation: write a 200–500 word note on what you learned that week, in your own words, as if teaching a colleague. Push the note to a `notes/` folder in this same repo. Six months from now, that folder is your portfolio.

---

## Sync across devices

Progress is stored using the browser's **persistent storage API** — `localStorage` for the data, plus `navigator.storage.persist()` to mark it protected from automatic eviction. The status pill in the footer tells you which mode you're in:

- **◉ Persistent** — your progress is protected. The browser will not auto-clear it.
- **○ Best-effort** — stored locally but evictable under storage pressure. Click the pill to request an upgrade. Browsers typically grant this once you've used the site a few times.
- **◌ Local only** — old browser without the Persistence API. Use Export to back up.

Storage is per-browser, per-device. To sync between devices:

1. Click **↓ Export progress** on whichever device is most up-to-date. Saves a `progress.json` file.
2. Commit that `progress.json` into this repo.
3. On the other device, download `progress.json` from your repo and click **↑ Import progress**.

A simple workflow: export on weekends, commit it, pull on the other device.

If you want this automated, you can fork this repo and add a small GitHub Action or write a userscript — out of scope here, but doable.

---

## Files in this repo

```
ai-lead-tracker/
├── index.html         # the tracker (single file, self-contained)
├── README.md          # this file
├── notes/             # ← create this. Your weekly Saturday notes go here.
└── progress.json      # ← optional, your committed progress backup
```

The `notes/` folder is the most important one. It's what makes this real.

---

## Customizing

Everything is in `index.html`. Open it in any editor.

- The curriculum is the `const curriculum = [...]` array near the top of the `<script>` block. Each week is one object. Edit titles, tasks, or swap resources freely.
- Resource links are defined once in the `R = {...}` object and referenced by key. Add your own.
- Colors and typography are CSS variables at the top of the `<style>` block.

If you want a totally different aesthetic, change the four to five CSS variables (`--ink`, `--paper`, `--amber`, `--rule`) and the fonts at the top.

---

## A note on the plan itself

The plan optimizes for one specific outcome: you, six months from now, having shipped a real AI feature at your company and being credible enough to lead AI work. It is not a survey of ML. It skips a lot of theory on purpose. The bet is that for a strong programmer aiming at engineering leadership, depth on the LLM/agent stack + evals + production concerns beats breadth across all of ML.

If your goal shifts (e.g. you want to do research), the plan should shift with it. Don't follow it on autopilot.

---

## License

Yours. Fork, modify, share, sell, ignore — whatever helps.

— Built for the long game.
