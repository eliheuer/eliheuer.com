# Domain Migration: elih.blog → eliheuer.com

## Overview

Migrating the blog from the expired `elih.blog` domain to `eliheuer.com`. The site is an Astro project hosted on GitHub Pages. DNS is managed through Namecheap.

---

## Code Changes

The following files reference `elih.blog` and need to be updated to `eliheuer.com`:

- **`CNAME`** — GitHub Pages custom domain file. Change `elih.blog` to `eliheuer.com`.
- **`astro.config.ts:24`** — The `site` property. Change `https://elih.blog` to `https://eliheuer.com`.
- **`src/consts.ts:7`** — The `href` property. Change `https://elih.blog` to `https://eliheuer.com`.
- **`package.json:2`** — The `name` field. Change `elih.blog` to `eliheuer.com` (cosmetic, but keeps things consistent).

---

## DNS Setup (Namecheap)

Go to **Namecheap → Domain List → eliheuer.com → Advanced DNS**.

Remove any default parking/redirect records, then add:

### A Records (apex domain → GitHub Pages)

| Type | Host | Value             |
| ---- | ---- | ----------------- |
| A    | @    | 185.199.108.153   |
| A    | @    | 185.199.109.153   |
| A    | @    | 185.199.110.153   |
| A    | @    | 185.199.111.153   |

### CNAME Record (www subdomain)

| Type  | Host | Value                |
| ----- | ---- | -------------------- |
| CNAME | www  | eliheuer.github.io   |

---

## GitHub Pages Settings

Go to the repo **Settings → Pages** and:

1. Update the **Custom domain** field from `elih.blog` to `eliheuer.com`.
2. Check **Enforce HTTPS** (may need to wait for DNS propagation first).

---

## Optional: Rename the GitHub Repo

Rename `eliheuer/elih.blog` to `eliheuer/eliheuer.com` in **Settings → General → Repository name**. GitHub auto-redirects the old URL so nothing breaks.

---

## Checklist

- [x] Update `CNAME` file to `eliheuer.com`
- [x] Update `astro.config.ts` site URL to `https://eliheuer.com`
- [x] Update `src/consts.ts` href to `https://eliheuer.com`
- [x] Update `package.json` name to `eliheuer.com`
- [x] Commit and push code changes
- [x] Configure DNS A records on Namecheap (4 GitHub Pages IPs)
- [x] Configure DNS CNAME record on Namecheap (`www` → `eliheuer.github.io`)
- [x] Remove any conflicting default Namecheap DNS records (URL redirect couldn't be deleted, but doesn't conflict)
- [x] Update GitHub Pages custom domain in repo settings to `eliheuer.com`
- [x] Enable "Enforce HTTPS" in GitHub Pages settings
- [x] Verify site loads at `https://eliheuer.com`
- [ ] (Optional) Rename GitHub repo from `elih.blog` to `eliheuer.com`
