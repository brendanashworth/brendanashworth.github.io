---
layout: post
title:  "Programming and Corruption: an Anomaly"
date:   2014-12-03 04:24:33 -0700
---
As someone who has always been interested in politics and computer science, I never really put much thought into putting them both together -- until a dark and rainy night when I decided to put [Google Trends](http://www.google.com/trends/) to the test in its ability to find [interesting data correlations](http://xkcd.com/522/).

I had always believed that some programming languages attracted different crowds than others, and I had developed stereotypes for various languages (validity pending): Perl was for system administrators, JavaScript was "hip, new, and fast", and Java was a tested, true, and bulky language that was used only in enterprise-level companies (and a [quirky game](http://java.com/en/download/faq/minecraft.xml) to boot). The fact was that as an American, I stereotype way too easily!

[![stereotypes](/images/2014-12-03/xkcd_850.png)](https://xkcd.com/850/)

The issue is that *some* stereotypes are true to a degree (yes, we all have guns). I decided the only way to prove or disprove the many predefined stereotypes of mine would be to test with some data. Lo and behold, my question: is there any correlation ([causation?](https://xkcd.com/552/)) between programming language popularity and government corruption?

Yes, I am aware that computer language choice and government corruption are two very different subjects, and don't *necessarily* say anything about the people that use them. It could all be a coincidence... or not.

I decided to compare six popular programming languages: JavaScript, PHP, Python, Java, Perl, and Ruby. I used the data from the [Corruptions Perception Index](http://www.transparency.org/research/cpi/overview) to compare the countries, and the "Regional Interest" section of Google Trends for each keyword to deduce the most popular countries.

Three notecards, 45-50 unique countries and a flashback to 5th grade math later, a correlation appeared. An anomaly, *right in the numbers themselves*. I couldn't believe it. Some languages (Perl and Ruby) topped the leaderboards with primarily English speaking, [first-world countries](http://en.wikipedia.org/wiki/First_World), while other languages (PHP and Java) tailed with a hodgepodge of developing countries, out of primarily Africa and Asia.

When I took those same countries for each respective language and calculated the average corruption ranking (from the Corruption Perception Index), the data was definitive and clear. There *was indeed correlation* between specific programming languages and the corruption level of the countries they were most popular in!

Perl -- most commonly used by Luxembourg, Japan, India, Germany, the United States and Singapore -- showed the best average corruption ranking at 71.7 (higher is better). It was followed by Ruby (New Zealand and USA), then Python (Cuba and Iceland), JavaScript (India and Cuba), and finally PHP (Cuba and the Phillipines). Bringing up the rear was Java: with an average corruption ranking of 33.4, its top 10 assortment of countries contained Cameroon, Togo, Bangladesh, Madagascar, and Indonesia.

> Per capita <sup>[[1](https://support.google.com/trends/answer/4365533?hl=en&ref_topic=4365599)]</sup>, Java and PHP are substantially more popular in corrupt countries, when compared to alternatives like Python and Perl.

Maybe a graph will help you visualize the percepted corruption for each language. The highest score achieved in 2013 for the corruption perception index was 91, for New Zealand and Denmark -- and over two thirds of the countries surveyed scored below a 50 in the ranking.

![corruption and programming languages](/images/2014-12-03/corruption-by-language.png)

Yes, correlation does not imply causation -- however, the anomaly here clearly lies in the numbers (and a nice graph). Programming language popularity per capita does indeed have unexpected associations with the corruption ranking for each respective country. Where do you stand on the scale?
