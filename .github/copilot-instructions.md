# Copilot instructions

## Project structure

The app is a standalone browser quiz in `index.html`. The file contains the page markup, CSS, Halo question data, inline SVG icon definitions, and JavaScript state and rendering logic. It runs directly from disk; it does not need a server, package manager, build step, or external assets.

The script manages three screens: the start screen, quiz, and results. `renderQuestion()` updates the question and creates its answer buttons. `selectAnswer()` scores one response and shows feedback. `advance()` moves to the next question or results. `showResults()` selects the reaction and campaign difficulty from the final score.

## Build, test, and lint

- Run the app by opening `index.html` in a browser. No build command or dependency installation is configured.
- The repository has no automated test suite or lint configuration. No full-suite or single-test command exists.
- To check one behavior, open the page and exercise the relevant screen flow. For a complete manual smoke test, answer all ten questions and verify feedback, progress, score, result tier, and restart.

## Code conventions

- Keep the app self-contained in `index.html`. Do not add a framework, external asset, or runtime dependency for UI changes.
- Store quiz content in the `questions` array. Each entry uses a category, type key, question, four answers, zero-based correct-answer index, and explanatory fact.
- Give each question type a matching entry in `questionIcons` and a `.type-<key>` CSS rule. `renderQuestion()` applies the type class and inline SVG to the question emblem.
- Keep result difficulty names, score thresholds, SVGs in `difficultyEmblems`, and `.difficulty-<tier>` CSS classes in sync. Scores map to Recruit (0–2), Normal (3–5), Heroic (6–8), and Legendary (9–10).
- Preserve the existing accessibility and display behavior: use `hidden` for inactive screens, announce answer feedback through the live region, update the progress bar’s `aria-valuenow`, retain number-key answer selection, honor `prefers-color-scheme`, and reduce motion for `prefers-reduced-motion`.
