# ZODIAC SEEKER — The Cyber Hunt

A single-page cyber-hunt game. Students log in as "agents", a mission clock
starts at **00:00** the moment they enter, and the leaderboard ranks them by
who cracks **Level 1 in the least time**.

## Files

```
index.html             the entire game (HTML + CSS + JS in one file)
images/case_file.png   the handwritten Zodiac notesheet shown at the end
```

## Run it

Just open `index.html` in any browser — no server, no build, no install.

## Put it on GitHub Pages

1. Create a new repository on GitHub.
2. Upload `index.html`, the `images` folder and this README (keep the folder
   structure exactly as above).
3. Go to **Settings → Pages**.
4. Under *Source* choose **Deploy from a branch**, pick `main` and `/ (root)`,
   then **Save**.
5. After a minute your site is live at
   `https://<your-username>.github.io/<repo-name>/`

## Adding levels

Open `index.html` and scroll to the block marked:

```html
<script id="GAME-CONFIG">
```

Inside it you'll find `const LEVELS = [ ... ]`, currently empty with a template
in the comments. Add one block per level:

```js
{
  title:   "The First Signature",
  riddle:  "Your question text here (HTML allowed).",
  cipher:  "",                   // optional code block, "" to hide it
  answers: ["zodiac"],           // all accepted answers (case/space insensitive)
  hint:    "An optional nudge.", // "" to hide the hint button
  points:  100
},
```

Level 1's timer starts automatically at 00:00 when the agent enters; every
later level starts the instant the previous one is solved. The hunt page,
progress bar, leaderboard and scoring all update themselves — nothing else
needs editing.

### Other settings

In the same block, `SETTINGS` controls:

| Setting | What it does |
| --- | --- |
| `defaultSort` | `"level1"` (default), `"total"` or `"points"` |
| `hintPenaltySeconds` | seconds added when a hint is opened (default 30) |
| `wrongAnswerPenaltySeconds` | seconds added per wrong answer (default 10) |
| `sequential` | whether levels must be solved in order |

## Note on scores

Progress and the leaderboard are saved in each browser's local storage, so
every device keeps its own board. For a shared leaderboard across all students
you'd need a small backend (Firebase, Google Sheets, etc.).
