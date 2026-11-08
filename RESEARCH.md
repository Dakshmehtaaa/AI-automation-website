# How to build a best-in-class website in November 2026

Research for Daksh's AI automation site. Done 7 Nov 2026 by Claude (Opus 5.5).

## 1. What wins awards right now

- **Immersive 3D won 61% of Awwwards Site of the Day in Q1 2026** (23% in 2024). Source: [Digital Strategy Force, Mar 2026](https://digitalstrategyforce.com/journal/why-are-immersive-experiences-dominating-the-2026-awwwards/).
- Judges reward **spatial thinking, creativity and interaction** over classic layout polish.
- **Scroll-driven stories** win: the page feels like a film you control. Scroll back and it rewinds.
- WebGL 2 is in every browser, and Three.js makes it cheap to build.
- Awwwards "Creative Pass" examples studied: 3D WebGL scroll (Monogrid, Evensix, Vivid Co, Novo Holdings, Fort Vega, Wamos, Cumulus), horizontal scroll, depth scroll, mobile layouts ([awwwards.com/inspiration](https://www.awwwards.com/inspiration/3d-webgl-scroll-monogrid-com)).

### What people love on these sites
1. A live 3D scene behind the text, not a picture.
2. Shapes that **morph** with scroll (particles, objects).
3. Huge, tight display type with very few words.
4. Pinned chapters: the page stops, the content changes, then moves on.
5. Horizontal scroll strip inside a vertical page.
6. Smooth (inertia) scrolling.
7. Big numbers that count up.
8. A short loader that sets the mood.
9. The background colour changing per chapter.
10. Everything reacting to the mouse a little.

## 2. AI design repos people talk about (and what each teaches)

| Repo | What it is | Stars | Lesson used |
| --- | --- | --- | --- |
| [Nutlope/hallmark](https://github.com/nutlope/hallmark) | Anti "AI slop" design skill for Claude Code, Cursor, Codex. By Together AI | 50k | The main rulebook. 80+ "gates" that catch the tells of AI-made pages |
| [Leonxlnx/taste-skill](https://github.com/Leonxlnx/taste-skill) | "Taste" skill: page plan depends on the kind of business | popular | Show the client's real subject; one section per screen; equal edges |
| [pbakaus/impeccable](https://github.com/pbakaus/impeccable) | Design skill + linter + browser extension | popular | Audit by rule, not by feel |
| [anthropics frontend-design](https://github.com/anthropics/claude-code/tree/main/plugins/frontend-design) | Anthropic's own design plugin | official | Pick a bold direction and commit |
| [greensock/gsap-skills](https://github.com/greensock/gsap-skills) | Official GSAP skills for AI agents | official | Correct scroll animation patterns |
| [emilkowalski/skills](https://github.com/emilkowalski/skills) | Motion + UI craft by Emil Kowalski | popular | Easing, duration, performance |
| [INSANE0777/Awwwards-mcp](https://github.com/INSANE0777/Awwwards-mcp) | Lets an agent search Awwwards winners, read palettes/motion, score a build | 245 | Search, build, then score against the reference |
| [AThevon/genjutsu](https://github.com/AThevon/genjutsu) | Motion design skills: write an "interaction thesis" before code | 595 | Decide what moves and why before coding |
| [dembrandt/dembrandt](https://github.com/dembrandt/dembrandt) | Pulls design tokens from any site + 45 UX skills | 3.7k | Tokens first, then components |
| [responsively-org/responsively-app](https://github.com/responsively-org/responsively-app) | Test phone, tablet, desktop at once | 25.4k | Always check the phone |
| [zhuyansen/awesome-claude-design-skills](https://github.com/zhuyansen/awesome-claude-design-skills) | 197 vetted design skills, ranked | list | Where to find more |
| [VoltAgent/awesome-agent-skills](https://github.com/VoltAgent/awesome-agent-skills) | 1000+ agent skills | list | Where to find more |

Picked as the "taste" source: **Hallmark** (most stars, newest, built exactly to stop AI-looking pages, credits all the others as inspiration).

## 3. Hallmark: what humans read as "made by AI" (avoid all)

- A small label above every heading ("eyebrow").
- Small UPPERCASE letter-spaced labels, monospace used as decoration.
- One coloured word inside a headline.
- Purple-to-blue or cyan gradient text.
- Near-black page with one neon accent. Cream paper + serif + clay accent.
- Inter, Roboto, Poppins, Space Grotesk as the headline font.
- Hero + three feature cards + call to action + footer.
- "A · B · C" middle-dot strings, arrows glued to buttons ("Learn more →"), pulsing status dots.
- Em dashes and buzzwords (seamless, empower, unlock, supercharge, elevate).
- Glowing blurred blobs behind text.
- Content hidden until JavaScript runs.
- Invented numbers or testimonials.
- Custom cursors, scroll cues ("Scroll ↓"), "01 / 04" counters.

What it asks for instead: one real idea that only this person has, real facts, few words (under 80 per screen), one strong thing per screen, contrast, keyboard focus, reduced-motion support, and a phone layout that works.

## 4. How it was combined into Daksh's site

**Idea:** *your scroll is the automation.* 14,000 particles = loose tasks. Each scroll step sorts them into a process. Scroll back and the mess returns.

| Chapter | Particles become | Text |
| --- | --- | --- |
| Hero | a swirling cloud (chaos) | "I automate the boring." |
| Before / after | a flowing ribbon | Manual → Mapped, Repetitive → Automated, Messy → Measured (words wipe over) |
| Method (pinned) | flowchart, double helix, sphere, bar chart | Map, Automate, Train, Measure |
| Numbers | a galaxy | 50+, 600, 17, 18, 4, 3+ yrs (all from his CV) |
| Work (horizontal) | a wave field | Honeybees, Dataiku, Thales, Back Market |
| Side project | a network graph | His own multi-agent job pipeline: Find → Screen → Tailor → Audit → Review → Apply |
| Toolbox | chaos again | Power Automate, Power Platform, GenAI, Dataiku, Power BI… (pausable marquee) |
| Contact | a ring (portal), page turns bright cobalt | "Let's automate something of yours." |

- **Look:** night cobalt blue (his AI track colour), one warm amber signal colour for the main button and 3% of particles. Fonts: Rethink Sans (headlines) + Onest (text), both off Hallmark's overused list.
- **Tech:** Three.js 0.160 (WebGL particles, custom shader, mouse pushes particles away), Lenis smooth scroll, plain CSS/JS. No build step. Libraries stored in `vendor/` so GitHub Pages never depends on a CDN.
- **Hallmark fixes applied** after v1 failed: removed eyebrows, caps labels, mono labels, gradient text, accent word, middle dots, status dot, scroll cue, custom cursor, grain, glow bloom, em dashes. Page reads fully without JavaScript. Reduced motion respected. Focus rings on all links.
- **Tested:** desktop 1440 and phone 390, every chapter, no horizontal scroll, no console errors.

## 5. Not done / next

- Hallmark's own linter (`sloplint.mjs`) could not run here (the sandbox blocks running downloaded scripts). Rules were checked by hand.
- Awwwards MCP scoring not run (needs local install).
- Next: GitHub repo + Pages, a share image (og:image), maybe a French version.
