## Phase 1 — Core data model + Admin web app

The foundation everything else depends on.

Auth (staff/admin roles)
Class model: recurring schedule, teacher, capacity, type (group/private)
Client accounts: profile, credit balance, preferences (stub fields, no real notifications yet)
Admin dashboard: day/week/month views, class roster, cancellations
Individual client view: upcoming classes, purchases, customer details
No real payments yet — just a manual "mark as paid" field so you can build booking logic without Stripe complexity blocking you

This phase alone is a full SSDLC learning project on its own — worth its own ADRs on the recurrence model and role-based access.

## Phase 2 — Booking logic + waitlist

This is the trickiest business logic, so isolate it before adding more surfaces.

Class capacity enforcement
Waitlist join/promote-on-cancel logic
Cancellation flow (and admin visibility into who cancelled)
Achievements logic (100-classes milestone) — good self-contained feature to practice event-driven design (e.g. "on booking completed, check achievement thresholds")

## Phase 3 — Payments (Stripe)

Now wire real money into the model you've already validated.

Stripe Checkout for one-off packs
Stripe Billing for subscriptions
Webhook handling (payment success/failure → update credit balance)
Pricing tab data (classes, bundles, packs, "what's included")

Doing this third, after booking logic is solid, means you're not debugging payment webhooks and scheduling logic at the same time.

## Phase 4 — Client-facing web (GHP website)

Now build the client experience against your finished API.

Dashboard, schedule browsing, "show full classes" toggle
Account tab, pricing tab
Reuse a lot of your admin-side API endpoints, just filtered to the logged-in user

## Phase 5 — Mobile app (React Native/Expo)

Last, and now mostly a UI exercise since the API and business logic are proven.

Port client-web screens to React Native
Push notifications (this is genuinely new work, not a port)
App store submission process (this alone can eat 1-2 weeks — Apple review, provisioning profiles, etc., budget for it)

## Phase 6 — Polish
Preferences wiring (marketing emails/texts actually sending — SendGrid/Twilio)
Reporting/bug flow from account tab
Analytics on total spend/reservations for admin summary views
