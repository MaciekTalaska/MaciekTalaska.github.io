title: Linkr - description of the project
date: 2017-03-12 22:49:01
tags:
- programming
- elixir
- my open source projects
category:
- get-noticed-2017
---

This week I have been preparing for starting work on my Linkr project. I have been thinking about functionalities, and what mechanisms the project should support. What I have planned so far is:

Milestone 1: 
- any user should be allowed to add a link (URI) + short description of the resource
- any user should be able to search (the search mechanism should look for the search term in the description and the URI itself)

Milestone 2:
- user should be allowed to add tags
- user should be allowed to sort filter links by tags 

Milestone 3:
- user should be allowed to create an acount - i.e. only registered users should be able to add new links (that whould be a change to what is M1)
- only owner should be able to change description of the link (I think it should not be possible to remove added links)

Milestone 4:
- user should be able to see only links of tags of interest (global filtering for logged in user)

Mileston 5:
- 'likes' - users should be able to sort links starting with those which were given the highest rank in the category. I am not sure how the sorting should actually work. I guess it should not sort all the links within particular tag - that would be a nonse, as it could happen that old link were displayed on the top all the time. Maybe it should be as follows: "sort by date first (descending) and then after the ranking"?

Milestone 6:
- users should be allowed to use rss/atom - so that they're constantly updated with new links being added

Milestne 7:
- users should recieve email notification on new links - this option should be configurable, so that it is possible to receive a notifaction in following scenarios:
  - no notifications at all
  - after there is a new link added
  - daily
  - on a specific day/time of the week (I am not really sure about that. I am not 100% sold to that idea, as I don't know if such a flexibility is important. It may as well be fixed as - Friday 6PM GMT or something alike)

If I were to sum the whole idea of the project - I'd say that it is something like 'delicious for a group of people'. I have a strong feeling that this could be useful for a group of people who may be exploring a specific area of knowledge, and this would be a nice thing to share their finding among the group.
