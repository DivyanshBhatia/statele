# Statele — Know the Indian State, one clue at a time

A [Worldle](https://worldle.teuteuf.fr/)-style daily geography game for India's
**28 states and 8 union territories**. Each day picks one state and walks you
through up to **13 rounds** of clues about it — all in a single self-contained
`index.html` with no build step, no dependencies, and no server.

## The rounds

1. **Shape** — name the state from its silhouette in 6 tries, with distance,
   compass direction, and proximity clues after each guess.
2. **Capital** — type the capital city (3 attempts).
3. **Pinpoint the capital** — pick the capital's location from points on the map.
4. **Locate on the map** — tap the state's position on the map of India.
5. **How many neighbours** — choose how many states & UTs border it (the answer doesn't name them — that's the next round).
6. **Name the neighbours** — type each bordering state/UT, with a type-ahead list.
7. **River** — type a major river, choosing from a type-ahead dropdown of all rivers.
8. **Spot the landmark** — pick the state's landmark from four photos (no names, and the answer never names it either).
9. **Name the landmark** — see the photo, then choose its name from four options.
10. **Find the landmark** — pin its location on the state map.
11. **Languages** — type the two most widely spoken languages.
12. **Largest district** — study the district map, then type the name of the biggest district (by area), with a type-ahead list.
13. **Area** — choose the state's area from a set of ranges.


Earn a **badge** for every round you clear. Each round has a **"See answer & skip
to next round"** button if you're stuck, and a **"Give up & see results"** link to
end the run early. The final summary shows your badge grid and score, with
**Share on WhatsApp**, **Copy result**, and **Practice another**.

Rounds that don't apply to a place are skipped automatically — e.g. islands with
no land borders skip the "name the neighbours" round, and places with no major
river skip the river round, and the largest-district round only appears for states with
enough districts to make it interesting — so the round count adapts (10–13).

## Play locally

Open `index.html` in any browser, or serve the folder:

```bash
python3 -m http.server 8000   # then visit http://localhost:8000
```

## Deploy to GitHub Pages

1. Create a new repository on GitHub (e.g. `statele`).
2. Add `index.html` to the root of the repo and push:
   ```bash
   git init
   git add index.html
   git commit -m "Add Statele game"
   git branch -M main
   git remote add origin https://github.com/<your-username>/statele.git
   git push -u origin main
   ```
3. In the repo, go to **Settings → Pages**.
4. Under **Build and deployment → Source**, choose **Deploy from a branch**.
5. Set the branch to **main** and the folder to **/ (root)**, then **Save**.
6. Wait a minute, then visit `https://<your-username>.github.io/statele/`.

## Landmark photos

The three landmark rounds use **real photos**, loaded from Wikipedia at play-time
(so they need an internet connection — fine for GitHub Pages or any browser). You
first pick the state's landmark from four photos with **no names**, then name that
photo from four options, then pin its location. A **"See answer & skip"** button is
always available.

If a photo can't be fetched for a round, it falls back to labelled emoji cards so it
stays playable. To pin a specific image, add `"Landmark name": "https://your-host/photo.jpg"`
to the `LMIMG` map near the top of the script (it overrides the Wikipedia lookup);
the `LM_WIKI` map just below maps a landmark to a specific Wikipedia article title
where the two differ.

## Notes & caveats

- **Cultural facts are hand-curated** for fun and practice — capitals, rivers,
  landmarks, languages. The geography (shapes, areas, neighbours, capital/landmark
  coordinates) is computed from current boundary data and is reliable; the cultural
  details are best-effort. Corrections are easy — they live in a single `DATA`
  object near the top of the embedded script.
- A few very small union territories (e.g. **Lakshadweep**) have tiny footprints,
  so their silhouettes are hard to recognize by shape alone — lean on the distance
  and direction clues there.
- District boundaries (used for the largest-district round) come from a 2011-era
  district dataset, so the "largest district" reflects those boundaries; India has since
  created many new districts, but the biggest by area (e.g. Kutch, Jaisalmer, Leh) is stable.
- Boundaries are simplified for fast loading and are meant for a game, not for any
  official or legal use.
- Not affiliated with Worldle or Teuteuf Games — an independent homage.
