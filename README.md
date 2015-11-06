# ConferenceOrganization

Download and install Python 2.7 from https://www.python.org/downloads/ if not already installed on your machine 
Download and install Google App Engine SDK. The isntructions are provided here:
https://cloud.google.com/appengine/downloads
If using Windows or Mac, Google App Engine will have a nice GUI icon. If using Linux, use command line tools such as 
devappserver.py and appconfig.py
Install Git
From the terminal, navigate to working directory, run “git clone http://github.com/uzmasyed00/ConferenceOrganization”. This will give you a directory named ConferenceOrganization.
In a web browser, go to "console.developers.google.com" and create a new project. Insert the project id in the application field in app.yaml in Conference Central directory.
Then, in Google App Engine launcher, add an existing application and navigate to the cloned directory.
Run the application.
In a browser of your choice,, navigate to localhost:port/_ah/api/explorer and start working with the end points.


#Task1

A session is implemented as a child of a conference entity. A websafe conference key is passed in the request that can be used to query the conference entity the key pertaains to. This key is then set as the parent of a session entity in the datastore.
Speaker is one of the properties of the session entity and is implemented as a string.

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





