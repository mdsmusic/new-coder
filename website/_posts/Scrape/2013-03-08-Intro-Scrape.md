---
layout: post.html
title: "Introduction to Web Scraping using Scrapy and PostGres"
tags: [intro-scrape]
url: "/scrape/intro/"
---

Your favorite website doesn’t have an API? Web scraping is a great alternative to grabbing the data you want.

This tutorial will walk you through how to make a web scraper, save the data to a database, and schedule the scraper to run daily. We will also introduce you to some simple queries to use on the database so you can query the information you scraped at your leisure.


### The Project

We will build a web scraper using [Scrapy](http://scrapy.org/) to scroll through [LivingSocial](http://www.livingsocial.com), and save local deals to our Postgres database. We’ll schedule our computer to run this script daily, so that rather than getting those annoying emails, we can query our database when we want a deal on sky diving or hot yoga.

### Goals

The goals of this particular tutorial are to:
* Develop a more solid understanding of Python classes and inheritance
* Generators
* Reading and writing to a database

Other topics we’ll touch on:
* Using an ORM
* Iterators
* Proper import statements
* Making a portable application

### About Web Scrapers

Web scraping is a technique for gathering data or information on web pages. You could revisit your favorite web site every time it updates for new information. Or you could write a web scraper to have it do it for you!  

A **scraper** is just a script that parses an HTML site – much like the parser we wrote for our CSV data in our [DataViz]({{ get_url('dataviz/')}}) tutorial.

Quick “rules of the road” for scraping websites:
* This isn’t our data that we’re scraping – check a site‘s terms and conditions before you scrape them.
* Scrapers can and do break – Sites change their layout all the time. This will require you to rewrite and adapt your code.
* Web pages are inconsistent – There’s sometimes some manual clean up that has to happen even after you’ve gotten your data.

### About Scrapy

[Scrapy](http://scrapy.org/) is one of the popular web scraping frameworks written in Python. It uses [Twisted](http://twistedmatrix.com/trac/), a Python networking engine, and [lxml](http://lxml.de/), a Python XML + HTML parser.  

**Note for the curious:** The lxml library builds on C libraries for parsing, giving the lxml library speed. This is why we needed to install a compiler.

Scrapy uses Twisted under the hood, a Python library used for networking (which is introduced in the [next tutorial]({{ get_url('networks')}}). Using Twisted allows scrapy to grab hostnames, handle events (e.g. starting, stopping a crawler), as well as gives you the ability to send mail, use the crawler within a Python console, and monitor and control a crawler using a web service. 

Scrapy also has this great [tutorial](http://doc.scrapy.org/en/0.16/intro/tutorial.html) which this follows closely, but extends beyond it with the use of Postgres and a cronjob.

### About SQLAlchemy

[SQLAlchemy](http://www.sqlalchemy.org/) is a Python library that allows developers to interact with databases (Postgres, MySQL, MS SQL, etc) without needing to write raw SQL code within a database shell. It also provides an ORM – Object Relational Mapper – to developers that essentially abstracts the database further.  You can define tables and fields with classes and instance variables instead.  If you have worked through the Django tutorial, perhaps you remember its ORM through the setup of `models.py` and the querying of data within the Django dbshell.

### About Postgres

Postgres is a very popular database that is free and open source. Other popular databases include MySQL, MS SQL, and MongoDB.  Which database you choose depends on what you’ll need it for. Postgres is object-relational DBMS – meaning that it is similar to relational databases, but is object-oriented with objects, classes, and inheritance.  We don’t dive into the difference between relational and object-relational, but just know that Postgres, combined with SQLAlchemy and Scrapy, allows us to capitalize on relational databases with object-oriented programming. 

To learn why Postgres is go great, [Craig Kerstiens](http://twitter.com/craigkerstiens) of Heroku wrote up a nice [explanation](http://www.craigkerstiens.com/2012/04/30/why-postgres/).

As an aside: when I first started learning how to code, the concept of having a database _on_ my computer blew me away. I assumed databases lived in headless computers that could handle the ubiquitous data. Turns out, it’s just like a simple program on your computer. Sure, if you’re a company, you’d want machines dedicated for serving up production-level data. But we’re not heavy-duty number crunching (yet!).

### What is a cronjob?

A cron is a job scheduler for Unix-like computers. It bases its schedule off of a crontab (cron table), of which each line on the table is a job (cron job).

You can schedule a cron job to go every minute, every hour, every day, etc. Wiki has an [overview](http://en.wikipedia.org/wiki/Cron#Predefined_scheduling_definitions) of the actual syntax to use for a cron job.

**If you’re on a Windows Machine**, the cron-equivalent is the [Windows Task Scheduler](http://support.microsoft.com/kb/308569).  The scope of the tutorial does not cover how to configure the Windows Task Scheduler, but you can [read how](http://technet.microsoft.com/en-us/library/bb726974.aspx) or use the [schtask](http://technet.microsoft.com/en-us/library/cc725744.aspx) tool.

[Move onto the Setup &rarr;]({{ get_url("/scrape/part-0/")}})
