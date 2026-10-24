---
name: daypublish
description: "When the user wants to generate a full day of marketing content for Raju Teller — brainstorm topics, draft the pieces, audit them, and save everything into a day-n folder. Also use when the user mentions 'daypublish,' '/daypublish,' 'today's content,' 'content for day 1' (or any day number), 'generate the day folder,' 'daily content batch,' 'prepare tomorrow's posts,' or 'run the day plan.' Use this to produce one campaign day's drafts (Reels, Shorts, WhatsApp messages, images, video scripts) from the Raju Teller 10-day plan, saved under day1/, day2/, etc. Output is always drafts for review — never auto-post. For the overall strategy, see the 10-day plan and brand guide; for individual pieces, this skill orchestrates social, copywriting, image, and video."
metadata:
  version: 1.0.0
---

# Day Publish

You run one campaign day of content production for **Raju Teller** end to end: brainstorm, draft, audit, and file every piece for a specified day into its own `day-n` folder. The output is always **drafts for the user's review** — you never post, schedule, or publish anything.

Raju Teller is a Peter Answers-style party-trick app: the performer secretly controls the answer, and spectators believe Raju knows everything. Raju is the master; **Tota, his parrot, is the fortune teller** (the in-app button reads "Ask Tota Parrot"). The audience-facing illusion is the product. Protecting it is a hard rule, not a style choice.

## Inputs

Ask only for what is missing:

1. **Day number (required).** Which campaign day to produce — `day1` through `day10` of the 10-day plan, or a day number in an extended plan. If the user says "today's content," confirm which plan day today is before generating.
2. **Product marketing context.** If `.agents/product-marketing.md` (or `.claude/product-marketing.md`) exists, read it first.
3. **Brand guide.** Read the current Raju Teller product & brand guide if available in the workspace. It owns the palette (black, purple, gold), voice, mascot rules, and the performer-only mechanics section. Product facts change — verify anything load-bearing against the live demo at https://rajuteller.pages.dev/ before you put it in copy.

## Step 1 — Brainstorm

For each content piece the day calls for (see the day map below), research angles before drafting:

- Trending formats and hooks in prank, magic, mentalism, and reaction content on Instagram Reels and YouTube Shorts.
- What similar novelty/entertainment apps are posting and which of their posts travel.
- Campus and friend-group content patterns in India (the ICP: 18–25, students and young professionals, the prank-loving center of attention in their friend group).

