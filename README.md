# Haul Index

A single-page reference for US consumer truck and trailer rentals — specs, capacities, requirements, and how each company structures its charges.

**Live site:** https://bip-river.github.io/USA-Truck-and-Trailer-Rentals/

## What it covers

38 records across six sources: U-Haul, Penske, Budget, Enterprise, Home Depot, and equipment yards — box trucks, cargo vans, pickups, cargo trailers, utility trailers, equipment trailers, and towing gear.

Consumer moving only. No CDL freight, no RVs or travel trailers, no equipment haulers beyond what a rental yard will hand a walk-up customer.

## Features

- **Reference tab** — searchable, filterable index by company, type, cost tier, and trip type; sortable by volume, payload, MPG, or relative cost. Star records, attach your own notes, and compare any selection side by side.
- **Pick a vehicle tab** — enter what you know (load size, volume, tow vehicle curb weight and tow rating, trip type, distance, fuel price) and get ranked matches. Ranking favors the smallest unit that still fits. Includes an inventory counter that converts what you own into packed cubic feet, and a curb-weight check against the fully loaded trailer, which is U-Haul's actual requirement and stricter than the hitch rating on most vehicles.
- **Reading it tab** — how the cost tiers, spec plate fields, confidence flags, and colour coding work, plus the towing rules that get rentals refused at the counter.

## On pricing

No dollar figures anywhere. Local rates are stable and quotable; one-way rates are dynamically priced by lane, season, and fleet imbalance and can swing several-fold between two quotes a week apart. Every record instead describes the *rate structure* — what you're charged for and what gets charged again on top — and carries two ordinal `$`-tiers, one for a local day and one for a roughly 1,000-mile lane. Tiers are judgment calls anchored to those two scenarios, not quotes.

## Technical notes

- One self-contained `index.html`. No build step, no dependencies, no framework. The only external request is the Overpass web font from Google Fonts.
- Stars, notes, counted inventory, and fuel settings are kept in browser `localStorage` under the `haulindex.*` keys. Nothing is sent anywhere and nothing syncs between devices.
- Active filters are written to the URL, so a filtered view can be bookmarked or shared.
- Mobile-first layout: cards on narrow screens, a data grid on wide ones.

## Running locally

Open `index.html` in a browser, or serve the directory:

```sh
python3 -m http.server 8000
```

Then visit http://localhost:8000.

## Publishing

The site is served from the repository root. In **Settings → Pages**, set the source to *Deploy from a branch* and pick the branch with `/ (root)` as the folder. The empty `.nojekyll` file tells GitHub Pages to serve the files as-is instead of running them through Jekyll.

## Accuracy

Specs come from published vendor figures and carry a confidence flag: **High** means stable and widely published, **Med** means right in shape but possibly a model year off, **Low** means verify before relying on it. Trailer interior volumes are the worst offenders — published cubic-foot claims frequently don't reconcile with the published interior dimensions.

Nothing here is a quote, and none of it is affiliated with or endorsed by any of the companies listed. Confirm specs, requirements, and prices with the vendor before you rent.

## License

[MIT](LICENSE).
