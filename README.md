# 45 Networks — website

Static site for 45 Networks (CCTV, structured cabling, networking, server installation, and AMC support), built for GitHub Pages with a GoDaddy domain and Zoho Mail.

## Files
```
index.html       Home
services.html    Services
projects.html    Projects / portfolio
about.html       About
contact.html     Contact (form + map)
css/style.css    All styles
js/main.js       Nav toggle, scroll reveal, project filters
assets/          Logo files + favicons
CNAME            Tells GitHub Pages to serve 45networks.in
```

## 1. Put this on GitHub

1. Create a new **public** repository on GitHub — name doesn't matter (e.g. `45networks-website`).
2. Upload all files in this folder to the repository (keep the folder structure — `css/`, `js/`, `assets/` as subfolders, and `CNAME` at the root).
3. Go to the repo's **Settings → Pages**.
4. Under "Build and deployment", set **Source: Deploy from a branch**, branch **main**, folder **/(root)**. Save.
5. GitHub will give you a URL like `https://yourusername.github.io/45networks-website/` — that confirms the site is live before the custom domain is connected.

## 2. Point your GoDaddy domain to GitHub Pages

In GoDaddy → **My Products → DNS** for `45networks.in`, add/edit these records:

**A records** (for the root domain `45networks.in`) — add all four, pointing to GitHub's IPs:
| Type | Name | Value |
|------|------|-------|
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |

**CNAME record** (for `www.45networks.in`):
| Type | Name | Value |
|------|------|-------|
| CNAME | www | yourusername.github.io |

Remove any existing GoDaddy "parked page" A record or forwarding first — it will conflict.

Back in GitHub → **Settings → Pages**, enter `45networks.in` as the custom domain and save (this also writes the CNAME file — it's already included here). Once DNS propagates (can take up to a few hours), tick **Enforce HTTPS**.

## 3. Keep Zoho Mail working

Website hosting and email are independent — moving the site to GitHub Pages does **not** touch mail, as long as you don't delete the existing Zoho DNS records on GoDaddy. Zoho typically needs:

- **MX records** pointing to Zoho's mail servers (already set up if `info@45networks.in` currently works)
- **TXT record** for SPF (e.g. `v=spf1 include:zoho.in ~all` — use whichever Zoho data center your account is on)
- **CNAME/TXT** for domain verification and DKIM

If email is already working today, leave those records untouched — only add the A and CNAME records above for the website. If you're setting Zoho up fresh, follow Zoho Mail's DNS setup page for your exact records, since they vary slightly by data center (.com vs .in) and plan.

## 4. Before going live — things to personalize

- **Contact form**: the form on `contact.html` posts to a placeholder Formspree URL (`https://formspree.io/f/your-form-id`). Create a free account at formspree.io, create a form, and replace that URL with your real endpoint — otherwise submissions will go nowhere.
- **Project photos**: `projects.html` currently uses styled placeholder tiles for each project category. Swap in real photos from completed jobs when available.
- **Google Map**: the embed on `contact.html` currently centers on the Hyderabad 500018 area generally — replace with your exact office location/pin if you want a precise marker.
- **Social links**: none are included yet — add them to the footer if you have business social profiles.
