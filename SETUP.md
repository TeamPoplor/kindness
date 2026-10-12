# The Pilgrimage of Kindness website: setup and care

## What's in this folder
| File | What it is |
|---|---|
| index.html | The whole website (words, colors, layout, and the live counter) |
| CNAME | Tells GitHub the site's address. Don't delete or rename it. |
| Pilgrimage-of-Kindness-2026-Letter.pdf | Printable board, U.S. Letter |
| Pilgrimage-of-Kindness-2026-A4.pdf | Printable board, A4 (most other countries) |
| board-front.webp, board-back.webp | Preview pictures of the board |
| logo-2026.webp, logo-2027.webp | The yearly logos |
| world.svg, usa.svg, canada.svg | The maps that fill in as people log their kindness |
| favicon.png | The little icon in the browser tab |
| signature.png | Tess and Rory's signature |
| share-image.jpg | The picture that shows when someone texts or posts the link |

---

## Part 1: Put the site on GitHub Pages
1. On github.com, create a new **public** repository (for example, `pilgrimage-of-kindness`).
2. Click **Add file → Upload files**. Drag in every file from this folder and click **Commit changes**.
3. Go to **Settings → Pages**. Under "Build and deployment," choose **Deploy from a branch**, branch **main**, folder **/ (root)**, then **Save**.
4. Still on the Pages screen, the **Custom domain** box should say `pilgrimageofkindness.org` (the CNAME file fills it in). If it's empty, type it in and click **Save**.

## Part 2: Point pilgrimageofkindness.org at GitHub (Squarespace)
1. Go to **account.squarespace.com/domains** and click **pilgrimageofkindness.org**.
2. Open **DNS** (DNS Settings).
3. If you see a **Squarespace Defaults** group of records, delete it with its trash icon. Those records point the domain at Squarespace and will fight with GitHub.
4. Under **Custom records**, add these five records:

| Host | Type | Data |
|---|---|---|
| @ | A | 185.199.108.153 |
| @ | A | 185.199.109.153 |
| @ | A | 185.199.110.153 |
| @ | A | 185.199.111.153 |
| www | CNAME | YOUR-GITHUB-USERNAME.github.io |

5. Wait. It can take anywhere from a few minutes to a day. When GitHub's Pages screen shows a green "DNS check successful," tick **Enforce HTTPS**. (If the box is greyed out, give it a few more hours; GitHub has to issue the security certificate first.)

**Recommended:** in your GitHub **account** settings (your profile picture → Settings → Pages), use **Add a domain** to *verify* pilgrimageofkindness.org. GitHub gives you one TXT record to add in Squarespace the same way as above. This stops anyone else from ever claiming the domain on GitHub.

## Part 3: Forward thepilgrimageofkindness.org to the main site
1. In **account.squarespace.com/domains**, click **thepilgrimageofkindness.org**.
2. Click **Website**, scroll to **Domain Forwarding Rules**, and click **Add rule**.
3. **Subdomain:** `@`. **Website URL:** `pilgrimageofkindness.org` (no https://).
4. Under **Advanced settings**, choose **Permanent Redirect (301)** and **Remove paths**. Make sure the **SSL** toggle is on. **Save**.
5. Add a second rule the same way, with **Subdomain** `www`, so www.thepilgrimageofkindness.org forwards too.
6. If Squarespace complains about conflicting records, delete that domain's existing A / CNAME records (this domain doesn't need any). Forwarding can take up to 48 hours.

## Part 4: Test the whole loop before launch
1. Visit pilgrimageofkindness.org and thepilgrimageofkindness.org. Both should land on the site with a padlock in the address bar.
2. Scan the QR code on a printed board with a phone. It should open the site.
3. Download both boards (Letter and A4) and open them.
4. Submit a test report through the form. Within a few minutes, the counter on the site should change.
5. Delete that test: in the Google Form, **Responses → Individual**, trash icon; then delete its row in the response sheet.

---

## Uploading an update
Drag the changed files onto **Add file → Upload files** and **Commit changes**. Files with the same name replace the old ones.

## Changing the site with Claude
The whole site is one plain file, `index.html`, so you can redesign it with Claude any time.

1. Start a chat with Claude, attach the **current** `index.html` from GitHub (open the file on GitHub → the download icon), and describe what you want: new colors, a new section, different wording, anything.
2. Ask Claude for the complete updated `index.html`. Look at it in your browser first (double-click the file) before uploading.
3. On GitHub, **Add file → Upload files**, drop in the new `index.html` (same name, it replaces the old one), and **Commit changes**. The live site updates in a minute or two.

**Golden rules**
- Always start from the version that's on GitHub, so nobody's changes get lost.
- Keep the file names the same, and never delete **CNAME**.
- Don't change the `COUNTER_CSV_URL` line near the bottom of index.html unless the counter sheet itself changes.
- Nothing is ever truly lost: GitHub keeps every version. Open a file → **History** to see or restore an older one.
- Quick color change: the site's colors are listed at the top of index.html under "SITE COLORS."

## In November: the Honor Roll and stories
In index.html, search for **Nine for Nine Honor Roll**. There are examples inside `<!-- -->` marks:
- **Honor Roll:** copy the `<li>...</li>` line for each name, *outside* the `<!-- -->` marks.
- **Seeds of good:** copy a whole `<div class="story">...</div>` block for each story, *outside* the `<!-- -->` marks.

The "coming soon" messages disappear by themselves once there's at least one name or story, and the ← → arrows appear by themselves once there are two or more stories. (Or ask Claude to add them for you.) Post only first names and last initials (or what the person asked for), and read every story before it goes up.

## How the counter and maps work (for reference)
The form's answers go to "The Pilgrimage of Kindness 2026 (Responses)." A separate sheet, "Kindness Counter," copies only the acts, country, state, and province columns (no names or stories), and its **Counter** tab is published to the web. The site reads row 1 of that tab:

| Cell | What it is |
|---|---|
| A1 | acts of kindness |
| B1 | pilgrims (people who logged at least one act) |
| C1 | full boards |
| D1 | countries reached |
| E1 | U.S. states reached (not shown on the site any more, but harmless) |
| F1 | list of countries, separated by \| (fills the world map) |
| G1 | list of U.S. states/territories (fills the U.S. map) |
| H1 | list of Canadian provinces/territories (fills the Canada map) |

**Lives touched** on the site = acts of kindness + pilgrims (every act touches a life, and so does doing them). Google refreshes the published sheet every few minutes.

**Removing or fixing a response:** the form and the response sheet each keep their own copy. Delete (or correct) the row in the **response sheet**, since that's what the website reads; delete it in the form too (Responses → Individual → trash) to keep the form tidy.

## Next year
Add the new logo (e.g., `logo-2027.webp`) and new board PDFs, then ask Claude to update the year, the logo, the downloads, and the "Pilgrimages through the years" section. Make a fresh form and counter sheet (or clear the old responses) so the new year starts at zero.
