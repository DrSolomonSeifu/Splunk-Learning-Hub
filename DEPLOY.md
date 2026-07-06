# Deploying the Splunk Learning Hub (for the instructor / maintainer)

This guide is for whoever publishes and maintains the hub. Learners do not need
it — they only need the app link (see `README.md`).

## What is included

```
index.html              ← the hub application (open this / start_url)
manifest.json           ← PWA manifest (name, icons, theme)
service-worker.js       ← offline caching of visited pages
.nojekyll               ← tells GitHub Pages to serve files as-is
icons/
  icon-192.png
  icon-512.png
  icon-maskable-512.png
  apple-touch-icon.png
  favicon-32.png
```

## Required: place the portal files next to index.html

The hub links to the lesson and lab portals by relative path, so all of these
must sit in the **same folder** as `index.html`:

```
student_guide_200_1.html
student_guide_200_2.html
student_guide_200_3.html
student_guide_200_4_5.html
student_guide_200_6.html
student_guide_200_7_8.html
splunk_lab_portal.html
```

This is a learner-only build: it ships the seven learner guides plus the labs
portal, and no instructor guides. (Lessons 4 & 5 share one portal; Lessons 7 & 8
share one portal — that is why those two files each serve two lesson cards.)

## Deploy to GitHub Pages

1. Create a repository (for example `Splunk-Learning-Hub`) and add every file
   above, keeping the folder structure.
2. In the repo, go to **Settings → Pages**, set **Source** to *Deploy from a
   branch*, choose `main` and `/ (root)`, and save.
3. Open the published URL. On Chrome or Edge, use **Install app** in the top
   bar. On iPhone, tap **Share → Add to Home Screen**.

The service worker and installability require HTTPS, which GitHub Pages
provides automatically.

Once the site is live, copy the published URL into the **App link** line in
`README.md` so learners can open it directly.

## Maintenance notes

- Progress and bookmarks are stored on each learner's device only
  (browser `localStorage`) — nothing is uploaded anywhere.
- Web search opens results in a new tab, scoped to Splunk.
- To update a lesson later, replace its portal HTML file — no change to the
  hub is needed. To change lesson titles or descriptions shown on the cards,
  edit the `MODULES` array near the bottom of `index.html`.
- To add an instructor build later, ship the instructor guide files alongside
  and restore the per-card instructor links.

---

Designed & Authored by **Dr. Solomon Seifu** — Lead Technical Instructor
