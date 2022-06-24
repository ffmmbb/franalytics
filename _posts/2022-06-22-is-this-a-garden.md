---
toc: true
layout: post
description: on recommendations within property searches
categories: [recommendations]
title: Is this a Garden?
hide: false
image: /images/property_recs/not-garden.webp
---

## Why do you even care?

Recently we've been looking to buy a property, obviously we have a set idea of what *kind* of property we want; what our deal-breakers are; what our nice-to-haves are. Like most people, I imagine, in the UK our search starts on property search engines like RightMove or Zoopla. 

This is where the fun starts. Whilst all engines have the same basic filters (area, bedrooms, price) it becomes much much more difficult to filter for the more detailed items (garden, floorplan ideals, types of blah), and whilst everywhere offers *some* degree of filtering; the level of detail varies, and the properties you're shown do not exactly match what you believed when you filter.

## Types of Recommendations
Before we go too deep into specifics around property, I want to talk a bit about the different types of recommender systems.

There are three main types of system:
- Collaborative - an approach that bases recommendations based upon the actions of other users/myself
- Content - an approach that bases recommendations on the attributes of items I've engaged with in the past
- Knowledge - an approach that bases recommendations based on *specific* attributes provided by the user

Users looking for property aren't going to do this regularly, and may be looking for something different than the previous time they successfully purchased (upsizing/downsizing); so the optimal way of building a recommender system for property will be utilising knowledge based techniques. 

## Knowledge based filtering
The way this works for property searches will be a user gives you a list of specific filters for an item. The main three being:
- Area
- Price
- Number of Bedrooms
![]({{ site.baseurl }}/images/property_recs/basic-search.png "basic filters when searching in RightMove")


Then the search engine will filter results that match this criteria and expose them to the user. The ordering of results is where the search engine can play around in the recommendation space, often a user will be given the option of how to sort; else it may be popularity or a more fun complex recommender solution.

The user can further refine the results using additional filters.
![]({{ site.baseurl }}/images/property_recs/must-haves.png "additional filters when searching in RightMove")


Now this is where it becomes much more difficult - most of these filters are binary/categorical - but is this how they actually should work?
Let's think about `garden`. If I tick for a garden, am I expecting a front garden? back garden? direct access? communal/private?. An estate agent could easily argue for all of these being a garden (and maybe even just a balcony if they're being especially tricky) but if a user is explicitly filtering for a garden, what are they expecting? Does the search engine have a sufficient signal to know?

## Importance
I've already touched on it briefly, but is there an element of soft-filtering that a user can do instead. I may *prefer* to have a garden, but want to see other properties too because it's not a deal-breaker. This is one of the areas which shouldn't change the content of results; but the ordering. I've seen some new (well, to me anyway) aggregators do this quite well.

OnTheMarket has the concept of a 'Wish List' where it won't exclude results from showing; but will flag the ones that match criteria on the wishlist. This is useful, a user doesn't need to re-search to expand their result set, but it still feels refined. 
![]({{ site.baseurl }}/images/property_recs/otm.png "OnTheMarket search UX")


## Quality of metadata
A big big issue is the actual quality of data a search engine has on a property, and where this has come from. Assuming everything is inputted by estate agents, then there is a problem of agents manipulating and exaggerating properties to make sure they appear in as many searches as possible. If I know that a search engine utilises `garden` as a filter, why wouldn't I say a property has a garden if there was access to a communal one? It's not a lie, and it will increase how many users see my property.

As AI systems progress, it could become more commonplace for these features to be extracted from other sources: photos, free text, floor plans & blueprints. But there are similar issues here (we all know how good estate agents are at taking flattering photos) and unless there is a way of extracting data from sources without bias (neither sellers or buyers) then even this will struggle to provide accurate and high quality attributes for properties. 

## So how can we fix it?
With great difficulty, probably. There's two main areas I would focus on:

### The right data
Data quality will always be an issue, property search engines need a way of measuring how *accurate* given data is for a property - with the amount of properties listed on these sites, and the maturity of work in the area, it wouldn't be too difficult to build a predictive model of how likely a property is to sell given all the attributes provided, and therefore any anomalous behaviour (a property taking too long to sell than expected) could be a reflection of the accuracy of certain attributes provided.

Once we have that, I'd then lean towards combining these supplied features with more programmatically extracted features (through image detection - both property images and floorplans and topic extraction from property descriptions), potentially with the supplied features weighted by how accurate we believe they are.  

### Conversational & Responsive engines
Once we have the right data, we can start exploring ways of presenting that data to the customer. There's a few things you could do here:
- Maintain the same ecosystem and just respond to browsing behaviour, a positive interaction on these sites will be defined as a click through to contact the agent - once we have that you can match and find similar properties based on these collected features.
- I love the idea of conversational recommender systems, buying/renting property is such a massive purchase that you almost want to be able to explain exactly what you want. I imagine most people will want to do this to a human, but I'd be happy with some clever AI using NLP techniques to take my poorly written explanation of what I want to match to similar properties based on the feature space it has on properties
- I would also combine the above with responsive engine (e.g. "I like this flat but on the ground floor") would be amazing. Tech companies used to describe themselves as *"uber for..."*, and then that became *"tinder for..."* - but there's value in that type of system. You're asking the user to provide explict binary feedback (whereas for property searches this is unary) and you can learn what's good AND bad for a user.

## Measurement
I'm glad I don't work in this space because I would be a pain when talking about measurement. In an ideal world the optimal metric you would have is whether or not that customer liked the property enough to make an offer. 
The only explicit action you have is whether or not a user enquired about the property - this is just a unary signal (you cannot infer they didn't like everything they did not enquire about) and it's not a signal that the property was an actual match. 
Interestingly success could be defined by a user **not** coming back and making further enquiries, but it's then difficult to infer:
- what property was the successful property - you'd imagine a user can make multiple enquiries at once
- whether or not it's because they bought a property or because they got sick of searching

All in all, it's tough - I'd obviously lean on 'Making an Enquiry' to be a measure of success, but I'd never feel that confident.

## I might be wrong

I may outline all of this and it's actually just what companies are currently doing, or it offers little value - whilst property search engines provide the user a way of finding properties, the core of the business will be through it's relationship with estate agents, so maybe the objective of recommender systems won't be to find the right **one** property for the customer, but a breadth of properties that gets these consumers to multiple estate agents who can then lead the user to the perfect property.

But really, I just want to filter for a garden and only see properties with an actual garden, please. 

