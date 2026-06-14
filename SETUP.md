# Setup: Get Themed Neurons Live (Free)

Everything here is free. Two parts: (1) host the site on GitHub Pages, (2) put a free
custom domain in front of it. Part 1 gets you live immediately. Part 2 is optional polish.

The site is already built and committed in this folder (`/Users/nate/themed-neurons-site`).

═══════════════════════════════════════════════
PART 1 — Host on GitHub Pages (gets you live)
═══════════════════════════════════════════════

You need a GitHub account (free). If you have one, skip to step 2.

1. CREATE THE GITHUB ACCOUNT (if needed)
   - Go to https://github.com/signup
   - Pick a username (e.g. "natesillman" or "themedneurons")

2. CREATE A NEW REPOSITORY
   - Go to https://github.com/new
   - Repository name: themed-neurons   (or whatever you like)
   - Set it to PUBLIC (required for free Pages)
   - Do NOT check "Add a README" — we already have files
   - Click "Create repository"

3. PUSH THE SITE
   GitHub will show you commands. But since the repo is already built here,
   just tell OWL "push the site to <your-repo-url>" and I'll handle it —
   OR run these yourself (replace YOURNAME):

     cd /Users/nate/themed-neurons-site
     git remote add origin https://github.com/YOURNAME/themed-neurons.git
     git branch -M main
     git push -u origin main

   It'll ask for your GitHub username and a password. NOTE: the "password"
   must be a Personal Access Token, not your account password. Get one at:
   https://github.com/settings/tokens  (Generate new token → classic → check "repo")
   OWL can walk you through this when you're ready.

4. TURN ON PAGES
   - In your repo, click Settings → Pages (left sidebar)
   - Under "Build and deployment" → Source: "Deploy from a branch"
   - Branch: main  /  folder: / (root)  → Save
   - Wait 1-2 minutes

5. YOU'RE LIVE
   Your site will be at:
     https://YOURNAME.github.io/themed-neurons/

   That's a real, shareable URL. Done. Part 2 just makes it prettier.

═══════════════════════════════════════════════
PART 2 — Free custom domain (optional)
═══════════════════════════════════════════════

This swaps the long github.io URL for something like:
   themedneurons.us.kg   or   themedneurons.dpdns.org

Using DigitalPlat FreeDomain (https://dash.domain.digitalplat.org/) + Cloudflare DNS.

1. REGISTER THE FREE DOMAIN
   - Go to https://dash.domain.digitalplat.org/
   - Sign up / log in
   - Search for an available name. Extensions offered:
       .dpdns.org   .us.kg   .qzz.io   .xx.kg   .qd.je
   - Suggested: themedneurons.us.kg  (short, clean)
   - Register it (free)

2. SET UP DNS (Cloudflare — free, recommended by FreeDomain)
   - Create a free Cloudflare account: https://dash.cloudflare.com/sign-up
   - Add your new domain as a site (Free plan)
   - Cloudflare gives you two nameservers — copy them
   - Back in the FreeDomain dashboard, set your domain's nameservers to
     the Cloudflare ones

3. POINT THE DOMAIN AT GITHUB PAGES
   In Cloudflare → DNS → add these records:

     Type: CNAME   Name: @ (or www)   Target: YOURNAME.github.io
     (Cloudflare supports CNAME at root via "flattening")

   For an apex/root domain, you can instead add 4 A records pointing to
   GitHub's IPs:
     185.199.108.153
     185.199.109.153
     185.199.110.153
     185.199.111.153

4. TELL GITHUB ABOUT THE DOMAIN
   - Repo → Settings → Pages → "Custom domain"
   - Enter your domain (e.g. themedneurons.us.kg) → Save
   - Check "Enforce HTTPS" once it's available (may take an hour)
   - This creates a CNAME file in the repo — leave it there

5. WAIT
   DNS can take anywhere from minutes to a few hours to propagate.
   Then your site lives at your custom domain with free HTTPS.

═══════════════════════════════════════════════
NOTES
═══════════════════════════════════════════════
- The whole stack is free: GitHub Pages (hosting), FreeDomain (domain), Cloudflare (DNS/HTTPS).
- To UPDATE the site later: edit index.html, then `git add -A && git commit -m "update" && git push`.
  Changes go live in ~1 minute. OWL can do this for you anytime.
- To add a 4th album later: drop the cover in img/, add a card block in index.html. Ask OWL.
- FreeDomain's only official channels are their website + Discord. They warned their
  Telegram was compromised — ignore any Telegram messages claiming to be them.
