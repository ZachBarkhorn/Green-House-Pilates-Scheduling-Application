Important to define because every authorization decision is based on these roles and the actions they are allowed to partake in. If this isn't inherently built into the system it is a high likelihood that authorization security will be weak.

List what each role can see, and what they can do.

## Admin (no access to database schema or code)
- Can view: all clients (and their data [no card numbers]), all classes, all payments, all cancellations, all staff members, class prices, staff wages (may need to split into another role if front desk help is hired later)
- Can do: create/edit/cancel classes, edit the price of classes, send notifications to people signed up for the class, send notifications to all users signed up to receive marketing/updates, set the hours of the studio, remove users from the classes, ban people from the studio
- Cannot: view source code, access db schema, can only access things relevant to the business, not the technological aspects

## Staff
- Can view: Clients that are signed up for classes they are teaching (their experience level, age, things that are helpful to know for the instructor, injuries etc...), available classes, classes available for pickup, times of the classes,
- Can do: offer their scheduled class to be picked up by another instructor, pick up another instructors offered class, message individual clients through the app to ask specific questions about injuries
- Cannot: view all clients PII (only what's needed), view client spend amount, remove clients from classes, ban clients, view other staff wages, view clients outside their classes, edit class prices
 
## Client
- Can view: Available classes, classes that are full (join waitlist), membership options, recommended Pilates skill level for each level of class, their own profile (how many classes they have gone to, transaction history, past classes attended, how close they are to a milestone
- Can do: book classes within their skill level (if selected beginner when making account level 2 n 3 classes are blocked. can only sign for level 1 until x amt of classes are completed), cancel their reservation, add a notes for the instructor to view (regarding injury/limitation maybe), add their payment method to be saved, alter payment method, change account details

## Anonymous Visitor
- Can view: the home page (displays what the studio is, the mission statement, what they are about, their methodology of teaching, who they cater to), testimonials, pictures of the studio and people being happy taking classes,
- Can do: create an account,

## System/Service (Stripe)
- Can do: update payment status, webhook payloads must be signature-verified before being allowed to do their action.
