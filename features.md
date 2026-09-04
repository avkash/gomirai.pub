# What GOmirai can do

A complete feature reference, area by area. Availability of some items depends on
your plan — see [plans.md](plans.md).

---

## Email

A full Outlook-style client, not a cut-down viewer.

- **Three-pane layout** — folders, message list, reading pane (side or bottom).
- **Real browser rendering** — newsletters and rich HTML mail look the way they
  were designed to, because they render in a real web view.
- **Remote images blocked by default** for privacy, with one-click loading.
- **Multi-select** with cmd/shift, delete-focuses-next, message-list separators.
- **Search** across your mail.
- **Per-account folder trees** mapped to Gmail labels — Inbox, Sent, Drafts,
  Deleted Items, Junk, plus your own labels.
- **Workspaces** — group accounts (Work, Personal, a client) and switch context.
- **Combined views** across every account, in an order you set by dragging.

### Send and compose

- Rich-text composer with font family and size control.
- To/Cc/Bcc as validated address chips.
- Reply, Reply-all and Forward with correct threading.
- Attachments.

### Sync and offline

- Mail is **cached on disk** — the app opens instantly and works offline.
- **Delta sync**: only new messages are fetched, which is friendly to Gmail's
  quota.
- **Backfill**: a one-time month-by-month pull for longer history windows.
- Sync is quiet — a brief toast, no spinners; mail streams in.
- Gmail rate-limits are surfaced clearly and recover on their own.

### AutoDelete

Mark a sender for automatic deletion straight from an open email. Three filter
types: exact address, whole domain (`*@shop.com`), or partial match
(`*.*shop*`). Applies immediately and on every fetch, with a running count of
what it removed.

---

## AIBox — the intelligence layer

- **Response Needed** and **Attention Needed** as two independent judgements,
  each its own tab.
- **Today** — a daily briefing aggregated across every account.
- **Categories and projects** — mail organised by what it is about.
- **Summaries and action items** per message and per thread.
- **Entities** — define people, businesses and projects with their addresses and
  domains so related mail groups automatically.
- **Background processing** that continues while you work elsewhere, and
  survives restarts.
- **Per-account AI opt-out** — exclude any mailbox from analysis entirely.

---

## Calendar

- All calendars synced, primary and secondary/subscribed, with per-account
  colours.
- **My Day rail** — agenda, event popups, meeting links.
- Full month grid and grouped per-account lanes.
- **Create and edit events**, 15-minute slots, with a Google Meet toggle (the
  link is created before invites go out).
- **Join buttons** for Meet, Zoom, Teams and Webex — links detected anywhere in
  the invite.
- **Save & Send** confirmation showing the guest list, with an outside-domain
  warning.
- **Meeting reminders** 30 minutes before — Join, Snooze or Close, as floating
  alerts that stay visible above other applications.
- **Calendar invites (.ics)** — RSVP accept / tentative / decline from the mail.
- **AI scheduling** — the local model proposes times from your mail and
  calendar; nothing is booked without your confirmation.

---

## Obsidian vault — notes

A real markdown vault on disk, not a proprietary note store.

- On-disk `.md` folder tree; create, rename and delete folders and notes.
- Markdown editor with a live-preview toggle.
- `[[wiki-links]]` with autocomplete — click to open or create.
- Backlinks panel and full-text search across the vault.
- YAML frontmatter tags.
- Append-only cloud backup of the whole vault, with restore.
- Send content from mail or AI straight into a note.

---

## Vault — document memory

- Add documents; they are catalogued, text-extracted and made searchable.
- Local AI summaries and extracted facts.
- Full-text search designed around finding the right document fast.

---

## Ask GOmirai

Ask a question in plain language; get an answer drawn from your own mail, notes
and documents, with the sources it used.

---

## Tasks, Projects and Routines

- **Tasks** you define, tracked in the app.
- **Projects** — rule-driven grouping of mail and work.
- **Routines** — recurring work with progress rolled up from its parts.

---

## Security and accounts

- **650 AI Lab sign-in** — passwordless email code, or Sign in with Google.
- **Per-user data scoping** — each signed-in user has completely isolated local
  data on the machine.
- **Server-brokered Gmail OAuth** — connect, disconnect or delete a mailbox,
  with a full local data wipe on delete.
- **Diagnose** per mailbox — checks token, scopes, Gmail, calendar and Meet
  access, and tells you which step failed.
- **App lock** and granular **Reset** controls (data / account / everything).
- **Secure notes** — a private space gated by an authenticator code.

---

## Appearance

- Two-axis theming: pick a theme (accent, band, motif) and independently choose
  Light, Dark or System.
- Configurable heading weight and size, and text scale.

---

## Storage and backup

- Pluggable cloud backup — GOmirai Cloud (managed) today, personal Google Drive
  planned.
- **Append-only**: backup never deletes your cloud data on its own. Deleting a
  synced item asks whether you mean locally or in both places.
- Hash-diff manifests — only what actually changed is uploaded.
- Restore onto a new machine.
- Low cadence by design: on-demand sync plus a lazy periodic pass, never live
  streaming.
- Per-domain permission toggles and a usage view.

---

## Mobile companion

A **read-only** phone app (iOS and Android) that syncs your AIBox through a
zero-knowledge relay — the server cannot read the content it carries. Pairing is
QR-only.

---

## Translation

Multi-provider translation with lazy language detection and multiple target
languages, configured in Settings.

---

## Platform

- **macOS** — universal build, Apple Silicon and Intel.
- **Windows** — 10 and 11, 64-bit.
- Native notifications, including floating meeting alerts that appear above
  full-screen applications.
- In-app update notification when a newer release is published.

---

## Not in GOmirai

Full document viewing and editing (PDF, Word, Sheets, Slides) lives in a
separate application, **GOmisuite**. GOmirai handles attachments and extracts
document text for the Vault, but is not a document editor.
