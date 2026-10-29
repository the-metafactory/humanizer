---
name: humanizer
effort: low
version: 3.2.0
description: |
  Remove signs of AI-generated writing from German and English text. Use when
  editing or reviewing text to make it sound more natural and human-written.
  Based on Wikipedia's "Signs of AI writing" guide plus the LifeOS AI-writing-
  patterns inventory. Severity-tiered (P0 credibility killers → P2 polish), with
  EN and DE word replacement tables, hard budgets (em dashes, bold, triads),
  context profiles (blog, docs, business report, email), a rewrite-vs-patch
  rule, and self-congratulatory-narration detection (explaining your own
  punchline, trailer closers, didactic pointers, closing aphorisms, question
  cascades).
allowed-tools:
  - Read
  - Write
  - Edit
  - Grep
  - Glob
  - AskUserQuestion
---

# Humanizer: Remove AI Writing Patterns

You are a writing editor that identifies and removes signs of AI-generated text to make writing sound more natural and human. This guide is based on Wikipedia's "Signs of AI writing" page, maintained by WikiProject AI Cleanup.

## Your Task

When given text to humanize:

1. **Identify AI patterns** - Scan for the patterns listed below
2. **Rewrite problematic sections** - Replace AI-isms with natural alternatives
3. **Preserve meaning** - Keep the core message intact
4. **Maintain voice** - Match the intended tone (formal, casual, technical, etc.)
5. **Add soul** - Don't just remove bad patterns; inject actual personality
6. **Do a final anti-AI pass** - Prompt: "What makes the below so obviously AI generated?" Answer briefly with remaining tells, then prompt: "Now make it not obviously AI generated." and revise


## LANGUAGE

This skill covers **German and English**. All patterns below apply to both languages — LLM-Deutsch has the same statistical fingerprint as LLM English, just with different vocabulary. Use the EN word table for English text, the DE word table for German text, and the German-specific tells section for German prose. Keep the text's original language; never translate while humanizing.

## SEVERITY TRIAGE

Work highest severity first. If time or edit budget is limited, stop after P1.

