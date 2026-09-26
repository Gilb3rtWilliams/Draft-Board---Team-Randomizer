# Draft Board — Team Randomizer

A single-page web app for putting together balanced teams for a school league tournament (originally built for a chess league, but works for any rated activity). Give it a roster of players with a rating, tell it how many teams you need, and it drafts balanced line-ups for you — while keeping things genuinely random instead of the same predictable order every time.

## What it does

- **Balances teams by rating.** The strongest players are spread across teams instead of stacking one team with all the top talent.
- **Guarantees a Captain per team.** The top-rated "seed" players (one per team) are locked in as team captains; everyone else is distributed around them.
- **Keeps it actually random.** A loose, controlled shuffle lets players near each other in rating swap boards between runs, so hitting "Reshuffle" gives you a genuinely different line-up rather than relabeling the same groups.
- **Gender is informational, not a constraint.** Each player has a gender tag for reference, but team selection is driven entirely by rating.
- **Two ways to size teams.** Choose either the number of teams you want, or how many players per team, and it works out the rest.
- **Fast roster entry.** Add players one at a time in an editable table, or paste a list — either plain names (one per line) or Name / Gender / Rating columns copied straight out of a spreadsheet.
- **Manual fine-tuning.** Not happy with a specific match-up? Drag any player onto another player's row to swap them directly — works across teams or within one.
- **Animated splash screen.** A short intro screen with a shuffling-pieces animation before you land on the roster/team-builder view.

## How the drafting works

1. Players are sorted by rating (highest to lowest).
2. The top *N* players (where *N* = number of teams) become the team **captains** — each is randomly assigned to a different team.
3. Everyone else is run through a "loose shuffle" that nudges each player's position by a bounded random amount, so nearby-rated players can trade places (a Board 2 might land where a Board 3 would have, etc.), instead of the exact same rank order being used every time.
4. The shuffled remainder is distributed to teams using a **snake draft** (team order reverses each round), which keeps total team strength roughly balanced.
5. You can freely drag-and-drop players afterward to make manual adjustments — team totals, averages, and the Captain badge all recalculate automatically.

## Getting started

This is a single self-contained HTML file — there's no build step and nothing to install.

1. Download `index.html` from this repo.
2. Open it directly in any modern browser (double-click it, or drag it into a browser window).

That's it. React, ReactDOM, and Babel Standalone are loaded from a CDN at runtime (via `<script>` tags in the `<head>`), and Google Fonts are loaded the same way, so an internet connection is needed the first time the page loads.

### Hosting it online

Because it's a single static HTML file, it works with any static hosting — GitHub Pages, Netlify, Vercel, or just opening it locally. For GitHub Pages:

1. Push this repo to GitHub.
2. In the repo settings, enable **GitHub Pages** and point it at the branch/folder containing `index.html`.
3. Your Draft Board will be live at `https://<your-username>.github.io/<repo-name>/`.

## Usage

1. **Enter the draft room** from the splash screen.
2. **Build your roster** in the table (Name, Gender, Rating), or paste a list in the "Add a list" box.
3. **Set your tournament format** — pick either "Number of teams" or "Players per team."
4. Click **Randomize teams**.
5. Review the results. Drag any player onto another player's row to swap them if you want to adjust a match-up manually.
6. Click **Reshuffle** any time for a fresh random draft.

## Tech stack

- [React](https://react.dev/) and ReactDOM (loaded via CDN, no bundler)
- [Babel Standalone](https://babeljs.io/docs/babel-standalone) to compile JSX directly in the browser
- Plain CSS (no framework) for styling
- No backend, no database — everything runs client-side and resets on page reload

## Project structure

```
index.html   # the entire application: markup, styles, and React component logic
README.md    # this file
```

## Notes and limitations

- All data lives in memory for the current browser session — refreshing the page clears the roster and results. There's no save/export feature built in yet.
- Requires an internet connection to load React/Babel/fonts from their CDNs on first load.
- Designed and tested for modern desktop and mobile browsers; drag-and-drop swapping uses the native HTML5 drag API.

## License

No license has been set yet — add one (MIT is a common, permissive choice) before sharing this repo publicly if you want to make the terms explicit.
