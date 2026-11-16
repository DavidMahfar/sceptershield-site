# Scepter and Shield LLC website

This folder is the complete website for sceptershield.com. It is plain HTML and CSS: there is nothing to install or build. Whatever is in this folder is what gets published.

## What is in the folder

| File or folder | What it is |
| --- | --- |
| `index.html` | Home page |
| `government/index.html` | Government Contracting page |
| `products/index.html` | Products page |
| `contact/index.html` | Contact page ("Request a quote") |
| `privacy/index.html` | Privacy page |
| `404.html` | "Page not found" page |
| `assets/styles.css` | The one stylesheet every page uses |
| `assets/favicon.svg`, `assets/apple-touch-icon.png`, `favicon.ico` | Temporary browser icon (navy square, gold "S") |
| `sitemap.xml`, `robots.txt` | Files for search engines |
| `_headers` | Security settings read by Cloudflare Pages (other hosts ignore it) |
| `.nojekyll` | Empty file that tells GitHub Pages to publish the folder exactly as it is |

The site uses no JavaScript, no cookies, no analytics, and loads nothing from other websites.

## Preview the site on your own computer

1. Open the **Terminal** app.
2. Type `cd ` (with a space after it), drag this folder onto the Terminal window, and press Return.
3. Run:

   ```bash
   python3 -m http.server 8000
   ```

4. Open <http://localhost:8000> in a browser.
5. To stop the preview, go back to Terminal and press Control+C.

Double-clicking `index.html` also opens the home page, but links between pages will not behave the way they do on the real site. Use the steps above to see it properly.

## Editing the files

Open the files in a plain-text code editor such as Visual Studio Code. Avoid Word, Pages, or TextEdit in its default mode, because they change the file format.

Every item that is waiting to be switched on is marked with the words `TODO-ACTIVATE:`. Use your editor's "find in all files" search for `TODO-ACTIVATE` to see them all.

## Switching on the items that are not ready yet

None of these appear on the site today. Switch each one on only when it is true.

| Item | Where | What to do |
| --- | --- | --- |
| Logo | `assets/styles.css` | Change one line |
| Favicon | `assets/` and the top folder | Replace three image files |
| CAGE code | `government/index.html` and `index.html` | Fill in the code, delete two marker lines in each file |
| SAM status | `government/index.html` | Delete two marker lines |
| Capability statement | `government/index.html` | Add the PDF, delete two marker lines |
| Certifications | `government/index.html` | Fill in the names, delete two marker lines |

In the HTML pages, each held-back item sits between two marker lines that look like this:

```
<!-- TODO-ACTIVATE: SAM STATUS. To switch on ... delete this line and the END line below.
  ...the hidden content...
END TODO-ACTIVATE: SAM STATUS -->
```

Deleting the first and the last of those lines (and nothing in between) makes the content appear.

### Logo

The header currently shows the company name as text.

1. Save the horizontal logo as `assets/logo-horizontal.svg`. It sits on the navy header, so it needs light (white or gold) artwork with a transparent background. Save the square logo as `assets/logo.svg` so it is on hand for other uses.
2. Open `assets/styles.css` and search for `TODO-ACTIVATE: LOGO`.
3. Just below the instructions, change the line `@media not all {` to `@media all {`.

That one change swaps the text for the logo on every page. If the logo looks too small or too large, adjust the `width` and `height` values on the lines just below. To use a different file name, change `logo-horizontal.svg` on the `background` line.

### Favicon

The favicon is the small icon in the browser tab. To replace the temporary one, save your real icon over these three files, keeping the same names:

- `assets/favicon.svg` (square)
- `assets/apple-touch-icon.png` (180 × 180 pixels)
- `favicon.ico` in the top folder (32 × 32 pixels)

No page needs editing.

### CAGE code

Two places:

1. `government/index.html`: search for `TODO-ACTIVATE: CAGE CODE (company data table)`. Replace `XXXXX` with the code, then delete the marker line above the row and the `END TODO-ACTIVATE` line below it.
2. `index.html`: search for `TODO-ACTIVATE: CAGE CODE (home page strip)` and do the same.

### SAM status

Only do this once SAM.gov shows the registration as active.

In `government/index.html`, search for `TODO-ACTIVATE: SAM STATUS` and delete the marker line above the row and the `END TODO-ACTIVATE` line below it. A row reading "SAM.gov registration: Active" appears in the Company data table.

