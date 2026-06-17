# English AI-writing tells (secondary reference)

中文稿用 `patterns-zh.md`。这份是写**英文稿**时才需要的：先看「English-only tells」（中文表里没有、只对英文成立的），再用下面保留的原版 33-pattern 目录做完整对照。

> **Attribution.** This catalog is ported and adapted from **[blader/humanizer](https://github.com/blader/humanizer)** (© 2025 Siqi Chen, MIT License) and **[Wikipedia: Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing)** (WikiProject AI Cleanup). The MIT notice is retained in this plugin's `LICENSE-humanizer` file.

---

## English-only tells（中文表里没有的）

These do not have a Chinese equivalent — only check them on English drafts.

### Em dashes / en dashes — cut them
The final rewrite contains no em dashes (—) or en dashes (–). One of the most reliable AI tells; treat as a hard constraint. Replace each, in rough order of preference: a period (new sentence), a comma (tight aside), a colon (introducing an explanation), parentheses (true aside), or restructure. Also catch spaced em dashes (` — `) and double hyphens (` -- `). Before returning, scan for `—` and `–`; any hit means the draft isn't done.
> Before: The policy — announced without warning — affects thousands.
> After: The policy, announced without warning, affects thousands.

### Curly quotation marks
ChatGPT uses curly quotes (“...”, ‘...’) instead of straight ("...", '...'). Only a tell when stacked with others (most editors auto-curl).
> Before: He said “the project is on track.”  → After: He said "the project is on track."

### Title Case in headings
AI capitalizes all main words in headings; use sentence case.
> Before: ## Strategic Negotiations And Global Partnerships
> After: ## Strategic negotiations and global partnerships

### Hyphenated word-pair overuse
Words: third-party, cross-functional, client-facing, data-driven, decision-making, well-known, high-quality, real-time, long-term, end-to-end. AI hyphenates uniformly, even in predicate position. Keep attributive-position hyphens; drop them when the compound follows the noun.
> Before: The report is high-quality and data-driven.
> After: The report is high quality and data driven.

### Copula avoidance ("serves as" → "is")
Words: serves as / stands as / marks / represents [a], boasts / features / offers [a]. Substitute the simple copula.
> Before: Gallery 825 serves as the exhibition space and boasts 3,000 sq ft.
> After: Gallery 825 is the exhibition space and has 3,000 sq ft.

### High-frequency English AI vocabulary
actually, additionally, align with, crucial, delve, emphasizing, enduring, enhance, fostering, garner, highlight (verb), interplay, intricate/intricacies, key (adj), landscape (abstract), pivotal, showcase, tapestry (abstract), testament, underscore (verb), valuable, vibrant. They appear far more after 2023 and co-occur. Replace with plain words.

---

## Full original catalog（33 patterns，写英文稿时完整对照）

中文表 `patterns-zh.md` 已用中文讲透了其中跨语言的部分；这里保留原版英文 before/after，便于直接套用到英文稿。

### CONTENT PATTERNS
1. **Undue emphasis on significance/legacy** — stands/serves as, is a testament, pivotal moment, underscores its importance, reflects broader, marking a shift, evolving landscape, indelible mark. *Before:* "...established in 1989, marking a pivotal moment in the evolution of regional statistics..." *After:* "...established in 1989 to collect and publish regional statistics."
2. **Undue emphasis on notability/media** — cited in NYT, BBC, FT; active social media presence. Replace with one specific, sourced fact.
3. **Superficial -ing analyses** — highlighting/ensuring/reflecting/showcasing tacked on for fake depth. Cut the participle tail; state the fact.
4. **Promotional / advertisement language** — boasts a, vibrant, nestled, in the heart of, breathtaking, must-visit, stunning, renowned. Replace with neutral facts.
5. **Vague attributions / weasel words** — Experts argue, Observers have cited, Industry reports. Name the source or cut.
6. **Outline-like "Challenges and Future Prospects"** — Despite its... faces several challenges, Future Outlook. Replace with concrete, dated events.

### LANGUAGE & GRAMMAR
7. **Overused AI vocabulary** — see list above.
8. **Copula avoidance** — see English-only tells.
9. **Negative parallelisms / tailing negations** — "Not only...but...", "It's not just X, it's Y", and clipped tails like "no guessing". Write as a real clause.
10. **Rule of three** — forcing ideas into groups of three. Break the pattern.
11. **Elegant variation (synonym cycling)** — protagonist→main character→central figure→hero. Pick one and keep it.
12. **False ranges** — "from X to Y" where X and Y aren't on a real scale. List the actual items.
13. **Passive voice / subjectless fragments** — "No configuration file needed." Restore the actor when it's clearer.

### STYLE
14. **Em/en dashes** — see English-only tells (hard constraint).
15. **Overuse of boldface** — mechanical emphasis. Remove.
16. **Inline-header vertical lists** — "- **User Experience:** ...". Fold into prose.
17. **Title Case headings** — see English-only tells.
18. **Emojis** — decorating headings/bullets. Remove.
19. **Curly quotation marks** — see English-only tells.

### COMMUNICATION
20. **Collaborative artifacts** — "I hope this helps!", "Want me to...?", "Here is a...". Cut.
21. **Knowledge-cutoff disclaimers / speculative gap-filling** — "as of [date]", "while specific details are limited", "maintains a low profile", "likely grew up". Say what isn't known, or cut.
22. **Sycophantic / servile tone** — "Great question!", "You're absolutely right!". Cut.

### FILLER & HEDGING
23. **Filler phrases** — "in order to"→"to", "due to the fact that"→"because", "at this point in time"→"now", "has the ability to"→"can".
24. **Excessive hedging** — "could potentially possibly be argued that might". Trim to one modal.
25. **Generic positive conclusions** — "the future looks bright", "exciting times lie ahead". Replace with a concrete next step.
26. **Hyphenated word-pair overuse** — see English-only tells.
27. **Persuasive authority tropes** — "The real question is", "at its core", "what really matters", "fundamentally". State the ordinary point plainly.
28. **Signposting / announcements** — "Let's dive in", "here's what you need to know". Just say the thing.
29. **Fragmented headers** — a heading followed by a one-line restatement before real content. Delete the warm-up line.
30. **Diff-anchored writing** — narrating a change ("This was added to replace...") instead of describing the thing as it is. ⚠️ 这条和 `fair-copy` 的「过程性指向措辞」重叠：在 humanizer 里只把它当文风 tell；要系统清「自己改稿留下的过程痕迹」，用 fair-copy。 *Before:* "This function was added to replace the previous O(n²) approach." *After:* "This function uses a hash map for O(1) lookups."
31. **Manufactured punchlines / staccato drama** — every sentence a quotable closer; runs of short fragments. One short sentence is fine; a run sounds engineered.
32. **Aphorism formulas** — "X is the Y of Z", "X becomes a trap", "the language of", "the architecture of". Replace with the concrete claim.
33. **Conversational rhetorical openers** — "Honestly?", "Look,", "Here's the thing", as standalone fake-candid hooks. Just say the thing.

---

## Detection guidance (false positives)

A clean human writer can hit several patterns with no AI involvement. **Not reliable on their own:** perfect grammar; mixed casual/formal register; "bland" prose; formal vocabulary; letter-style salutations; one *however* or *moreover*; curly quotes alone; em dashes alone; one short emphatic sentence; "honestly"/"look" mid-sentence; unsourced claims; clean formatting from a template.

Look for **clusters**, not isolated tells. A single em dash means nothing; em dashes + rule-of-three + "vibrant tapestry" + a "Conclusion" section is a confession.

**Signs of human writing (preserve):** specific hard-to-fabricate detail; mixed feelings / unresolved tension; dated era-bound references and slang; first-person choices the writer can defend; variety in sentence length; genuine asides and self-corrections; anything edited before 2022-11-30 (ChatGPT launch).

---

## Full English worked example

**Before (AI-sounding):**
> Great question! Here is an essay on this topic. I hope this helps!
> AI-assisted coding serves as an enduring testament to the transformative potential of large language models, marking a pivotal moment in the evolution of software development. In today's rapidly evolving technological landscape, these groundbreaking tools—nestled at the intersection of research and practice—are reshaping how engineers ideate, iterate, and deliver, underscoring their vital role in modern workflows.
> At its core, the value proposition is clear: streamlining processes, enhancing collaboration, and fostering alignment. It's not just about autocomplete; it's about unlocking creativity at scale. The tool serves as a catalyst. The assistant functions as a partner.
> In conclusion, the future looks bright. Exciting times lie ahead. Let me know if you'd like me to expand on any section!

**Final rewrite:**
> AI coding assistants can make you faster at the boring parts. Not everything. Definitely not architecture.
> They're great at boilerplate: config files, test scaffolding, repetitive refactors. They're also great at sounding right while being wrong. I've accepted suggestions that compiled, passed lint, and still missed the point because I stopped paying attention.
> People I talk to tend to land in two camps. Some use it like autocomplete for chores and review every line. Others disable it after it keeps suggesting patterns they don't want. Both feel reasonable.
> The productivity metrics are slippery. GitHub can say Copilot users "accept 30% of suggestions," but acceptance isn't correctness, and correctness isn't value. If you don't have tests, you're basically guessing.

Stripped: chatbot framing, significance inflation, promotional/-ing padding, rule-of-three, copula avoidance, em dashes/emojis/boldface, the generic upbeat conclusion — then rebuilt with varied rhythm and concrete detail.
