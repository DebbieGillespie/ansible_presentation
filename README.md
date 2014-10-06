## One Stop Queueing System


### Demo

Note:
We'll start off with a demo. Seeing things in action will make our discussion a little more clear, hopefully.


### Play Along!
#### http://z.umn.edu/queue
#### http://z.umn.edu/signage
##### (Or Do Both)


## Simple


## That's What We Thought, Too


## Here's What We Thought the Project Was

1. Read a card swipe
2. Post data to SalesForce API
3. Receive updates via SalesForce over HTTP

Note: And that was pretty much what we knew. And, as you saw, that pretty much looks like what the app does.


## Onwards!
### Let's Code

Note:
- We started with an Ember app running in the Kiosk
- Simple solution for a simple problem
- Would satify the first two of the requirements


## Or, you know, not.

Note:
- This Ember app could handle card swipes and name entry, but


As we began to discuss, we found we also needed ways to:

- Show the Queue to people waiting
- Get preferred names from SalesForce
- Maintain our oAuth credentials with SalesForce
- Release new versions of the Ember applications
- Tell the Kiosks when One Stop is closed
- Prevent malicious users from running their own kiosks
- Get configuration data quickly from SalesForce
- Receive updates about students being called to the desk

Note:
- Think back to that demo.
- Did it look like 6 different systems, 3 languages and 3 protocols?


# Lesson 1
## NoDUF isn't always better than BDUF

Note:
- Agile stereotype of 'not desgining'
- Instead, concern should be 'over desgining'
- You need to understand the problem
- That can be simpler before coding
- In future we plan on spending 3-5 days doing paper prototyping


## Onwards!
### To Complexity and Beyond

Note:
But we didn't do that. Instead we kept working and as the complexity grew we tried to tackle it quickly or ignored it. Pretty classic 'firefighting' mentality emerged quickly.


# Lesson 2:
## Surprises = Regroup

Note:
Since our initial understanding of the system turned out to be flawed, any one of these surprises should have led to us to say, "Wait, let's regroup and figure out what this system is." That's a responsible response to change, which is a core Agile tenet.


## Onwards!
### External Services and Integration


As we worked, our systems grew. We had to handle communication between:

- Ember Kiosk app
- Ember Signage app
- Rails for HTTP services
- PeopleSoft for names
- SalesForce for everything else


# Lesson 3:
## Stub what you don't control

Note:
- Difficult communicating with all those services
- SalesForce security particularly tricky
- Especially when not all development is done
- SalesForce endpoints were changing frequently
- Stubs isolate you from what you can't control, letting you develop


# Lesson 3.1:
## But stubs will destroy you

Note:
- Your stubs will always be flawed
- Code that works against a stub will break against the real service
- Test suite needs to run against both
- Otherwise you just end up hoping, or hot patching your staging environment


## Onwards!
### Let's Deploy This Stuff


### What is of more value?

1. A deployed app that's missing a feature
2. A great app that only runs on your laptop

Note:
- We, of course, had option 2.


# Lesson 4:
## Deploy First
(AKA: 'Works fine on my machine' isn't working)

Note:
- Our mental map of a project is: Design, Develop, Deploy
- This puts the most important, and hardest task at the end
- Deploying to 'staging' isn't deploying
- Deploying to a production environment should be the first task, not the last


### Onwards!
#### Students, Students Everywhere

Note:
- Without students, the queue doesn't serve much purpose
- We deployed in summer and things went well
- 800 students a day visit One Stop when school starts
- But if it works for 20 students a day, 800 has to be fine.
- Right?


# Lesson 5:
## Browsers still matter, sadly

Note:
- As students return, the signage gets super laggy
- Not predictable, not consistent
- IE leaks memory like a stuck RAM pig
- Yes, even IE11.
- No, we can't use any other browser
- Identify technology constraints, test them specifically.


# Lesson 6:
## Even flawed projects can be awesome

Note:
- This app is great
- Taught us a bunch about Ember, web-sockets, oAuth and more
- Replaced a $50,000 per/year system
- Saves One Stop staff a ton of time and hassle
- Can be extended in a ton of ways
