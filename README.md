# Starship Launch Counter

A single-page web app that tracks time elapsed since SpaceX's last Starship integrated flight test, with a full launch history table and gap-between-flights stats.

## What it does

- **Live counter** — days, hours, minutes, and seconds since the last launch (Flight 11, Oct 13 2025)
- **Next flight callout** — shows the current NET date for the upcoming flight
- **Launch history table** — all 11 IFT flights with date, outcome (Success / Partial / Failure), and days between each flight
- **Live gap row** — a pending IFT-12 row that updates in real time alongside the counter

## Stack

Plain HTML, CSS, and vanilla JavaScript — no build step, no dependencies, no framework. Open `index.html` directly in a browser.

## Updating after a new launch

All data lives in `index.html`:

1. **Add the new flight** to the `LAUNCHES` array near the bottom of the `<script>` block:
   ```js
   { flight: 12, date: "YYYY-MM-DD", outcome: "success" },
   ```
2. **Update `LAST_LAUNCH`** to the exact UTC liftoff time:
   ```js
   const LAST_LAUNCH = new Date("YYYY-MM-DDTHH:MM:00Z");
   ```
3. **Update the badge and tagline** in the hero section:
   ```html
   <div class="flight-badge">Flight 12 · MMM DD, YYYY</div>
   <p class="tagline">Last Starship integrated flight test</p>
   ```
4. **Update the next-flight callout** with the new NET date.
5. **Update the footer** timestamp line.

## Outcome values

| Value | Meaning |
|-------|---------|
| `success` | Full mission success |
| `partial` | Partial success (e.g. vehicle lost on reentry, catch not attempted) |
| `failure` | Early anomaly / RUD before mission objectives |

## License

Not affiliated with SpaceX. Hero photo from [Official SpaceX Photos on Flickr](https://www.flickr.com/photos/spacex/52822653368) under CC BY-NC 2.0.
