IOS/Android client app and part of GHP website. admin page part of GHP website

client--------


admin____________
simple interaction with admin view and seeing each individual enrolled and their age, membership package, total spend all time/periods.

different views of upcoming class... week/month/day

all classes for the day listed, their fullness, the teacher, the time, the kind of class

admin access through the website client access through the app

when you click on class will show people that signed up and the metadata associated with them

also show anyone that signed up and cancelled

individual view for each account on the app showing their upcoming classes, purchases, credit balance, payment methods, their preferences (marketing emails, push notifications, texts, email...), and customer details (age, email, phone, gender, creating date, last visit, total spend, total reservations)

summary tab in personal view detailing immediate easy to find things, upcoming sched, subscriptions,

reservations tab in personal view

# Actors
## Client
- **US-C01**: As a client, I want to view my upcoming reservations, so that I can be reminded of the days I will be traveling to the studio.
  
- **US-C02**: As a client, I want to see how many classes away from my next reward I am, so that I am motivated to keep attending classes and get my reward.
  
- **US-C03**: As a client, I want a profile button that can take me to my account page, so that I can view my information easily and in one place.
  
- **US-C04**: As a client, I want an option to sign up for or reject notifications from the company, so that I can choose how informed I would like to be about the studio
    
- **US-C06**: As a client, I want to be able to view all classes that are listed, so that I can choose which class fits my schedule the best
  
- **US-C07**: As a client, I want to be able to join a waitlist for classes that are full, so that I can potentially get into a better time or better class
  
- **US-C08**: As a client, I want to be able to toggle a view of classes that are full, so that I can join the waitlist **dependency** - C07
  
- **US-C09**: As a client, I want to be able to sign up for a class, so that my spot is reserved for when I show up
  
- **US-C10**: As a client, I want to be able to sign up for both private lessons and group classes, so that I can choose what kind of experience I would like to have **D** - C09
  
- **US-C11**: As a client, I want to be able to click a link to the studios social medias, so that I can be a closer part of the community
  
- **US-C12**: As a client, I want to be able to directly email the support team, so that I can get help with a problem I have.
  
- **US-C13**: As a client, I want to be able to report a bug on the app, so that it can be fixed and work more functionally.
  
- **US-C14**: As a client, I want to to view prices of different classes and what's offered, so that I can make decisions about which classes I'd like to go to.
  
- **US-C15**: As a client, I want to view different subscription tiers and their value, so that I can decide what is best for me.
  
- **US-C16**: As a client, I want to cancel my reservation for a class, so that I can free up my spot if I can no longer attend. **D** - C09
  
- **US-C17**: As a client, I want to see my recommended skill level when browsing classes, so that I can identify which classes are appropriate for my experience.
  
- **US-C18**: As a client, I want to be restricted from booking classes above my skill level, so that I don't end up in a class I'm not prepared for. **D** - C09, C17
  - *Note: acceptance criteria will need to define the unlock threshold (e.g. "level 1 unlocks level 2 after X classes completed") — flag ❓ for your girlfriend's input on the exact number.*
    
- **US-C19**: As a client, I want to add a note about an injury or physical limitation when booking a class, so that my instructor is aware before class starts. **D** - C09
  - *🔒 flag: this note likely needs to be visible to Staff (per actors.md) but should not be editable by them — worth a dedicated abuse case later.*

- **US-C20**: As a client, I want to add a payment method to my account, so that I can pay for classes and packages without re-entering my card details each time.

- **US-C21**: As a client, I want to change or remove a saved payment method, so that I can keep my payment information current. **D** - C20

- **US-C22**: As a client, I want to purchase a subscription, bundle, or class pack, so that I can pay for and access the classes I want to attend. **D** - C15, C20
  - *Note: this is your first "money changes hands" story — will need its own acceptance criteria pass once Stripe integration is designed (Phase 3).*

- **US-C23**: As a client, I want to view my current credit balance, so that I know how many classes or what value I have available to use.

- **US-C24**: As a client, I want to view my transaction history, so that I can review what I've purchased and paid for.

- **US-C25**: As a client, I want to view a history of classes I've attended, so that I can track my own progress and consistency.

