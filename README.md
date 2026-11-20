# Dr. J. H. Jensha Haennah – Profile Website

A single-page academic profile with downloadable biodata. It runs on GitHub Pages with no server.

Live site: https://kings-326royal.github.io/Jensha-website/

This site uses the same design and features as the King website (`kings-326royal/king-website`), but it is a **separate site** with its own records, settings and download key. See *Kept separate from the King website* below.

| File | What it is |
| --- | --- |
| `index.html` | The website: profile, statistics, all records, download box and the editor |
| `data.js` | All the records (publications, patents, grants and so on). The site reads this file. |
| `metrics.js` | Citation figures, refreshed automatically (do not edit by hand) |
| `scripts/update_metrics.py` | Fetches the citation figures |
| `.github/workflows/update-metrics.yml` | Runs the fetcher on GitHub every week |
| `.github/workflows/static.yml` | Publishes the site to GitHub Pages on every push |
| `.nojekyll` | Tells GitHub Pages to serve the files as they are |

## What visitors can do

- See the headline statistics and three charts: publications by type, journal papers by indexing, and publications per year.
- Read every section that has records (experience, publications, patents, grants, service, training and so on). Empty sections are hidden from visitors; they appear in edit mode so you can add to them.
- Pick a **Document** and a **File type**. Only the owner (and visitors the owner approves) can download; see *Download requests* below.

| Document | File types |
| --- | --- |
| One-page infographic (colour) | PDF, PNG image, Word |
| One-page summary (professional) | PDF, Word |
| Standard resume (2–3 pages) | PDF, Word |
| Full biodata (every record, nothing omitted) | PDF, Word |

- Press **Show preview** to see the document on the page. Everyone can preview.

The files are built in the browser from `data.js`, so they always match the website.

## Put it on GitHub Pages (one time)

1. Push this folder to `kings-326royal/Jensha-website` (already the `origin` remote).
2. On GitHub, open the repository and go to **Settings → Pages**. Under **Build and deployment → Source**, choose **GitHub Actions**. The included `static.yml` workflow then publishes the site on every push.
3. Go to **Settings → Actions → General → Workflow permissions**, choose **Read and write permissions** and save. The weekly citation job needs this to save `metrics.js`.
4. After about a minute the site is live at https://kings-326royal.github.io/Jensha-website/

## Kept separate from the King website

Both sites live under `kings-326royal.github.io`, so a browser treats them as the same site and shares their saved data. To keep them apart, this site stores everything under its own names (`jh-…`), while the King website uses `gk-…`:

- Unpublished edits (drafts) made on one site never show up on the other.
- **GitHub settings** (repository and token) are saved separately. Enter `kings-326royal/Jensha-website` here; the King website keeps its own.
- **Download access** uses a separate key. Set up this site's key on its own; the key file is saved as `jensha-biodata-owner-key.json`.
- Download requests go to **jenshahaennah@gmail.com** (the first email in the profile), not to the King website's address.

## Download requests

