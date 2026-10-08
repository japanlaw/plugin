---
name: japanese-law
description: Read, cite and explain Japanese statutes from the text itself — the Japanese as published, the Ministry of Justice's English translation where there is one, and labelled machine translation where there is not — via japanlaw.org. Use whenever a question turns on a Japanese law (法律, 政令, 省令), an article such as 第三十六条 or "Article 36(2)", or an English translation of one.
---

# Japanese law, from the text

Answer questions of Japanese law from the statute, not from memory. japanlaw.org
holds Japanese statutes split into addressable provisions, each with its English
and a record of whose English it is.

## Where to read it

**With MCP** — if the japanlaw tools are available (add `https://japanlaw.org/mcp` as a remote MCP
server; no key):

- `search` — Finds provisions, laws and defined terms by Japanese or English words, best match first. Each result has an id for fetch and the page's URL.
- `fetch` — Reads what a search result's id names: a provision in Japanese with its English, each line marked as the Ministry's translation or machine translation — in force, or as it stood on a day; or a law's overview and outline.
- `list_laws` — Every law japanlaw.org holds: title, number, kind, date of the text in force and how much of it has English.
- `get_law` — One law: what it is for, who it binds and who it does not — its exceptions and how it is enforced on request — the texts of it held, earlier and to come, and its chapters, or what is under one of them.
- `get_provision` — An article, paragraph or item by its citation — 第三十六条第二項, Article 36(2) or art-36/par-2 — in Japanese and English, with what it cites, the terms it defines and its URLs: in force, or as it stood on a day. Shown as a card where the app can draw one.
- `get_citing_provisions` — Every provision in the collection that cites the one given, with links. No official source publishes this direction.

**Without MCP** — plain HTTP, no key:

- Search: `https://japanlaw.org/api/search?q=<words>` (Japanese or English)
- A provision as Markdown: `https://japanlaw.org/md/en/<law-slug>/<address>`
- What is held, and how addresses work: `https://japanlaw.org/llms.txt`

A good order: search (or `get_provision` when the law and article are known) →
read the provision itself → answer, quoting it and linking its `url`.

## Citing a provision

Japanese statutes are numbered 条 (article), 項 (paragraph), 号 (item):

| Japanese | Ministry of Justice English | japanlaw.org address |
|---|---|---|
| 第三十六条 | Article 36 | `art-36` |
| 第三十六条第二項 | Article 36, paragraph (2) — "Article 36(2)" | `art-36/par-2` |
| 第三十六条第二項第一号 | Article 36, paragraph (2), item (i) | `art-36/par-2/item-1` |
| 第三十二条の三の二 | Article 32-3-2 | `art-32-3-2` |
| 附則 | Supplementary Provisions | `suppl-…` (from search or get_law) |
| 別表第一 | Appended Table 1 | `appdx-1` |

- 第五条の二 is a separate article inserted after 第五条 by an amendment, not a
  paragraph of it. Repealed articles stay as 削除 ("deleted"); numbers are not
  reused.
- An article with one paragraph has no "paragraph (1)" in English; its items are
  cited straight off the article.
- Give the reader the provision's japanlaw.org link. A link to a paragraph or item
  opens the article at that point.

## What kind of law it is

The kind decides who made it and what it can do, so never call all of them "law":

- 憲法 — the Constitution.
- 法律 — an Act of the Diet.
- 政令 — a Cabinet Order, made under an Act.
- 府令・省令 — a Cabinet Office or Ministerial Order (施行規則 is usually one), made
  under an Act or a Cabinet Order.
- 条例 — a local ordinance; none are held here.

An Act often leaves the detail to an order: 「厚生労働省令で定める」 means the rule is
in a Ministerial Order. Follow it there before saying what the rule is.

## Which English, and how to say so

Every English paragraph is marked (`englishWhose`, or the line under it in Markdown):

- **ministry** — the Ministry of Justice's translation (Japanese Law Translation).
  Still not official: only the Japanese has legal effect.
- **corrected** — the Ministry's translation with a slip japanlaw.org corrected; say so.
- **machine** — japanlaw.org's machine translation, not official, not reviewed by a
  lawyer. Say "machine translation" whenever you quote it.

Never present machine translation as the Ministry's. When the precise words matter,
quote the Japanese.

## Versions

A law is a sequence of versions. japanlaw.org gives the text in force (and says
since when) unless asked for another. `get_law` lists the texts it holds — earlier
ones, and those amendments passed but not yet in force will leave — and
`get_provision` and `fetch` read one with `asOf` (a day, YYYY-MM-DD) or
`version`. A day whose text is not held is answered "not held": say so, and do
not quote the nearest text instead. When an answer is not the text in force, say
which text it is and the days it stands, as `version` and `notice` give them.

## Honesty

- If a law is not held (`list_laws` lists every law that is), say so; do not
  reconstruct its text.
- If an address does not exist, the tools say so and suggest what to ask for —
  never guess an article's content from its number.
- This is information about the law, not legal advice. For a decision, point the
  reader to the official text on e-Gov (each provision links it) and to a lawyer.
