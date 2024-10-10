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

### Why Microservices?
Microservices are a great way to split our system into many smaller parts that are all connected. While we know that our customer want a scalable system because it should be available world wide, we want to maximize our efforts and distribute work. Our customer has made it clear that they are considering outsourcing due to the financial aspect of the project, which would be made more accessible with microservices.
Using microservices also means that we do not need to worry about our whole system being coded in one language. By using these services, we can make sure that each part of our system will be tailored to fit its needs, even reflected within the choice of language it’s coded in.
By dividing our system into smaller pieces, we can also make sure that we can isolate possible bugs or errors. This means that if there were to be an error with our search function, it might not affect our users ability to stream the movies or series they want to watch. Due to our system being so divided, it also benefits the security aspect of our system, a big factor for our system being based in the EU would be GDPR, which using these services would be much easier to secure data and comply with the security standards set by GDPR. The business also benefits from multiple services by allowing the business to analyze based on users feedback or data analysis, and which parts of the system needs to be adjusted.

With microservices, we enable our system to be more open to changes or implementations in the future. If we need a new feature for our video player, like streaming in 4K, if there were to be a premium feature down the line, the new developers working on the system will find it easier to access what they need without much confusion.

Even though microservices are expensive, they allow us to pay for what we use on our cloud based services. This means that we would only need to pay for the cloud based services that are used on our services, essentially making sure that we maximize what we are paying for.


### Microservices vs Monolithic
#### Advantages and disadvantages of Monolithic architecture
Having only one code base and one directory makes development and deployment easier. Likewise, in a centralized code base and repository, one API can perform the same funktion as multiple microservices
Since monolithic architecture uses a single, centralized unit, testing and debugging is faster and easier to follow.

This, however, comes at the cost of slower development speed and increased complexity. Individual components can not be scaled and if any module has an error, ic could potentially affect the entire application. Any changes to the framework or language will affect the entire application, making changes often more expensive and time consuming, requiring the entire monolith to be redeployed. Monolithic architecture also constrains which technologies can be used.

#### Advantages and disadvantages of microservices
Microservices allow teams to work agile with frequent deployments. It allows flexible scaling and continuous deployment. Microservices allow teams to select the tools the need and allow for deployment of changes without risking the entire application.

This does, however, add more complexity than monolithic architecture, as more services are created by more teams. This also requires better communication between teams and collaboration to coordinate updates. Each service may also require it's own infrastructure as well as testing suites and logs. This can make debugging more difficult and increase costs. Also, it can lead to a variety of languages, logging standards and monitoring leading to a lack of standardization.


Based on these points, we chose to use microservices as this would allow us to use outsourcing to reduce costs, implement multiple languages such as python for machine learning, and allow us to better implement future features without compromising the integrity of the application or requiring a complete redeployment.
