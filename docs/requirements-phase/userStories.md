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
  
- **EPIC-C-Dashboard**: As a client, I want a dashboard that shows the most important information I need a glance, so that I don't have to spend time navigating different menus to find what I need. **Dependency** = C01,C02, (more if I decide on another dashboard display).
  
- **US-C03**: As a client, I want a profile button that can take me to my account page, so that I can view my information easily and in one place.
  
- **EPIC-C-AccountPage**: As a client, I want an account page with all my data and information, so that I can edit my preferences and change data in one place. **Dependency** = C04, C20, C21, C23, C24, C26
  
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
 
- **EPIC-C-Booking**: As a client, I want a complete, safe booking flow, so that I can reserve, manage, and get the most out of my class attendance. **Dependency** = C09, C10, C16, C17, C18, C19, C27
 



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
