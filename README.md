# japanlaw.org for Claude and ChatGPT

Japanese law, read from the text itself. This plugin lets Claude, ChatGPT and
Codex look up a Japanese statute on [japanlaw.org](https://japanlaw.org), quote the article,
link to it, and say whose English translation it is quoting: the Ministry of
Justice's, or a machine translation. It can also say what a word the law defines
means there, and what an amendment changed.

It has two parts:

- **A connection to japanlaw.org** (an MCP server at `https://japanlaw.org/mcp`) that the
  assistant uses to search and read the law.
- **A skill**, `japanese-law`: instructions that teach the assistant how a
  Japanese provision is cited (第三十六条第二項 is Article 36, paragraph 2), the
  difference between an Act (法律), a Cabinet Order (政令) and a Ministerial Order
  (省令), and to say "machine translation" whenever it quotes one.

No account, no key, nothing to configure. What you ask is not recorded.

## Install

**Claude Code** — type these in Claude Code:

```
/plugin marketplace add japanlaw/plugin
/plugin install japanlaw@japanlaw
```

**Codex** — in a terminal:

```
codex plugin marketplace add japanlaw/plugin
codex plugin add japanlaw@japanlaw
```

**Claude (claude.ai, the desktop app) and ChatGPT** — until the plugin is listed
in their directories, add the connection and the skill yourself; the steps are at
[https://japanlaw.org/en/agents](https://japanlaw.org/en/agents).

## Then ask

- "Under Japanese law, how many hours of overtime can my employer ask of me in a month? Quote the article."
- "What does Article 36 of the Labor Standards Act say? Show the Japanese and say whose English it is."
- "I'm renting an apartment in Tokyo. When can the landlord refuse to renew the lease?"

## What the assistant can do with it

- **Search Japanese law** (`search`): Finds provisions, laws and defined terms by Japanese or English words, in every law held or in one, best match first. Each result has an id for fetch and the page's URL.
- **Read a provision or a law** (`fetch`): Reads what a search result's id names: a provision in Japanese with its English, each line marked as the Ministry's translation or machine translation — in force, or as it stood on a day; or a law's overview and outline.
- **List the laws held** (`list_laws`): Every law japanlaw.org holds: title, number, kind, date of the text in force and how much of it has English.
- **Describe one law** (`get_law`): One law: what it is for, who it binds and who it does not — its exceptions and how it is enforced on request — the texts of it held, earlier and to come, and its chapters, or what is under one of them.
- **Read one provision** (`get_provision`): An article, paragraph or item by its citation — 第三十六条第二項, Article 36(2) or art-36/par-2 — in Japanese and English, with what it cites, the terms it defines and its URLs: in force, or as it stood on a day. Shown as a card where the app can draw one.
- **Find what cites a provision** (`get_citing_provisions`): Every provision in the collection that cites the one given, with links. No official source publishes this direction.
- **Look up the words a law defines** (`get_definitions`): The words a law defines for itself — 労働者, 賃金 — each with the statute's own definition, its English and whose that is, a plain explanation, where it is defined and how far it reaches. Given a provision, the definitions that apply in it and the legal vocabulary it uses.
- **See what amendments changed** (`get_amendments`): A law's amendments: the amending Act, its number, the day it takes effect and whether it is in force. Given one, every provision it changes, before and after, in Japanese and English, each English marked as the Ministry's or machine translation.

Every tool only reads. None of them can change anything, anywhere.

## Good to know

- Ask the assistant which laws japanlaw.org holds: it can list them, and it says
  so when a law is not among them.
- Only the Japanese text has legal effect. The Ministry of Justice's English is a
  reference translation, and machine translation is marked as such.
- This is information about the law, not legal advice.
- [Privacy](https://japanlaw.org/en/privacy) · [Terms](https://japanlaw.org/en/terms)

## About this repository

Every file here is generated from japanlaw.org's own source by its release
process, so the skill is the same text as
[https://japanlaw.org/skills/japanese-law/SKILL.md](https://japanlaw.org/skills/japanese-law/SKILL.md) and
the server address is the live one. Please don't send changes to these files;
they would be overwritten at the next release.

The files in this repository are under the MIT licence. The law the server
returns is not in it.
