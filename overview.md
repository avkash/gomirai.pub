# What is GOmirai?

GOmirai is a desktop email and calendar application with a privacy-first AI layer
that understands your mail as a whole, not one message at a time. It runs on
macOS and Windows, and it is built by **650 AI Lab**.

---

## The problem

Email has worked the same way for thirty years: a list of individual messages you
process one by one. The volume grew; the tool didn't change. Most people now have
several accounts — work, personal, a business, a side project — and no single
place that tells them what actually needs attention across all of them.

The obvious fix is to point an AI at your inbox. The obvious problem with that
fix is that it means shipping your entire private correspondence to somebody
else's servers.

GOmirai's answer: **run the AI on your own machine.**

---

## Two experiences, one application

GOmirai gives you two ways to work, and you switch between them freely.

### Email — the familiar side

A complete Outlook-style client. Three-pane layout, folder trees, a reading pane,
search, compose, reply, reply-all, forward. Your calendar, your contacts,
multiple mailboxes side by side or combined. If you have used Outlook, you
already know how to use it.

Nothing here depends on AI. If you never turned the AI on, GOmirai would still be
a capable email client.

### AIBox — the intelligence layer

The same mail, read across every account at once and turned into something you
can act on:

- **What needs a reply** and **what needs attention** — tracked as two separate
  judgements, because "someone is waiting on you" and "you should know about
  this" are different problems.
- **A daily briefing** of what matters today across all accounts.
- **Summaries and action items** — what a sender or thread needs from you,
  what is already handled, what is still open.
- **Projects and entities** — define the people, businesses and projects that
  matter to you, with their addresses and domains, and related mail groups
  itself.

---

## Where the AI runs

On your computer. GOmirai downloads a language model to your disk and runs it
locally. Your email content is analysed on-device and is **not** sent to any
third-party AI service — not to 650 AI Lab, and not to any model provider.

For the details of that model — what it is, how big it is, what it can and
cannot do — see **[gomirai-llm.md](gomirai-llm.md)**.

---

## Beyond the inbox

GOmirai has grown past email alone. It also includes:

- **Obsidian vault** — a real on-disk markdown notebook with wiki-links,
  backlinks, full-text search and cloud backup.
- **Vault** — document memory: files you add are catalogued, made searchable and
  summarised by the local AI.
- **Ask GOmirai** — ask a question and get an answer drawn from your own mail,
  notes and documents.
- **Tasks, Projects and Routines** — work you define, tracked in the same place.
- **Calendar and AI scheduling** — the model proposes meeting times from your
  own mail and calendar; nothing is booked without your confirmation.
- **A mobile companion** — a read-only phone app that syncs your AIBox through
  an end-to-end encrypted relay.

Availability of some of these depends on your plan — see [plans.md](plans.md).

---

## Your account

GOmirai uses a **650 AI Lab account**. Sign in with Google, or with a one-time
code emailed to you — there is no password to remember or leak.

Your data is bound to your account and stored locally, scoped to whoever is
signed in. A different account on the same machine gets a completely separate,
private workspace.

---

## In one line

A familiar inbox you already know how to use, plus an AI that understands all of
it — running on your own hardware, so none of it has to leave.
