# Who Wants to Be a Millionaire?

> Is that your final answer? A single-file, dependency-free trivia game in the style of the classic quiz show. Lock-in drama, a 50:50 lifeline, and a gold-and-blue climb to $1,000,000.

**Play it live:** [tingzhoudesigns.github.io/Tandem-Millionaire](https://tingzhoudesigns.github.io/Tandem-Millionaire/)

No build step. No npm. No CDN. No fonts or images to load. Just one HTML file you can open, host, or paste into almost any website. The whole game (markup, styling, and logic) lives in a single file and runs entirely in memory, so it drops into restrictive embed contexts without complaining.

It ships with a 12-question sample quiz, but the questions are the easiest thing to swap. Bring your own and the game is yours.

## Live demo

Play it here:

**[https://tingzhoudesigns.github.io/Tandem-Millionaire/](https://tingzhoudesigns.github.io/Tandem-Millionaire/)**

Forking it for your own quiz? Enable GitHub Pages under **Settings → Pages → Deploy from a branch** (`main`, `/root`), and add an empty file named **`.nojekyll`** to the repo root so Pages serves the HTML as-is instead of trying to build it with Jekyll. Your copy will land at `https://<your-username>.github.io/<repo-name>/`.

## Features

- **Truly self-contained.** HTML, CSS, and JavaScript in one file. Zero dependencies, zero network calls, zero local storage.
- **The signature feel.** Pick an option, then hit *Final Answer* to lock it in. A suspenseful pulse builds, then the reveal: correct turns green, a wrong pick turns red while the right answer lights up.
- **A 12-rung money ladder** climbing to $1,000,000, with the current rung highlighted.
- **Safe havens** at rung 4 ($500) and rung 8 ($8,000). Pass one and that money is guaranteed, even if you stumble later.
- **One 50:50 lifeline** per game that knocks out two wrong options.
- **Win and game-over screens** with a clean *Play Again* reset.
- **Classic mood, drawn in pure CSS.** Deep blue spotlight gradient, gold accents, hexagon answer buttons, and all animations done with CSS, no images.
- **Responsive and accessible.** Reflows to mobile, fully keyboard-playable, and respects reduced-motion preferences.

## Quick start

1. Download the HTML file (rename it to `index.html` if you want GitHub Pages to serve it automatically).
2. Open it in any modern browser. That's it. It runs straight from the file.
3. Want it on a site? See **Embed it anywhere** below.

## Embed it anywhere

Because everything is inline and self-contained, embedding is copy-and-paste:

- **Squarespace:** add a **Code Block** to your page and paste the full file contents in.
- **Most site builders / CMSs:** drop the file contents into any raw-HTML or embed block.
- **Your own site:** link to the file, or paste it inline. No assets to wire up.

## Make it your own

Everything you'd want to change sits at the top of the `<script>` block.

**Swap the questions.** Each item needs exactly four options and a `correct` index from `0` to `3` (A=0, B=1, C=2, D=3):

```js
const QUESTIONS = [
  {
    q: "Where is the company headquartered?",
    options: ["Option A", "Option B", "Option C", "Option D"],
    correct: 1   // "Option B" is the right answer
  },
  // ...add as many as you like
];
```

The number of rungs follows your question count, so keep `QUESTIONS` and `LADDER` the same length.

**Retune the money and the safe havens.** `LADDER` lists the prize for each rung (bottom to top); `SAFE_RUNGS` lists the guaranteed checkpoints by rung number:

```js
const LADDER = [100, 200, 300, 500, 1000, 2000, 4000, 8000, 16000, 64000, 250000, 1000000];
const SAFE_RUNGS = [4, 8];
```

**Dial the drama.** Tweak the reveal pacing (in milliseconds):

```js
const PULSE_MS        = 1300; // suspense before the answer is revealed
const CORRECT_HOLD_MS = 1600; // how long the green sits before climbing
const WRONG_HOLD_MS   = 2300; // how long the red/green sits before game over
```

**Rename the title** by editing the `<h1>` near the top of the `<body>`.

## Controls

| Action | How |
| --- | --- |
| Select an answer | Click it, or press **A / B / C / D** (or **1–4**) |
| Lock it in | Click **Final Answer** (or focus it and press **Enter**) |
| Use the lifeline | Click **50:50** (once per game) |
| Navigate by keyboard | **Tab** between controls; focus rings are always visible |

## Accessibility

- Fully keyboard operable with visible focus states.
- Correct/incorrect verdicts and prize changes are announced via an ARIA live region for screen readers.
- Honors `prefers-reduced-motion` by dropping the pulses and shimmer.
- Layout reflows down to small screens (the money ladder collapses to a scrollable strip up top).

## Under the hood

Around 600 lines of vanilla HTML, CSS, and JavaScript. A few touches worth a peek if you're curious: the hexagon answer buttons are shaped entirely with CSS `clip-path` (no image assets), and the focus and selection glows use `filter: drop-shadow()` so the highlight traces the hexagon outline instead of a boring rectangle.

## Browser support

Any modern browser (Chrome, Edge, Firefox, Safari). It leans on `clip-path` and CSS custom properties, both broadly supported.

## License

MIT. Use it, remix it, swap in your own questions, ship it wherever. Add a `LICENSE` file to make it official.

## Credits

Created by **Ting Zhou** — [tingzhoudesigns.com](https://tingzhoudesigns.com)
