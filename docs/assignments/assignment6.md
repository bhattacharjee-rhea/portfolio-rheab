---
title: A6
layout: doc
---

# Assignment 6: User Testing & Analysis

## Task List

Title | Instruction | Rationale
----- | ----------- | ---------
Basic posting | Open the app, create an account, and then create a post without any permisssions | Basic functionality of the app (creating a post) can be used easily and intuitively without a broader understanding of the app. users who have no experience with the app should be able to do this (as opposed to a familiar creator in a cognitive walkthrough)
First friends | Send friend requests to three users: rheab, test, test2 | Friending is critical to the unique components of this app. The process of sending a request needs to be intuitive enough to users to be able to easily accomplish this task without knowledge of how friendship concept works. 
Group creation | Once the requests have been accepted, create two groups with those three users. Then, modify one group to only have two users: test and test2 | Grouping is one of the more unique components of this app, so first time users will not be the most familiar with the concept. Regardless, users need to be able use grouping for the core functionality of this app to work. As an extra bonus, modifying a group uses the same steps as every other modification in the app so this user test will confirm the feasibility of those other modification components.
Add permissions | Modify the previously created post’s permissions so that one of the groups can view the post. [Ask users if they know what it means to do this.] | Permissions are the backbone of the app. This user tests ensures that a user without knowledge of the app can understand the concept of permissions enough to add a permission to an existing post and understand what it means for them to do so. 
Create post with permissions | Create another post and give both groups view permissions but only the two-person group like permissions | This user test puts it all together. Users by now should have an understanding of how to both create posts and add permissions to posts. This tests if the user is able to learn those processes well enough to combine them in one task, and if they have any difficulties that the layout of the app can guide them. 
Like a post | Log out then log in as test (user: test, password: test) and like the posts originally created | This final test is to ensure a user understands the concept of different view and like abilities, which is the entire point of this app. logging in and out tests that those components match the user’s mental models. The user should be able to look at the result of what they made in the test and understand why some posts are likable and some posts are not because this is the value that the app brings. 

## User Test 1 Report

The overall impression of the first user test was that the app was well designed. All of the tasks were completed without issue or confusion. For every action of the test, the user intuitively understood which page they needed to navigate to. When navigating to a new page, the user would take a few moments to digest the layout of the page. From there, the user reported that the layout was standard enough to the social media they were used to that they could complete the tasks without difficulty. 

The user was not confused by the tasks because they had built the requisite knowledge in previous tasks and any gaps in that knowledge was addressed by the clear signposting of the app. They shared that, despite the new features and concepts, because there was not much else going on in the app it was simple for them to use for the first time. The user also shared at the end of the test that they would be more likely to use this app than another social media app (e.g. Facebook or Instagram).

While the overall app layout was intuitive enough for the user to easily use on the first try, there were some implementation details. When first viewing the app, the user immediately asked if there was a dark mode. This was not implemented because I considered it out of scope for the project, but the fact that the user asked it suggests that the user automatically looks for it to add value to their apps. The user also mentioned that they thought it would be useful to automatically create groups for all friends.

A small implementation issue occurred when the user was clicking the boxes to select friends for groups or groups for permissions. The user would click on the text itself instead of the checkbox for a few attempts before clicking on the checkbox itself. The user mentioned that checkboxes normally activate when they click the word and they expected this to be the case for this app. The user also grew frustrated at clicking each friend and suggested a “select all” option. Additionally, there was a long load time for posts. This was especially impactful for the like button as the lag caused the user to click it multiple times, which would unlike the post.

## User Test 2 Report

This user also felt that the app was functionally well designed. The operation was smooth and everything was where the user expected it to be, so they were able to use the app without prior instructions. The user went through the various tests without difficulty or confusion, confidently navigating to the correct pages and clicking the necessary buttons to make the requested actions occur. The user reported at the end of the test that they felt they could have navigated the app even without the guiding tasks. They believed the app layout was simple enough to not require a lot of thought to use. 

One interaction the user particularly liked, and commented on liking, was the like interaction. The user commented that they enjoyed the reactivity of the button and the fact that the color was noticeably different from the rest of the app. On the other side, one interaction the user commented on disliking was creating permissions and groups. The user, like the previous one, clicked on the text instead of the checkboxes. The user mentioned that it felt like a lot of work to select all of those groups and friends. The user further elaborated that they felt the app required too many clicks to create permissions with all the steps they needed to do.

The last functionality the user commented on was the lag time of the posts. During the liking test the user reacted to the long loading time while waiting for the posts to render in the feed. At the end of the test they commented that it started to feel frustrating to have to wait that long to do such a simple action. Especially with the small number of posts in the feed, the user had expected to have a quick loading time similar to other social media platforms. 

## Design Opportunities	

- Physical, minor: select checkboxes when the corresponding label is clicked. This should be a simple code fix that would definitely ease the user experience with friend and group selection.  
- Linguistic, moderate: include a select all option for the group and friend selection boxes. While minor with only two or three options, for ten or more options this would definitely become a more pressing issue as it would quickly become difficult. This should be an easy code fix.
- Conceptual, moderate: create an “all friends” group that always includes all friends. Currently, this group has to be manually created, which would probably become annoying after repetitive use and might eventually make the app unusable. One option to fix this is to create a friends group when an account is created and update it (on the backend, probably) when a friend is created or removed.
- Conceptual, major: slower lag times. The app is currently very hard to use because loading posts for the feed takes a very long time. This is probably because of all the server requests that need to be completed before the feed is shown. Two options to fix this are a) create a new endpoint on the backend to only retrieve the visible posts, significantly lowering the number of API requests, and b) to increase the granularity of updating server calls so each update call runs faster.
