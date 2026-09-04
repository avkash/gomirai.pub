# Frequently asked questions

### Does my email get sent to an AI company?

No. The model runs on your own machine. Your email content is not sent to
OpenAI, Anthropic, Google Gemini or any other AI service — and not to 650 AI Lab
either. See [gomirai-llm.md](gomirai-llm.md).

### Can 650 AI Lab read my mail?

No. Your mail is cached on your device. In direct mode — the default — our server
issues a short-lived access token and GOmirai calls Gmail itself, so your mail
content does not pass through us at all.

### Do I have to use the AI?

No. Skip the model download and GOmirai is a complete Outlook-style email and
calendar client. The AI is a layer on top.

### How big is the AI model, and what will it cost me in disk and memory?

About 4.7 GB to download and keep on disk, plus a small 139 MB embedding model.
16 GB of RAM is the practical minimum to run it comfortably. Full detail in
[gomirai-llm.md](gomirai-llm.md).

### Will it slow my computer down?

Analysis runs in the background and yields to what you are doing. On Apple
Silicon it uses the Metal GPU. On a machine at the 16 GB minimum you will notice
it during heavy processing; at 24 GB or more, generally not.

### Does it work offline?

Mail is cached on disk, so reading and searching work offline, and the app opens
instantly. The AI also runs offline once the model is downloaded. Sending mail
and syncing need a connection.

### Why does it want permission to modify my Gmail?

Because a mail client has to write: marking read, starring, labelling, archiving
and moving to Trash are all changes. Read-only access cannot do them.
`gmail.modify` is the narrowest scope that covers a working client. GOmirai does
**not** request the full-access mail scope. See
[privacy-and-data.md](privacy-and-data.md).

### Can GOmirai permanently delete my mail?

No, by design. Deleting moves a message to Trash. Permanent deletion would
require a much broader Google permission, so we removed the feature instead of
asking for it. Empty Trash in Gmail — it also clears automatically after about
30 days.

### Why do I have to sign in every week?

Sessions last 7 days. When one expires GOmirai returns you to the sign-in screen
and says why. Your mailboxes, mail and analysis are untouched.

### What is the difference between signing in and connecting a mailbox?

Two separate things. **Signing in** is your GOmirai account (650 AI Lab), renewed
about weekly. **Connecting a mailbox** is granting Google access to one email
account, renewed with **Reconnect** on that account's row. An expired sign-in
does not mean you have lost a mailbox.

### How many email accounts can I connect?

5 on Basic Pro, 25 on Executive, unlimited on Ultimate. See [plans.md](plans.md).

### Which platforms?

macOS (Apple Silicon and Intel, one universal build) and Windows 10/11 64-bit.
There is a read-only mobile companion for iOS and Android on the Ultimate plan.

### Is the macOS build safe to open?

Yes — it is signed with an Apple Developer ID and notarised by Apple, so it opens
with a normal double-click.

### Where are my notes stored?

In a real markdown vault on your disk — plain `.md` files in ordinary folders.
You can open them with any editor, including Obsidian itself. Nothing is locked
in a proprietary format.

### What happens to my data if I stop using GOmirai?

Your mail stays in Gmail — GOmirai never removes it. Your notes are plain
markdown files you already have. Use **Settings → Reset** to clear local data,
and revoke access at <https://myaccount.google.com/permissions>.

### Can I use a different AI model?

Yes — the AI panel can install other open models such as Qwen3. The email
pipeline is tuned and validated against GOmirai LLM, so that is the supported
default.

### Is my mail backed up to the cloud?

No. Cloud backup is opt-in and covers your **notes and documents** only. It is
append-only: it never deletes your cloud data on its own.
