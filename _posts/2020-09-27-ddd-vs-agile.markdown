---
layout: post
title:  "Domain-driven teams in agile organizations"
date:   2020-09-27 15:34:19 +0200
categories: org
comments: true
---
One of the great advantages of an agile organization is that the teams are loosely coupled, and they can execute the whole end-to-end process of the implementation lifecycle independently of other teams. This feature eliminates unnecessary waits, so the team can deliver much faster, making it one of the keys of success in large enterprises.

I think there is a common misconception about this *end-to-end team* principle, especially in companies where agile is taken as a silverbullet for all the problems. The misconception is that such a team should build basically anything from scratch which is needed for its work, just as a subcontractor of the company who has to build all of the components and a full development infrastructure independently from the company.

While this approach do have some advantages (for example there is not a single point of failure which can stop the work of all teams when breaking), mostly it just causes lots of extra work, and at the end of the day just degrades the efficiency of the teams, oppositely to the original intentions.

## Domain-driven end to end teams

My opinion is that it is much better to organize people around a specific domain (or a set of similiar domains), so that the tasks of the team will:

- **have the same complexity level**

    for example a team shouldn't work on a specific component (eg. a library) and at the same time on a solution which is based on several other components (eg. a microservice)
    
- **have the same type of reporters / users**

    this is not the case when a team has to implement a new feature in some common code which is used by many other teams (so the users are members of other teams), but at the same time they have to develop a product which is used by the customers of the company.
    
- **be about similiar business domain**

    this way the team can have strong focus on a specific domain, which will result higher quality.
    
## The inner source pattern

All of this doesn't mean that such teams are not allowed to contribute to projects outside of their domain. This would cause major slow down when some parts of the common code get lots of feature requests, and the owner team does not have enough resources to handle them all. This problem is solved by the *inner source pattern*.

It means that the whole codebase is available for each team. Anyone can contribute to any project, but only with the approval of the owner team, which has to take the responsibility for all the changes.

## Summary

Domain-driven teams are responsible for code pieces (projects) with same complexity level, same users and similiar business domain. They can contribute to other parts as well, but only with the approval of the owner team, which has to take the responsibility for all the changes. Such organization can be highly effective because of the low level of duplicated efforts, and the stronger focus of teams on a specific business domain.
