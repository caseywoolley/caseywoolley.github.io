---
layout: post
title:  "Question Everything"
date:   2015-10-24 18:35:05
categories: tech
tags: code hackreactor
image: /images/XNBK7TFBAU.jpg
---

Working with a team I recently had the opportunity to push new features onto an already functional full stack app built by another team.  It was a well architected app and we were looking forward to getting our hands dirty in the code.  We had great aspirations for the features we’d add.  We pegged a couple of mundane tasks that we’d get taken care of on the first day and then we’d move on to the really fun stuff.  But as these things typically seem to go, what we thought would be easy to knock out in a few hours quickly turned into multiple days of pain.

I remember hearing a story a while back from someone who had struggled with getting a piece of code in a legacy app to pass its tests for hours, banging their head against the wall and struggling with one bizarre issue after another.  And in the end found out what they were trying to do was perfectly correct.  The bug wasn’t in their code after all, it was in the tests they were provided.

In coding it’s very easy to sometimes take things at face value.  We are supposed to strive for abstraction and encapsulation after all.  But when errors occur, as they always do, we have to be willing to broaden our search even beyond our initial intuition.

So, even though I had heard that other coder's story and thought I had internalized it we still had to learn it again the hard way.  Our issue revolved around fixing a piece of the api routes that wasn’t communicating correctly.  We spent hours looking up details on all the components involved and attempting every potential bug fix we could find.  All of our code seemed to match the documentation perfectly.  Finally we decided to play around a little more with some of the working routes in our file.  What we found was they weren’t working either.  We couldn’t understand it.  Was this a joke left by our classmates to see how much time we’d waste on it?  It was as though the entire file we’d been working in wasn’t even connected to the app.

Eventually we found the real issue. When we were trying to test the api calls directly.  We had used a standard path seen in the documentation.  The server had responded so we had never thought to give the request path a second thought.  It still appeared to be responding to our requests, just in totally weird and unpredictable ways.  Had we been slightly more familiar with the codebase we probably would have noticed our flawed path immediately but unfortunately this wasn’t the case.

When we finally began to question the existing code around us in the file, and ask what’s even working here, we were able to quickly stumble across our mistake.  Hopefully the lesson sticks this time.  When coding, question your code, question your documentation, question your assumptions, question your questions… in other words question everything.


