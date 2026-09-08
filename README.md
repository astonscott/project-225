# Project 225

Long drive Phase 1 — a 12-week mass-and-speed program as an installable phone app. Daily sessions, set-by-set logging with a rest timer, best-so-far and estimated 1RMs, a competition-set clock for speed days, ball-speed and bodyweight charts, and a calendar file that does the reminding.

Everything runs in the browser and saves on the phone. No account, no server, works offline once opened.

## Files

| File | What it is |
|---|---|
| `index.html` | The whole app |
| `sw.js` | Service worker — makes it work offline and picks up updates |
| `manifest.webmanifest` | Lets Chrome install it as an app |
| `icons/` | App icons |
| `project-225.ics` | Calendar with every session, weeks 0–13, at the default times (11:30 weekdays, Sat range 11:00, Sat gym 5 pm) |

## Put it online (one time, ~3 minutes)

1. Sign in at github.com → **+** (top right) → **New repository**. Name it `project-225`, keep it **Public** (GitHub only serves free pages from public repos), leave everything else unticked → **Create repository**.
2. On the empty-repo page, click **uploading an existing file**. Drag in `index.html`, `sw.js`, `manifest.webmanifest`, `project-225.ics`, `README.md` **and the `icons` folder** (drag the folder itself so the files land in `icons/`). Click **Commit changes**.
3. In the repo: **Settings → Pages**. Under *Build and deployment* set Source to **Deploy from a branch**, Branch to **main** and folder **/ (root)** → **Save**.
4. Wait about a minute, then open `https://<your-username>.github.io/project-225/`. That URL is the app.

## Install it on the phone

1. Open the URL in **Chrome** on the phone.
2. Tap **⋮ → Add to Home screen** (or **Install app** if Chrome offers it) → **Install**.
3. Open it from the home screen. It runs full-screen and works without signal after the first load.

## Reminders (Google Calendar)

1. In the app: **More → Session times** — set the times you actually train, then **Download calendar (.ics)**. (The `project-225.ics` in this folder is the same thing at the default times.)
2. Open the downloaded file with **Google Calendar** on the phone (Files app → tap it → Calendar), or on a computer at calendar.google.com → ⚙ **Settings → Import & export → Import**.
3. Every session lands with two alarms (30 and 15 minutes before by default), plus a daily weigh-in, the Sunday review, and a nudge the day before each deload week.

Change a time later → download again → import again. Events carry stable IDs, so re-importing updates them instead of duplicating.

## Daily use

- **Today** shows the day's sessions in order. Tap **Start** to enter one.
- Gym sessions go exercise by exercise. Each set has weight and reps pre-filled from last time (or from your estimated 1RM on the main lifts); tap the check to log it and the rest timer starts. **Best so far** and **Beat it** show what to beat.
- Speed days have the protocol as a checklist and a **competition set clock**: start the 2:45, type each ball speed as the radar reads it, mark in-grid balls, **Save set**. Peak and top-3 are calculated and logged when you finish.
- Weigh in from the box at the bottom of Today. The Sunday **review card** (also on the Log tab) tells you whether to adjust calories.
- **Log** has the charts, the maxes table, and manual entry for anything logged outside a session.

## Backups and sending logs

**More → Export backup** saves a JSON file; **Share…** sends it straight to Google Drive. Do this at each retest (weeks 4, 8, 12) so the next block can be written from real numbers, and before switching phones. **Import** restores it.

## Updating the app

When a new version is ready, upload the changed files to the repo the same way (drag and drop onto the repo page → **Commit changes**). The installed app notices within a minute of being opened and shows a **Reload** banner. Your logs are untouched — they live on the phone, not in the repo.

## Native Android app (later)

The plan is to wrap this same page in a native shell (Capacitor) built by GitHub Actions, which adds proper scheduled notifications. When we get there, a workflow file goes in this repo, GitHub builds the APK, and you download it from the **Actions** tab and install it directly. Until then the calendar reminders do the job.
