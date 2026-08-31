# Energy Audit of E-Waste

Single-page measurement bench for an energy audit of obsolete appliances.
No build step, no dependencies — `index.html` is the whole site.

Enter voltage, current and power factor for an appliance and its replacement
(or derate a nameplate rating) and it returns real power, annual energy, cost
against the telescopic TANGEDCO slabs, CO2, simple payback, and the carbon
payback of manufacturing the replacement.

## Deploy

Any static host works. **This repo is not currently connected to Vercel**, so
merging to `main` does not redeploy — either connect the repo under the Vercel
project's Settings > Git, or deploy by hand:

    npx vercel --prod    # from this folder

**Netlify Drop** — drag this folder onto https://app.netlify.com/drop

**GitHub Pages** — Settings > Pages > deploy from `main`, root.

## Running it locally

Open `index.html` directly and everything works except saved state: Chrome
blocks `localStorage` on `file://`, so inputs and banked pairs will not
survive a reload. Serve it over HTTP to get that back:

    npx serve .          # or: python -m http.server

## Tests

Arithmetic checks for the telescopic tariff and the embodied-carbon
derivation are built into the page. Append `?selftest` to the URL and read the
console:

    http://localhost:3000/?selftest

They also expose `window.__selftest` as `{passed, failed, log}` for a headless
runner.

## Notes

- Tariff slabs, the CEA emission factor and the embodied-energy shares are all
  documented in the page footer, including which figures are cited and which
  are assumptions.
- Every table cell is labelled `measured`, `derived`, `typical` or
  `calculated`, so a printed sheet never passes an assumption off as a reading.
- Inputs and banked pairs are stored in the visitor's browser only. Nothing is
  uploaded.