- **US-C26**: As a client, I want to change my account details (name, phone, gender, email, etc.), so that my profile stays accurate and up to date. **D** - C05

- **US-C27**: As a client, I want to add a note to my account about an injury or physical limitation when booking a class, so that I do not have to input it each time I sign up for a class. **D** - C09, C19
  - *🔒 flag: this note likely needs to be visible to Staff (per actors.md) but should not be editable by them — worth a dedicated abuse case later.*
 
### Epics
 
- **EPIC-C-Booking**: As a client, I want a complete, safe booking flow, so that I can reserve, manage, and get the most out of my class attendance. **Dependency** = C09, C10, C16, C17, C18, C19, C27

- **EPIC-C-AccountPage**: As a client, I want an account page with all my data and information, so that I can edit my preferences and change data in one place. **Dependency** = C04, C20, C21, C23, C24, C26

- **EPIC-C-Dashboard**: As a client, I want a dashboard that shows the most important information I need a glance, so that I don't have to spend time navigating different menus to find what I need. **Dependency** = C01,C02, (more if I decide on another dashboard display).

 
## Staff

- **US-S01**: As staff, I want to view the classes I'm scheduled to teach, so that I know my upcoming teaching commitments.

- **US-S02**: As staff, I want to view the roster of clients enrolled in a class I'm teaching, so that I know who to expect.
  - *🔒 flag: this must be scoped to classes the staff member is currently assigned to teach — not all classes studio-wide. This is your actors.md "cannot view clients outside their classes" rule in action; write the abuse case for this one (staff attempts to view a roster for a class they aren't teaching).*

- **US-S03**: As staff, I want to see relevant client details for my roster (skill level, age, injury/limitation notes), so that I can teach safely and appropriately.
  - *Note: this is the "helpful to know" data from your actors.md — deliberately narrower than what Admin/full client profile shows. Don't let this story's acceptance criteria accidentally expose fields staff shouldn't see (e.g. total spend, full contact info) — worth cross-referencing against US-C19 (injury note) so the field set is consistent everywhere it's displayed.*

- **US-S04**: As staff, I want to view all available class times studio-wide, so that I understand the full schedule context around my own classes.

- **US-S05**: As staff, I want to offer one of my scheduled classes to be picked up by another instructor, so that I can get coverage if I'm unavailable.

- **US-S06**: As staff, I want to view classes currently available for pickup, so that I can choose to cover a class another instructor has offered.

- **US-S07**: As staff, I want to pick up a class that's been offered by another instructor, so that I can claim it and be assigned as the new teacher. **D** - S06

- **US-S08**: As staff, I want to message an individual client through the app about a specific question (e.g. an injury note), so that I can clarify anything before their class.
  - *🔒 flag: needs an abuse case — can staff message clients outside their own roster? This should almost certainly be scoped the same way as US-S02.
 
- **US-S09**: As staff, I want to be able to un-offer my classes for pickup, so that I can change my mind. **D** - S05, S06

- **US-S10**: As staff, I want to be notified when a class is offered for pickup, so that I can have the knowledge its available. **D** - S05 

### Epics
- **EPIC-S-MyClasses**: As staff, I want a view of my teaching schedule and rosters, so that I can prepare for and manage my classes without digging through the full studio schedule. **Dependency** = S01, S02, S03

- **EPIC-S-Pickup**: As staff, I want a way to offer and claim class coverage, so that scheduling gaps get filled without needing admin intervention. **Dependency** = S05, S06, S07, S09, S10


## Admin

### Class management
- **US-A01**: As an admin, I want to create a new class, so that it appears on the studio schedule for clients to book.
- **US-A02**: As an admin, I want to edit an existing class (time, teacher, type, capacity), so that I can correct or update schedule details.
- **US-A03**: As an admin, I want to cancel a class, so that clients and staff are notified it's no longer happening.
  - *❓ flag: what happens to clients already booked when a class is cancelled — automatic refund/credit, or notification only? Needs your girlfriend's input before acceptance criteria.*
- **US-A04**: As an admin, I want to edit the price of a class, so that I can adjust pricing without needing developer involvement.
- **US-A05**: As an admin, I want to set the studio's operating hours, so that the schedule reflects when the studio is actually open.

### Schedule views
- **US-A06**: As an admin, I want to view the class schedule in day, week, or month views, so that I can plan and review at whatever level of detail I need.
- **US-A07**: As an admin, I want to see all classes for a given day listed with their fullness, teacher, time, and class type, so that I can get a quick operational overview.
- **US-A08**: As an admin, I want to click into a specific class and see everyone signed up along with their relevant metadata, so that I can manage that class's roster directly.
- **US-A09**: As an admin, I want to see anyone who signed up and then cancelled for a class, so that I have visibility into cancellation patterns.

### Client management
- **US-A10**: As an admin, I want to view a list of all enrolled clients with their age, membership package, and total spend, so that I can get a quick overview of the client base.
- **US-A11**: As an admin, I want to view an individual client's full profile — upcoming classes, purchases, credit balance, payment methods (excluding raw card numbers), preferences, and customer details (age, email, phone, gender, account creation date, last visit, total spend, total reservations) — so that I have complete context when helping a client or making decisions about their account.
- **US-A12**: As an admin, I want a summary section within a client's profile showing immediate at-a-glance info (upcoming schedule, active subscriptions), so that I don't have to dig through the full profile for common questions.
- **US-A13**: As an admin, I want a reservations tab within a client's profile showing their booking history, so that I can review their attendance pattern.
- **US-A14**: As an admin, I want to remove a client from a class, so that I can manage a roster manually if needed (e.g. resolving a conflict or error).
- **US-A15**: As an admin, I want to ban a client from the studio, so that I can enforce studio policy in serious cases.
  - *🔒 flag: high-impact action — will need strong acceptance criteria (confirmation step, audit trail of who banned whom and why) and its own abuse case (e.g. can a compromised admin session ban clients en masse without detection).*

### Staff management
- **US-A16**: As an admin, I want to view all staff members, so that I have visibility into who's on the team.
- **US-A17**: As an admin, I want to view individual staff wages, so that I can manage payroll-related information.
  - *Note: per your own actors.md note, this may need to move to an Owner-only tier if front-desk help is hired later. Worth keeping this story separate from US-A16 now specifically so it's easy to re-scope later without touching the rest of Admin.*

### Notifications
- **US-A18**: As an admin, I want to send a notification to everyone signed up for a specific class, so that I can communicate class-specific updates (e.g. a cancellation or time change).
- **US-A19**: As an admin, I want to send a marketing/update notification to all clients who've opted in, so that I can promote the studio or share news.

### Epics
- **EPIC-A-ClassMgmt**: As an admin, I want full control over class scheduling and pricing, so that I can run studio operations without developer involvement. **Dependency** = A01, A02, A03, A04, A05

- **EPIC-A-ScheduleView**: As an admin, I want flexible views into the studio's schedule, so that I can operate at whatever zoom level a task requires. **Dependency** = A06, A07, A08, A09

- **EPIC-A-ClientMgmt**: As an admin, I want complete visibility and control over individual client accounts, so that I can support clients and manage the business relationship. **Dependency** = A10, A11, A12, A13, A14, A15

- **EPIC-A-StaffMgmt**: As an admin, I want visibility into staff and payroll information, so that I can manage the team. **Dependency** = A16, A17

- **EPIC-A-Notifications**: As an admin, I want to communicate with clients at both the class and studio-wide level, so that I can keep clients informed. **Dependency** = A18, A19


# Non-Functional Reqs
- **NFR-01**: Client must be able to complete a class booking in 3 taps or fewer 
  from the dashboard.
- **NFR-02**: Dashboard must load upcoming reservations within 2 seconds on a 
  typical mobile connection.

# Design Constraints
- **DC-01**: Studio logo must appear in the header on every client-facing screen, for brand consistency.
- **DC-02**: Profile button will be in the top right of the screen in the header.
- **DC-03**: Achievements features where client gets rewards displayed in a circular graphic and it fills as you get closer.
- **DC-04**: Checkbox on the schedule screen to show the full classes (US-C08) will be right next to schedule list
- **DC-05**: Client roster view for staff must exclude spend, membership package cost, and full contact details — matches actors.md restriction.
- **DC-06**: Admin UI must not expose raw database records, schema details, or code — only business-object views (clients, classes, payments).
