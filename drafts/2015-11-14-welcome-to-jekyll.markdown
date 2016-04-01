---
layout: post
title:  "Callbacks vs Promises"
date:   2015-11-14 16:52:07
categories: tech
tags: code hackreactor
image: /images/XNBK7TFBAU.jpg
---
Callbacks are a huge part of javascript and were a difficult part of the learning curve for me.  But when I finally did get it, passing over the callback barrier felt amazing and it opened up a whole new world of javascript programming to me.

Suddenly, each, map, and filter were no longer just magical boxes that do my bidding.  I could understand their innerworkings and build them from scratch.  This was a major milestone for me.

But as my learning has progressed I’ve found out out the callbacks have drawbacks.  There’s something that programmers fondly call “callback hell” where callbacks become so deeply embedded into one another that they make almost no sense to look at and can’t be unentangled without possibly destroying your code.

{% highlight javascript %}
User.logIn("user", "pass", {
  success: function(user) {
    query.find({
      success: function(results) {
        results[0].save({ key: value }, {
          success: function(result) {
            // the object was saved.
          },
          error: function(result, error) {
            // An error occurred.
          }
        });
      },
      error: function(error) {
        // An error occurred.
      }
    });
  },
  error: function(user, error) {
    // An error occurred.
  }
});
{% endhighlight %}


Enter promises.  A promise represents a task that may or may have not completed yet.  At this point promises are still a little magical to me.  I can use them and generally they work for me but their internal workings is still a little mysterious and magical.  On the surface promises seem pretty similar to callbacks.  Nothing special.

But as you dive in deeper with them you can see their major benefits.  From what I understand the major difference with promises is that they’re kind of like self aware callbacks.  They know when they are fulfilled or not fulfilled and they can act accordingly.  

But the even greater benefits come from promise chaining. They are aware if the callback from the then function is another promise then they won’t be fulfilled until the next promise completes.  This is killer when it comes to error handling.  A failed promise can bubble up through the chain to the final catch all rather than being handled independently by each independent callback function.

Same code as above with promises:

{% highlight javascript %}
User.logIn("user", "pass").then(function(user) {
  return query.find();
}).then(function(results) {
  return results[0].save({ key: value });
}).then(function(result) {
  // the object was saved.
}, function(error) {
  // there was some error.
});
{% endhighlight %}


With promises we can lay off the ugly deep nesting and understand much better what the code is doing at each point along the way.  I’ve still got a ways to go with understanding these magical promise keepers but for now they will be serving to make my code look much cleaner and manageable.


