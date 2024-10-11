---
title: A4 Beta
layout: doc
---

# Assignment 4: Backend Design & Implementation (Beta)

## Abstract Data Models

```
concept Authenticating
state
	created: set Account
	username: created → one String
	password: created → one String
```

```
concept Session-ing[Account]
state
	active: set Session
	account: active → one Account
```

```
concept Posting[Account]
state
	posted: set Post
	author: Post → one Account
	content: Post → one String
```

```
concept Friending[Account]
state
	friends: set Friends
	user1: Friends → one Account
	user2: Friends → one Account
	
	requests: set FriendRequests
	from: requests → one Account
	to: requests → one Account
	status: requests → one {"rejected", "pending", "accepted"}
```

```
concept Grouping[Account]
state
	groups: set Group
	name: groups → one String
	creator: groups → one Account
	includes: groups → set Account
```

```
concept Liking[Post, Account]
state
	liked: set Like
	item: Like → one Post
	likedBy: Like → one Account
```

```
concept Permitting[Target, Resource]
state
	permissions: set Permission
	target: Permission → one Target
    resource: Permission → one Resource
```

## App Definition

```
app Updates
	include Authenticating, Session-ing[Authenticating.Account], Posting[Authenticating.Account], Friending[Authenticating.Account], Grouping[Authenticating.Account], Liking[Posting.Post, Authenticating.Account], Permitting[Grouping.Group, Posting.Post], Permitting[Grouping.Group, Posting.Post]
```

## Dependency Diagram

![diagram](../img/a4_diagram.png)

## Code Repository

Link: [https://github.com/bhattacharjee-rhea/a4-backend](https://github.com/bhattacharjee-rhea/a4-backend)

## Deployed Service

Link: [https://a4-backend-tau.vercel.app/](https://a4-backend-tau.vercel.app/)

## Design Reflection

When implementing the backend, I made a few minor changes to my concept designs and one major change. The first minor 
change I made was exchanging my following concept for the provided friending concept. I liked the inclusion of accepting 
or rejecting following requests which fit with my design goal of giving users more control over their online experience. 
I considered this a minor change because it did not require any changes to my synchronizations. 

The remaining minor changes I made were adding actions to my concepts to better support my synchronizations. For my grouping 
concept, I added actions to retrieve the groups a user created and the groups a user was a member of. These were useful for 
implementing synchronizations for my permitting concept. For my liking concept, I added some actions that I had overlooked 
when designing the concept, such as checking whether or not a post was liked. 

The major change I made was to my permitting concept. I implemented the concept as designed, but then realized that my 
synchronizations were too complicated. The problem was that permitting acted on groups, but I needed to know whether a user 
had permission to view or like a post. I considered changing permitting to operate on users instead, but decided I wanted it 
to operate on groups, as I wanted users added to or removed from a group to have their permissions changed in response. I 
eventually realized that my permitting concept could be split into two instances of the same concept: view permissions and 
like permissions. This drastically simplified the concept. The change allowed me to implement the synchronizations I initially 
envisioned. 
