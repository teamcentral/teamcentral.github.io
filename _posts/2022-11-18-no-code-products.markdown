---
layout: post
title:  "No Code"
date:   2022-11-18 10:34:36 -0400
categories: release notes
---

### Why Dev's hate no code products

#### My background
For the last 25 years I have been building software solutions.  I love it.  I love to read and learn about it. I love the history of it.  I love the reaction by users when you have solved a problem or made their lives in some way better.  It can be really hard work, but it is rewarding, and I think most good developers feel this same way.  So I am kind of a nerd.<br/><br/>

For most of my career I cringed at low code and code gen products.  The reason is builders love their tools and they love the control over the solution they are dreaming up.  No different than the carpenter who has their favorite hammer.  If you feel like you do not have control of the solution or the tools you are using are kind of working against you it is frustrating.  So what was the turning point for me and motivated me to build a no code platform? <br/><br/>

The first reason is I believe we are just beginning the next wave of software for business that is driven by AI and will include new ways of consumption with voice, text, and virtual reality.  In order to build the types of ideas I have in my head you have to access large amounts of data, so the logical starting point for that is to build a data platform. <br/><br/>

The second and more practical reason which ties into the purpose of this post is the no code integration and data management platform I invisioned I could not find, and I felt the need for it in the work I was doing.  I wanted to find something with the power of the more IT driven products I consulted on, but with the simplicity of a citizen developer or no code product.  So that became our mission.  We want to help create more builders in the world, but just as important to that we want to make the current builders like myself more efficient.  We want to make Central one of those tools they are passionate about and cannot work without.<br/><br/>


#### Our product
When we started what was it about "no code" automation products in the market that turned us off?  Well let's first start with there are some amazing products out there automating millions of hours of time from the global workforce.  It was just our opinion that for the problems we were trying to solve existing products were just not a fit for various reasons.  The core of it was we could not find a product that effectively handles all of the steps a developer would take to build an automation, and do it with the simplicity of citizen developer products.  That is a hard multi-year problem to solve that I feel like we are just starting, but let me give a peak into our philosophy that I will be writing separate posts on. <br/><br/>

We focused on two things 1) The full development process 2) The data.

#### The full development process
Using a canvas that you can drag a data connection onto and "auto-magically" start moving some data from point A to point B is definitely the part of the solution that looks great in demos, but it is a small part and probably the easiest part of the solution to build.  When a developer sits down to start working on a new solution the process starts much earlier before you get to that step, and once that step is complete there are many more steps to get the solution into production, support it, and change it as the business changes. <br/><br/>

For that reason we designed our product to include all of those steps, and we organize them into 
- Design/Build
- Test
- Deploy
- Monitor

We wanted to support the whole process of detailed design, solution configuration, automated unit testing, version control, deployment workflows, both micro and macro level monitoring and maintenance.  We felt we could not skip any of those steps, and if we do it right we can help train a larger community of people to build very complex solutions, and for the people who are builders today they would love using our product for certain use cases where "no code" made sense for them.  It works for both worlds!

#### The data
The data is the hard stuff.  I could build the connectivity to a new API or database in most cases in less than an hour.  Most customers think that connectivity is the differentiator but actually to us it is more of the commodity.  The hard part is the actual data.  Let me give an example to my point.  In just a few minutes you could connect to the Salesforce API and pull some data on recently "Won" opportunities that you may want to integrate with your Financial system, which is lets say Oracle NetSuite.  It is a pretty typical thing most large companies do, especially with high volume sales.  The connectivity into Salesforce and then on the other end NetSuite is the easy part.  Think about all of that data that we want to capture from SF to NS about that order....the sales rep who made the sale, the region that may own the deal, the customer you sold it to, the products and services the customer purchased.  In order to cross reference all of that data across systems most no code products do two things and sometimes both 1) you have to make dozens of extra steps to query that data creating very point to point and complex orchestrations 2) they inject a bunch of custom fields and scripts into your source systems.  Both are not desirable, and that is why we started with including master data management concepts into the product from the very beginning.


#### Thanks
Thanks for hanging with me on a very lengthy post, but I wanted to set the stage for the types of content and things we will be posting on our product blog. <br/><br/>

Marc Johnson
CEO - TeamCentral