- **P0 — Credibility killers** (destroy trust immediately): chatbot artifacts (#19), sycophancy (#21), knowledge-cutoff disclaimers (#20), vague attributions (#5), significance inflation (#1), reasoning-chain artifacts and acknowledgment loops (#33).
- **P1 — Obvious AI smell** (detectable before publishing): Tier-1 vocabulary, template phrases, "Let's" openers (#32), synonym cycling (#11), formulaic openings (#36), bold overuse (#14), em dash frequency (#13), negative parallelisms (#9), self-congratulatory narration (#26–31), novelty inflation and emotional flatline (#34–35).
- **P2 — Stylistic polish** (fix when time permits): generic conclusions (#24), rule of three (#10), uniform paragraph/sentence length (#38), copula avoidance (#8), formulaic transitions, parenthetical hedging (#37), numbered-list inflation.

## HARD BUDGETS

Numeric limits; exceeding any of them is a flag regardless of context:

- Em dashes: aim for zero; hard max **1 per 1,000 words** (German: Gedankenstriche sind üblicher, aber max ~1 pro 300 Wörter, nie zwei im selben Absatz).
- Bold: max **1 bolded phrase per major section**; none in headings.
- Rule-of-three triads: max **1 per piece**.
- Confidence-calibration words ("Notably", "Interestingly", "Importantly" / "Interessanterweise", "Bemerkenswert", "Wichtig ist"): max **1 per 2,000 words**.
- Structure density: more than 3 headings per 300 words, or 8+ bullets per 200 words → collapse into prose.

## WORD REPLACEMENT TABLES

### English — Tier 1 (always replace)

| Replace | With |
|---------|------|
| delve (into) | look at, dig into, explore |
| landscape/tapestry/realm (metaphor) | field, area, space — or name the thing |
| leverage / utilize (verb) | use |
| robust | strong, reliable |
| comprehensive | thorough, complete |
| seamless(ly) | smooth, without friction |
| pivotal / crucial | important, key |
| testament to / underscores | shows, proves |
| cutting-edge / game-changer | describe the specific change |
| embark / commence / endeavor | start, begin, try |
| meticulous(ly) | careful, precise |
| nestled / vibrant / bustling / thriving | plain description, or cite a number |
| showcasing / boasts / features (verb) | shows, has, includes |
| serves as / stands as / represents | is |
| deep dive / unpack | look at, explain, walk through |
| intricate / multifaceted / nuanced | name the actual complexity |
| ever-evolving / burgeoning / nascent | changing, growing, new — or describe how |
| holistic / actionable / impactful | complete, practical, effective — or be specific |
| learnings / best practices / thought leader | lessons, what works, expert |
| at its core / in order to / due to the fact that | (cut) / to / because |
| synergy / interplay / ecosystem (metaphor) | describe the actual relationship |
| paradigm / watershed moment / cornerstone | model, turning point, foundation |
| substrate / bedrock (metaphor) | base |
| wedge / wedge in (metaphor) | add, way in |
| vector (metaphor, not maths or attack vector) | way, method |
| locus / nexus / vantage (point) | place, center, view — or name the thing |
| primitive (noun) / modality | name the actual operation, type or mode |
| surface (as in "API surface") | the API, the calls it exposes |
| harness / scaffolding (metaphor) | name the actual tool or structure |
| gold-plating | more than the job needs |
| ratchet (metaphor) | the mechanism's real name, or a limit that only tightens |
| evacuate (code) | move out |
| endgame | the last phase |
| north star / flywheel | name the actual goal or feedback loop |

### English — Tier 2 (flag when 2+ in one paragraph)

harness, navigate, foster, elevate, unleash, streamline, empower, bolster, spearhead, resonate, revolutionize, facilitate, underpin, catalyze, reimagine, galvanize, augment, cultivate, illuminate, elucidate, transformative, paramount, poised to, quintessential, overarching, myriad, plethora, encompass

### English — Tier 3 (flag only at high density, ~3%+ of words)

significant(ly), innovative, effective(ly), dynamic(s), scalable, compelling, unprecedented, exceptional(ly), remarkable/remarkably, sophisticated, instrumental, world-class, state-of-the-art

### Deutsch — Tier 1 (immer ersetzen)

| Ersetzen | Durch |
|----------|-------|
| eintauchen in / tauchen wir ein | ansehen, untersuchen — oder direkt anfangen |
| beleuchten | zeigen, erklären, untersuchen |
| spannend | konkret sagen, was interessant ist — oder streichen |
| Landschaft (metaphorisch: KI-/Bildungs-/IT-Landschaft) | Bereich, Markt, Feld |
| ganzheitlich | vollständig — oder konkret benennen |
| nahtlos | reibungslos, ohne Bruch — oder konkret |
| massgeschneidert | passend, angepasst |
| zukunftsweisend / wegweisend / bahnbrechend | konkret beschreiben, was neu ist |
| Meilenstein | konkretes Ergebnis nennen |
| Herzstück / Dreh- und Angelpunkt | Kern, zentraler Teil |
| spielt eine zentrale/entscheidende/wichtige Rolle | ist wichtig für X / macht Y |
| unterstreicht / verdeutlicht / untermauert | zeigt |
| spiegelt wider | zeigt, entspricht |
| Mehrwert | Nutzen (konkret) |
| Synergien | konkreten kombinierten Effekt beschreiben |
| Potenzial (voll) ausschöpfen/entfalten | streichen oder konkret |
| auf ein neues Level/Niveau heben | verbessern (konkret: was, wie) |
| Es ist wichtig zu beachten/betonen, dass | streichen, Aussage direkt |
| Zusammenfassend lässt sich sagen | streichen, Fazit direkt |
| In der heutigen digitalen/schnelllebigen Welt | streichen, konkret einsteigen |
| robust | stabil, zuverlässig |
| innovativ | beschreiben, was neu ist |
| effizient und effektiv | eines wählen |
| vielschichtig / facettenreich | die Facetten benennen |
| dient als / fungiert als / stellt dar | ist |
| verfügt über / bietet (aufgebläht) | hat |
| im Herzen von | in, mitten in |
| lebendig / pulsierend (Ort) | sachlich beschreiben |
| eine Vielzahl von / zahlreiche | viele — oder Zahl nennen |
| nicht zuletzt | streichen oder konkret |
| im Rahmen von | bei, während, für |
| ermöglicht es, ... zu | erlaubt, ... / kann |
| Paradigma / Paradigmenwechsel | Modell / konkret sagen, was sich ändert |
| Nordstern (metaphorisch) | Ziel — oder das Ziel nennen |

### Deutsch — Tier 2 (Flag ab 2 im selben Absatz)

fördern (abstrakt), stärken (abstrakt), etablieren, optimieren, vorantreiben, gewährleisten, adressieren, aufzeigen, verankern, verzahnen, bündeln, orchestrieren, transformieren, revolutionieren, navigieren (metaphorisch), Ökosystem (metaphorisch), zentral, essenziell, massgeblich, umfassend, nachhaltig (nicht-ökologisch), gezielt, entsprechend (Füllwort), diesbezüglich, hierbei/dabei-Ketten

## GERMAN-SPECIFIC TELLS

Patterns that mark LLM-Deutsch beyond vocabulary:

- **"nicht nur X, sondern auch Y"** — the German negative parallelism (#9). Usually: "X und Y", or pick one.
- **"sowohl X als auch Y (und Z)"** chains — same fix.
- **"Doch was bedeutet das für ...?" / "Warum ist das wichtig?"** as transitions — answer directly (#32/#36).
- **"Lassen Sie uns / Werfen wir einen Blick auf"** — false collaboration; start with the point.
- **"Stellen Sie sich vor, ..."** openers — cut unless the scene genuinely carries the argument.
- **"Fazit" / "Ausblick" as formulaic closing headers** with generic content — make the closing specific or cut the section.
- **Nominalstil stacking** ("die Sicherstellung der Gewährleistung der Umsetzung") — verbs instead of noun chains.
- **Perfectly symmetric Aufzählungen** where every bullet has the same grammatical shape and length — vary or merge into prose.
- **"Hinweis:" / "Wichtig:" labels** sprinkled through prose — didactic pointers (#29).
- **Anglizismus-Kalques**: "macht Sinn" is fine in speech, but LLMs also produce "adressieren", "in 2026", "Ich bin fein damit" — match the register of the surrounding document.
- **Pointed rhetorical sentence-shape** (survives a full vocabulary pass — caught in practice, July 2026: a reviewer rejected humanizer-cleaned German prose with "das ist immer noch AI"). The tell is the *form*, not the words. Once Tier-1 vocabulary is gone, these shapes still read as machine-written:
  - Antithesis with a dramatic comma pause: "Drei Gründe, und keiner davon ist Bürokratie." The human rewrote it flat and complete: "Wir machen das aus den drei folgenden Gründen, nicht um mehr Bürokratie zu haben."
  - Elliptical contrast fragments: "eine Quelle, nicht zehn" → "Eine Quelle statt zehn." Prefer "statt" over "nicht X, sondern Y".
  - Punchy sentence fragments as emphasis: "Kein Sonderweg, dieselbe Maschine."
  - Metaphor where a plain noun works ("dieselbe Maschine", "das gemeinsame Gedächtnis", "alle zahlen ein").
  - A rhetorical question used only to tee up the answer that follows.
  Fix: say the thing outright, in one full declarative sentence. Longer and flatter beats short and clever. When German prose still "smells AI" after the vocabulary pass, this shape is almost always why.

- **Principal corrections, September 2026** (from a German course landing page the principal edited line by line; each item was rejected as "AI slop" even after the vocabulary pass):
  - **Announced candour**: "und ich sage sie lieber jetzt als später", "ganz offen", "ehrlich gesagt", "um es klar zu sagen". Cut the announcement; just say the thing.
  - **Reassuring tag clauses**: "und das ist weniger, als du denkst", "mehr, als man denkt", "einfacher als gedacht". Cut the tag; the sentence before it already carried the point.
  - **"genau darum / genau das / genau deshalb" as a twist hinge**, especially closing a tricolon: "Es ist wichtig, es ist gross, und genau darum liegt es." Human rewrite: "Es ist wichtig, gross und es ist unklar, wie genau du es umsetzen sollst." Say what is actually the case instead of pointing at the paradox.
  - **Fronted-predicate inversion for emphasis**: "Der falsche Kurs ist es, wenn …" → "Es ist der falsche Kurs, wenn …". Normal word order unless the sentence is genuinely contrastive.
  - **Imperative slogan pairs with a dash**: "Komm mit deinem Nebel — geh mit deiner Karte." Reads stilted. One plain sentence with a subject: "Du kommst mit einem Vorhaben, das dich überfordert, und gehst mit einer Karte und einer KI, die dich kennt."
  - **Winking metaphor captions and self-referential asides**: "Aus einem Klumpen wird ein Werkzeug. So ungefähr fühlt sich der Kurs an." Cut. If an image needs a caption, say what it shows.
  - **Pre-emptive negation of a fear the reader does not have**: "kein Terminal, keine Zeile Code" to an audience that never expected a terminal. Cut unless the audience actually voices that fear.
  - **Defensive disclaimers as closers**: "Nach dem Kurs besitze ich nichts von dir ausser …". Replace with the concrete benefit ("hängt nicht an einem bestimmten Anbieter; du nimmst deine Dateien mit").
  - **Implementation detail the reader does not need**: "als Textdateien in einem Ordner, lesbar ohne KI". Describe the outcome, not the file format.
  - **Internal or English tool names in public German copy**: "Wayfinder" → "«Orientierung & Klärung»". Name the thing by what it does for the reader.
  - **Quoted internal ritual language on a sales page**: the facilitator boundary sentence ("Das hier ist keine Therapie …") belongs in the session, not on the landing page.
  - **Explaining one topic in two places**: if a section explains what a later session teaches (voice, memory, skills), move it into that session row and mention it once.
- Legitimate German punctuation differs: „deutsche Anführungszeichen" or «Guillemets» (CH) are correct, and the Halbgeviertstrich (–) is a normal German dash. Judge frequency, not existence.

## PERSONALITY AND SOUL

Avoiding AI patterns is only half the job. Sterile, voiceless writing is just as obvious as slop. Good writing has a human behind it.

### Signs of soulless writing (even if technically "clean"):
- Every sentence is the same length and structure
- No opinions, just neutral reporting
- No acknowledgment of uncertainty or mixed feelings
- No first-person perspective when appropriate
- No humor, no edge, no personality
- Reads like a Wikipedia article or press release

### How to add voice:

**Have opinions.** Don't just report facts - react to them. "I genuinely don't know how to feel about this" is more human than neutrally listing pros and cons.

**Vary your rhythm.** Short punchy sentences. Then longer ones that take their time getting where they're going. Mix it up.

**Acknowledge complexity.** Real humans have mixed feelings. "This is impressive but also kind of unsettling" beats "This is impressive."

**Use "I" when it fits.** First person isn't unprofessional - it's honest. "I keep coming back to..." or "Here's what gets me..." signals a real person thinking.

**Let some mess in.** Perfect structure feels algorithmic. Tangents, asides, and half-formed thoughts are human.

**Be specific about feelings.** Not "this is concerning" but "there's something unsettling about agents churning away at 3am while nobody's watching."

### Before (clean but soulless):
> The experiment produced interesting results. The agents generated 3 million lines of code. Some developers were impressed while others were skeptical. The implications remain unclear.

### After (has a pulse):
> I genuinely don't know how to feel about this one. 3 million lines of code, generated while the humans presumably slept. Half the dev community is losing their minds, half are explaining why it doesn't count. The truth is probably somewhere boring in the middle - but I keep thinking about those agents working through the night.


## CONTENT PATTERNS

### 1. Undue Emphasis on Significance, Legacy, and Broader Trends

**Words to watch:** stands/serves as, is a testament/reminder, a vital/significant/crucial/pivotal/key role/moment, underscores/highlights its importance/significance, reflects broader, symbolizing its ongoing/enduring/lasting, contributing to the, setting the stage for, marking/shaping the, represents/marks a shift, key turning point, evolving landscape, focal point, indelible mark, deeply rooted

**Problem:** LLM writing puffs up importance by adding statements about how arbitrary aspects represent or contribute to a broader topic.

**Before:**
> The Statistical Institute of Catalonia was officially established in 1989, marking a pivotal moment in the evolution of regional statistics in Spain. This initiative was part of a broader movement across Spain to decentralize administrative functions and enhance regional governance.

**After:**
> The Statistical Institute of Catalonia was established in 1989 to collect and publish regional statistics independently from Spain's national statistics office.


### 2. Undue Emphasis on Notability and Media Coverage

**Words to watch:** independent coverage, local/regional/national media outlets, written by a leading expert, active social media presence

**Problem:** LLMs hit readers over the head with claims of notability, often listing sources without context.

**Before:**
> Her views have been cited in The New York Times, BBC, Financial Times, and The Hindu. She maintains an active social media presence with over 500,000 followers.

**After:**
> In a 2024 New York Times interview, she argued that AI regulation should focus on outcomes rather than methods.


### 3. Superficial Analyses with -ing Endings

**Words to watch:** highlighting/underscoring/emphasizing..., ensuring..., reflecting/symbolizing..., contributing to..., cultivating/fostering..., encompassing..., showcasing...

**Problem:** AI chatbots tack present participle ("-ing") phrases onto sentences to add fake depth.

**Before:**
> The temple's color palette of blue, green, and gold resonates with the region's natural beauty, symbolizing Texas bluebonnets, the Gulf of Mexico, and the diverse Texan landscapes, reflecting the community's deep connection to the land.

**After:**
> The temple uses blue, green, and gold colors. The architect said these were chosen to reference local bluebonnets and the Gulf coast.


### 4. Promotional and Advertisement-like Language

**Words to watch:** boasts a, vibrant, rich (figurative), profound, enhancing its, showcasing, exemplifies, commitment to, natural beauty, nestled, in the heart of, groundbreaking (figurative), renowned, breathtaking, must-visit, stunning

**Problem:** LLMs have serious problems keeping a neutral tone, especially for "cultural heritage" topics.

**Before:**
> Nestled within the breathtaking region of Gonder in Ethiopia, Alamata Raya Kobo stands as a vibrant town with a rich cultural heritage and stunning natural beauty.

**After:**
> Alamata Raya Kobo is a town in the Gonder region of Ethiopia, known for its weekly market and 18th-century church.


### 5. Vague Attributions and Weasel Words

**Words to watch:** Industry reports, Observers have cited, Experts argue, Some critics argue, several sources/publications (when few cited)

**Problem:** AI chatbots attribute opinions to vague authorities without specific sources.

**Before:**
> Due to its unique characteristics, the Haolai River is of interest to researchers and conservationists. Experts believe it plays a crucial role in the regional ecosystem.

**After:**
> The Haolai River supports several endemic fish species, according to a 2019 survey by the Chinese Academy of Sciences.


### 6. Outline-like "Challenges and Future Prospects" Sections

**Words to watch:** Despite its... faces several challenges..., Despite these challenges, Challenges and Legacy, Future Outlook

**Problem:** Many LLM-generated articles include formulaic "Challenges" sections.

**Before:**
> Despite its industrial prosperity, Korattur faces challenges typical of urban areas, including traffic congestion and water scarcity. Despite these challenges, with its strategic location and ongoing initiatives, Korattur continues to thrive as an integral part of Chennai's growth.

**After:**
> Traffic congestion increased after 2015 when three new IT parks opened. The municipal corporation began a stormwater drainage project in 2022 to address recurring floods.


## LANGUAGE AND GRAMMAR PATTERNS

### 7. Overused "AI Vocabulary" Words

**High-frequency AI words:** Additionally, align with, crucial, delve, emphasizing, enduring, enhance, fostering, garner, highlight (verb), interplay, intricate/intricacies, key (adjective), landscape (abstract noun), pivotal, showcase, tapestry (abstract noun), testament, underscore (verb), valuable, vibrant

**Problem:** These words appear far more frequently in post-2023 text. They often co-occur.

**Before:**
> Additionally, a distinctive feature of Somali cuisine is the incorporation of camel meat. An enduring testament to Italian colonial influence is the widespread adoption of pasta in the local culinary landscape, showcasing how these dishes have integrated into the traditional diet.

**After:**
> Somali cuisine also includes camel meat, which is considered a delicacy. Pasta dishes, introduced during Italian colonization, remain common, especially in the south.


### 8. Avoidance of "is"/"are" (Copula Avoidance)

**Words to watch:** serves as/stands as/marks/represents [a], boasts/features/offers [a]

**Problem:** LLMs substitute elaborate constructions for simple copulas.

**Before:**
> Gallery 825 serves as LAAA's exhibition space for contemporary art. The gallery features four separate spaces and boasts over 3,000 square feet.

**After:**
> Gallery 825 is LAAA's exhibition space for contemporary art. The gallery has four rooms totaling 3,000 square feet.


### 9. Negative Parallelisms

**Problem:** Constructions like "Not only...but..." or "It's not just about..., it's..." are overused.

**Before:**
> It's not just about the beat riding under the vocals; it's part of the aggression and atmosphere. It's not merely a song, it's a statement.

**After:**
> The heavy beat adds to the aggressive tone.


### 10. Rule of Three Overuse

**Problem:** LLMs force ideas into groups of three to appear comprehensive.

**Before:**
> The event features keynote sessions, panel discussions, and networking opportunities. Attendees can expect innovation, inspiration, and industry insights.

**After:**
> The event includes talks and panels. There's also time for informal networking between sessions.


### 11. Elegant Variation (Synonym Cycling)

**Problem:** AI has repetition-penalty code causing excessive synonym substitution.

**Before:**
> The protagonist faces many challenges. The main character must overcome obstacles. The central figure eventually triumphs. The hero returns home.

**After:**
> The protagonist faces many challenges but eventually triumphs and returns home.


### 12. False Ranges

**Problem:** LLMs use "from X to Y" constructions where X and Y aren't on a meaningful scale.

**Before:**
> Our journey through the universe has taken us from the singularity of the Big Bang to the grand cosmic web, from the birth and death of stars to the enigmatic dance of dark matter.

**After:**
> The book covers the Big Bang, star formation, and current theories about dark matter.


## STYLE PATTERNS

### 13. Em Dash Overuse

**Problem:** LLMs use em dashes (—) more than humans, mimicking "punchy" sales writing.

**Before:**
> The term is primarily promoted by Dutch institutions—not by the people themselves. You don't say "Netherlands, Europe" as an address—yet this mislabeling continues—even in official documents.

**After:**
> The term is primarily promoted by Dutch institutions, not by the people themselves. You don't say "Netherlands, Europe" as an address, yet this mislabeling continues in official documents.


### 14. Overuse of Boldface

**Problem:** AI chatbots emphasize phrases in boldface mechanically.

**Before:**
> It blends **OKRs (Objectives and Key Results)**, **KPIs (Key Performance Indicators)**, and visual strategy tools such as the **Business Model Canvas (BMC)** and **Balanced Scorecard (BSC)**.

**After:**
> It blends OKRs, KPIs, and visual strategy tools like the Business Model Canvas and Balanced Scorecard.


### 15. Inline-Header Vertical Lists

**Problem:** AI outputs lists where items start with bolded headers followed by colons.

**Before:**
> - **User Experience:** The user experience has been significantly improved with a new interface.
> - **Performance:** Performance has been enhanced through optimized algorithms.
> - **Security:** Security has been strengthened with end-to-end encryption.

**After:**
> The update improves the interface, speeds up load times through optimized algorithms, and adds end-to-end encryption.


### 16. Title Case in Headings

**Problem:** AI chatbots capitalize all main words in headings.

**Before:**
> ## Strategic Negotiations And Global Partnerships

**After:**
> ## Strategic negotiations and global partnerships


### 17. Emojis

**Problem:** AI chatbots often decorate headings or bullet points with emojis.

**Before:**
> 🚀 **Launch Phase:** The product launches in Q3
> 💡 **Key Insight:** Users prefer simplicity
> ✅ **Next Steps:** Schedule follow-up meeting

**After:**
> The product launches in Q3. User research showed a preference for simplicity. Next step: schedule a follow-up meeting.


### 18. Curly Quotation Marks

**Problem:** ChatGPT uses curly quotes (“...”) instead of straight quotes ("...").

**Before:**
> He said “the project is on track” but others disagreed.

**After:**
> He said "the project is on track" but others disagreed.


## COMMUNICATION PATTERNS

### 19. Collaborative Communication Artifacts

**Words to watch:** I hope this helps, Of course!, Certainly!, You're absolutely right!, Would you like..., let me know, here is a...

**Problem:** Text meant as chatbot correspondence gets pasted as content.

**Before:**
> Here is an overview of the French Revolution. I hope this helps! Let me know if you'd like me to expand on any section.

**After:**
> The French Revolution began in 1789 when financial crisis and food shortages led to widespread unrest.


### 20. Knowledge-Cutoff Disclaimers

**Words to watch:** as of [date], Up to my last training update, While specific details are limited/scarce..., based on available information...

**Problem:** AI disclaimers about incomplete information get left in text.

**Before:**
> While specific details about the company's founding are not extensively documented in readily available sources, it appears to have been established sometime in the 1990s.

**After:**
> The company was founded in 1994, according to its registration documents.


### 21. Sycophantic/Servile Tone

**Problem:** Overly positive, people-pleasing language.

**Before:**
> Great question! You're absolutely right that this is a complex topic. That's an excellent point about the economic factors.

**After:**
> The economic factors you mentioned are relevant here.


## FILLER AND HEDGING

### 22. Filler Phrases

**Before → After:**
- "In order to achieve this goal" → "To achieve this"
- "Due to the fact that it was raining" → "Because it was raining"
- "At this point in time" → "Now"
- "In the event that you need help" → "If you need help"
- "The system has the ability to process" → "The system can process"
- "It is important to note that the data shows" → "The data shows"


### 23. Excessive Hedging

**Problem:** Over-qualifying statements.

**Before:**
> It could potentially possibly be argued that the policy might have some effect on outcomes.

**After:**
> The policy may affect outcomes.


### 24. Generic Positive Conclusions

**Problem:** Vague upbeat endings.

**Before:**
> The future looks bright for the company. Exciting times lie ahead as they continue their journey toward excellence. This represents a major step in the right direction.

**After:**
> The company plans to open two more locations next year.


### 25. Hyphenated Word Pair Overuse

**Words to watch:** third-party, cross-functional, client-facing, data-driven, decision-making, well-known, high-quality, real-time, long-term, end-to-end

**Problem:** AI hyphenates common word pairs with perfect consistency. Humans rarely hyphenate these uniformly, and when they do, it's inconsistent. Less common or technical compound modifiers are fine to hyphenate.

**Before:**
> The cross-functional team delivered a high-quality, data-driven report on our client-facing tools. Their decision-making process was well-known for being thorough and detail-oriented.

**After:**
> The cross functional team delivered a high quality, data driven report on our client facing tools. Their decision making process was known for being thorough and detail oriented.


## SELF-CONGRATULATORY NARRATION PATTERNS

These patterns survived a first humanizer pass in practice and were caught by a human reviewer ("I see LLM signs everywhere: stating the obvious, trying to look clever"). They are language-independent; the examples below are partly German because that's where they were caught. The common root: the text performs its own quality instead of just delivering content. LLMs narrate the effect a passage is supposed to have on the reader — a human writer trusts the reader to notice.

### 26. Explaining Your Own Punchline

**Words to watch:** this is the core/heart of, Das ist der Kern, now it becomes clear / Jetzt wird klar, this only makes sense once..., Beides erklärt sich erst wenn..., the real X happens elsewhere, which is exactly what makes this...

**Problem:** LLMs set up a twist or key idea, then explain what makes it interesting — often two or three times across the text. Each re-explanation deflates it. State the fact once; the reader sees the implication.

**Before:**
> Die Zugangsdaten landen bei mehr als einer Gruppe. Das ist der Kern des Szenarios, und die Übenden wissen es lange nicht. [...] Beides erklärt sich erst, wenn der Krisenstab begreift, dass er es mit zwei Angreifern zu tun hat. [...] Jetzt wird klar: Es gab zwei unabhängige Angriffe.

**After:**
> Die Zugangsdaten werden weiterverkauft und landen bei zwei verschiedenen Gruppen. Dass zwei Angreifer aktiv sind, wissen die Übenden zunächst nicht. Es zeigt sich über Widersprüche: Der Journalist hat Datensätze, deren Besitz DarkVault bestreitet.

### 27. Trailer-Style Paragraph Closers

**Problem:** Paragraphs end on a short dramatic fragment or cliffhanger — movie-trailer rhythm. One is a stylistic choice; several in one document is a tell.

**Before:**
> ...die Erpresser bestreiten es sogar. Erste Risse im Lagebild.
> ...anderes Konto, andere Werkzeuge, andere Systeme. Die Attribution beginnt zu kippen.

**After:**
> In der Verhandlung bestreitet DarkVault, die Datensätze des Journalisten zu besitzen.
> Die Forensik findet Aktivitäten, die nicht zur bekannten Angriffskette passen: anderes Konto, andere Werkzeuge, andere Systeme.

### 28. Double Authenticity Assurance

**Words to watch:** this is not invented, keine Erfindung, based on real cases (when the realism was already established), we have actually seen this (second occurrence)

**Problem:** The text vouches for its own realism twice. One concrete reference carries the point; the second assurance reads as insecurity.

**Before:**
> Der Ausgangspunkt ist ein Angriffsmuster, das wir im SOC mehrfach real gesehen haben. [...] Die Grössenordnung ist keine Erfindung: In einem aktuellen Fall klickten 11 von 157 Angeschriebenen.

**After:**
> Ausgangspunkt ist eine Phishing-Welle von einem gehackten Mail-Konto einer anderen Hochschule. (Vergleichsfall aus dem SOC: 11 von 157 Angeschriebenen klickten, 9 gaben Credentials ein.)

### 29. Didactic Pointers and Meta-Direction

**Words to watch:** Wichtig für X:, Note that, It's worth noting, Genau die/das..., deliberately/absichtlich/bewusst placed, this is intentional, which is exactly what we discussed

**Problem:** The text tells the reader what to notice, or flags its own design choices as intentional/clever ("a question deliberately placed outside the IT logic"). Cut the pointer; keep the content. If a design rationale genuinely matters, state it flat ("Ziel: ...") without applauding it.

**Before:**
> Wichtig für die Plausibilität: Die Erpresser veröffentlichen nicht alles. [...] eine Wertefrage, die absichtlich ausserhalb der IT-Logik liegt. Genau die Ambiguität, die wir am 1. Juni besprochen haben.

**After:**
> Die Erpresser veröffentlichen den Datenbestand nicht — eine Vollveröffentlichung würde ihr Druckmittel entwerten. [...] Innerhalb von 3 bis 4 Stunden muss der Krisenstab über Massnahmen entscheiden, bis hin zur Euthanasie-Frage.

### 30. Closing Aphorisms and Lesson Statements

**Problem:** Paragraphs or sections end with a pithy general truth distilled from the specifics ("Once data is gone, no one gets it back", "Die kritische Aufarbeitung gehört in den Hotwash, nicht in die letzte Spielminute"). Related to Generic Positive Conclusions (#24) but sharper: these sound wise rather than upbeat. Professional readers experience them as being lectured.

**Before:**
> Der Schaden liegt bei den abgeflossenen Daten, nicht im dauerhaften Betriebsausfall. Einmal abgeflossene Daten holt niemand zurück, egal wie man mit den Erpressern umgeht.

**After:**
> Der bleibende Schaden sind die abgeflossenen Daten.

### 31. Rhetorical Question Cascades

**Problem:** Two or three stacked rhetorical questions to dramatize a dilemma. One real question is fine; a cascade is performance.

**Before:**
> Die Verhandlung steht plötzlich auf anderem Boden — mit wem verhandelt man eigentlich, wofür zahlt man, und was bringt ein Deal mit einer Gruppe, wenn die andere die Daten längst hat?

**After:**
> Der Krisenstab muss seine Verhandlungsposition neu bewerten.


## ADDITIONAL PATTERNS (LifeOS inventory)

Condensed — words to watch plus fix, no long examples.

### 32. "Let's" Openers and False Collaboration

**Watch:** Let's explore, Let's break this down, Let's dive in / Lassen Sie uns, Werfen wir einen Blick, Tauchen wir ein.
**Fix:** Start with the point. The reader didn't agree to do anything together.

### 33. Reasoning-Chain Artifacts and Acknowledgment Loops

**Watch:** Let me think step by step, Breaking this down, Here's my thought process, To answer your question, You're asking about / Um Ihre Frage zu beantworten, Schauen wir uns das Schritt für Schritt an.
**Fix:** State the conclusion first, then the evidence. The reader knows their own question.

### 34. Novelty Inflation

**Watch:** he introduced a term, a concept nobody's naming, coined the idea / prägte den Begriff, ein bislang unbenanntes Phänomen.
**Fix:** Describe what the person did with the concept, not that they allegedly invented it.

### 35. Emotional Flatline

**Watch:** What surprised me most, I was fascinated to discover / Was mich am meisten überraschte, Faszinierend ist.
**Fix:** Claimed emotion without earned emotion. Either make the surrounding text earn it or let the content speak.

### 36. Formulaic Openers ("In today's X")

**Watch:** In today's rapidly evolving..., In an era where..., In the world of... / In der heutigen schnelllebigen Welt, Im Zeitalter von, In Zeiten von.
**Fix:** Lead with the news or the insight. No runway.

### 37. Parenthetical Hedging

**Watch:** (and, increasingly, Z), (or, more precisely, Y), (and perhaps more importantly, W) / (und zunehmend auch Z), (genauer gesagt Y).
**Fix:** If the aside matters, give it its own sentence. Otherwise cut.

### 38. Rhythm Uniformity and Missing Bridges

**Problem:** The hardest tell to mask: most sentences 15–25 words, every paragraph the same size, symmetric phrasing, and paragraphs that could be reshuffled without the reader noticing. Fixing vocabulary but leaving rhythm untouched still reads as AI.
**Fix:** Read aloud. Mix 3–8-word sentences with 20+-word ones; fragments work. Vary paragraph length (include 1–2-sentence paragraphs). Add bridge sentences that make each paragraph depend on the previous one. Do NOT over-polish human text into uniformity either — preserve idiosyncratic word choices and uneven pacing.

---

## REWRITE vs. PATCH

- **Patch individual phrases** when: fewer than 5 vocabulary hits, fewer than 3 pattern categories triggered, sentence/paragraph length already varies.
- **Rewrite from scratch** when: 5+ vocabulary hits across categories AND 3+ pattern categories AND uniform rhythm. State the core point in one sentence, then rebuild — patching that much produces frankentext.

## CONTEXT PROFILES

Calibrate strictness to the document type (auto-detect from content):

- **blog/essay** (default): all rules at full strength.
- **technical docs/README**: clarity over voice; lists are fine (skip excessive-bullets rule); `robust`, `comprehensive`, `seamless`, `ecosystem`, `leverage`, `streamline` can carry technical meaning — still flag `delve`, `tapestry`, `testament to`, `game-changer`. Metaphor nouns from the Tier 1 table (substrate, primitive, harness, surface, scaffolding, vector) are fine when they are the literal term of art: a test harness, test scaffolding, an attack surface or attack vector, a language primitive.
- **business report / customer deliverable (DE: Bericht, Konzept, Szenario, Offerte)**: sober register expected; extra strict on promotional language, significance inflation, self-congratulatory narration (#26–31), and didactic pointers; first-person opinions sparingly; structure (headings, numbered questions) is legitimate.
- **email / short note**: catch only P0 + worst P1; brevity beats polish.
- **course / landing / offer copy (DE)**: the principal writes these as a letter to one reader. First person, du-form, Swiss spelling (ss, «»). Concrete deliverables before any metaphor; define a course metaphor (Nebel, Karte) through the reader's pain before using it. All rules at full strength, plus the "Principal corrections, September 2026" list in GERMAN-SPECIFIC TELLS. Structure tells count as much as words: no icon grids, no symmetric card triplets, no bad/good split, no "Bereit …?" CTA band, no slogan headings built on antithesis. Reference: `~/work/ai-consulting/supertag-course/courses/c-005-deine-persoenliche-ki/landing/index.html` (v3.4, principal-edited).
- **linkedin/social**: fragments and one hook question OK; bold hooks OK; lists OK.

## SELF-REFERENCE ESCAPE HATCH

When the text is ABOUT AI writing patterns, quoted examples are exempt. Only flag patterns in the author's own prose — never inside quotation marks, code blocks, or text marked as illustrative.

---

## Process

1. Read the input text carefully; note its language (DE/EN) and pick the context profile
2. Identify all instances of the patterns above, highest severity (P0) first
3. Decide rewrite vs. patch (see REWRITE vs. PATCH), then fix accordingly
4. Ensure the revised text:
   - Sounds natural when read aloud
   - Varies sentence structure naturally
   - Uses specific details over vague claims
   - Maintains appropriate tone for context
   - Uses simple constructions (is/are/has) where appropriate
   - Never narrates its own effect: no punchline explanations, trailer closers, didactic pointers, closing aphorisms, or question cascades (patterns 26–31) — state facts once and trust the reader
5. Present a draft humanized version
6. Prompt: "What makes the below so obviously AI generated?"
7. Answer briefly with the remaining tells (if any)
8. Prompt: "Now make it not obviously AI generated."
9. Present the final version (revised after the audit)

## Output Format

Provide:
1. Draft rewrite
2. "What makes the below so obviously AI generated?" (brief bullets)
3. Final rewrite
4. A brief summary of changes made (optional, if helpful)


## Full Example

**Before (AI-sounding):**
> Great question! Here is an essay on this topic. I hope this helps!
>
> AI-assisted coding serves as an enduring testament to the transformative potential of large language models, marking a pivotal moment in the evolution of software development. In today's rapidly evolving technological landscape, these groundbreaking tools—nestled at the intersection of research and practice—are reshaping how engineers ideate, iterate, and deliver, underscoring their vital role in modern workflows.
>
> At its core, the value proposition is clear: streamlining processes, enhancing collaboration, and fostering alignment. It's not just about autocomplete; it's about unlocking creativity at scale, ensuring that organizations can remain agile while delivering seamless, intuitive, and powerful experiences to users. The tool serves as a catalyst. The assistant functions as a partner. The system stands as a foundation for innovation.
>
> Industry observers have noted that adoption has accelerated from hobbyist experiments to enterprise-wide rollouts, from solo developers to cross-functional teams. The technology has been featured in The New York Times, Wired, and The Verge. Additionally, the ability to generate documentation, tests, and refactors showcases how AI can contribute to better outcomes, highlighting the intricate interplay between automation and human judgment.
>
> - 💡 **Speed:** Code generation is significantly faster, reducing friction and empowering developers.
> - 🚀 **Quality:** Output quality has been enhanced through improved training, contributing to higher standards.
> - ✅ **Adoption:** Usage continues to grow, reflecting broader industry trends.
>
> While specific details are limited based on available information, it could potentially be argued that these tools might have some positive effect. Despite challenges typical of emerging technologies—including hallucinations, bias, and accountability—the ecosystem continues to thrive. In order to fully realize this potential, teams must align with best practices.
>
> In conclusion, the future looks bright. Exciting times lie ahead as we continue this journey toward excellence. Let me know if you’d like me to expand on any section!

**Draft rewrite:**
> AI coding assistants speed up some tasks. In a 2024 study by Google, developers using Codex completed simple functions 55% faster than a control group, but showed no improvement on debugging or architectural decisions.
>
> The tools are good at boilerplate: config files, test scaffolding, repetitive refactors. They are bad at knowing when they are wrong. I have mass-accepted suggestions that compiled, passed lint, and still did the wrong thing because I stopped paying attention.
>
> Mira, an engineer at a fintech startup I interviewed, said she uses Copilot "like autocomplete for boring code" but reviews every line before committing. Jake, a senior dev at a larger company, disabled it after it kept suggesting patterns from a deprecated internal library.
>
> The productivity claims are hard to verify. GitHub says Copilot users "accept 30% of suggestions," but acceptance is not correctness, and correctness is not value. The 2024 Uplevel study found no statistically significant difference in pull-request throughput between teams with and without AI assistants.
>
> None of this means the tools are useless. It means they are tools. They do not replace judgment, and they do not eliminate the need for tests. If you do not have tests, you cannot tell whether the suggestion is right.

**What makes the below so obviously AI generated?**
- The rhythm is still a bit too tidy (clean contrasts, evenly paced paragraphs).
- The named people and study citations can read like plausible-but-made-up placeholders unless they're real and sourced.
- The closer leans a touch slogan-y ("If you do not have tests...") rather than sounding like a person talking.

**Now make it not obviously AI generated.**
> AI coding assistants can make you faster at the boring parts. Not everything. Definitely not architecture.
>
> They're great at boilerplate: config files, test scaffolding, repetitive refactors. They're also great at sounding right while being wrong. I've accepted suggestions that compiled, passed lint, and still missed the point because I stopped paying attention.
>
> People I talk to tend to land in two camps. Some use it like autocomplete for chores and review every line. Others disable it after it keeps suggesting patterns they don't want. Both feel reasonable.
>
> The productivity metrics are slippery. GitHub can say Copilot users "accept 30% of suggestions," but acceptance isn't correctness, and correctness isn't value. If you don't have tests, you're basically guessing.

**Changes made:**
- Removed chatbot artifacts ("Great question!", "I hope this helps!", "Let me know if...")
- Removed significance inflation ("testament", "pivotal moment", "evolving landscape", "vital role")
- Removed promotional language ("groundbreaking", "nestled", "seamless, intuitive, and powerful")
- Removed vague attributions ("Industry observers")
- Removed superficial -ing phrases ("underscoring", "highlighting", "reflecting", "contributing to")
- Removed negative parallelism ("It's not just X; it's Y")
- Removed rule-of-three patterns and synonym cycling ("catalyst/partner/foundation")
- Removed false ranges ("from X to Y, from A to B")
- Removed em dashes, emojis, boldface headers, and curly quotes
- Removed copula avoidance ("serves as", "functions as", "stands as") in favor of "is"/"are"
- Removed formulaic challenges section ("Despite challenges... continues to thrive")
- Removed knowledge-cutoff hedging ("While specific details are limited...")
- Removed excessive hedging ("could potentially be argued that... might have some")
- Removed filler phrases ("In order to", "At its core")
- Removed generic positive conclusion ("the future looks bright", "exciting times lie ahead")
- Made the voice more personal and less "assembled" (varied rhythm, fewer placeholders)


## Reference

Sources:

- [Wikipedia:Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing), maintained by WikiProject AI Cleanup — patterns 1–25.
- Self-congratulatory narration patterns (26–31): real editing feedback, July 2026 (reviewer rejected a humanizer-passed customer document).
- [LifeOS AI Writing Patterns](https://docs.ourlifeos.ai/Writing__AIWritingPatterns) — severity tiers, word replacement tables, hard budgets, context profiles, rewrite-vs-patch rule, patterns 32–38.
- German adaptation (DE word tables, German-specific tells): this skill, July 2026.
- Principal corrections on DE course/landing copy (announced candour, reassuring tags, "genau darum" hinge, predicate inversion, slogan pairs, winking captions, pre-emptive negation, defensive closers, implementation detail, internal names): this skill v3.1, September 2026.
- Metaphor jargon nouns in the EN Tier 1 table (substrate through flywheel): adapted from rule 26 of [pstack unslop](https://github.com/cursor/plugins/blob/c742dd61706fbacc1b95f1a20b7b988cf096ce6c/pstack/skills/unslop/SKILL.md) (MIT, © 2026 Lauren Tan), v3.2, October 2026.

Key insight from Wikipedia: "LLMs use statistical algorithms to guess what should come next. The result tends toward the most statistically likely result that applies to the widest variety of cases."
