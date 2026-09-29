"Given (starting point), when (action occurring), then (expected observable outcome)"
each independently testable, describes behavior not implementation

For each story going forward, work through in this order:

- Happy path (1-2 ACs) 
- Edge cases / preconditions not met (ask "what if the normal state isn't true?")
- Side effects on related data (what else does this touch that could end up inconsistent?)
- Audit/logging — only if the action is high-impact or disputable
- Abuse case as a hard AC — only for 🔒-flagged stories
- Note any new questions or child stories that surfaced — don't force an answer, just flag it

## Admin

- **US-A15**
  - AC1: Given an admin is viewing a client's profile, when they select "ban client", then they are shown a confirmation dialog before the ban is applied
  - AC2: Given an admin is viewing the confirmation dialog, when they select "yes", then they are given a text box to enter the reason why they are banning the client at hand with a confirm and cancel option present.
  - AC3: Given an admin confirms the ban action, when the confirmation is submitted, then the client's account status is set to "banned" and they can no longer log in or book classes.
  - AC4: Given a client has upcoming reservations at the time of the ban, when the ban is applied, then those reservations are automatically cancelled and the affected class rosters are updated accordingly 24 hours after the ban.
  - AC5: Given a client has an active subscription at the time of the ban, when the ban is applied, then the subscription is cancelled (not silently left active and billing) 24 hours after the ban.
  - AC6: Given a client had a credit balance at the time of ban, when the ban goes into effect, then the client is sent a message asking them to confirm or provide the payment method they'd like the balance to be refunded to. (saved card/default card on the account given as option to confirm)
  - AC7: Given a client responds with a refund destination, when the admin (or system) processes it, then the balance is refunded to that method and the audit log records the refund completion.
  - AC8: Given an admin bans a client, when submitted, then the client must be notified through email/text (depending on their account preferences) that they were banned, that they are going to be refunded any funds left on the account (also have a statement saying they will receive another notification prompting them to specify where they would like the refund to go [card]), and the reason that they were banned (written by admin), and a link to the contact us page to write an appeal email if they choose.
  - AC9: Given a ban is in effect (refund pending), when the banned client attempts to log in or use their account, then access remains fully blocked regardless of the refund's pending/completed state.
  - AC10: Given a ban is applied, when it takes effect, then an audit log entry is created recording: which admin performed the ban, the timestamp, and the client affected.
  - AC11: Given the audit log, when an admin views a banned client's profile, then they can see who banned the client, when, and why, not just that the account is currently banned.
  - AC12: Given a non-admin user, when they attempt to call the ban endpoint directly (bypassing the UI), then the request is rejected with an authorization error and no account status changes.
  - AC13: Given an admin session token, when it is used to submit a ban request, then the server independently re-verifies the caller's admin role - it does not trust a client-side "isAdmin" flag alone.
  - AC14: Given a client never responds to the refund request, when it has sat for 30 days, then a follow-up email will be generated and sent to them to prompt them for where they would like the refund to go. Until they provide information the funds just sit in their account.
 
- **US-A20**:
  - AC1: Given a client account is banned, when an admin selects "unban" on their profile, then they are shown a confirmation dialog before the unban is applied
  - AC2: Given an admin is viewing confirm dialog, when they select "yes", then they are given a text box to enter the reason why the are unbanning the client.
  - AC3: Given an admin confirms the unban, when submitted, then the client account status is set back to active and they can log in and book classes again.
  - AC4: Given a client is unbanned within 24 hours of the original ban, when the unban is confirmed, then the pending reservation and subscription cancellations are reverted, any in-progress manual refunds are cancelled, and the client's account is restored to exactly the state it was in before the ban (nothing lost).
  - AC5: Given an admin unbans a client, when submitted, then the client must be notified through email/text (depending on their account preferences) that they were unbanned, if occurring within 24 hours of the original ban they will be informed that "no action has been taken on their booked classes, subscription, or funds", the reason they were unbanned written by the admin (for <24 & >=24), and that they are able to access their account again.
  - AC6: Given a client is unbanned 24 hours or later, when their account becomes active, then their previously cancelled reservations and subscriptions are NOT automatically restored - the client starts fresh and must re-book/re-subscribe.
  - AC7: Given an unban is applied, when it takes effect, then an audit log entry is created recording: which admin performed the unban, the timestamp, and the client affected, and the reason.
  - AC8: Given a client's full ban/unban history, when an admin views their profile, then they can see the complete timeline (banned by whom/when/why, unbanned by whom/when/why) — not just the current status.
  - AC9: Given a non-admin user, when they attempt to call the unban endpoint directly, then the request is rejected with an authorization error.
  - AC10: Given an admin session token, when it is used to submit an unban request, then the server independently re-verifies the caller's admin role - it does not trust a client-side "isAdmin" flag alone.

