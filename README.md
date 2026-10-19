# jonathan-silva.com — your new portfolio

Everything the site needs is in this folder:

| File | What it is |
|---|---|
| `index.html` | The whole website (one file). |
| `images/` | Your screenshots, maps, and portrait go here. |
| `resume.pdf` | *(you add this)* Drop your résumé here and a "Résumé" button appears automatically. |
| `CNAME`, `.nojekyll` | Tell GitHub Pages your domain and to serve files as-is. Leave them alone. |

---

## Step 1 — Images and media (done)

Your images were downloaded from Squarespace and converted to WebP in `images/`. Videos and audio from your T7 Shield drive are in `media/`, loudness-matched and compressed for the web. Re-upload the demo reel, *Lyram* gameplay, and *Almighty Aura* cutscene to YouTube (Unlisted) and add the links in Step 2.

## Step 2 — Add your links

Open `index.html` in a text editor (TextEdit in plain-text mode, or VS Code). Near the bottom find `const LINKS = {` and paste URLs between the quotes. Empty links keep their buttons hidden.

Pre-filtered links for applications: `jonathan-silva.com/#audio` · `#narrative` · `#systems` · `#level` · `#art`

## Step 3 — Publish to GitHub Pages

Your repo is **github.com/TomGanks/TomGanks.github.io** and this folder is its contents.

**First publish (Terminal):**
```
cd ~/Downloads/TomGanks.github.io
git init -b main
git add .
git commit -m "Portfolio site"
git remote add origin https://github.com/TomGanks/TomGanks.github.io.git
git push -u origin main
```
If Terminal asks for a password, GitHub needs a **token**, not your password: github.com → Settings → Developer settings → Personal access tokens → Tokens (classic) → Generate, tick **repo**, copy it, and paste it as the password.

Then on GitHub: repo **Settings → Pages** → Source **Deploy from a branch** → **main**, **/(root)** → Save. Live in a minute or two at **https://tomganks.github.io**.

**Later updates:**
```
cd ~/Downloads/TomGanks.github.io
git add . && git commit -m "Update" && git push
```

## Step 4 — Move the domain and point it at GitHub

GitHub doesn't sell domains, so the domain moves to a registrar. **Cloudflare** charges what the registry charges (about $10–11/yr for a .com), with no markup, and its free Email Routing makes **Me@Jonathan-Silva.com** work.

**A. Verify the domain with GitHub first** (stops anyone else from claiming it)
- Your profile picture → **Settings** → **Pages** → **Add a domain** → `jonathan-silva.com`. GitHub gives you a TXT record. Keep that tab open.

**B. Move DNS to Cloudflare**
1. dash.cloudflare.com → **Add a domain** → `jonathan-silva.com` → **Free** plan.
2. Cloudflare imports your current records. **Delete** the old Squarespace ones (A/CNAME records pointing at Squarespace). Keep any **MX** or email records.
3. Add these records with the cloud icon set to **grey (DNS only)**:

   | Type | Name | Value |
   |---|---|---|
   | A | @ | 185.199.108.153 |
   | A | @ | 185.199.109.153 |
   | A | @ | 185.199.110.153 |
   | A | @ | 185.199.111.153 |
   | CNAME | www | TomGanks.github.io |
   | TXT | (GitHub gives the name) | (GitHub gives the value) |

4. Cloudflare shows two nameservers. In Squarespace → Domains → jonathan-silva.com → **Nameservers** → use custom → paste them.
5. Wait until Cloudflare says **Active** (minutes to a few hours). Back on GitHub click **Verify**.

**C. Turn on the custom domain**
- Repo **Settings → Pages → Custom domain**: `www.jonathan-silva.com` → **Save** (the included `CNAME` file already says this). When the check passes, tick **Enforce HTTPS** (can take up to 24h).
- Both `jonathan-silva.com` and `www.jonathan-silva.com` now load the site.

**D. Transfer the registration**
1. Squarespace → Domains → jonathan-silva.com: Domain Lock **off** (done), turn off **DNSSEC** if it's on, click **Request transfer code**. It's emailed to you within 24h.
2. Cloudflare → **Domain Registration → Transfer Domains** → paste the code → pay.
3. Approve Squarespace's email, or wait about 5 days for auto-approval. Then click Cloudflare's verification email.

**E. Set up Me@Jonathan-Silva.com**
- Cloudflare → your domain → **Email → Email Routing** → create `me@jonathan-silva.com` → forward to your Gmail/Hotmail. Send a test email.

**F. Cancel the Squarespace website plan**, only after the site loads from GitHub and the transfer finishes.

---

## Making the portfolio stronger (from the research)

Recruiters skim first and hiring managers dig in. The site leads with who you are, puts the best work first, and tags each project by discipline. What's still missing is mostly **content only you have**:

- **Design notes on the featured projects.** For each one, add 2–4 sentences: the design goal, one problem and how you solved it, what you'd change. There's a `<!-- ADD -->` comment in each project marking the spot.
- **A demo reel, 2–3 minutes max**, with your strongest work in the first 30 seconds.
- **Audio:** say exactly what you did on each clip (ambience, Foley, UI, music…). Keep a **sound-only reel** separate from your **music**. Studios hiring a sound designer often want no music in the reel. If you used FMOD, Wwise, or did in-engine implementation, say so; it's a big plus.
- **Narrative:** 3 short, polished writing samples that show range (a dialogue scene, item/quest text, a lore excerpt). Plus at least one playable piece (a short Twine game works great).
- **Systems:** show the work behind the game: a balance spreadsheet, a card list, a flowchart of the Luxenomicon run structure.
- **A résumé PDF** (`resume.pdf` in this folder).
