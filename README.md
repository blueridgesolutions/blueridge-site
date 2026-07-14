# Blue Ridge Solutions LLC — website

A dependency-free static site (plain HTML + CSS, no build step).

```
index.html      Home
services.html   Services
contact.html    Contact
styles.css      Shared styles
CNAME           Custom domain (used by GitHub Pages)
```

Open `index.html` in a browser to preview locally, or run
`python -m http.server` in this folder and visit http://localhost:8000.

---

## Deploy to Cloudflare Pages (recommended)

1. Push this folder to a GitHub repo (see below), or use **Direct Upload**.
2. Cloudflare dashboard → **Workers & Pages** → **Create** → **Pages**.
3. Connect the repo (or drag-and-drop the folder for Direct Upload).
4. Build settings: **Framework preset = None**, **Build command = (blank)**,
   **Build output directory = /** (the files are already the output).
5. Deploy. You'll get a `*.pages.dev` URL immediately.
6. **Custom domain:** Pages project → **Custom domains** → add
   `blueridgesol.com` and `www.blueridgesol.com`. Cloudflare shows the exact
   DNS records to add in your **Squarespace** domain's DNS settings
   (usually a CNAME to your `*.pages.dev` target). SSL is automatic.

> The `CNAME` file in this repo is only read by GitHub Pages; Cloudflare Pages
> ignores it, so you can leave it or delete it.

---

## Deploy to GitHub Pages

1. Create a repo and push these files (commands below).
2. Repo → **Settings** → **Pages** → **Source: Deploy from a branch** →
   branch `main`, folder `/ (root)` → **Save**.
3. The `CNAME` file already contains `blueridgesol.com`, so Pages will serve
   the custom domain once DNS is configured.
4. In **Squarespace** DNS settings for the domain, add:
   - Four `A` records for the apex `@` → GitHub's IPs:
     `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - One `CNAME` for `www` → `<your-github-username>.github.io`
5. Back in **Settings → Pages**, tick **Enforce HTTPS** once the cert is issued.

---

## First push to GitHub

```bash
cd blueridge-site
git init
git add .
git commit -m "Initial Blue Ridge Solutions site"
git branch -M main
git remote add origin https://github.com/<your-username>/<repo>.git
git push -u origin main
```

## Editing content

All copy lives directly in the three `.html` files. The email address
`solutions@blueridgesol.com` appears in each page's footer and on `contact.html`.
Colors and layout are in `styles.css` (see the `:root` variables at the top).
