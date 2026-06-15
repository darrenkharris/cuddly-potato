# darren-harris.co.uk — Website README

## Folder Structure

```
darren-harris-site/
├── index.html          ← Homepage
├── publications.html   ← Publications page
├── privacy.html        ← Privacy page
├── 404.html            ← Custom 404 error page
├── css/
│   └── style.css       ← All site styles
├── js/
│   └── main.js         ← Navigation and scroll effects
├── assets/
│   ├── favicon.svg     ← Placeholder favicon (replace with your own)
│   ├── favicon.png     ← Placeholder (generate from your SVG)
│   └── og-image.png    ← EDIT: Add a 1200×630px Open Graph image
└── README.md           ← This file
```

---

## Before You Publish — Customisation Checklist

Search all HTML files for `EDIT:` comments. Every one is something you need to update.

### Essential (do before going live)

- [ ] Replace all `YOURUSERNAME` placeholders with your real usernames on LinkedIn, Gumroad, Mixcloud and Instagram
- [ ] Replace `YOUR@EMAIL.COM` with your real email address
- [ ] Replace `https://www.amazon.co.uk/YOURAUTHORPAGE` with your real Amazon Author Page URL
- [ ] Add the real Gumroad product URL to each "View on Gumroad" button in `publications.html`
- [ ] Add the real Amazon product URL to each "View on Amazon" button in `publications.html`
- [ ] Create and add an Open Graph image (`assets/og-image.png`, 1200×630px) — used when sharing on LinkedIn and social media
- [ ] Replace the placeholder favicon (`assets/favicon.svg`) with your own design — use a tool like realfavicongenerator.net to generate all sizes

### Recommended

- [ ] Update the publication count in the stats bar on the homepage if it changes
- [ ] Review all body copy and adjust any specific wording to your preference
- [ ] Update the footer "Hosted on Cloudflare Pages" text if you use a different host
- [ ] Update the privacy page last-updated date
- [ ] Add your real career dates to the timeline items if you want specifics

---

## Deployment Instructions

### Option 1: Cloudflare Pages (Recommended)

Cloudflare Pages is fast, free and includes global CDN and HTTPS.

1. Push this folder to a **GitHub** or **GitLab** repository (create one at github.com if you don't have one)
2. Go to **dash.cloudflare.com** and log in (create a free account if needed)
3. Click **Workers & Pages → Create → Pages → Connect to Git**
4. Select your repository
5. Set **Build output directory** to `/` (or leave blank — this is a static site with no build step)
6. Click **Save and Deploy**
7. Cloudflare will give you a `*.pages.dev` preview URL. Test it.
8. To connect your custom domain, go to **Custom Domains** in your Pages project and add `darren-harris.co.uk`

---

### Option 2: Netlify

1. Push to GitHub (same as above)
2. Go to **app.netlify.com → Add new site → Import an existing project**
3. Connect GitHub and select your repository
4. Leave Build Command blank, set Publish Directory to `.` (current directory)
5. Click **Deploy**
6. To connect your custom domain: **Site settings → Domain management → Add custom domain**
7. Netlify will give you DNS values to configure

---

### Option 3: GitHub Pages

1. Push to GitHub
2. Go to your repository → **Settings → Pages**
3. Set Source to **Deploy from a branch**, select `main`, folder `/root`
4. GitHub Pages will publish at `https://YOURUSERNAME.github.io/REPONAME/`
5. To use a custom domain, add a `CNAME` file to the root of the repo containing: `darren-harris.co.uk`
6. Then configure DNS at FastHosts (see below)

---

## DNS Configuration at FastHosts

> **Important:** Do not copy DNS values from this file. Always copy exact values from your chosen hosting provider's dashboard.

### General approach for connecting darren-harris.co.uk:

1. Log in to your **FastHosts** control panel
2. Find **Domain Management** or **DNS Settings** for `darren-harris.co.uk`
3. You will need to add or update DNS records. The exact values depend on your hosting platform:

**For Cloudflare Pages:**
- Cloudflare will guide you through this when you add your custom domain. If your domain is also managed via Cloudflare, it will configure DNS automatically.
- If your domain stays at FastHosts, you will add a **CNAME record** pointing `www` to your `*.pages.dev` URL, and an **A record** or **CNAME** for the root domain (`@`) — Cloudflare will show you the exact values.

**For Netlify:**
- Netlify provides specific A record IP addresses and a CNAME value under **Domain settings → DNS panel** — copy these exactly.
- You typically set: root domain `@` → **A record** → Netlify's Load Balancer IP, and `www` → **CNAME** → your Netlify subdomain.

**For GitHub Pages:**
- GitHub provides four A record IP addresses for the root domain. Find the current values at: https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site
- Add `www` as a **CNAME** pointing to `YOURUSERNAME.github.io`

### DNS propagation

DNS changes typically propagate within 1–24 hours. HTTPS certificates are issued automatically by all three platforms once DNS is confirmed.

---

## Optional: Adding Google Analytics

If you later decide to add analytics, add this block inside `<head>` on each HTML page and replace `G-XXXXXXXXXX` with your Measurement ID:

```html
<!-- OPTIONAL: Google Analytics — remove if not needed -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXXXX');
</script>
```

If you add this, update your `privacy.html` to mention the use of Google Analytics and cookies.

---

## Updating Publications

To add a new publication to `publications.html`, copy one of the `<article class="pub-card">` blocks and update:
- The guide number in `<div class="pub-number">`
- The `id` on `<h3>` (e.g. `pub12-title`)
- The `aria-label` on each button
- The title, description, audience and href values

---

*Built as a static site. No backend, no database, no trackers by default.*
