# ConferenceOrganization

#Task1

A session is implemented as a child of a conference entity. A websafe conference key is passed in the request that can be used to query the conference entity the key pertaains to. this key is then set as the parent of a session entity in the datastore.

#Task 3 -  Additional queries
The 2 additional queries are as follows:
removeSessionFromUserWishList() - The user can remove any session that are there in the wish list. If the wish list is empty, there is nothing to remove and user is told there is nothing to remove. 

updateConferece() - The user who created the conference can update conference details. The updated details will be saved to the data store.

#Task 3 - Query problem
The problem with implementing the given query is that inequality filters, in this case (< and != ) can not be applied to 2 different properties (start time and Type) at the same time. 
To solve the problem I thought of not using an inequality operator for one of the queries, so for example, use OR operator rather than != operator or IN operator across non-workshop sessions.
e.g :
Session.query().\
filter(Session.startTime < 19:00).\
filter(Session.Type IN (comma separated values of sessions that are not of type workshop).\

Note: Using the IN operator requires that all values in the list be knows. Thus, to achieve this, we can limit the user's options by providing a set of pre-defined values in a drop down list that the user can switch from. This will give the program control over what possible values of non-workshop sessions can be queried.