### Capability statement

1. Save the PDF as `assets/capability-statement.pdf`.
2. In `government/index.html`, search for `TODO-ACTIVATE: CAPABILITY STATEMENT` and delete the two marker lines. A "Download capability statement (PDF)" button appears next to "Request a quote".

### Certifications

In `government/index.html`, search for `TODO-ACTIVATE: CERTIFICATIONS`.

1. Replace each `CERTIFICATION NAME` line with a certification the company actually holds. Add or remove `<li>...</li>` lines as needed.
2. Delete the two marker lines. A "Certifications" section appears after "Compliance".

## Changing the contact details

The contact details are repeated on several pages. The reliable way to change one is your editor's "replace in all files" command, using these exact pieces of text:

| To change | Search for | Appears in |
| --- | --- | --- |
| Email address | `admin@sceptershield.com` | Every page (footer), plus the Government Contracting, Contact, and Privacy pages and the hidden company data on the home page |
| Phone number as shown | `(917) 745-6057` | Government Contracting and Contact pages |
| Phone number in the tap-to-call link | `+19177456057` | Government Contracting and Contact pages |
| Phone number in the hidden company data | `+1-917-745-6057` | `index.html` |
| Contact name | `David Mahfar` | Government Contracting and Contact pages |
| Contact title | `<dd>Manager</dd>` | Government Contracting and Contact pages. Also edit the description line near the top of `contact/index.html` |

Change all three phone formats together so the number people see matches the number their phone dials.

The "Email a quote request" button on the Contact page is the long link beginning `mailto:` in `contact/index.html`. Replacing the email address everywhere updates it too.

Do not add a street address. The site deliberately shows only "Boston, Massachusetts".

## Publishing

> **Warning: do not change or delete the domain's email records.**
> The business email runs on Google Workspace and depends on DNS records that already exist at Squarespace Domains: the **MX** records, and the **TXT** and **CNAME** records used for email (SPF, DKIM such as `google._domainkey`, DMARC such as `_dmarc`, and any Google verification record). Changing or deleting any of them can stop email from arriving or being delivered. When publishing the website you only ever add or change the website records listed below: **A**, **AAAA**, and **CNAME** records for `@` and `www`. If a step seems to ask you to touch an MX or email TXT record, stop.

Before you start, take a screenshot of the current DNS records at Squarespace so you have a copy of how they looked.

To reach the DNS records: sign in at <https://account.squarespace.com/domains>, click `sceptershield.com`, then click **DNS**. Squarespace changes its screens from time to time, so the button names may differ slightly from what is written here.

Two hosting options follow. Both are free for a site like this. Pick one.

- **GitHub Pages (Option B)** can serve the site at `https://sceptershield.com` with the DNS staying at Squarespace. It is the simpler fit for this site.
- **Cloudflare Pages (Option A)** can serve `www.sceptershield.com` with the DNS staying at Squarespace. It can serve the bare `sceptershield.com` only if the whole domain's DNS is moved to Cloudflare, which is a bigger change that involves the email records.

### Option A: Cloudflare Pages

**1. Make a clean copy of the site to upload.** In Terminal, from this folder:

```bash
git archive --format=zip -o ../sceptershield-site.zip HEAD
```

This creates `sceptershield-site.zip` next to this folder, containing the committed site without this README. (Commit any edits first, or they will not be in the zip.)

**2. Create the project.**

1. Create a free account at <https://dash.cloudflare.com>.
2. Go to **Workers & Pages**, then **Create application**, and choose the option to **drag and drop your files** (under Pages).
3. Name the project, for example `sceptershield`.
4. Drag `sceptershield-site.zip` into the upload area and select **Deploy site**.
5. Open the address Cloudflare gives you (it looks like `sceptershield.pages.dev`) and check every page.

**3. Connect `www.sceptershield.com`.** Do these in this order:

