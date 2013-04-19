---
layout: post
title: Piki retrospective
---
Late last year I released [Piki](http://piki.heroku.com), a web app designed to make it as intuitive and comfortable as possible to create and maintain personal wikis. It was supposed to be a breath of fresh air in an ecosystem filled with heavy and complicated solutions--a [Sculptris](/images/sculptris.png) among [ZBrushes](/images/zbrush.jpg).

Some liked it, but it didn't take off and become a trendsetter like I was confident it would. Here are the lessons I've learned in hindsight:

## A web app needs to be able to handle traffic 

As Piki was [bubbling up on Hacker News](https://news.ycombinator.com/item?id=4646665), visitors were often greeted with a server error message. This was due to a combination of lack of caching, Google Docs-style autosaving and faulty database-handling code, all on Heroku’s free plan. “Don’t scale early” is sensible advice, but I should at least have had a bank account prepared for an extra dyno or two at launch.

## Front-end MV* and testing frameworks are a great idea

The wiki editor had to be perfect, it was to be the app’s killer feature. Pressing enter once had to make a new paragraph, twice had to make a header. The first line had to always be the page’s title, and changing it had to instantly modify its index entry below. Mentioning the title of another page had to automatically create a link to it.

I implemented all of this using a mess of untested jQuery and rangy calls on a contenteditable HTML element which I dare not touch today. I could have saved myself a great deal of trouble by skipping the contenteditable element altogether and taking advantage of Backbone and Jasmine to build the editor with a solid and extensible architecture.

## People like their private stuff truly private

Piki’s target market is people who want to organize their own thoughts and ideas. Some people expressed unease trusting a small web app with that sort of information, which I understand. It would have been better to make Piki save to local storage by default with optional syncing to the server.

## Piki doesn't solve a real problem

Typical wiki engines are heavy and focus on large collaborative efforts, and Piki was made to be a light, single-person alternative to that. Piki may have a polished user experience that handles a lot of typical wiki micromanagement with an elegant editor based on novel web technology, but does it really scratch an itch that people have? Is Piki truly that compelling a writing tool over something like Notepad or Google Docs?

I think I was correct in prioritizing usability, but should have focused less on the editor and more on the ideas that popularized the wiki medium in the first place. If I were to design a wiki app today, it would be edited using a mere textarea that accepts Markdown, have easy-to-traverse history, and have forking and merging in favor of centralized collaboration. But then again, one could just use Google Docs or Notepad and Github for something close to that.
