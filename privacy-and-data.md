# Privacy and data

GOmirai's design goal is that your email can be understood by an AI without
leaving your control. This document sets out exactly what that means in practice.

---

## The short version

- The AI runs **on your machine**. Your email content is never sent to OpenAI,
  Anthropic, Google Gemini, or any other third-party AI service.
- Your mail, calendar, notes and the AI's analysis are stored **locally**, in a
  folder scoped to your signed-in account.
- 650 AI Lab does not read your mail, does not sell your data, does not use it
  for advertising, and does not train generalised AI models on it.
- Cloud backup is **opt-in** and covers your notes and documents — not your mail.

---

## What GOmirai accesses from Google

GOmirai asks for exactly four OAuth scopes — no more.

| Scope | Class | Why |
|---|---|---|
| `gmail.modify` | Restricted | Read and display your mail; send what you compose; manage mailbox state — read/unread, star, labels, archive, move to Trash |
| `calendar.events` | Sensitive | Read, create, edit and delete your calendar events, and RSVP to invitations |
| `openid`, `email` | Basic | Identify the account being connected |

### Why `gmail.modify` and not something narrower

Read-only access plus send-only access cannot do what a mail client must do.
Marking a message read, starring it, applying a label, archiving it and moving it
to Trash are all *write* operations. `gmail.modify` is the narrowest scope that
covers them.

### What GOmirai deliberately does *not* request

GOmirai does **not** request `https://mail.google.com/`, the full-access mail
scope. The single capability that costs us is permanently deleting mail, and we
removed that feature rather than ask for the broader permission. Deleting in
GOmirai moves a message to Trash; you empty Trash in Gmail, which also clears it
automatically after about 30 days.

### Limited Use

GOmirai's use of information received from Google APIs adheres to the
[Google API Services User Data Policy](https://developers.google.com/terms/api-services-user-data-policy),
including the Limited Use requirements.

---

## Where your data lives

Everything is stored on your own computer, under your operating system's
application-support directory, in a folder keyed to your 650 AI Lab account:

- Cached mail and calendar
- The AI's analysis
- Your Obsidian vault and Vault documents
- Preferences

Signing out unloads that data. A different account signing in on the same machine
gets a separate, private space and cannot see it.

---

## How the AI handles your mail

The model file sits on your disk. Analysis runs on your own CPU or GPU, reached
over `127.0.0.1` — your computer talking to itself. No network hop is involved,
so there is nothing to intercept and nothing to log.

See [gomirai-llm.md](gomirai-llm.md) for the model's details.

---

## What does leave your machine

Being precise about this matters more than a broad reassurance:

1. **Gmail and Google Calendar API calls** — to Google, over HTTPS, to fetch and
   change your own mail and events at your direction.
2. **Sign-in** — with 650 AI Lab, to authenticate you and check your plan.
3. **Model downloads** — fetching the AI model files.
4. **Cloud backup, if you turn it on** — your notes and documents, to your
   configured storage. Append-only, and never your mail.
5. **Mobile companion, if you pair a phone** — your AIBox summaries through an
   end-to-end encrypted relay. The relay is zero-knowledge: it carries data it
   cannot read.

Your email *content* is not in that list, except as it travels between you and
Google — where it already lives.

---

## Mail access modes

GOmirai supports two ways of reaching Gmail, switchable in
**Settings → Privacy & Security**:

- **Direct** — 650 AI Lab's server holds the encrypted refresh token and issues
  a short-lived access token; GOmirai then calls Gmail itself. **Your mail
  content never passes through our server.**
- **Server-proxied** — the server relays the API calls.

Refresh tokens are encrypted at rest before they are stored.

---

## Security posture

- Sign-in is passwordless — an emailed code or Google. There is no password to
  breach.
- Google refresh tokens are encrypted before storage.
- All Google API traffic is HTTPS.
- The 650 AI Lab service enforces HSTS, a restrictive Content-Security-Policy,
  and a full set of HTTP security headers, behind a CDN front door.
- Because GOmirai uses a Restricted Google scope, the service undergoes an
  independent **ADA-CASA** security assessment against OWASP ASVS Level 1,
  repeated annually. Ours is **in progress**, scheduled for completion by
  2 December 2026 — see the status section in [README.md](README.md).
- Remote images in mail are blocked by default, so senders cannot track you by
  opening a message.

---

## Your controls

- **Per-account AI opt-out** — exclude any mailbox from AI analysis entirely.
- **Disconnect** a mailbox — revokes GOmirai's Google access, keeps local
  history.
- **Delete** a mailbox — revokes access *and* wipes its cached mail and analysis
  from the device.
- **Reset** — clear data, the account, or everything.
- **Revoke from Google directly**, at any time, at
  <https://myaccount.google.com/permissions>.
