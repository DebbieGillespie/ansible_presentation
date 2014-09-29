## One Stop Queueing System


### Demo

Note:
We'll start off with a demo. Seeing things in action will make our discussion a little more clear, hopefully.


#### http://z.umn.edu/queue

Note:
After people have the URL, switch to a browser that is running the Signage. Call people up, if possible.


### Simple!

Note:
There's not much there, right? You put in your ID or name, you show up on that list of people waiting and then we call you up.


Here's how we understood the project at the beginning:

1. Read a card swipe
2. Post data to SalesForce API
3. Receive updates via SalesForce over HTTP

Note: And that was pretty much what we knew.


### Let's get Agile!

Note:
Being a quick-moving Agile team we hopped in and started writing code. Work began on an Ember application that would serve as the kiosk.


### Maybe less Agile!

Note:
Think back to that demo. How much complexity did you see? Did it look like 6 different systems communicating over 3 different protocols? Because that's what it is.


# Lesson 1
## NoDUF isn't always better than BDUF

Note:
There's a misapprehension about Agile that teams shouldn't design. Instead they should 'discover as they go'. And, as a reaction to huge, tedious waterfall designs, it seems logical to think that Agile teams shouldn't design.

But here, by jumping into coding, we set ourselves up for endless rewrites.

What could we have done differently? I think if we'd spent 3 days paper protyping the system and its interactions, we would have revealed its complexities and we would have ended up with a better design.


## Our Final App Design

- One Ember app as the Kiosk
- One Ember app displaying the queue
- PeopleSoft, for preferred name lookups
- SalesForce, which
  - we query to get configuration details
  - we POST student data to, adding students to the queue
  - POSTS to us when a student is called
- A Rails app that 
  - serves the Ember apps
  - manages communication with SalesForce
  - manages communication with PeopleSoft
  - mantains oAuth credentials with SalesForce
- Faye, a web-socket based pub/sub libary
  - Pushes queue updates to the Ember app
  - Channel for managing the Ember apps (releasing new versions, reloading, etc.)


### Onwards!
#### To Complexity and Beyond

Note:
But we didn't do that. Instead we kept working and as the complexity grew we tried to tackle it quickly or ignored it. Pretty classic 'firefighting' mentality emerged quickly.


# Lesson 2:
## Suprises = Regroup

Note:
Since our initial understanding of the system turned out to be flawed, any one of these surprises should have led to us to say, "Wait, let's regroup and figure out what this system is." That's a responsible response to change, which is a core Agile tenet.


### Onwards!
#### External Services and Integration

Note:
Earlier we mentioned that this is made up of 6 systems. Let's quickly describe the 5 of those we knew about at this time: A Ember app for the kiosk, another Ember app for the Signage, a Rails app and then SalesForce and Peoplesoft. PeopleSoft knew the students' names and SalesForce handled all the CRM stuff.


## Lesson 3: Stub what you don't control

Note:
This is a perfect case for using some dummy services or stubbed out responses. SalesForce hasn't implemented the endpoint yet? No problem. Away from the internet, no problem.


## Lesson 3.1: But stubs will destroy you

Note:
And then you try testing against the real service and your app won't run. Your stub has something quoted that the service doesn't. The key names are slightly different. Whatever the reason, you have to have tests that exercise your app against both stubs and real services. We didn't and eventually fell into a paranoia of not testing any code until we saw it run in Staging. Then we hoped that the services wouldn't change unexpectedly.


### Onwards!
#### Let's Deploy This Stuff

Note:
After fighting our fires and unwapping all the hidden complexity, we ended up with an app that actually worked pretty well. It took us longer than it should have, but at least it worked. Now to show it off.


## Lesson 4: Works fine on my machine

Note:
And, of course, it didn't deploy. We almost always get the order of development wrong. In our mind it's a list [Test, Develop, Deploy]. But that means we always save the hardest and most valuable step for last. Which do you think your customer would prefer?
