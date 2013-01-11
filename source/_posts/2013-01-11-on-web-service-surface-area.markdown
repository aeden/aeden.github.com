---
layout: post
title: "On Web Service Surface Area"
date: 2013-01-11
comments: true
categories: musings
---
What is the optimum surface area of a web service. This is one of the questions that keeps coming up when I think about building web applications, and I feel it would be beneficial to write down some of these ideas to work through them a bit.

On the one end of the spectrum there is the monolithic web application. For example, this could be a Rails application with a large number of models and controllers providing a wide range of services. On the other end of the spectrum there is the micro-service model, where each API end point is its own service. An example of this might be a service that binds to a port and only handles one HTTP method on one particular type of resource. Naturally there is a wide swath of space in between the two of these, and it is in this swath that we tend to end up. 

How far should we push towards the micro-service end of the spectrum?
