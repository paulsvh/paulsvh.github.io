---
layout: post
title:      "There's a gem for that..."
date:       2020-07-28 01:28:45 +0000
permalink:  theres_a_gem_for_that
---


One of the biggest benefits of working in Ruby/Rails is the access to Ruby gems. If you've been working in Ruby, you've undoubtedly already been working with at least a few gems to help you along, but what really IS a Ruby gem?

A gem is just a library of Ruby code and some extra data. The code packaged within the gem specifies what that gem will be doing. By installing a gem for your project, you have access to it's code and whatever that code has built or supplied for you. For example, by installing the SQLite gem, you're giving your application access to use SQlite as it's database for ActiveRecord. There are tons of helpful gems that can manage different tasks or give you access to different options and abilities without having to program them in yourself.

When discussing my project with another student, we came down to talking about how he managed to include pagination in his view to separate all of his listings onto multiple pages. I had done a bit of research and it seemed like it wasn't going to be an easy implementation. He told me he had just found a gem to do it for him (shout out to the [Will Paginate](https://github.com/mislav/will_paginate) gem). Awesome, there's a gem that handles most of the work for you! We later got to talking about how he implemented a voting system to display amount of upvotes/downvotes on a product, and of course, there's a [gem for that](https://github.com/ryanto/acts_as_votable) too. It brought me to a realization that I definitely wasn't utilizing gems as well as I could be, and needed a reminder on how best to find them.

So we know that there are gems floating out in the ether for us to utilize, how do I find them? There's a way to search for gems straight from your terminal, but it requires having an idea of the gem you want and looking for it by name. What if you're just trying to see if a gem exists for something you're trying to do? This will more often than not be the case, and as with most things programming-related, Google is your best friend. Simply googling "Ruby gem for pagination" will give you plenty of results, but if you want something a bit more concise and easily viewable, try searching on [Ruby Gems](http://rubygems.org) or [Ruby Toolbox](http://ruby-toolbox.com) where you can search for gems and see how many people have used them to get an idea of their popularity. 

In the future I'll have to remind myself that if there's something complex that relates to a specific task, someone has probably already made a gem for it, and as a lazy programmer you know I'm going to try to find a gem first!


