---
layout: page
title: Terrificus
length: 2 weeks
tags:
type: project
---

## Project Description

The goal of this project is to create a successful web application from a project idea. You will create an app that will authenticate with a third-party service, consume an api, and solve an actual problem.

The project requirements are listed below:

* [Learning Goals](#learning-goals)
* [Technical Expectations](#technical-expectations)
* [Project Concepts](#project-concepts)
* [Check-ins](#check-ins-and-milestones)
* [Evaluation](#evaluation)

## <a name="learning-goals"></a> Learning Goals

* Learning how to build a full Rails app from idea to delivery
* Revisiting previous concepts such as APIs and OAuth
* Finding the strengths and gaps in your knowledge of Ruby, Rails, and organizing
a project.
* Use an agile process as you develop features
* Configure a continuous integration server

## <a name="meeting-schedule"></a> Meeting Schedule

Projects with open ended requirements are frequently the most enjoyable and strongest projects at Turing. With the freedom comes the possibility of different opinions that lead to tension and possible conflict. Some of this tension can be good but it can also prevent a team from being productive. Use [this meeting template](../projects/materials/terrificus_meeting_schedule) to use this tension in a positive way. Our goal is for every group to have made the difficult decisions by the end of day two and for everyone to be coding on day three.

## <a name="technical-expectations"> Technical Expectations

Every project will be a bit different, but they need to share some
common technical characteristics:

* Use an external OAuth provider to authenticate users
* Consume an external API
* Implement a production quality user interface
* Optimize your application optimizing your database, implementing caching, using background workers, and sending AJAX requests

### Project Scope

A good project idea should:

* Break down into logical iterations so that you can deliver a strong product on  every checkin
* Be something that real people would want to use to solve a problem
* Have enough *technical* challenge to be worth your time (as opposed to a *content* challenge)

### APIs

Your application **must make good use of one external dataset or API**. Some examples include:

#### Government Data

* [Data.gov](https://www.data.gov/)
* [ProPublica](http://www.propublica.org/tools/)
* [NASA](http://data.nasa.gov/api-info/)
* [US Census](http://www.census.gov/data/developers/data-sets.html)
* [Socrata Listings](https://opendata.socrata.com/dataset/Socrata-Customer-Spotlights/6wk3-4ija)
* [Bureau of Labor & Statistics](http://www.bls.gov/developers/api_ruby.htm)
* [United Nations](https://www.undata-api.org/) (3rd party API)
* [Google's Directory of Public Data](http://www.google.com/publicdata/directory)
* [OpenColorado](http://data.opencolorado.org/)
* [Denver Regional Council of Governments](https://drcog.org/services-and-resources/data-maps-and-modeling)

#### Corporate Data

* [Twitter](https://dev.twitter.com)
* [Facebook](https://developers.facebook.com)
* [Instagram](https://instagram.com/developer)
* [Github](https://developer.github.com/v3)
* [FitBit](https://dev.fitbit.com)
* [Spotify](https://developer.spotify.com/web-api)
* [Strava](https://www.strava.com/developers)
* [Google Maps](https://developers.google.com/maps)

However, the list is not limited to these. You can choose to integrate with a service of your choosing, as long as it is approved by your client.

## <a name="project-concepts"></a> Project Concepts

Your idea must be approved by an instructor and should be supplied in a gist using the following template...

### Project Template

```markdown
### [Project Title]

### Pitch

1 sentence that explains the value proposition of the application. How would you explain it to a potential business partner, team member, or investor?

### Problem

1-3 sentences describing the problem that you are trying to solve.

### Solution

1-3 sentences describing how your application will solve that problem.

### Target Audience

1-3 sentences describing what type of user your app would be applicable to.

### Integrations

* Which APIs will you use?
* Which OAuth integration are you planning to use?
```

## Milestones & Agile Process

You will meet with instructors periodically during the project. The goals of each check-in roughly what should be completed before the check-in is listed below.

### Setup

* Create a board on Pivotal Tracker and invite your PM as a contributor.
* Before you begin to implement code, write up 5-10 stories on your new Pivotal Tracker board. These stories must be written in present tense.
* Once step two is complete, send your tracker board over to your PM.
* Setup a [CI Server](http://backend.turing.io/module3/lessons/ci_and_staging_environments)

### Pull Requests

* For each story you create, there will be an associated story ID number. You'll use this in your pull requests.
* PR's must be formatted as the following: 123456: Add user to database table, 789101: Add get_all action for user resource, 194385: Add create action for user resource, etc
* Copy and paste the story URL into the PR. Tag your PM if you have specific questions. No need to have our approval to merge unless there is an issue that needs to be resolved.
* Once you have run through and completed your original story list, write an additional 5-10 stories and send us a notification that they have been written. We'll be expecting to see consistent updates.

### "Standup" and Checkins

* Every weekday at 2PM send your PM a remote "daily standup" style update via Slack that answers the following questions:
  * What have you been working on?
  * What are you going to be working on?
  * Is anything blocking you?
* Every two days you will commit to the work you will have complete over the next two days and a specific time it will be complete. Work with your PM to determine when this will be.

## <a name="evaluation"></a> Evaluation


### Feature Delivery

* **4:** Team well exceeded project manager's expectations.
* **3:** Team completed all the user stories and requirements set by the project manager.
* **2:** Team completed most user stories set out but fell short of project manager's expectations.
* **1:** Team fell well short of project manager's expectations.

### Technical Quality

* **4:**  Project demonstrates extractions that are above and beyond and might include SOA (Service Oriented Architecture) or takes on a new technology that outside the scope of the curriculum and includes all below expectations.
* **3:**  Project uses abstraction in ways that make it easy to change (example: if an API changes, Propublica to Google Civic, we make changes in as few places as possible). Project shows a solid understanding of MVC principles (this may include but is not limited to: no logic in views, clean controllers, serializers and presenters to handle formatting rather than models etc.) and includes all below expectations.
* **2:**  MVC is overall good but might have logic or hashes in views, formatting in models, or controllers with complex logic and includes all below expectations.
* **1:**  Project has significant gaps in understanding of MVC and with several examples of logic or hashes in view, controllers remain un-refactored, and models are used for formatting.

### Testing
* **4:** Project demonstrates exceptional testing using advanced techniques such as spies. And includes below expectations.
* **3:** Project demonstrates high value testing at different layers (above 90%) and I would be happy paying for the test suite. And includes below expectations.
* **2:** Test suite coverage is greater than 80% but misses the most meaningful functionality and I would not be happy paying for/inheriting it. And includes below expectations.
* **1:** Test suite coverage is low (less than 80%). And includes below expectations.

### Product Experience

* **4:** User experience is exceptional, page is easy to use, responsive, and meets all of the criteria in 3. Page load times average under 300 milliseconds.
* **3:** Project is ready to demo. Page load times average under 500 milliseconds with a max page load time of 600 milliseconds using New Relic or Skylight.io in production on a hosted service.
* **2:** Project is not ready to demo or page load times average are slower than 600 milliseconds on average.
* **1:** Project is not ready to demo, does not measure page load times, page load times are over 700 milliseconds on average, or max page load takes longer than 1000 milliseconds.

### Communication
* **4:** Group member did all the things mentioned in the bullet point below, but also was a catalyst for communication with the whole group.
* **3:** Group member communicated clearly when they would and wouldn't be available well ahead of time. It was clear what they were working on and what the status was.
* **2:** Group member would communicate when they would or wouldn't be available, but not until the last minute, or they would miss deadlines and not notify the group until the last minute.
* **1:** It was unclear what the group member was working on, or they would fail to notify the team when they weren't going to meet a commitment.

### Group member contributed code (quantity and quality)...

* **4:** above expectations.
* **3:** as expected.
* **2:** below expectations.
* **1:** well below expectations.

### I would like to work with this group member professionally.
* **4:** Absolutely. I will likely seek them out in the future with the hopes of working with them again.
* **3:** Yes, I think I would enjoy working with them.
* **2:** I would prefer not to.
* **1:** I would actively avoid working with them again.
