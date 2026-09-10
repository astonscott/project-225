# Project 225

Long drive Phase 1 — a 12-week mass-and-speed program as an installable phone app. Daily sessions, set-by-set logging with a rest timer, best-so-far and estimated 1RMs, a competition-set clock for speed days, ball-speed and bodyweight charts, and a calendar file that does the reminding.

Everything runs in the browser and saves on the phone. No account, no server, works offline once opened.

## Files

| File | What it is |
|---|---|
| `index.html` | The whole app |
| `sw.js` | Service worker — makes it work offline and picks up updates |
| `manifest.webmanifest` | Lets Chrome install it as an app |
| `icon-192.png`, `icon-512.png`, `icon-maskable-512.png` | App icons (kept at the root so drag-and-drop uploads stay flat) |
| `project-225.ics` | Starter calendar. Generate the current one from the app (**More → Download calendar**) so it carries your times and the daily 8 AM plan alerts. |

## Put it online (one time, ~3 minutes)

1. Sign in at github.com → **+** (top right) → **New repository**. Name it `project-225`, keep it **Public** (GitHub only serves free pages from public repos), leave everything else unticked → **Create repository**.
2. On the empty-repo page, click **uploading an existing file**. Drag in every file from the unzipped folder — `index.html`, `sw.js`, `manifest.webmanifest`, `project-225.ics`, `README.md` and the three `icon-*.png` files. Click **Commit changes**.
3. In the repo: **Settings → Pages**. Under *Build and deployment* set Source to **Deploy from a branch**, Branch to **main** and folder **/ (root)** → **Save**.
4. Wait about a minute, then open `https://<your-username>.github.io/project-225/`. That URL is the app.

## Install it on the phone

1. Open the URL in **Chrome** on the phone.
2. Tap **⋮ → Add to Home screen** (or **Install app** if Chrome offers it) → **Install**.
3. Open it from the home screen. It runs full-screen and works without signal after the first load.

## Reminders (Google Calendar)

1. In the app: **More → Session times** — set the times you actually train and the **Morning plan alert** time, then **Download calendar (.ics)**. Always generate it from the app; the `project-225.ics` committed here is only an early starter file and will lag behind.
2. Open the downloaded file with **Google Calendar** on the phone (Files app → tap it → Calendar), or on a computer at calendar.google.com → ⚙ **Settings → Import & export → Import**.
3. You get a **daily 8 AM alert naming that day's work** ("P225 · Max hit day + Upper hypertrophy") with the session times and your daily targets in the description. Every session also lands with two alarms (30 and 15 minutes before by default), plus a daily weigh-in, the Sunday review, and a nudge the day before each deload week.
4. Change the 8 AM time in **More → Session times → Morning plan alert**.

Change a time later → download again → import again. Events carry stable IDs, so re-importing updates them instead of duplicating.

## Daily use

- **Today** shows the day's sessions in order. Tap **Start** to enter one.
- Gym sessions go exercise by exercise. Each set has weight and reps pre-filled from last time (or from your estimated 1RM on the main lifts); tap the check to log it and the rest timer starts. **Best so far** and **Beat it** show what to beat.
- Speed days have the protocol as a checklist and a **competition set clock**: start the 2:45, type each ball speed as the radar reads it, mark in-grid balls, **Save set**. Peak and top-3 are calculated and logged when you finish.
- **Every day** on Today: a checklist for morning weight, creatine, calories, protein, water, mobility and sleep. Tap the box to tick it, or type the number — calories/protein/sleep tick themselves once you're within 5% of target, and habits build a streak.
- Targets live in **More → Daily targets** (adjust calories ±200 every second Sunday).
- The Sunday **review card** (also on the Log tab) reads your weight, speed, calories and sleep together and tells you which one to fix.
- **Log** has the charts — toggle **Ball speed / Club speed / Smash**, each with your sessions and a 3-session rolling average — plus the maxes table and manual entry.

## Backups and sending logs

**More → Export backup** saves a JSON file; **Share…** sends it straight to Google Drive. Do this at each retest (weeks 4, 8, 12) so the next block can be written from real numbers, and before switching phones. **Import** restores it.

## Updating the app

When a new version is ready, upload the changed files to the repo the same way (drag and drop onto the repo page → **Commit changes**). The installed app notices within a minute of being opened and shows a **Reload** banner. Your logs are untouched — they live on the phone, not in the repo.

## Why reminders come from Calendar, not the app

A web app cannot schedule a notification for a future time — Chrome never shipped the API for it (`Notification.prototype.showTrigger` is absent), and service workers are killed when idle, so no timer survives. Calendar is the reliable path until the app is wrapped natively.

## Native Android app (later)

The plan is to wrap this same page in a native shell (Capacitor) built by GitHub Actions, which adds proper scheduled notifications at exact times, offline, surviving reboots. When we get there, a workflow file goes in this repo, GitHub builds the APK, and you download it from the **Actions** tab and install it directly. Until then the calendar reminders do the job.
