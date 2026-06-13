# Build brief: the AI literacy guided web tool

## What this is

A small, calm, guided website that walks one person through the same thinking sequence I run as a live staff workshop. It is a self-paced version of an in-person session about building a KS3 AI curriculum. A teacher, or a whole department working through it together, lands on the page and is taken step by step through four moves: rank nine areas of AI, write down the human capacities they want a pupil to develop, mark each capacity against AI, and arrive at a single insight. It ends by sending them to my existing Digital Innovations site to see a curriculum built around exactly that thinking.

The point of the tool is not assessment and not data capture. It is to make one person have the argument with themselves that they would otherwise only have in a room full of colleagues. The structure of the site has to replace the facilitator, so it must be genuinely guided: one step visible at a time, a clear way forward, and no way to get lost.

## Who uses it and where it runs

The audience is teachers and school leaders, often on an iPad or a phone, sometimes on a laptop, frequently with patchy school wifi. So the build must be a single self-contained static site with no backend, no login, no database and no analytics. It needs to be hostable on GitHub Pages alongside my existing project. Everything runs client side. Nothing is sent anywhere. If the person wants to keep their work they can copy it to their clipboard or print the page, and that is the only persistence.

Do not use localStorage or any browser storage API. State lives in memory for the session only. Touch support is essential because most of the audience is on iPads, so any dragging must work with pointer events, not the native HTML5 drag and drop, which fails on touch.

## Technology

A single self-contained HTML file with the CSS and JavaScript inline, vanilla, no framework and no external dependencies or CDNs. This keeps it dependency free, fast on poor connections, and trivial to drop into GitHub Pages. If a framework genuinely helps it can be considered, but the default and strong preference is plain HTML, CSS and JavaScript in one file.

I already have a working drag-and-drop Diamond 9 component built in vanilla JS using pointer events. It can be reused as the engine for step two rather than rebuilt from scratch. The rest of the steps wrap around it.

## Look and feel

Calm, uncluttered, confident. Lots of whitespace. One idea per screen. This is the palette, which matches my slide deck and my Digital Innovations site so the whole thing feels of a piece.

- Ink (primary text and dark panels): `#262338`
- Warm terracotta (the human accent, used for values and for emphasis): `#D9733F`
- Teal (the cool accent, used for AI and tools): `#2F8F83`
- Muted text: `#6E6A82`
- Hairline and borders: `#D9D6E2`
- Warm tint (card and panel backgrounds for human content): `#FAEDE4`
- Teal tint (for AI content): `#E4F0EE`
- Page background: `#FBFAFD`, cards white `#FFFFFF`

Headings in a serif (Georgia is a safe web default), body in the system sans stack. No decorative lines under headings, no gradient banners, no clip art. Card style is a white rounded rectangle with a soft shadow, a small reference letter top left in terracotta, and a small teal dot top right. Keep it close to the printed cards so the physical and digital versions clearly belong together.

For the threat and amplify marks use a clear red `#D64541` for threat and a clear green `#3FA34D` for amplify, kept distinct from the teal. A capacity marked as both shows both colours.

All user-facing copy is UK English, plain, and in a practitioner-to-peer voice. No exclamation marks, no marketing tone.

## The nine areas (data for step two)

Each card has a single letter, a short title and a one-line gloss. Ship the cards in a shuffled order each time so the starting layout does not bias the ranking.

- A. Deepfakes and Disinformation — Can you trust what you see and hear?
- B. Using AI Well — The practical skill of prompting.
- C. Understanding What AI Is — Does it think, or just predict?
- D. Bias in Data — Who gets harmed when data is skewed?
- E. Knowing What to Trust — Checking claims for yourself.
- F. The Environmental Cost — The energy price of every query.
- G. Your Data, Their Model — Your data as raw material.
- H. Keeping Humans in Charge — When must a person decide?
- I. AI Companions — Bonding with a chatbot.

## The guided flow

The site is a single page that shows one step at a time. A slim progress indicator across the top shows the four main stages. Every step has a primary forward button and, after step one, a quiet back button. Forward is enabled only when the step is genuinely complete, so the person cannot skip the thinking.

### Step 1. Welcome

A short title and two sentences of orientation. Something close to: "Nine areas of AI, and a question about what really matters. This will take about ten minutes and works best if you argue with yourself as you go." A single button to begin. Nothing else on screen.

