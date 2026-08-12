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
- **EPIC-C-AccountPage**: As a client, I want an account page with all my data and information, so that I can edit my preferences and change data in one place. **Dependency** = C04,C05,...
- **US-C04**: As a client, I want an option to sign up for or reject notifications from the company, so that I can choose how informed I would like to be about the studio
- **US-C05**: As a client, I want the option to change my email, so that if I need to redirect where the emails are going I can
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