**Connectors (optional).** If the user has configured research connectors, use them per piece:
- **Exa** (`EXA_API_KEY`) — semantic web search for trend and competitor research.
- **Firecrawl** (`FIRECRAWL_API_KEY`) — scrape specific pages (a competitor's profile, a trend roundup) into readable text.
- **Apify** (`APIFY_TOKEN`) — run actors for structured social data (e.g., hashtag or profile scraping).

These are third-party services that need the user's own accounts and API keys. If none are configured, say so in one line and fall back to your built-in web search. **Never fabricate research.** If you could not research something, mark the brainstorm point `[UNRESEARCHED]` instead of inventing a trend, statistic, or example.

Deliver 2–3 angle options per piece with a one-line rationale each. Pick the strongest to draft; keep the rejects in the day folder's notes.

## Step 2 — Draft

Draft each piece using the relevant skill in this repository:

| Piece type | Skill to use |
|---|---|
| Reels/Shorts concept, caption, hook, posting copy | `social` |
| WhatsApp one-to-one seeding and status messages | `social` (and `sms` for WhatsApp specifics) |
| Headlines, taglines, CTAs, any persuasive copy | `copywriting` |
| Thumbnails, memes, carousels, static graphics | `image` |
| Video scripts, shot lists, storyboards | `video` |

Rules for every draft:
- **Keep the illusion.** Spectator-facing pieces show Raju answering impossible questions and real reactions. They never explain, hint at, or wink about how it works. No screenshots or screen recordings of the petition/answer field, ever. Performer-facing how-to material (recruiting other performers) may be honest about it being a trick — label those files `performer-` so they are never mixed into audience posts.
- **Match the voice.** Playful, confident, a little mysterious. Raju is the master, Tota the parrot tells the fortune. No AI tells (no "it's not X, it's Y," no "game-changer," no broetry).
- **Right-size the ask.** The plan is under 30 minutes of work per day at zero budget. A day's output should be filmable/postable by one person with a phone.
- **Free and honest.** The demo is free at rajuteller.pages.dev. Do not advertise pricing, payments, or store availability as live unless you have verified they actually are — monetization (3 free questions daily, renewed each day, then ₹11 per additional question) is decided but NOT live — the paywall is a placeholder and no payment checkout is connected. Do not advertise paid checkout as live or imply an enforced per-user entitlement. When in doubt, leave money claims out and flag them `[VERIFY]`.
- **Real assets only.** If image or video generation tooling is available, use the `image`/`video` skills to produce assets. If it is not, deliver a detailed asset brief (shot list, framing, text overlays, colors from the brand palette) the user can film or make herself. Never claim an asset exists when only a brief was produced.

## Step 3 — Audit

Audit every drafted piece before filing it. A piece fails the audit if any item is a "no":

1. **Facts.** Every factual claim is true and verifiable (what the app does, where it lives, what it costs). No invented statistics, fake testimonials, or staged reactions presented as real without disclosure.
2. **Brand.** Follows the brand guide: black/purple/gold where visual, correct character names (Raju the master, Tota the parrot fortune teller), playful tone, no off-brand promises.
3. **Channel fit.** Formatted for its channel: Reels/Shorts hooks in the first 2 seconds, vertical 9:16 assumptions, caption length and hashtag conventions per platform, WhatsApp messages short and personal, no links that 404.
4. **Illusion check.** Nothing spectator-facing reveals or hints at the method. Performer-facing files are labeled and separated.
5. **Claims check.** No payment, pricing, store, or "available now" claims that are not currently true.

Fix failures and re-audit. Record the audit result per piece in the day's `audit.md` — one line per piece: pass, or what was fixed. Anything you could not verify goes in `audit.md` as an open `[VERIFY]` item for the user, not in the copy.

## Step 4 — File the day

Save everything for the specified day in its own folder:

```
day1/
  README.md            # the day's plan, pieces, and where each stands (draft / needs asset / ready to review)
  brainstorm.md        # researched angles per piece, including rejected options and [UNRESEARCHED] marks
  reel-1-hook.md       # one file per content piece, named for the piece
  whatsapp-seed-1.md
  asset-brief-1.md     # or the generated asset file when tooling exists
  performer-howto.md   # only when the day includes performer recruiting; performer- prefix is mandatory
  audit.md             # audit result per piece + open [VERIFY] items
day2/
  ...
```

Use `day<n>` exactly (`day1`, `day2`, … `day10`) so folders sort with the plan. Never mix days in one folder. If the folder already has content, add new files alongside it — do not overwrite earlier drafts without saying so.

## The 10-day plan (default day map)

| Day | Focus | Typical pieces |
|---|---|---|
| 1 | Practice the trick on one friend | — (no content; optionally a WhatsApp status teaser) |
| 2 | Film 2–3 friends' reactions (ask first) | shot list, consent ask |
| 3 | Post Reel 1 | Reel script + caption + hashtags |
| 4 | Seed personally to 10 friends | WhatsApp one-to-one message + challenge line |
| 5 | Live canteen/hostel demo | WhatsApp status + group message |
| 6 | Post Reel 2, reply to everything | Reel script + reply bank for comments/DMs |
| 7 | Recruit 5 performers | performer- how-to + recruiting message |
| 8 | Post Reel 3 (best-reactions compilation) | compilation outline + caption |
| 9 | Second live demo, new audience | event post + same-evening recap |
| 10 | Review and plan the next 10 days | results summary template |

When the user names a day, default to this map; adjust if she redirects.

## Guardrails

- **Drafts only.** Never post, schedule, DM, or publish. Everything waits for the user's review.
- **No spend.** No paid tools, ads, boosts, or connector signups on the user's behalf. Optional connectors above are used only when the user has already set them up.
- **No fake proof.** No invented testimonials, view counts, or reaction clips described as real.
- **The method stays hidden.** Treat the petition/answer-field mechanics like a password: it appears in no audience-facing file, caption, comment reply, or asset.

## Related Skills

- `social` — the drafting engine for Reels, Shorts, WhatsApp, captions
- `copywriting` — hooks, CTAs, taglines
- `image` — thumbnails and static assets
- `video` — scripts, shot lists, storyboards
- `marketing-loops` — if the user wants this run on a daily cadence instead of one day at a time
- `content-strategy` — planning beyond the 10-day window
