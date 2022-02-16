---
title: "WebDev Bootcamp — Week 5"
last_modified_at: 2022-02-16
toc: true
categories:
 - WebDev
 - Code
tags:
 - WebDev Bootcamp
 - freeCodeCamp
---

I finished week 5 of the Web Development Bootcamp, which covered concepts like flexboxes, grids, variables and media queries.  

{% capture notice-text %}
**Read more about the Bootcamp here:**
- [Introduction](/posts/webdev-bootcamp-intro/)
- [Week 1](/posts/webdev-bootcamp-w1/)
- [Week 2](/posts/webdev-bootcamp-w2/)
- [Week 3](/posts/webdev-bootcamp-w3/)
- [Week 4](/posts/webdev-bootcamp-w4/)
{% endcapture %}

<div class="notice--info">
  {{ notice-text | markdownify }}
</div>

# Schedule

Date | Description | Link
-------------------------------------|-------------|----
Feb 7 (Mon)| Learn CSS Variables by Building a City Skyline | [freeCodeCamp](https://www.freecodecamp.org/learn/2022/responsive-web-design/#learn-css-variables-by-building-a-city-skyline)
Feb 8 (Tue)| Learn CSS Grid by Building a Magazine | [freeCodeCamp](https://www.freecodecamp.org/learn/2022/responsive-web-design/#learn-css-grid-by-building-a-magazine)
Feb 8 (Tue) | Guest Session: You Really Don't Need All That JavaScript, I Promise | [YouTube](https://www.youtube.com/watch?v=0t7UJnAA8zY&ab_channel=ClassCentral)
Feb 9 (Wed) | Project: Build a Product Landing Page Project | [freeCodeCamp](https://www.freecodecamp.org/learn/2022/responsive-web-design/#build-a-product-landing-page-project)
Feb 10 (Thu) | Guest Session: How to Read Code? | [YouTube](https://www.youtube.com/watch?v=xZZ74d8XUl0&ab_channel=ClassCentral)

<br>

# Building a city skyline
For this lesson, we created a city skyline that changes from night to day when you change the width of the screen. This lesson’s focus was on variables, flexboxes and gradients (`linear-gradient`, `repeating-linear-gradient` and `radial-gradient`).

<div class="full">
  <p class="codepen" data-height="600" data-default-tab="html,result" data-slug-hash="ExbywrO" data-user="fadilla-wahyudi" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
    <span>See the Pen <a href="https://codepen.io/fadilla-wahyudi/pen/ExbywrO">
    City Skyline (freeCodeCamp)</a> by fadilla-wahyudi (<a href="https://codepen.io/fadilla-wahyudi">@fadilla-wahyudi</a>)
    on <a href="https://codepen.io">CodePen</a>.</span>
  </p>
  <script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>
</div>

<br>

# Building a magazine
This lesson was about creating a magazine using grids. We also covered FontAwesome, pseudo-elements (`::first-letter`, `::before`, `::after`) and media queries again. It should be noted that for the purpose of this lesson, we used `text-align: justify`. It is not recommended to do this in real life because it can be difficult for people with dyslexia to read it.

<div class="full">
  <p class="codepen" data-height="600" data-default-tab="html,result" data-slug-hash="PoObMop" data-user="fadilla-wahyudi" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
    <span>See the Pen <a href="https://codepen.io/fadilla-wahyudi/pen/PoObMop">
    Magazine (freeCodeCamp)</a> by fadilla-wahyudi (<a href="https://codepen.io/fadilla-wahyudi">@fadilla-wahyudi</a>)
    on <a href="https://codepen.io">CodePen</a>.</span>
  </p>
  <script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>
</div>

<br>

# Project: Building a product landing page
For our project, we had to create a product landing page that fulfilled 15 user stories, which included creating a navigation bar and a form that enables users to submit their email address, embedding a video and making it responsive.

<div class="full">
  <p class="codepen" data-height="600" data-default-tab="result" data-slug-hash="JjObgZX" data-user="fadilla-wahyudi" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
    <span>See the Pen <a href="https://codepen.io/fadilla-wahyudi/pen/JjObgZX">
    [Project] Product Landing Page (freeCodeCamp)</a> by fadilla-wahyudi (<a href="https://codepen.io/fadilla-wahyudi">@fadilla-wahyudi</a>)
    on <a href="https://codepen.io">CodePen</a>.</span>
  </p>
  <script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>
</div>

<br>

# Guest sessions
This week, we had two guests come over and speak, Stuart Langridge and Felienne Hermans.

## Stuart Langridge — You Really Don't Need All That JavaScript, I Promise
[Stuart Langridge](https://twitter.com/SIL) is consultant CTO and developer. His talk was mainly about JavaScript and because I haven’t learnt it yet, I didn’t understand much about what he was talking about.

Here are couple key messages that I got from his session:

- Browsers are really good at rendering HTML. It is [faster for a browser to load 27,000+ tweets using HTML versus 1 tweet using React](https://twitter.com/zachleat/status/1169998370041208832) (which I learnt is a JavaScript library).
- There are many reasons why a person may not be able to load the JavaScript:
    - They disabled JavaScipt
    - They are not using a browser that supports JavaScript.
    - They are behind a corporate firewall.
    - They may be using using a data plan and it may have disabled the scripting.
    - They may have browser extensions or plugins that are interfering with JavaScript.
    - ISPs can block JS or certain JS libraries (this has personally happen to me where some of my friends could not load `bootstrap.min.js`)
- If you can achieve the same thing in HTML or CSS, then write it in those languages. These languages have gotten smarter over the years

## Felienne Hermans — How to Read Code?
[Felienne Hermans](https://felienne.com/) is an associate professor at Leiden University. She developed a gradual programming language, called [Hedy](https://hedycode.com/), that is suitable for kids who want to learn programming and for people’s whose first language may not be English. Her talk was about how to learn how to read code.

Here's what I took home from her session:

- We have three types of memories:
    1. Short-term memory — items that are held in your memory if you are exposed to it for a few seconds (e.g. a series of letters flashing once on your screen). A person can hold 5-9 things in their short-term memory.
    2. Working memory — works together with your short-term and long-term memory; it helps actively manipulate items in your short-term memory (e.g. performing calculations in your head).
    3. Long-term memory
- It is easier to hold more things in your short-term memory when they are part of your long-term memory. For example, it is easier to remember a short sentence flashing on your screen versus a series of symbols.
- Different types of issues arise when you’re learning a language. Different issues require different solutions:

Issue | Example | Possible solution(s)
------|------------|----------
Long-term memory | When you see a term/item/thing and you don't know what it means. | Practice syntax, perhaps use flashcards
Short-term memory | You know other programming languages but with this language, you are unfamiliar with the syntax. | Rewrite it in a programming language that you understand
Working memory | You are familiar with the language and you know what the generally does but it takes you a lot of processing power to understand exactly what is going on. For example, there are too many variables and you find it hard to retain what each variable represents. | Support your working memory. Write it down; draw it out.

- Understanding your own misunderstanding makes you a better programmer.