1. In the Cloudflare project, open **Custom domains**, select **Set up a domain**, enter `www.sceptershield.com`, and continue.
2. At Squarespace, in the DNS screen, add this record:

   | Type | Name | Data |
   | --- | --- | --- |
   | CNAME | `www` | `sceptershield.pages.dev` (use your own project's address) |

   If a CNAME for `www` already exists (Squarespace adds a default one), edit that record instead of adding a second.
3. Wait for Cloudflare to show the domain as active. This can take from a few minutes to a few hours.

**4. Decide what the bare domain does.** Visitors who type `sceptershield.com` without `www` need to land on the site too. There are two ways:

- **Keep DNS at Squarespace (smaller change).** Use Squarespace's domain forwarding to send `sceptershield.com` to `https://www.sceptershield.com`. Forwarding affects web visits only. Then tell search engines the site lives at `www`: use "replace in all files" to change `https://sceptershield.com/` to `https://www.sceptershield.com/` (it appears in the five main pages, `sitemap.xml`, and `robots.txt`), and upload again.
- **Move the DNS to Cloudflare (bigger change).** Cloudflare can then serve `sceptershield.com` directly. This means changing the domain's nameservers at Squarespace, after which *all* DNS records, including the email records, are managed at Cloudflare. Cloudflare copies the existing records when you add the domain, but before you switch nameservers you must compare its list against your Squarespace screenshot and confirm every MX, TXT, and CNAME record for email is present and identical. Do not take this route unless you are comfortable doing that check.

**To update the site later:** make a new zip (step 1), open the project in Cloudflare, choose **Create deployment**, and upload it.

### Option B: GitHub Pages

**1. Put the site on GitHub.**

1. Create a free account at <https://github.com>.
2. Create a new repository, for example `sceptershield-site`. On a free account the repository must be **Public** for GitHub Pages to work. Everything in this folder, including this README, will then be publicly readable on github.com. It contains nothing private.
3. Upload the site. In Terminal, from this folder (replace `USERNAME` with your GitHub username):

   ```bash
   git remote add origin https://github.com/USERNAME/sceptershield-site.git
   ```

   ```bash
   git push -u origin main
   ```

**2. Turn on GitHub Pages.**

1. In the repository, go to **Settings**, then **Pages**.
2. Under **Build and deployment**, set **Source** to **Deploy from a branch**, choose the `main` branch and the `/ (root)` folder, and save.
3. After a minute or two, GitHub shows an address like `https://USERNAME.github.io/sceptershield-site/`. Open it and check every page.

**3. Tell GitHub the domain. Do this before changing DNS.**

On the same **Pages** screen, under **Custom domain**, enter `sceptershield.com` and save. GitHub adds a small file named `CNAME` to the repository. Leave it there.

**4. Add the DNS records at Squarespace.**

Squarespace may already have default **A** and **CNAME** records for `@` and `www` that point to Squarespace's own parking page. Those website records need to be removed or edited so they do not compete with the ones below. Do not remove anything else.

| Type | Name | Data |
| --- | --- | --- |
| A | `@` | `185.199.108.153` |
| A | `@` | `185.199.109.153` |
| A | `@` | `185.199.110.153` |
| A | `@` | `185.199.111.153` |
| CNAME | `www` | `USERNAME.github.io` (your GitHub username, no repository name) |

Optional, for visitors on newer (IPv6) networks:

| Type | Name | Data |
| --- | --- | --- |
| AAAA | `@` | `2606:50c0:8000::153` |
| AAAA | `@` | `2606:50c0:8001::153` |
| AAAA | `@` | `2606:50c0:8002::153` |
| AAAA | `@` | `2606:50c0:8003::153` |

`@` means the bare domain, `sceptershield.com`. With these records GitHub serves the site at `https://sceptershield.com` and sends `www.sceptershield.com` visitors there automatically.

These addresses were taken from GitHub's documentation in November 2026. Check them against GitHub's "Managing a custom domain for your GitHub Pages site" help page before entering them.

**5. Turn on HTTPS.** Back on the **Pages** screen, wait until the domain check passes, then tick **Enforce HTTPS**. It can take up to 24 hours before the box can be ticked.

**To update the site later:** commit your changes, then run `git push`.

### After publishing, on either host

- Open every page at the real address and click the email and phone links.
- Send a test email to and from the business address to confirm email still works.
- If the site is at `https://sceptershield.com`, the sitemap is at `https://sceptershield.com/sitemap.xml`. You can submit it in Google Search Console if you want the site indexed sooner.

## Keeping the site accurate

The site is written to state only what is true today. When editing, keep it that way: no past performance, customers, certifications, set-aside statuses, delivery promises, or government seals and imagery until they are real and you are entitled to show them. The footer line saying the company is not affiliated with or endorsed by any government agency should stay on every page.
