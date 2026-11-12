# Energy Audit of E-Waste

Single-page measurement bench for an energy audit of obsolete appliances.
No build step, no dependencies — `index.html` is the whole site.

It compares the three pairs the project names:

- Old CRT monitor vs LED monitor
- CFL lamp vs LED lamp
- Old induction fan vs BLDC fan

For each pair, enter voltage, current and power factor for the old appliance
and its replacement (or derate a nameplate rating) and it returns apparent
power, real power, annual energy, the energy saved, the cost saved at your
electricity rate, the CO2 avoided and the simple payback. A table at the
bottom totals all three pairs. A fourth "custom" slot takes any other pair.

## Deploy

Any static host works. **This repo is not currently connected to Vercel**, so
merging to `main` does not redeploy — either connect the repo under the Vercel
project's Settings > Git, or deploy by hand:

    npx vercel --prod    # from this folder

**Netlify Drop** — drag this folder onto https://app.netlify.com/drop

**GitHub Pages** — Settings > Pages > deploy from `main`, root.

## Running it locally

Open `index.html` directly, or serve the folder:

    npx serve .          # or: python -m http.server

## Tests

Arithmetic checks are built into the page: power, energy, saving, CO2, cost
and payback for the preset pairs, plus the fallbacks for a blank current or
power factor. Append `?selftest` to the URL and read the console:

    http://localhost:3000/?selftest

They also expose `window.__selftest` as `{passed, failed, log}` for a headless
runner.

## Notes

- The preset wattages, load factors and power factors are typical values, not
  readings. Replace them with your own measurements.
- Every table cell is labelled `measured`, `derived`, `typical` or
  `calculated`, so a printed sheet never passes an assumption off as a reading.
- The emission factor is 0.710 kg CO2/kWh (CEA CO2 Baseline Database v21.0,
  FY 2024-25, national grid average).
- The electricity rate is a single flat figure you enter; the default is only
  an example.
- Each pair keeps its own inputs, stored in the visitor's browser only.
  Nothing is uploaded.
