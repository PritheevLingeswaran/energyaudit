# Energy Audit of E-Waste

Single-page measurement bench. No build step, no dependencies to install —
`index.html` is the whole site.

## Deploy

Any static host works. Pick one:

**Vercel** (from this folder)
    npx vercel          # first run asks you to log in, then preview URL
    npx vercel --prod   # promotes it to your real domain

**Netlify Drop** — drag this folder onto https://app.netlify.com/drop

**GitHub Pages**
    git init && git add . && git commit -m "Energy audit bench"
    # push to a repo, then Settings > Pages > deploy from branch (root)

## Editing

`index.html` is the deployed copy. The working file lives one level up at
`../energy-audit-calculator.html` — copy it over before deploying if you edit
that one instead:

    cp ../energy-audit-calculator.html index.html
