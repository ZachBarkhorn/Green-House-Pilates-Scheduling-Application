"Given (starting point), when (action occurring), then (expected observable outcome)"
each independently testable, describes behavior not implementation

## Admin

- **US-A15**
  - AC1: Given an admin is viewing a client's profile, when they select "ban client", then they are shown a confirmation dialog before the ban is applied
  - AC2: Given an admin is viewing the confirmation dialog, when they select "yes", then they are given a text box to enter the reason why they are banning the client at hand with a confirm and cancel option present.
  - AC3: Given an admin confirms the ban action, when the confirmation is submitted, then the client's account status is set to "banned" and they can no longer log in or book classes.
  - AC4: Given a client has upcoming reservations at the time of the ban, when the ban is applied, then those reservations are automatically cancelled and the affected class rosters are updated accordingly 24 hours after the ban.
  - AC5: Given a client has an active subscription at the time of the ban, when the ban is applied, then the subscription is cancelled (not silently left active and billing) 24 hours after the ban.
  - AC6: Given a client had a credit balance at the time of ban, when the ban goes into effect, then the card used to add the balance will be refunded that amount 24 hours after the ban.
      - ❓ flag: what if the balance is added with a visa gift card or something that can't be refunded? I suppose client could just be spoken to as to which card they want a refund on.
  - AC7: Given an admin bans a client, when submitted, then the client must be notified through email/text (depending on their account preferences) that they were banned, that they are going to be refunded any funds left on the account, and the reason that they were banned (written by admin), and a link to the contact us page to write an appeal email if they choose.
  - AC8: Given a ban is in effect (refund pending), when the banned client attempts to log in or use their account, then access remains fully blocked regardless of the refund's pending/completed state.
  - AC9: Given a ban is applied, when it takes effect, then an audit log entry is created recording: which admin performed the ban, the timestamp, and the client affected.
  - AC10: Given the audit log, when an admin views a banned client's profile, then they can see who banned the client, when, and why, not just that the account is currently banned.
  - AC11: Given a non-admin user, when they attempt to call the ban endpoint directly (bypassing the UI), then the request is rejected with an authorization error and no account status changes.
  - AC12: Given an admin session token, when it is used to submit a ban request, then the server independently re-verifies the caller's admin role - it does not trust a client-side "isAdmin" flag alone.
 
- **US-A20**:
  - AC1: Given a client account is banned, when an admin selects "unban" on their profile, then they are shown a confirmation dialog before the unban is applied
  - AC2: Given an admin is viewing confirm dialog, when they select "yes", then they are given a text box to enter the reason why the are unbanning the client.
  - AC3: Given an admin confirms the unban, when submitted, then the client account status is set back to active and they can log in and book classes again.
  - AC4: Given a client is unbanned within 24 hours of the original ban, when the unban is confirmed, then the pending reservation cancellations, subscription cancellation, and refund are all cancelled, and the client's account is restored to exactly the state it was in before the ban (nothing lost).
  - AC6: Given an admin unbans a client, when submitted, then the client must be notified through email/text (depending on their account preferences) that they were unbanned, if occurring within 24 hours of the original ban they will be informed that "no action has been taken on their booked classes, subscription, or funds", the reason they were unbanned written by the admin (for <24 & >=24), and that they are able to access their account again.
  - AC7: Given a client is unbanned 24 hours or later, when their account becomes active, then their previously cancelled reservations and subscriptions are NOT automatically restored - the client starts fresh and must re-book/re-subscribe.
  - AC8: Given an unban is applied, when it takes effect, then an audit log entry is created recording: which admin performed the unban, the timestamp, and the client affected, and the reason.
  - AC9: Given a client's full ban/unban history, when an admin views their profile, then they can see the complete timeline (banned by whom/when/why, unbanned by whom/when/why) — not just the current status.
  - AC10: Given a non-admin user, when they attempt to call the unban endpoint directly, then the request is rejected with an authorization error.
  - AC11: Given an admin session token, when it is used to submit an unban request, then the server independently re-verifies the caller's admin role - it does not trust a client-side "isAdmin" flag alone.

