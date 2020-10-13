# REST API Theoretical Deep Dive

In the previous chapters we have explored the basics behind REST APIs. In this addendum content we will focus on the constraints behind a well designed REST API. While these constraints are wildly accepted REST is not a very strict standard and leaves a lot of room for interpretation. This means that you can't always rely on an API you are encountering in the wild to exactly follow these constraints and rules. 

## A History of REST

REST was first introduced and defined by Roy Fielding, one of the principles behind the HTTP protocol specification and a co-founder of the Apache HTTP Server project that is powering almost 30% of all web pages in the internet.

Fielding defined REST in Chapter 5, aptly named *Chapter 5: Representational State Transfer (REST)*, of his 2000 dissertation titled *Architectural Styles and the Design of Network-based Software Architectures* by introducing a set of six constraints that a *RESTful* application should follow. In the rest of this chapter we will have a look at each of these constraints. 

## Uniform Interface

The uniform interface constraint aims at making sure that you have a defined interface for each of the resources within your system. Each resource, think of a user in a shop system or a message in a chat application, should only have one logical URI. 

The uniform interface also demands that your representation is consistent. This means that all your resources should follow a common naming convention and data format. Note that the specific naming convention and data format is up to the API architect to decide. The *Uniform Interface* constraints just aims at providing consistency *across* the API itself. 

This also implies that your API interface and the underlying service it is exposing to the outside (think for example of the schema that is actually storing the data in the database) can evolve independently from each other. You can do whatever changes you want to the underlying infrastructure as long as you keep the data and interaction represented to the user the same. By providing the same set of properties instead of a application-specific interface REST compromises efficiency in favour of providing a universal and easier-to-consume interface.

## Client-Server

This constraint simply states that your application should have a client that queries the server for information. Client and server can evolve independently from each other as long as the interface is kept the same and should not depend on each other.

## Statelessness

Probably the most important constraint for the success of REST is it's statelessness. This means that each request has to carry all the information needed to fulfill the request. The server does not store any history or session information. Keeping track of these information is left entirely to the client.

What seems like a small little constraint allows for some of the major benefits of REST. 

By being stateless monitoring a API server becomes significantly easier. To track down errors you only have to look at the one request a user is sending and don't have to take into account any previous requests.

Scalability is made easy by statelessness as you can simply scale up the number of servers handling your requests. There is no need to synchronize state between requests and/or make sure that a chain of requests from the same client always lands on the same server. Instead, typical API architectures using REST rely on the backend services like the database to take care of things like data integrity. 

Since there is no free lunch this constraint also implements some disadvantages. Most important the application can cause network overhead since all information has to *always* be send in each request instead of the server storing the common data of multiple requests in i.e. a session store. 

## Cache

This constraint makes it easier to relief the burden of a API on it's backend services. Essentially the aim is to allow resources to mark themselves as *cacheable*. When a resource is marked as *cacheable* the cache that is positioned in front of the API server is allowed to reuse the previous data for a later, equal request. 

Think of multiple different users requesting a `User` resource with id 15 from a REST API(i.e. a request like `GET /api/v1/users/15`). For the first request the API server will need to query the backend database for all the information and retrieve the JSON representation of that user. 

After this initial request and as long as the `User` resource does not change, there is no need to query the database again for the information of the user with id 15 as they won't change! 

This means we can scale much easier and reduce the load on our backend systems. This is a crucial aspect for web-scale systems that need to satisfy thousands of requests per second.

Note that caching can be applied both at the server **and** client side leading to a faster client experience.

## Layered System

REST adds a *layered system* constraint to it's standard. In plain English this means that a client can't tell what part of the service it is talking to. This means that while your client might *think* it's talk to a single server your service can, in the backend, have a load balancer that decides which API server to send the request to. This API server in turn can then talk to other services to gather all the resources required and return the information back to the client. And all of this is done without the client knowing. 

From a systems design point of view this allows our API to *wrap* legacy systems and/or provide a simplification of the data used internally to how it is represented to the API user. And while this approach adds overhead and latency since your API service needs to communicate with multiple subsystem it also allows for a clear boundary between internal and external data. 

## Code-On-Demand

Lastly there is the *optional* constraint of Code-on-Demand. Code-on-Demand simply allows a API to server code in the form of scripts and applets to the client that can then use it to enhance its functionality. A optional constraint this is one of the least adopted features of the REST standard and is rarely seen in the wild.

<div align="right">
   
   [Back](../Readme.md)
</div>