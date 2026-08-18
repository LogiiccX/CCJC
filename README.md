# CCJC Daily Trade Coordination

A single-file web app for running the daily trade coordination meeting on the **CCJC** project (Yates–Metcon). Built to mirror the AEX meeting app, adapted for CCJC's multiple buildings plus site-wide coordination:

**Sitewide · Courthouse · Detention Center · Sheriff's Office**

Everything lives in one `index.html` — no build step, no server, no dependencies. It runs straight from GitHub Pages.

---

## Tabs

- **📋 Summary** — live meeting overview (manpower, attendance, open tasks/conflicts/inspections), manpower-by-trade rollup, open-conflicts list, and **Export PDF Summary**.
- **🦺 Safety & 5S** — today's safety topic, Toolbox Talk / JHA sign-off per trade, 5S daily checklist, and safety observations / near-miss log.
- **👥 Attendance** — add people; click the status dot to cycle **Here → Remote/Teams → Absent**.
- **💪 Manpower** — head counts by trade (Supv / Journ / Labor / App / Safety) with live totals.
- **🏗 Trade Coord** — building sub-tabs (**Sitewide** first, then the three buildings). Add tasks under any trade block; each task carries a status (Planned / Active / Blocked / Complete).
- **⚠️ Conflicts** — log conflicts/issues with **Building**, trade, type, blocking flag, and target resolution.
- **🔍 Inspections** — log inspections with **Building**, type, and status.
- **🏢 Manage Trades** — add/remove trades; they propagate to every dropdown in the app.
- **⏱ Man Hours** — set default hrs/worker/day, click **📌 Log Today** to snapshot the day's manpower as man hours, and **Export PDF**.

Header carries the **Date / Facilitator / Safety Topic**, a meeting **elapsed timer**, a save indicator, and **New Day / Export / Import**.

---

## Daily workflow

1. Open the page. Fill in **Date**, **Facilitator**, and **Safety Topic**.
2. Hit **▶** on the timer as the meeting starts.
3. Mark **Attendance**, set **Manpower** counts, run **Safety & 5S**.
4. Walk **Trade Coord** building by building; log **Conflicts** and **Inspections** as they come up.
5. Before closing, hit **📌 Log Today** on the Man Hours tab.
6. Tomorrow, click **🗓 New Day** and choose what to carry forward (open tasks, conflicts, inspections, roster, etc.). The Man Hours log always persists.

Everything saves automatically to the browser's local storage on the device you're using.

### Keeping a record

Local storage is per-browser, per-device. To keep a permanent record or share it, click **↧ Export** to download a dated JSON file (`ccjc-coordination-YYYY-MM-DD.json`). **↥ Import** loads one back. You can commit those exports into the repo (e.g. a `/records` folder) if you want a running history in GitHub.

---

## Deploy to GitHub Pages

**New repo (mirrors the AEX setup):**

1. Create a repo, e.g. `ccjc-meeting`.
2. Add this `index.html` at the repo root (and this `README.md` if you like).
3. **Settings → Pages → Build and deployment → Source: Deploy from a branch**, branch `main`, folder `/ (root)`. Save.
4. Your app is live at `https://<your-username>.github.io/ccjc-meeting/`.

**Update later:** edit `index.html`, commit to `main`, and Pages redeploys in a minute or so.

---

## Notes

- I rebuilt this to match the AEX app's full feature set from its live page — the AEX repo's raw source isn't reachable from this project's scope, so the styling here is a clean CCJC template (navy / steel / brass) rather than a pixel copy. If you paste the AEX `index.html` source, I can align the look exactly.
- Buildings are defined in the `BUILDINGS` array near the top of the script; trades are managed live in the **Manage Trades** tab. Both are easy to change.
- Works fully offline once loaded. The only external request is Google Fonts; if fonts are blocked it falls back to system fonts with no loss of function.
