# system-design-primer

* [How Web Works!](https://github.com/reach2arunprakash/system-design-primer/tree/master/how-web-works) 
* [How Google works PhD paper - !](http://infolab.stanford.edu/~backrub/google.html)
* [System design topics: start here](#system-design-topics-start-here)
    * [Step 1: Review the scalability video lecture](#step-1-review-the-scalability-video-lecture)
* [Performance vs scalability](#performance-vs-scalability)
* [Latency vs throughput](#latency-vs-throughput)
* [Availability vs consistency](#availability-vs-consistency)
    * [CAP theorem](#cap-theorem)
        * [CP - consistency and partition tolerance](#cp---consistency-and-partition-tolerance)
        * [AP - availability and partition tolerance](#ap---availability-and-partition-tolerance)
* [Domain name system](#domain-name-system)
* [Content delivery network](#content-delivery-network)
* [Load balancer](#load-balancer)
    * [Horizontal scaling](#horizontal-scaling)
* [Reverse proxy (web server)](#reverse-proxy-web-server)
    * [Load balancer vs reverse proxy](#load-balancer-vs-reverse-proxy)
* [Application layer](#application-layer)
    * [Microservices](#microservices)
    * [Service discovery](#service-discovery)
* [Database](#database)
    * [SQL or NoSQL](#sql-or-nosql)
    * [Relational database management system (RDBMS)](#relational-database-management-system-rdbms)
        * [Sharding](#sharding)
        * [Denormalization](#denormalization)
    * [NoSQL](#nosql)
        * [Key-value store](#key-value-store)
        * [Document store](#document-store)
        * [Wide column store](#wide-column-store)
        * [Graph Database](#graph-database)
* [Cache](#Cache)
    * [Client caching](#client-caching)
    * [CDN caching](#cdn-caching)
    * [Web server caching](#web-server-caching)
    * [Database caching](#database-caching)
    * [Application caching](#application-caching)
    * [Caching at the database query level](#caching-at-the-database-query-level)
    * [Caching at the object level](#caching-at-the-object-level)
* [Asynchronism](#asynchronism)
    * [Message queues](#message-queues)
    * [Task queues](#task-queues)
    * [Back pressure](#back-pressure)
* [Communication](#communication)
    * [Transmission control protocol (TCP)](#transmission-control-protocol-tcp)
    * [User datagram protocol (UDP)](#user-datagram-protocol-udp)
    * [Remote procedure call (RPC)](#remote-procedure-call-rpc)
    * [Representational state transfer (REST)](#representational-state-transfer-rest)
    * [GraphQL](#graphql)
 * [Company engineering blog links](#Company-engineering-blog-links)
 * [System Design Interview Questions](#System-Design-Interview-Questions)

                       # Welcome
                       
  ![Image of Yaktocat](https://octodex.github.com/images/yaktocat.png)
  
  
  
  
  ## WHAT IS WEB APPLICATION ARCHITECTURE?

  ![Image of Scalable Archi]( https://github.com/reach2arunprakash/system-design-primer/blob/master/images/Web%20Archi.png)
  
  
    ## COMPONENTS OF WEB APPLICATION ARCHITECTURE
  
  ![Image of Scalable Archi](https://github.com/reach2arunprakash/system-design-primer/blob/master/images/intro-scalable-arch.png)
  
  
  Src :  https://www.digitalocean.com/community/tutorials/5-common-server-setups-for-your-web-application
  
  ## Details 
    
   ### 1. Everything On One Server
       
   ![Image of Scalable Archi]( https://github.com/reach2arunprakash/system-design-primer/blob/master/001-Single%20Server.png )
          
   ### 2. Content delivery network
    
   #### Content delivery network
    
   ![Using a CDN]( https://github.com/reach2arunprakash/system-design-primer/blob/master/002%20-%20using-cdn.png )
    
   ![Using a CDN]( https://github.com/reach2arunprakash/system-design-primer/blob/master/images/OverView%20CDN.png )
      
   ![Using a CDN]( https://github.com/reach2arunprakash/system-design-primer/blob/master/images/cdn.png )
   
   
   ![Using a CDN]( https://github.com/reach2arunprakash/system-design-primer/blob/master/images/Before%20After%20CDN.png )

   
   #### Use Cases:
   
   ![Using a CDN]( https://github.com/reach2arunprakash/system-design-primer/blob/master/images/When%20to%20use%20CDN.jfif )



   ### 3. Separate Database Server
    
   ![Image of Scalable Archi]( https://github.com/reach2arunprakash/system-design-primer/blob/master/003-u-separate_database.png )
      
   ### 4. Load Balancer (Reverse Proxy)
    
   ![Image of Scalable Archi]( https://github.com/reach2arunprakash/system-design-primer/blob/master/004-u-load_balancer.png )
      
   ### 5. Primary-replica Database Replication
    
   ![Image of Scalable Archi]( https://github.com/reach2arunprakash/system-design-primer/blob/master/005-u-primary_replica_database_replication.png )
   ### Cache
    
   ![Cache]( https://github.com/reach2arunprakash/system-design-primer/blob/master/006-cache.jfif )  
     
   ![Image of Scalable Archi](https://github.com/reach2arunprakash/system-design-primer/blob/master/007-redis%20cache.png )  
    
    
   
 ### Step 1: Review the scalability video lecture

[Scalability Lecture at Harvard](https://www.youtube.com/watch?v=-W9F__D3oY4)


## Performance vs scalability

A service is **scalable** if it results in increased **performance** in a manner proportional to resources added. Generally, increasing performance means serving more units of work, but it can also be to handle larger units of work, such as when datasets grow.<sup><a href=http://www.allthingsdistributed.com/2006/03/a_word_on_scalability.html>1</a></sup>

Another way to look at performance vs scalability:

* If you have a **performance** problem, your system is slow for a single user.
* If you have a **scalability** problem, your system is fast for a single user but slow under heavy load.

### Source(s) and further reading

* [A word on scalability](http://www.allthingsdistributed.com/2006/03/a_word_on_scalability.html)
* [Scalability, availability, stability, patterns](http://www.slideshare.net/jboner/scalability-availability-stability-patterns/)

## Latency vs throughput

**Latency** is the time to perform some action or to produce some result.

**Throughput** is the number of such actions or results per unit of time.

Generally, you should aim for **maximal throughput** with **acceptable latency**.

## CAP theorem

   ![CAP](https://github.com/reach2arunprakash/system-design-primer/blob/master/images/001-CAP.png )  
   
   
   ![CAP](https://github.com/reach2arunprakash/system-design-primer/blob/master/images/002-CAP.jfif )  
   
## Domain name system 

   ![DNS](https://github.com/reach2arunprakash/system-design-primer/blob/master/images/DNS.jfif)  

## Database

   ### ACID
   
   ![ACID](https://github.com/reach2arunprakash/system-design-primer/blob/master/images/001%20-ACID.png)  

   ![ACID and CAP](https://github.com/reach2arunprakash/system-design-primer/blob/master/images/ACID%20and%20CAP.jfif)  

   ### NoSQL

![SQL and NOSQL structure](https://github.com/reach2arunprakash/system-design-primer/blob/master/images/002%20-%20Sql%20vs%20NOSql%20Collection.png )  
  
  ![NoSQL](https://github.com/reach2arunprakash/system-design-primer/blob/master/images/001%20-%20Sql%20vs%20NOSql.png )  

  ![Image of Scalable Archi](https://github.com/reach2arunprakash/system-design-primer/blob/master/images/003-%20MySQL%20vs%20MongoDB.png )  
  

  
 ## GraphQL 
  
[GraphQL - arun prakash ](  https://www.youtube.com/watch?v=LO2tQtfGO2s)

## Asynchronism

  ![Message queues](https://github.com/reach2arunprakash/system-design-primer/blob/master/images/message_queue.png )  
  

## Company engineering blog links

courtesy [checkcheckzz](https://github.com/checkcheckzz/system-design-interview#toc)

Depending on where you are interviewing, go through the company blog. VERY USEFUL IN INTERVIEWS! It really helps if you have an idea of the architecture, as the questions asked will generally be of that domain and your prior knowledge will help out here.

* [Airbnb Engineering](http://nerds.airbnb.com/)
* [Bandcamp Tech](http://bandcamptech.wordpress.com/)
* [BankSimple Simple Blog](https://www.simple.com/engineering/)
* [Bitly Engineering Blog](http://word.bitly.com/)
* [Cloudera Developer Blog](http://blog.cloudera.com/blog/)
* [Dropbox Tech Blog](https://tech.dropbox.com/)
* [Engineering at Quora](http://engineering.quora.com/)
* [Etsy Code as Craft](http://codeascraft.com/)
* [Facebook Engineering](https://www.facebook.com/Engineering)
* [Flickr Code](http://code.flickr.net/)
* [Foursquare Engineering Blog](http://engineering.foursquare.com/)
* [Google Research Blog](http://googleresearch.blogspot.com/)
* [Groupn Engineering Blog](https://engineering.groupon.com/)
* [High Scalability](http://highscalability.com/)
* [Instagram Engineering](http://instagram-engineering.tumblr.com/)
* [LinkedIn Engineering](http://engineering.linkedin.com/blog)
* [Oyster Tech Blog](http://tech.oyster.com/)
* [Pinterest Engineering Blog](http://engineering.pinterest.com/)
* [Songkick Technology Blog](http://devblog.songkick.com/)
* [SoundCloud Backstage Blog](https://developers.soundcloud.com/blog/)
* [Square The Corner](http://corner.squareup.com/)
* [THE REDDIT BLOG](http://www.redditblog.com/)
* [The GitHub Blog](https://github.com/blog/category/engineering)
* [The Netflix Tech Blog](http://techblog.netflix.com/)
* [Twilio Engineering Blog](http://www.twilio.com/engineering)
* [Twitter Engineering](https://engineering.twitter.com/)
* [WebEngage Engineering Blog](http://engineering.webengage.com/)
* [Yammer Engineering](http://eng.yammer.com/blog/)
* [Yelp Engineering Blog](http://engineeringblog.yelp.com/)
* [Smarkets Blog](https://smarketshq.com/)

## System Design Interview Questions

A curated list of System Design interview questions for SDE-1 (Experienced),SDE-2 and above.

Targeted companies: Amazon, Google, Facebook and other biggies.

Hope it helps you to prepare for your upcoming interviews!
Questions

    Design commenting system
    Design subscription based sports website which can display scores, game status, history for any games.
    Design Netflix => search, video serving, authentication, encryption, dns lookup,caching strategy,serving multi quality video etc
    Design a Latency Management System
    Design a Library Management System
    Design a Notification service
    Design ESPN/Cricinfo/Cricbuzz
    Design Uber
    Design Whatsapp
    Design Quora
    Design Lookahead system
    Design Google Docs/ Collaborative Editing service
    Design URL Shortner service
    Design RedBus
    Design BookMyShow
    Design Domain Backdooring system
    Design Amazon Locker
    Design Movies Review Aggregator System > Data should be fetched from movie rating providers like imdb, rotten tomatoes, etc
    Design offline caching system for Ecommerce platform
    Design Amazon E-commerce
    Design Online chess game/Multiplayer game
    Design gaming platform. A number of games can be hosted on this platform. User can login and select a particular game
    Design a last-mile delivery platform in case of peak seasons
    Design Zomato/Swiggy/Foodpanda
    Design Meeting Calendar system
    Design Spotify
    Design Promo Code API by taking into account Amazon's customer traffic into picture
    Design Vending machine with following functionalities ==> Three types of Users : User, Operator, Admin
        User can select and buy multiple items at a time. Money can be inputted multiple times (you will get the item if there is a time gap > 30 secs). He can also do window shopping (see only the prices of items and buy nothing)
        Operator can load the items and mark the items as expired if needed, gets notified if a product goes out of stock.
        Admin can own multiple vending machines, he should have a analytics report of the items purchased in a month. He can also change the prices directly and it should reflect in all the vending machines which he owns.
        Exception handling in all the edge cases
    Design splitwise
    Design Google pay at scale
    Design a Job schedular => scalability, fault tolerance, high availability, how scheduler picks up job, how will you take care where one job can run for 30 min and one for 30 hour, how will you distribute jobs on servers. Based on frequency & time how will you execute them ? How will you notify back the user about start/stop or completion of a job ? How will your system know if a job is killed / terminated due to unknown reasons ?
    Design Meeting Scheduler
    Design Debugger
    Design Automatic Parking System
    Design a ranking system. We have an infinite supply of words ending with ‘.’ We need to implement a reader program that ranks words on the basis of certain criteria Example: This is my cat. This house belongs to my uncle An amazing country with so many tourist places And so on.. Ranking System criteria : rank the words on the basis of occurrence, for example Output : This:2, is:2, my:2… highest rank (sorted asc or desc based on provided flag) Design it completely and scalable Ranking System
    Design Amazon Cart system
    Design Google Search
    Design Twitter
    Design Facebook
    Design Snapchat
    Design Instagram
    Design App-store
    Design a music player application
    Design a distributed LRU Cache
    Design Gmail
    Design a recommendation system
    Design a food sharing application
    Design payment module for Uber app
    Design Truecaller type of system
    Design performance management system (appraisal workflow system) that can be used across companies.
    Design comment system like disqus
    Design flight system
    Design Tinder
    Design survey site like surveymonkey
    Design a geographically partitioned multi-player card game, that supports multiple players, multiple games at a time. Each game will have one contractor like ones we have in a bar, He can play a game or just watch it. Integrate payment systems
    Design a kind of kindle fire application where we can subscribe news channel and read the news from all publishers as a digital format
    Design a realtime Video chat like Google Duo
    Design News paper & Magazine subscription system
    Design a system like Hackerrank/Codechef/Topcoder
    Design a concurrent Hashmap
    Design an ATM Machine system which can support massive amount of transactions
    Design Airport Baggage system
    Design Flight Information Display system
    Design a conference room booking system for a company which can have offices in multiple cities, each city can have multiple buildings, each building can have multiple floors, each floor can have multiple rooms. Each room can have features like capacitiy, video conferencing available, etc.
    Design newsfeed feature of Facebook
    Design an efficient Mail delivery system
    Design like/dislike feature at Youtube scale.
    Design Paypal
    Design Air traffic control system
    Design a realtime service which tells your friends who is online
    Design Google Maps
    Design Grammarly

