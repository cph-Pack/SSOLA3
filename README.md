# SSOLA3

## Criteria for MyDRTV
Must have a high availability and provide access to the major collection of old TV programmes and movies at a global scale. These should be easy to search for with the ability to search for year of production, title, genre etc.
This is part of a digital transformation project and  therefore all aspects of the business cycle, including marketing of DR's services to customers, like interactivity with users through a rating system and a "if you liked this, you'll like this show/movie" feature to encourage users to stay on the app for a longer period of time.




## Requirements
In this section, we will outline the functional and non-functional requirements of the MyDRTV case, so we can choose a fitting software architecture for the solution.

Furthermore, we will describe one key use case in detail and include a full use case diagram. 

### Functional requirements
**Video player:** The system must include a video player for viewing films and TV programmes with basic controls, such as play, pause, rewind, and fast-forward.

**Social network:** The system must include social network features allowing users to find and befriend each other.

**Content library:** The system must provide access to a major collection of old DR films and TV programmes. 

**Search function:** Users must be able to search for content based on different criteria, such as year of production, title, and genre.

**User accounts:** Users must be able to create, manage, and delete their personal accounts.

**User ratings and interaction:** Users must be able to rate films and TV programmes 1-5 stars. Users must be able to view and comment on other users' ratings. 

**Recommendations:** The system must include a feature called '*More programmes you may like*' that recommends other content to users based on their viewing history and ratings.


### Non-functional requirements
**High availability:** The system should be operational 24/7 with minimal downtime. 

**Security and GDPR compliance:** The system should be protected against common security threads and all personal data must be encrypted and stored securely in compliance with GDPR rules. 

**Global accessibility:** The system must be accessible globally and have multi-language support, at least Danish and English. 

**Performance:** The system must have fast response times for searches and recommendations, and the video player should load fast and rarely buffer to keep users engaged.

### Use cases

#### UC1: Search film by title
**Description:** This use case describes the process in which a user searches for a specific film by its title.

**Actors:** User, the system

**Preconditions:** The user has created an account and is logged into the MyDRTV application. The user knows the title of the film they are searching for.

**Trigger:** The user enters the film's title into the search bar and presses the search button.

**Postcondition:** The search result is displayed.

**Basic flow:** 
- The user enters the film's title into the search bar and presses the search button.
- The system securely searches its database for a film with the given title.
-  The system finds the film in the database and retrieves it. [*AF1*], [*AF2*]
- The system displays the found film which is clickable, so the user can go and watch it if wanted.

**Alternative flows:** 

*AF1*:
- The database does not contain a film with such title
- The system displays the message: *"We don't yet have* [film title]*. Maybe you would like:"* and displays the '*More programmes you may like*' recommendations instead. Each recommendation should be clickable, so the user can go and watch it if wanted.

*AF2*:
- The database contains more than one film with such title, so the system retrieves them all.
- The system displays all found films. Each film should be clickable, so the user can go and watch it if wanted.

#### Use case diagram
![image](https://github.com/user-attachments/assets/022bd7c0-432a-4abe-93ba-0fb3f13673e0)

#### Bounded context diagram

As MYDRTV is to be a global project solved with microservices, we felt it would be very valueable to make a bounded context diagram. Splitting up the domain into different subdomains is a necessity for a microservice approach. We added most the actions from the use case diagram to the bounded context to draw clear lines on which sub domain the action is taken and where it should be sent to.


![MyDRTV](https://github.com/user-attachments/assets/2f78f702-7f57-4d2a-9cee-1662cfa73c8e)


