# Deploying to 213.kssarkaria.org

The site is a pure static site (HTML, CSS, small hand-rolled JS — no build step, no frameworks). It works anywhere static files can be served: Cloudflare Pages, Netlify, GitHub Pages, a plain Apache server, your laptop.

These instructions cover the target setup: **Cloudflare Pages** connected to this GitHub repo, on the subdomain `213.kssarkaria.org`, with DNS still at GoDaddy.

## One-time prerequisites

1. **Cloudflare account.** Free tier is fine. Sign up at https://dash.cloudflare.com/sign-up if you don't have one.
2. **GitHub repo access.** Cloudflare will ask permission to read this repo to build it.
3. **GoDaddy login** for `kssarkaria.org` — you'll need to add one DNS record.

## Step 1. Create the Cloudflare Pages project

1. Go to https://dash.cloudflare.com/ → **Workers & Pages** → **Create application** → **Pages** tab → **Connect to Git**.
2. Authorise GitHub, pick the `prabhjot-singh/kssarkaria-213` repo.
3. In the build settings:
   - Production branch: `main`
   - Framework preset: **None**
   - Build command: *(leave empty)*
   - Build output directory: `/`
4. Click **Save and Deploy**. Cloudflare will take ~30 seconds to publish. You'll get a URL like `kssarkaria-213.pages.dev`. Open it — the site should be live there.

## Step 2. Add the custom domain

1. In the same Pages project → **Custom domains** tab → **Set up a custom domain**.
2. Enter `213.kssarkaria.org` → **Continue**.
3. Cloudflare will detect the domain isn't on Cloudflare DNS and will give you a CNAME record to add at GoDaddy. It will look like:
   - Type: `CNAME`
   - Name: `213`
   - Value: `kssarkaria-213.pages.dev` *(or similar — use what Cloudflare shows you)*
   - TTL: 1 hour (default is fine)

## Step 3. Add the CNAME at GoDaddy

1. Log into https://dcc.godaddy.com/control/dnsmanagement?domainName=kssarkaria.org
2. Click **Add New Record** → **CNAME**.
3. Paste the values from Cloudflare's instructions:
   - **Name**: `213`
   - **Value**: `kssarkaria-213.pages.dev` *(use the exact value Cloudflare gave you)*
   - **TTL**: 1 hour
4. Save.

## Step 4. Verify

- In Cloudflare Pages → Custom domains, the domain will show "Verifying DNS" and then "Active" (usually within a few minutes, sometimes up to an hour).
- Cloudflare automatically issues a free SSL certificate — no action needed.
- Once active, `https://213.kssarkaria.org` serves the site with a valid certificate.

## Making updates later

Any `git push` to `main` triggers a redeploy automatically — typically live within 60 seconds. No separate deploy step.

## If something goes wrong

- **CNAME conflicts**: GoDaddy won't let you add a CNAME if an A record for `213` already exists. Delete the A record first.
- **Cloudflare says "Verifying DNS" forever**: DNS propagation can take up to 24 hours at GoDaddy, though usually ~5 minutes. Use `dig 213.kssarkaria.org` or https://dnschecker.org/ to see what's being returned.
- **SSL not working**: Cloudflare issues the cert automatically after DNS is verified. Wait 15 minutes after DNS goes active.

## Alternative: host on the existing Linux server via FTP

If the Cloudflare route isn't desired, this whole folder (minus `.git/`) can simply be uploaded via FTP into a `/213/` directory on the existing `kssarkaria.org` server, and linked from the main site. No build step needed.
