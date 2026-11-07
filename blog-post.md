# I Built a Web Game with AI in One Session — And You Can Too at AWS Student Community Day Buea, 21 November 2026

> **Come build with us.** AWS Student Community Day Buea is happening on **21 November 2026** at the University of Buea. If you are a student who wants to learn how AI-powered tools are changing how software gets built, this is exactly the event for you. [Register and follow updates from the AWS Student Builder Group at the University of Buea.]

---

🎮 **Play It Now:** [PASTE LIVE GITHUB PAGES URL HERE]

💻 **Explore the Source Code:** [https://github.com/defangjunior5-arch/Webgame](https://github.com/defangjunior5-arch/Webgame)

---

## Introduction: An Idea Turned Into a Real Game in a Single Session

Imagine sitting down with just an idea — no starter code, no templates, no teammates to ask for help — and walking away an hour or two later with a fully working, polished web game you built yourself. That is exactly what happened to me during **Pre-Session 4** of the AWS Student Community Day Buea preparation series, organized by the **AWS Student Builder Group at the University of Buea**.

The tool that made it possible? **Kiro IDE** — an AI-powered development environment that sits right inside your editor and writes, refines, and explains code alongside you.

I am not going to pretend I typed every line myself. That is the whole point. Kiro IDE is built so you can focus on *what* you want to build, while it handles a huge chunk of the *how*. This post is my honest account of that experience — what I built, how the prompts I used shaped the final product, where things got tricky, and what I took away from it.

---

[SCREENSHOT 1: The completed Memory Match game running in the browser]

---

## What I Built: Memory Match 🃏

The game is called **Memory Match**. It is a classic card-flipping memory game — a 4×4 grid of 16 face-down cards, each hiding one of eight emoji characters (🦊 🐸 🦁 🐙 🦋 🐳 🌸 🎸). You click a card to flip it, then try to find its matching pair. Matched pairs stay face-up with a satisfying green glow. Unmatched ones flip back after a short delay, and the challenge is to remember where each emoji was.

But the final version is far more than just a grid of cards. Here is what ended up in the game after the session:

- **Three difficulty levels** — Easy, Medium, and Hard. Difficulty changes the speed of the flip animation, how quickly unmatched cards flip back (1400 ms on Easy vs 450 ms on Hard), and whether there is a time limit. Hard mode adds a 90-second countdown that turns red and ticks loudly when you are down to the last 10 seconds.
- **A move counter and timer** — every attempt counts as a move, and your time is tracked from the first card flip.
- **A persistent high-score system** — your best score (fewest moves, with time as a tiebreaker) is saved per difficulty level in the browser's `localStorage`, so it survives page refreshes and browser restarts.
- **Ten synthesised sound effects** — every meaningful event has audio feedback: flipping a card, finding a match, failing a match, completing the last pair, winning, running out of time, starting a new game, setting a new best score, selecting a difficulty, and the Hard mode countdown tick. Every sound is generated live using the Web Audio API — there are zero external audio files.
- **A welcoming start screen** with a how-to-play guide, animated floating preview cards, and the difficulty selector, so first-time players know exactly what to do.
- **Canvas confetti** that fires on a win.
- **A professional visual design** — Inter font, a CSS design-token system, an animated mesh gradient background, glass-morphism card backs with a shimmer hover effect, layered shadows, and smooth spring animations throughout.

The entire game lives in a **single HTML file** — no frameworks, no build tools, no dependencies beyond a Google Fonts link.

---

## Building With Kiro IDE: Prompts, Code, and Iteration

[SCREENSHOT 2: Kiro IDE during development]

The session started with the simplest possible prompt:

> *"Build a Memory Match card game as a single HTML file. Create a 4×4 grid of cards face down. When clicked, cards flip to reveal emojis. If two flipped cards match, they stay face up. If not, they flip back after a moment. Track the number of moves and time. Show a victory message when all pairs are matched. Make it colorful and fun."*

Kiro generated a complete, working game from that one description. Cards flipped with a 3D CSS rotation, the grid was laid out correctly, matching logic worked, the victory screen appeared — all of it, from a single sentence of intent.

From there the session became a conversation. Each follow-up prompt added a new layer:

> *"Add sound effects for when the player scores, when the game ends, and for other important events. Use free web audio APIs so it works without any external files."*

Kiro built an entire synthesised audio engine using the Web Audio API — oscillators, gain nodes, bandpass filters, frequency ramps — ten distinct sounds, none of them requiring a single audio file to download.

> *"Add a high score system that saves the best score in the browser's local storage, so it persists between sessions. Display the high score alongside the current score."*

This added `localStorage` read/write logic, a scoring comparison function (fewest moves first, time as tiebreaker), a "🏆 New Best Score!" badge on the victory screen, and a per-difficulty storage key system.

> *"Add difficulty levels (Easy, Medium, Hard) that the player can choose before starting. Each level should change the game speed or challenge appropriately."*

Kiro introduced a difficulty configuration object, a CSS custom property (`--flip-dur`) that changes the card animation speed, a 90-second countdown mode on Hard complete with red-pulsing timer and audible ticks, and separate high-score records per difficulty.

> *"Add a start screen with the game title, instructions on how to play, and a 'Start Game' button. Make it look welcoming and easy to understand."*

A polished onboarding experience appeared: a full-screen entry with floating animated cards, a four-step how-to-play guide, the difficulty selector, and a large Start Game button — all in the same visual style as the game itself.

> *"Improve the visual design with a modern color scheme, smooth animations, better fonts, and subtle shadows. Give it a professional polished look."*

This is where the game went from "working" to "impressive". Kiro added the Inter font via Google Fonts, replaced every hardcoded colour with a CSS design-token system (custom properties like `--cyan`, `--violet`, `--amber`), added an animated multi-layer radial gradient background, redesigned the stats bar as a unified glass panel, gave card backs a shimmer sweep on hover, and tightened every animation curve to use spring easing.

[SCREENSHOT 3: Examples of prompts used in Kiro IDE]

What made this process feel different from just Googling and copy-pasting is that Kiro always read the existing code before making changes. It never broke what was already working. When I asked for sound effects, it didn't rewrite the card logic. When I asked for a visual redesign, it didn't touch a single line of JavaScript.

---

## Publishing With GitHub Pages

[SCREENSHOT 4: GitHub repository and GitHub Pages deployment]

Once the game was finished, the next step was getting it live so anyone with a link could play it. Here is exactly how to do it:

**Step 1 — Push to GitHub** (already done from the session):
```bash
git init
git add memory-match.html
git commit -m "Initial commit: my first web game"
git branch -m main
git remote add origin https://github.com/defangjunior5-arch/Webgame.git
git push -u origin main
```

**Step 2 — Enable GitHub Pages:**
1. Go to your repository on GitHub: `https://github.com/defangjunior5-arch/Webgame`
2. Click the **Settings** tab
3. In the left sidebar, click **Pages**
4. Under **Source**, select **Deploy from a branch**
5. Set the branch to `main` and the folder to `/ (root)`
6. Click **Save**

GitHub will take about 60–90 seconds to deploy. Your live URL will appear at the top of the Pages settings and will look like:
```
https://defangjunior5-arch.github.io/Webgame/memory-match.html
```

Because the game is a single self-contained HTML file with no server-side logic, GitHub Pages hosts it perfectly with zero configuration.

---

## Challenges and How I Solved Them

**The push to GitHub stalled mid-session.** Git was installed and the repository was set up correctly — the `git push` command just hung waiting for authentication. The fix is a GitHub Personal Access Token (PAT): generate one at *Settings → Developer settings → Personal access tokens*, give it `repo` scope, and paste it as the password when Git prompts you. If you use GitHub CLI (`gh auth login`), it handles this automatically.

**The visual design felt flat at first.** The initial game was functional but looked like a homework project. The prompt for a visual redesign was deliberately vague — "professional polished look" — and Kiro made significant decisions about typography, the colour system, and animation curves. The lesson here is that vague design prompts lead to confident but sometimes unexpected choices. Being more specific ("use Inter font, a dark navy background, and glass-morphism cards") would have got there faster. Iteration is the process.

**Sound on Hard mode became overwhelming.** Adding a countdown tick for every second of the final 10 was the right idea, but the first version fired the same sound as a card flip, making it feel noisy and confusing. Describing the problem to Kiro precisely — "the countdown tick should be a distinct short square-wave beep, not the flip sound" — got an immediate targeted fix without touching any unrelated code.

---

## What I Learned

**Prompt engineering is a real skill.** The quality of what Kiro generates is directly proportional to how clearly you describe what you want. "Make it look nice" and "use a dark navy background with glass-morphism card backs and spring-eased flip animations" produce very different results. The more specific and the more you mention the *feeling* you are after, the better the output.

**Iteration beats perfection.** No single prompt built the whole game. Each one added one thing, tested it mentally, then moved to the next. That incremental loop — describe, generate, review, refine — is the actual workflow. It is faster and less stressful than trying to write a perfect specification upfront.

**Reading the output matters.** Kiro writes code you need to understand, not just run. When it added the Web Audio API engine, reading through the oscillator and gain-node setup taught me more about browser audio than any tutorial would have in the same time. The code is also the documentation.

**One file can be a whole product.** The finished game — start screen, three difficulty levels, sound engine, high scores, confetti, professional visuals — is 1,366 lines in a single `.html` file. No build system, no npm, no frameworks. That is a powerful reminder that the web platform itself is already capable of a lot.

---

## What's Next

The game works well, but there is plenty of room to grow. A few ideas worth trying:

- Add more emoji themes so players can choose (animals, food, space, etc.)
- Build a 6×6 grid for an even harder challenge
- Add a global leaderboard using a simple backend or a service like Supabase
- Add a "preview" phase at the start of each game where all cards are briefly revealed before flipping back — classic memory game behaviour
- Make it a Progressive Web App (PWA) so it can be installed and played offline

More importantly: **try it yourself.** The best way to understand what Kiro IDE can do is to open it, type a description of something you want to build, and see what comes back. You do not need to know how to write a Web Audio API oscillator to end up with one in your project.

---

## Come Build With Us on 21 November 2026

This session was one of several Pre-Session events leading up to **AWS Student Community Day Buea**, taking place on **21 November 2026**. The day is organised by the **AWS Student Builder Group at the University of Buea** and is focused on making cloud and AI-powered developer tools real and accessible for students.

If this post made you curious about what you could build in a single focused session with an AI-powered IDE, imagine spending a full day surrounded by other students experimenting with the same tools, with mentors from the AWS community to help you level up.

Mark your calendar: **21 November 2026**. Follow the AWS Student Builder Group at the University of Buea for registration details and updates.

The barrier to building real things has never been lower. Come see for yourself.

---

*Built with ❤️ and Kiro IDE during Pre-Session 4 of the AWS Student Community Day Buea preparation series.*