### Step 2. Rank the nine (Diamond 9)

The nine area cards sit in a pool. The person drags them into a diamond of nine slots arranged one, two, three, two, one, with "most important" labelled at the top and "least important" at the bottom. Dragging must work by touch and by mouse. Cards can move between slots and back to the pool, and dropping onto an occupied slot swaps the two cards. The forward button stays disabled until all nine slots are filled.

When all nine are placed, before moving on, show the person their ranking grouped into tiers (most important, more important, middle, less important, least important) with a single quiet line: "Hold that thought. We will come back to it." This plants the ranking so it can be paid off at the end.

### Step 3. The human outline

A clean text-entry screen. The prompt: "Forget AI for a moment. Write the characters, skills and virtues you want a pupil to leave KS3 with." The person adds items one at a time into a growing list, the way you would jot a list on paper. Each item is a short phrase, for example courage, critical thinking, teamwork. They can add and delete freely. Encourage quantity with a gentle hint such as "Most people get to eight or ten." The forward button enables once there are at least, say, four items, so there is something to work with in the next step.

Do not pre-fill the list. The generative act of writing their own list is the whole value of this step.

### Step 4. Mark each one against AI

Now the list they just wrote is shown again, one row per item, each with three toggle options: at threat, can be amplified, both. Use the red and green colours, with both showing the two together. A short instruction: "For each one, ask what AI does to it. Does it threaten it, amplify it, or both?" Every item must be marked before moving on.

This is the step that quietly produces the insight, so the interaction should feel reflective rather than rushed. One clean row per capacity, easy to tap on an iPad.

### Step 5. The insight

Pull out the items the person marked as both and show them together under a line that lands the argument: "The ones you marked both are the whole point. Whether AI threatens or amplifies these comes down to one thing. How the task is set." If they marked nothing as both, show a gentler version that still makes the point, for example: "Even the ones you split into threat or amplify can flip, depending on how the task is set."

Keep this screen still and quiet. It is the punchline, so it should not be busy.

### Step 6. Close and hand off

Tie the whole thing together and send them onward. Copy along these lines: "You ranked nine areas of AI by importance. Then you wrote down what you actually want a pupil to become. A good curriculum is built around the second list, and uses the first only to serve it." Then a clear call to action linking out to my Digital Innovations site so they can see a curriculum built exactly that way.

The link is `https://twade-ai.github.io/Digital-Innovations` and should open in a new tab.

On this final screen also offer a "copy my work" button that puts a plain-text summary of everything the person produced onto the clipboard: their Diamond 9 ranking by tier, their list of human capacities, and how they marked each one. This lets a department lead gather responses by hand if they want to, without any backend. Offer a print option too, since some people will want a paper record.

## Accessibility and robustness

Make the drag usable by touch and mouse, and if it is not too much, give a keyboard or tap-to-place fallback so the diamond can be completed without dragging. Text must meet sensible contrast against its background. The layout must hold together from a narrow phone up to a laptop, with the diamond shrinking gracefully rather than breaking. Buttons and toggles need to be large enough to tap comfortably on an iPad.

## Out of scope

No user accounts, no saved sessions across visits, no server, no database, no third-party analytics or tracking, no cookie banners, no AI calls. Nothing that collects or transmits the person's input. The whole tool is a thinking aid that runs and forgets.

## A note on tone for the build

The site should feel like one of my lessons, not like a product. Calm, a little serious, generous with space, and confident enough to put a single idea on a screen and let it breathe. When in doubt, take something off the screen rather than adding to it.

---

### A starting instruction you can paste into Claude Code

"Build a single self-contained static HTML file, vanilla HTML CSS and JavaScript with no frameworks or external dependencies, hostable on GitHub Pages. It is a guided, one-step-at-a-time web tool that walks a user through the flow described in this brief: a welcome screen, a touch-and-mouse drag-and-drop Diamond 9 ranking of nine AI areas, a text-entry step where the user writes the human capacities they want a KS3 pupil to develop, a step where they mark each capacity as at threat, amplified, or both, an insight screen that surfaces the 'both' items, and a closing screen that links out to https://twade-ai.github.io/Digital-Innovations and offers copy-to-clipboard and print. Use pointer events for dragging so it works on iPad. Do not use localStorage or any storage API. Match the palette and tone in the brief. Build it mobile-first and keep every screen uncluttered."
