# Install and first run

## Download

**<https://650ailab.com/gomirai>**

The page detects your platform and offers the right build; you can also pick the
other one explicitly if you are downloading for a different machine.

Current version: **0.1.0051**

---

## System requirements

| | macOS | Windows |
|---|---|---|
| **OS** | macOS 12 or later | Windows 10 or 11, 64-bit |
| **Architecture** | Apple Silicon or Intel (universal build) | x64 |
| **RAM — email only** | 8 GB | 8 GB |
| **RAM — with local AI** | 16 GB minimum, 24 GB+ comfortable | 16 GB minimum, 24 GB+ comfortable |
| **Disk** | ~1 GB for the app, plus ~10 GB if you use the AI | same |

The macOS build is signed with an Apple Developer ID and notarised by Apple, so
it opens with a normal double-click — no Gatekeeper warning, no right-click
workaround.

---

## Installing

**macOS** — open the `.dmg` and drag **GOmirai** to Applications.

**Windows** — unzip the archive and run `GOmirai.exe`. Keep the folder together;
the executable needs the files alongside it.

---

## First run

### 1. Sign in

GOmirai uses a **650 AI Lab account**. Sign in with Google, or have a one-time
code emailed to you. There is no password.

You will be asked to sign in again roughly every 7 days.

### 2. Connect a mailbox

**Settings → Email Accounts → Connect Gmail via 650 AI Lab.** Your browser opens
Google's consent screen; approve, and you are returned to the app.

Repeat for each mailbox you want. How many you can connect depends on your plan.

Mail begins syncing immediately. Recent messages arrive first and the app is
usable straight away; older history backfills in the background.

### 3. Set up the AI — optional

**AI → LLM Setup**, then one flow with three steps:

1. **Download** the model — about 4.7 GB, with live progress.
2. **Instance** — register it with the local runtime.
3. **Verify** — a test prompt confirms it answers.

All three green means AI features switch on. Until then the app reports **Not
Ready** and keeps them off rather than half-working.

This step is optional. Skip it and GOmirai remains a complete email and calendar
client — you simply do not get AIBox. See [gomirai-llm.md](gomirai-llm.md).

---

## Updating

GOmirai checks for new releases and shows an update notification when one is
published; it also re-checks whenever you open a screen that displays the
version. Download the new build and install it over the old one — your data and
accounts are preserved.

---

## Uninstalling

**macOS** — drag GOmirai from Applications to the Trash.
**Windows** — delete the program folder.

To remove your local data as well, use **Settings → Reset** *before*
uninstalling, and revoke GOmirai's Google access at
<https://myaccount.google.com/permissions>.

---

## Troubleshooting

**"Your session has expired"** — sign-in renews every 7 days. Sign in again; your
mailboxes and mail are untouched.

**A mailbox says "Reconnect needed"** — its Google permission expired or was
revoked. Press **Reconnect** on that account's row. This is separate from your
GOmirai sign-in.

**"Can't reach 650 AI Lab"** — a network problem, not lost data. Your accounts
stay listed; press **Retry**.

**AI reports Not Ready** — re-run **AI → LLM Setup**. Each step shows its own
red/green state, so you can see which one failed.

**Per-mailbox diagnosis** — Settings → Email Accounts has a **Diagnose** button
on each account that checks token, scopes, Gmail, calendar and Meet access, and
reports which step failed.
