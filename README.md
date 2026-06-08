# Nasser Chams — Personal Website

A fast, single-page personal site (crisp white, indigo accent) built with plain
HTML/CSS/JS. No build step, no dependencies — just static files ready for free
hosting on **GitHub Pages**.

```
website/
├── index.html          ← all page content
├── styles.css          ← all styling (colors live in :root at the top)
├── .nojekyll           ← tells GitHub Pages to serve /assets as-is
├── README.md
└── assets/
    └── logos/          ← company logos (swap these for the real files anytime)
```

---

## 🚀 Deploy to GitHub Pages (free)

1. **Create a repo.** For a personal site at `https://<username>.github.io`, name the
   repo exactly `<username>.github.io`. (Any other repo name works too — it just lives
   at `https://<username>.github.io/<repo>/`.)

2. **Upload these files** to the repo root. Either:
   - Drag-and-drop everything in this folder into the repo on github.com, **or**
   - Use git:
     ```bash
     cd website
     git init
     git add .
     git commit -m "Initial personal site"
     git branch -M main
     git remote add origin https://github.com/<username>/<repo>.git
     git push -u origin main
     ```

3. **Turn on Pages.** Repo → **Settings → Pages** → *Build and deployment* →
   Source: **Deploy from a branch** → Branch: **main**, folder **/(root)** → **Save**.

4. Wait ~1 minute, then visit the URL shown on that Pages settings screen. Done. 🎉

---

## ✏️ Things you'll want to customize

### 1. Add your real testimonials  *(important)*
Upwork blocks automated copying, so the three testimonial cards in `index.html` are
**placeholders**. Open `index.html`, find the `TESTIMONIALS` section, and replace each
card's quote text and the `<strong>Client name</strong>` / project line with the real
feedback from your profile: <https://www.upwork.com/freelancers/nasserc4>
(Or just paste the feedback to me and I'll drop it in.)

### 2. Company logos — how they work
Four tiles load each company's **official logo live from their own CDN**; the other two
use clean local wordmarks because those companies only publish white-on-transparent
logos (which would be invisible on the white tiles):

| Company                   | Logo source                          | Local fallback file                         |
|---------------------------|--------------------------------------|---------------------------------------------|
| Alt Sports Data           | ✅ official logo (live)              | `assets/logos/alt-sports-data.svg`          |
| Allez Health              | ✅ official logo (live)              | `assets/logos/allez-health.svg`             |
| McMaster University       | ✅ official logo (live)              | `assets/logos/mcmaster-university.svg`      |
| The Wharton School        | ✅ official logo (live)              | `assets/logos/wharton.svg`                  |
| Common Thread Collective  | 📝 wordmark (no dark logo published) | `assets/logos/common-thread-collective.svg` |
| Originality.ai            | 📝 wordmark (no dark logo published) | `assets/logos/originality-ai.svg`           |

Each live tile **automatically falls back** to its local wordmark if the remote URL ever
changes, so the wall can never look broken. To replace any wordmark (or pin a logo
locally instead of hotlinking), download a **dark or full-color** version of the logo,
save it over the matching file above (keep the same filename), and change that tile's
`<img src="...">` in `index.html` back to the local path. Logos render in grayscale and
turn full-color on hover (a clean "trusted by" look) — remove the `filter: grayscale(...)`
line in `styles.css` under `.logo-tile` if you'd rather they always show in color.

> Tip: use each company's official press/brand page or a transparent-background PNG so
> the logos sit cleanly on the white tiles.

### 3. Make the contact form work  *(one-time, ~30 seconds)*
The contact form sends messages straight to **achams123@gmail.com** using
[Web3Forms](https://web3forms.com) — free, reliable, CORS-friendly, no account needed. To
activate it:

1. Go to **https://web3forms.com**, enter **achams123@gmail.com**, and submit.
2. Web3Forms emails you an **access key** (a long code). Copy it.
3. In `index.html`, find the line
   `<input type="hidden" name="access_key" value="YOUR_WEB3FORMS_ACCESS_KEY" />`
   and replace `YOUR_WEB3FORMS_ACCESS_KEY` with your key. Commit & push.

That's it — submissions arrive in your inbox immediately, with no per-message confirmation.

Notes:
- The form submits via AJAX, so visitors see a green "✓ Thanks!" message without leaving
  the page. If anything fails, it tells the visitor to email you directly.
- The free tier covers 250 submissions/month — plenty for a personal site.
- To change the destination, manage it from your Web3Forms dashboard (the key controls it).

### 4. Tweak text, colors, or your name
- **Name / headline / bio:** edit directly in `index.html` (it's all plain text).
- **Colors:** change the variables in the `:root { ... }` block at the top of
  `styles.css` — `--accent` is the indigo highlight; swap it for any hex you like.
- **Contact:** email `achams123@gmail.com` and phone `519-852-4916` appear in the hero,
  contact section, and footer — search/replace if they change.

### 5. Use a custom domain (optional)
Buy a domain, add a file named `CNAME` containing just your domain (e.g. `nasserchams.com`),
and point your DNS to GitHub Pages per their docs. If you switch domains, also update the
URLs in `sitemap.xml`, `robots.txt`, and the `canonical`/`og:url` tags in `index.html`.

### 6. Get found on Google (Search Console)
The site already ships with `sitemap.xml`, `robots.txt`, SEO meta tags, and Person
structured data. To get indexed:

1. Go to **https://search.google.com/search-console**, sign in, and add a property of type
   **URL prefix**: `https://nchams.github.io/`.
2. Choose the **HTML tag** verification method. Copy the token from the meta tag it shows.
3. In `index.html`, uncomment the `google-site-verification` line and paste your token, then
   commit & push. Back in Search Console, click **Verify**.
4. In Search Console → **Sitemaps**, submit `sitemap.xml`. Then use **URL Inspection** →
   *Request indexing* on the homepage to speed things up.

Indexing typically takes a few days to a couple of weeks.

---

Built as a static site — loads instantly, costs nothing to host.
