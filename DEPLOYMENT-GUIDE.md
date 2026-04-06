# Republic of United Land — Deployment Guide
## Domain: republicofunitedland.org (or fallback options below)

---

## FILE STRUCTURE
```
rul-deploy/
├── index.html              ← Main government portal (homepage)
├── 404.html                ← Custom 404 error page
├── robots.txt              ← SEO crawler instructions
├── sitemap.xml             ← Search engine sitemap
├── CNAME                   ← GitHub Pages custom domain config
├── assets/
│   └── favicon.svg         ← Republic seal favicon
└── pages/
    ├── citizenship.html    ← Citizenship & naturalization page
    └── constitution.html   ← Full constitution text
```

---

## STEP 1: PURCHASE DOMAIN

### Primary choice: `republicofunitedland.org`
### Fallback options (if taken):
1. `ulr.org` (United Land Republic)
2. `unland.org` (United Land)  
3. `rulrepublic.org`
4. `unitedlandrepublic.org`

### Where to buy (cheapest):
- **Cloudflare Registrar** → https://dash.cloudflare.com (wholesale pricing, ~$9-10/yr for .org)
- **Namecheap** → https://namecheap.com (~$9-12/yr for .org)
- **Porkbun** → https://porkbun.com (often cheapest, ~$8-10/yr)

### Purchase steps:
1. Create account at registrar
2. Search for domain name
3. Add to cart → checkout
4. Use WHOIS privacy (usually free/included) — keeps personal info private
5. Save your login credentials

---

## STEP 2: HOST THE SITE (FREE)

### Option A: GitHub Pages (RECOMMENDED — Easiest, free, reliable)

1. Go to https://github.com → create account (or sign in)
2. Click "+" → "New repository"
3. Name it: `rul-org` (or any name)
4. Set to **Public**
5. Click "Create repository"
6. Upload ALL files from this `rul-deploy/` folder:
   - Click "uploading an existing file"
   - Drag the entire contents of rul-deploy/ into the upload area
   - Commit the files
7. Go to repository **Settings** → **Pages**
8. Under "Source" select **Deploy from a branch**
9. Select **main** branch, **/ (root)** folder
10. Click **Save**
11. Site will be live at `https://yourusername.github.io/rul-org/` within 2 minutes

### Option B: Cloudflare Pages (Also free, faster CDN)

1. Go to https://dash.cloudflare.com
2. Click "Workers & Pages" → "Create" → "Pages"
3. Choose "Direct Upload"
4. Name project: `rul`
5. Upload all files from rul-deploy/ folder
6. Click "Deploy"
7. Site goes live at `rul.pages.dev` immediately

---

## STEP 3: CONNECT CUSTOM DOMAIN

### If using GitHub Pages:
1. In your repo, the `CNAME` file is already included (contains `republicofunitedland.org`)
2. Go to repo **Settings** → **Pages** → **Custom domain**
3. Enter `republicofunitedland.org` → Save
4. Go to your domain registrar's DNS settings
5. Add these DNS records:

```
Type    Name    Value
A       @       185.199.108.153
A       @       185.199.109.153
A       @       185.199.110.153
A       @       185.199.111.153
CNAME   www     yourusername.github.io
```

6. Wait 5-30 minutes for DNS to propagate
7. Back in GitHub Pages settings, check "Enforce HTTPS"
8. Site is now live at https://republicofunitedland.org with SSL

### If using Cloudflare Pages:
1. In Cloudflare Pages project → "Custom domains"
2. Click "Set up a custom domain"
3. Enter `republicofunitedland.org`
4. If domain is on Cloudflare, DNS is configured automatically
5. If domain is elsewhere, add the CNAME record shown
6. SSL is automatic

---

## STEP 4: POST-LAUNCH CHECKLIST

### Immediate (do today):
- [ ] Verify site loads at https://republicofunitedland.org
- [ ] Verify HTTPS padlock icon appears
- [ ] Test all navigation links work
- [ ] Test mobile responsiveness
- [ ] Update Instagram bio link to https://republicofunitedland.org

### Within first week:
- [ ] Submit sitemap to Google Search Console (https://search.google.com/search-console)
  - Add property → enter republicofunitedland.org → verify via DNS
  - Submit sitemap URL: https://republicofunitedland.org/sitemap.xml
- [ ] Submit to Bing Webmaster Tools (https://www.bing.com/webmasters)
- [ ] Create og-image.png (1200x630px) with Republic branding and place in /assets/

### Within first month:
- [ ] Create MicroWiki article (https://micronations.wiki)
- [ ] Reach out to other micronations for diplomatic recognition
- [ ] Consider adding: Press Kit page, Official Gazette/Blog, Embassy page

---

## DOMAIN NAME CHANGES

If you use a different domain than `republicofunitedland.org`, you need to update these files:

1. **CNAME** — replace `republicofunitedland.org` with your domain
2. **index.html** — find/replace all `republicofunitedland.org` with your domain (5 instances in meta tags)
3. **pages/citizenship.html** — find/replace `republicofunitedland.org` (2 instances)
4. **pages/constitution.html** — find/replace `republicofunitedland.org` (2 instances)
5. **sitemap.xml** — find/replace `republicofunitedland.org` (3 instances)
6. **robots.txt** — find/replace `republicofunitedland.org` (1 instance)

Quick command if on Mac/Linux:
```bash
find . -type f -name "*.html" -o -name "*.xml" -o -name "*.txt" -o -name "CNAME" | xargs sed -i 's/rul\.org/YOURDOMAIN\.org/g'
```

---

## TOTAL COST SUMMARY

| Item | Cost | Frequency |
|------|------|-----------|
| Domain (.org) | ~$9-10 | Yearly |
| Hosting (GitHub/Cloudflare Pages) | $0 | Free forever |
| SSL Certificate | $0 | Automatic |
| **TOTAL** | **~$9-10/year** | |

---

## TECH SUPPORT

The site is pure HTML/CSS/JS — no build tools, no frameworks, no server needed.
To update content: edit the HTML files and re-upload to GitHub/Cloudflare.
Everything renders client-side. No database. No backend.