Visitors can choose and preview any document, but get **Request download** instead of **Download**. They enter their name, email and an optional purpose, and the request is emailed through [FormSubmit](https://formsubmit.co) (free, no account). It goes to **Email for download requests** in **Edit profile details**, or to the first email if that is blank.

**One-time setup**

1. On your own computer, sign in at https://kings-326royal.github.io/Jensha-website/#edit (see *Who can edit*), open **Download access** and click **Set up this device**. Then click **Publish to GitHub**. From now on this browser downloads everything without a request.
2. Click **Save key file** and keep the file somewhere private. To use another computer or phone, open **Download access** there and choose **Import key file**.
3. Send a test request from a private window. The first time, FormSubmit emails an **Activate** link to jenshahaennah@gmail.com; click it, or no requests will arrive.

**Approving a request**

Open the link in the request email on the set-up device. The download box shows who asked and for what. Click **Approve and email the link**: your email app opens a reply containing a download link for that document, valid for 30 days. **Approve and copy the link** copies it instead. To decline, simply do not approve.

If you click **Create a new key**, links approved earlier stop working.

This is a static site, so the records themselves are visible on the page to everyone. The request step controls the ready-made downloads, not the data, and a technically skilled person could get around it.

## Who can edit

Visitors cannot edit. The **Update records** button is hidden from them, and opening the editor asks for a GitHub sign-in. Only someone whose GitHub access token has **write access to `kings-326royal/Jensha-website`** gets in: you, or a person you add on GitHub under **Settings → Collaborators** with the **Write** role (they create their own token).

The sign-in guards the editor, unpublished drafts and the **Download access** setup. The published records were never at risk: changing the live site has always needed write access to the repository.

### Sign in on your device (once per device)

1. Create a GitHub access token:
   1. On GitHub, open **Settings → Developer settings → Personal access tokens → Fine-grained tokens → Generate new token**.
   2. Under **Repository access**, choose **Only select repositories** and pick `Jensha-website`.
   3. Under **Permissions → Repository permissions**, set **Contents** to **Read and write**.
   4. Generate the token and copy it. It starts with `github_pat_`.
2. Open https://kings-326royal.github.io/Jensha-website/#edit, paste the token and click **Sign in**. The site asks GitHub whether the token's account can write to the repository, and opens the editor only if it can.
3. From then on, **Update records** appears at the bottom of the page on that device. If the token is deleted or expires, the device is signed out the next time the editor opens.

The token is kept only in that browser. Click **Sign out** in the editor before leaving a shared computer, and delete the token on GitHub if a device is lost.

## Update the records later

On a signed-in device, click **Update records** at the bottom of the page (or open https://kings-326royal.github.io/Jensha-website/#edit). The editor appears in the left column.

- **Edit mode** adds **+ Add** to every section and **Edit / ↑ / ↓ / Delete** to every record. Sections that are empty for visitors (for example Awards, Memberships, Administrative responsibilities) appear here.
- Tick **Show in resume and summary** on the records that should appear in the standard resume and one-page summary. The full biodata always includes everything.
- **Edit profile details** (in the About section) holds the photo, citations, h-index, areas of expertise, key contributions and the mission statement shown on the infographic. Choose a photo there; it is cropped to a square and stored inside `data.js`.
- In a citation, put text between `*single stars*` for italics (journal names) or `**double stars**` for bold.
- Edits are kept in this browser until you publish them. Visitors see nothing until you publish.

Then publish in one of three ways.

### Option A: one click (recommended)

Click **Publish to GitHub**. Signing in already filled in **GitHub settings** (repository `kings-326royal/Jensha-website`, branch `main`, file `data.js` and your token), so the changes go straight to the repository and the live site updates within about a minute.

### Option B: upload the file

Click **Download data.js** in the editor. On GitHub, open the repository, click **Add file → Upload files**, drop in the new `data.js` (it replaces the old one) and commit.

### Option C: edit by hand

`data.js` is plain JSON after `window.CV_DATA =`. You can open it on GitHub, click the pencil icon, edit, and commit.

## How the statistics stay exact

Every figure at the top of the page is counted from the records each time the page loads:

- Add a journal paper and "Journal publications" and "Total publications" go up by one.
- Add a grant and "Total funding received" adds that exact amount. You can type the amount as `1000000`, `10,00,000` or `10 lakh`.
- Years of experience is the current year minus the career start year in the profile (2021, the start of full-time Ph.D. research; change it in **Edit profile details** to count teaching only).

The same figures are used in all four downloads, so the files always agree with the website.

## Automatic citation figures (Google Scholar, Scopus, Web of Science)

`scripts/update_metrics.py` reads the IDs from `data.js`, fetches the latest figures and writes `metrics.js`. The website shows citations, h-index, i10-index, documents, citations per year and the most cited papers from that file.

GitHub runs it through `.github/workflows/update-metrics.yml`:

- every Monday at 08:00 IST,
- whenever `data.js` changes (for example after you publish an edit), and
- whenever you press **Actions → Update citation metrics → Run workflow** on GitHub.

| Source | What you need |
| --- | --- |
| Google Scholar | Profile `6huflbcAAAAJ` is set (https://scholar.google.com/citations?user=6huflbcAAAAJ). Refreshed from your Mac; see below. |
| Scopus | Author ID 57189850005 is set. Add a free API key from https://dev.elsevier.com ("I want an API key") under **Settings → Secrets and variables → Actions → New repository secret**, named `SCOPUS_API_KEY`. |
| Web of Science | Researcher ID AAT-4668-2021 is set. Add a free "Web of Science Starter API" key from https://developer.clarivate.com as a repository secret named `WOS_API_KEY`. |

Until a source is connected, it shows "Not connected yet" on the website. If a fetch fails, the site keeps the previous figures. The manual citation and h-index values in **Edit profile details** are used only if no source has ever returned figures.

The page uses the first available source for the headline citation and h-index tiles, in this order: Google Scholar, Scopus, Web of Science.

### Google Scholar is refreshed from your Mac

Google Scholar refuses requests from GitHub's servers (the weekly GitHub job gets "HTTP 403" and keeps the previous figures), so the Scholar figures are fetched from your Mac by `~/Library/Application Support/ProfileSites/update-scholar-metrics.sh`. It refreshes both profile sites (King and Jensha) and pushes `metrics.js` only when a figure has changed; the live site updates about a minute later.

- Refresh now: `bash ~/Library/Application\ Support/ProfileSites/update-scholar-metrics.sh`
- Daily refresh (09:30, or when the Mac next wakes up): load `~/Library/LaunchAgents/com.kings326royal.scholar-metrics.plist` with `launchctl bootstrap gui/$(id -u) ~/Library/LaunchAgents/com.kings326royal.scholar-metrics.plist`
- Stop the daily refresh: `launchctl bootout gui/$(id -u)/com.kings326royal.scholar-metrics`, then delete the plist file.
- Log of each run: `~/Library/Application Support/ProfileSites/update.log`

The Mac must be switched on (asleep is fine). The weekly GitHub job still handles Scopus and Web of Science once their API keys are added.

## Notes

- PDFs show the rupee sign as "Rs." because the built-in PDF font has no ₹ character. Word files keep ₹.
- The infographic is a picture of the page, so its text cannot be selected in the PDF or Word file. Use the one-page summary when text must be copyable.
- The page loads fonts and four small libraries (JSZip, jsPDF, jsPDF-AutoTable, html2canvas) from public CDNs, so downloads need an internet connection.
- To look at the site on your computer before uploading, double-click `index.html`. Everything works locally except **Publish to GitHub**, which also works locally once the token is set.
