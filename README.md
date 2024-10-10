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

As MYDRTV is to be a global project solved with microservices, we felt it would be very valueable to make a bounded context diagram. Splitting up the domain into different subdomains is a necessity for a microservice approach. We added most of the actions from the use case diagram to the bounded context, to draw clear lines on which sub domain the action is made and where it should be sent to.


![MyDRTV](https://github.com/user-attachments/assets/2f78f702-7f57-4d2a-9cee-1662cfa73c8e)

### Technology Stack
We have a frontend that consists of a React Native as it’s very flexible and it’s divided into components, Making it easier to also develop our app across different platforms. 

Our Back-end will mostly consist of C# code, with possibilities of code being written across different languages due to our use of microservices. An example could be that we would use python for our user recommendation service.

For our database we’ll use MongoDB as our NoSQL database, as it’s what we are most familiar with.

Hosting of the servers will be cloud based, all done from Azure for easy management.

### Microservices vs Monolithic
#### Advantages and disadvantages of Monolithic architecture
Microservices are a great way to allow teams to work agile with frequent deployments. It allows flexible scaling and continuous deployment. Microservices allow teams to select the tools the need and allow for deployment of changes without risking errors tied to the entire application.
This does, however, add more complexity than monolithic architecture, as more services are created by more teams. This also requires better communication between teams and collaboration to coordinate updates. Each service may also require it's own infrastructure as well as testing suites and logs, this is where microservices are great, because even though it takes more time to add tests, logs, etc on each separate service, each service can also be tailored to fit its needs. These extra steps can make debugging more difficult and increase costs. Also, it can lead to a variety of languages, logging standards and monitoring leading to a lack of standardization. It does however ensure us that we can isolate our services, which is great for security standards, especially if we take into consideration that we might want a service for user information and payments. Using different services also allows the business owning the system to analyze what parts need optimization or new features based on user feedback.
Based on these points, we chose to use microservices as this would allow us to use outsourcing to reduce costs, implement multiple languages such as python for machine learning, and allow us to better implement future features without compromising the integrity of the application or requiring a complete redeployment.
