# BREATHE Lab website — setup guide for GitHub Pages

This folder is a complete, static lab website. No build step, no frameworks: just
`index.html`, `style.css` and an `images/` folder. GitHub Pages will serve it as-is.

## What's in here

| File | Purpose |
|---|---|
| `index.html` | All five tabs (Home, Research, Lab Members, Publications, Contact) in one file. Edit the text directly. |
| `style.css` | Colours, fonts, layout. Change `--accent` at the top to re-theme. |
| `images/` | Put photos here. `placeholder-person.svg` is the grey avatar used for team members. |
| `README.md` | This file. |

---

## Step-by-step: put it on GitHub Pages

### Option A — Lab site at `https://<username>.github.io` (user site)

1. **Create a GitHub account** (or use your existing one). An organisation account
   (e.g. `breathe-lab`) is a good idea if several people will maintain the site.

2. **Create a new repository.** Click **New repository** and name it exactly
   `<username>.github.io` (e.g. `breathe-lab.github.io`). Make it **Public**.
   Don't add a README or .gitignore — leave it empty.

3. **Upload the files.** Either
   - on the repo page click **Add file → Upload files**, drag in `index.html`,
     `style.css` and the `images/` folder, and click **Commit changes**; or
   - from a terminal:
     ```bash
     cd breathe-lab-website
     git init
     git add .
     git commit -m "Initial lab website"
     git branch -M main
     git remote add origin https://github.com/<username>/<username>.github.io.git
     git push -u origin main
     ```

4. **Enable Pages.** Go to **Settings → Pages**. Under *Build and deployment*, set
   Source to **Deploy from a branch**, branch **main**, folder **/ (root)**. Save.

5. **Wait a minute or two**, then open `https://<username>.github.io`. The site is live.
   Every later push to `main` redeploys automatically.

### Option B — Site at `https://<username>.github.io/breathe-lab` (project site)

Same as above, but name the repository anything you like (e.g. `breathe-lab`).
The site will appear at `https://<username>.github.io/breathe-lab/`.
Nothing in the template needs changing because all paths are relative.

---

## Editing the site

- **Text:** open `index.html` in any text editor. Each tab is a `<section id="...">`
  block clearly labelled with a comment (`<!-- RESEARCH -->` etc.).
- **Add a team member:** copy one `<div class="person"> … </div>` block in the
  Lab Members section, change the name, role and image path.
- **Add a publication:** copy one `<li> … </li>` block in the Publications section.
- **Photos:** drop files into `images/` and reference them as `images/filename.jpg`.
  Keep them under ~500 KB each so the page loads fast.
- **Colours:** edit the `:root` variables at the top of `style.css`.
- **Preview locally:** just double-click `index.html` to open it in a browser.

## Optional next steps

- **Custom domain** (e.g. `breathelab.org`): Settings → Pages → Custom domain, then add
  a CNAME record at your domain registrar pointing to `<username>.github.io`.
- **Automatic publication list:** replace the hand-written list with an ORCID or
  Google Scholar link, or generate it from a BibTeX file with a small script.
- **Separate pages instead of tabs:** if the site grows, split each section into its own
  file (`research.html`, `members.html`, …) and change the nav links accordingly.
- **Jekyll:** GitHub Pages supports Jekyll natively if you later want templates, blog
  posts and Markdown content. Themes like *Minimal Mistakes* or *al-folio* are popular
  with academic labs.

## Institutional note

Check QMUL's web and branding guidance before publishing: some institutions require an
official university page as the canonical lab site, with an external site clearly
marked as independent. Avoid using the QMUL logo unless you have permission.
