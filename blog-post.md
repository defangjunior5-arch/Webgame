# I Built a Web Game With AI in One Session — Join Us at AWS Student Community Day Buea, 21 November 2026!

> **You're invited!** AWS Student Community Day Buea — **21 November 2026**, University of Buea.
> Follow the **AWS Student Builder Group at the University of Buea** for registration details.

🎮 **Play It Now:** [Play Memory Match](https://defangjunior5-arch.github.io/Webgame/memory-match.html)
💻 **Source Code:** [GitHub Repository](https://github.com/defangjunior5-arch/Webgame)

---

## The Story

During **Pre-Session 4** of the AWS Student Community Day Buea prep series, I opened **Kiro IDE** — an AI-powered development environment — with zero game-dev experience and one goal: build something real. I chose Memory Match and walked away with a fully polished, live web game.

![Game running in the browser](screenshot-game.png)

---

## What I Built

A 4×4 grid hiding 8 emoji pairs. Flip two cards — match them to keep them open, miss and they flip back. Find all 8 to win.

**All inside one HTML file:**
- 3 difficulty levels (Hard adds a 90-second countdown)
- Stats panel: moves, pairs, timer, and per-difficulty high scores in `localStorage`
- 10 synthesised sound effects via Web Audio API — zero audio files
- Animated start screen with how-to-play guide
- Canvas confetti on win

---

## Building With Kiro IDE

![Kiro IDE with the game open](screenshot-kiro-ide.png)

I typed plain English. Kiro wrote the code — one feature per prompt, never breaking what already worked.

![Kiro responding to the design prompt](screenshot-prompts.png)

**Prompts I used:**
> *"Build a Memory Match card game as a single HTML file… make it colorful and fun."*
> *"Add sound effects using the Web Audio API — no external files."*
> *"Add Easy, Medium, Hard difficulty. Hard gets a 90-second countdown."*
> *"Improve the design — modern colors, better fonts, professional polished look."*

Kiro read existing code before every edit, explained each decision, and never touched what it didn't need to.

---

## Publishing With GitHub Pages

![GitHub Pages live](screenshot-github-pages.png)

Committed the file, pushed to GitHub, then enabled Pages under **Settings → Pages → Deploy from branch → main → Save**. Live in 60 seconds — no config needed for a single HTML file.

---

## Challenges & Lessons

- **Git auth:** `git push` needs a Personal Access Token — generate one at *GitHub → Settings → Developer settings → Tokens*.
- **Be specific.** Precise prompts land closer first try.
- **One feature per prompt.** Test after each, then move on.
- **Read the output.** Generated code is a worked example.

---

## What's Next

More emoji themes, a 6×6 grid, a leaderboard. Fork the repo and build your own version.

---

## See You on 21 November 2026

**AWS Student Community Day Buea** — turn curiosity into real projects. No experience required.

*Built with Kiro IDE · Pre-Session 4 · AWS Student Builder Group, University of Buea*
