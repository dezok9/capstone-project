Full document: https://docs.google.com/document/d/12m6NJ7iIxK6u4OsEm7HqODg3fAbePe6dI8cZAqInszs/edit?usp=sharing (Meta access only) 


Meta University Eng Project Plan 
CS LinkedIn
Intern: Destiny Okonkwo
Intern Manager: Gianna Torpey
Intern Director: Paulina Anzaldo
Peer(s):  Paskal Asare, Kaushik Mishra
GitHub Repository Link: https://github.com/dezok9/cs-linkedin
Overview
A social platform creating a way to view the work with others, connect with others, and create with others in computer science (CS) without having to download and run code on your local computer. An in-web application used to collaborate with other forward-thinking individuals in CS and connect over code.

Category: Social networking
Story: A social network where innovators in computer science create an account, post and render their code utilizing GitHub Pages, and connect over code. 
Market: Individuals in computer science looking to connect with others in CS
Habit: This app would be used on a daily basis and potentially even multiple times per day to update a user’s connection on their code and receive updates on the progress of others.
Scope: This platform would initially be a platform to share code, renders of code, pictures, and videos with other users. 

Product Spec
User Stories
Required
User can login
User can create an account
User can create / edit / delete posts
User can view a feed of posts
User can add / remove other users as connections
User can upvote posts
Users can reshare posts
User can see their profile
User can see their friends’ profile
User can comment on posts
User can see their connections
User can edit their profile information
User can seamlessly post their code in posts
User can communicate privately with other users in real time (websockets)
User can see similar code and receive recommendations on users doing similar work in the field
Optional
User can render code it in-platform
User can create multi-media (photos, videos) posts
User can have create both business and personal accounts
User has option of providing feedback via an integrated system
User has option to experience a gamified social media experience (ie. badges, achievements, etc.)
User can receive notifications
User can log in with other authentications (i.e. Google, GitHub, etc.)
Screen Archetypes



Screens include a home screen where the user can see the posts of those they follow, a recommended feed where users see recommended posts curated based on a user’s project, and both a login and signup page. Additionally, the platform features a profile page, chat, and comments pages.

Data Model
The platform will require a number of tables. Listed below are tentative features of each table:
Users Table
User ID → Integer (unique)
First Name → String
Last Name → String
Location → String
User Handle → String (unique)
Email → String (unique)
(Hashed) Password → String
GitHub → String
Featured Projects → String[] 
Type (personal or business)* → Boolean
Posts → POSTS TABLE[]
Posts Table
Post ID → Integer (unique)
Author → USERS TABLE (required)
Media* → Database Connection
Tags → String[]
Date → String
Timestamp → String
Message/Text → String
Comment IDs → COMMENTS TABLE[]
Comments Table
Comment ID → Integer (unique) 
Comment Message → String
Date → String
Timestamp → String
Author → USERS TABLE
Upvotes/Likes → Integer
Replies → COMMENTS TABLE[]
Chat Table
Chat ID → Integer (unique)
User #1 → USER TABLE (required)
User #2 → USER TABLE (required)
Messages → MESSAGES TABLE[]
Messages Table
Message ID → Integer (unique)
Message Content → String
Sender → USERS TABLE
Sendee → USERS TABLE
Chat → CHAT TABLE (Chat ID)  (required)
Timestamp → String
Date → String

* Stretch feature fields; may be implemented later on in the project.

Additionally, I intend to use GitHub Pages API to access code that users want to feature on their page and in their posts and Websocket API for live chat features. 

Server Endpoints
This platform will require a number of endpoints in order to retrieve and deliver information to the database. 

GET ENDPOINTS
Feed
Query parameters: user
Recommended feed
Query parameters: user
POST ENDPOINTS
Profile
Body parameters: first name, last name, location, user handle, email, GitHub handle, type
PUT ENDPOINTS
Post
Body parameters: tags, media*, message/text
Comments
Body parameters: comment message
Comment replies
Body parameters: comment message
Chat messaging
Body parameters: message
DELETE ENDPOINTS
Delete user
Query parameters: user, password

* Stretch feature fields; may be implemented later on in the project.



Project Requirements
Technical Challenges
For your project, you should demonstrate that you can apply what you’ve learned so far and expand on that knowledge to write code and implement features that go beyond the scope of the projects you worked on during CodePath.

Based on the general idea and direction of your project requirements, your intern manager will create at least two (2) Technical Challenges for you. This section is all about explaining what they are and how you’re planning to tackle them - you’ll work together with your manager to fill it out. 

Technical Challenge #1 - Live Private Chats 
What
Enabling users to speak privately in-platform allows users to collaborate in real time and speak about their work on a platform that encourages connections. This feature goes beyond what I learned in CodePath as it introduces the concept of websockets and constantly waiting for new chats. 
How
I will equip users with the ability to chat live using websockets, which actively and constantly search for new information from users. This will require the use of an API that is able to manage and implement this. 


Technical Challenge #2 - Personalized Recommended Posts & Connection Opportunities
What
A key feature of this platform is to create a space in which users can create new connections with others performing similar work as them. This introduces the idea that the platform will need to analyze the user’s code and/or interests and then provide the user with similar projects and users. This goes beyond the scope of the CodePath as it introduces an algorithm or API meant to create individualized results based on user data and refined by user data. 
How
Although there are multiple ways in which this could be implemented, the use of an API or external algorithm may provide the best results for users. 

Database Integration
I will be using PostGresQL in order to store and update user information. Prisma will be used to simplify interactions with the database. Furthermore, an encryption tool will be used before storing user passwords and other sensitive information. 

External APIs
GITHUB PAGES API
For this project, I will be using GitHub Pages API extensively. This API provides information about GitHub users, their projects, and information about specific projects and repositories if GitHub Pages is given access. This will provide data that will go on to populate posts and profile pages at the user’s discretion. 

Authentication
User authentication is going to be handled using a combination of requests, database storage, and cookie authentication. 
SIGN UP 
Users without an account will be prompted to sign up and asked to provide information, such as their first and last name, email, GitHub, user handle, and location, to create an account. If fields that are meant to be unique, such as GitHub handles and user handles, are not, the user will be notified to make changes as needed before proceeding. 
LOGIN 
Users will then be asked to log in with their new user handle or email address and password. These will be compared against the information that is held in the database to confirm that the correct credentials are being provided. 
COOKIES & WEBSITE STATE 
Cookies will be used to ensure that the correct user is logged in when going from page to page within the website. To ensure privacy and security, the user will be automatically logged out after a certain period of time unless they request otherwise (for example, if they request for the site to “remember them”). 

Visuals and Interactions
INTERESTING CURSOR INTERACTION 
Cursors will change based on hovering, highlighting, and clicking by the user. This will go to ensure a creative and clean experience on the page and while interacting with the website. Technically, this will be accomplished through CSS styling and specifications, including using selectors in CSS such as :hover. 
UI COMPONENT WITH CUSTOM VISUAL STYLING 
Users will be able to have some autonomy over how their application looks and the overall feel of their page. Technically, this will be implemented using useStates that change the look of the website depending on a user’s selection(s) and preferences. 
LOADING STATE 
When loading information from the database, loading states will communicate to the user that there is currently some data being retrieved, either through loading icons or text. This will be implemented using a combination of CSS, HTML, and JavaScript. 

Focus
User Stories
Focus on the components that will serve as the skeleton of your project. You will probably be using most of what you learned in CodePath to set up things like the client and server repositories, initial routing, login / registration, creating a database with object models, etc.
User can navigate from page to page
User can identify and differentiate the different pages of the website easily
[OPTIONAL] User can see that the database and frontend are connected

Week 5 and 6 should be where you focus on the specific requirements of your project.
User can login
User can create an account
User can post and see their feed
User can see the chat page and who they are chatting with
User can upvote posts
User can reshare posts 

By this point, you should be getting started with your technical challenges as well.
User can see some information on recommended posts and users
User can reshare posts
User can comment on posts 
User can see comments on each post
User can see their friends’ profiles
You should focus on finishing your MVP and core requirements. By this point, you should be done with at least one of your technical challenges.
User can see recommended posts and profiles
User can see their connections
User can chat in real time


Continue work on finishing touches and stretch goals for your MVP. By this point, your core functionality and both TAPs should all be in place. It is also a good point to start working on stretch goals that could further expand on the functionality (and technical complexity) of your project.
This week you also have to submit your self-review, make sure you allocate enough time for this alongside your final submission for your project!
[STRETCH] User can render code it in-platform
[STRETCH] User can create multi-media (photos, videos) posts
[STRETCH] User can have create both business and personal accounts
[STRETCH]User has option of providing feedback via an integrated system
[STRETCH] User has option to experience a gamified social media experience (ie. badges, achievements, etc.)
[STRETCH] User can receive notifications
[STRETCH] User can log in with other authentications (i.e. Google, GitHub, etc.)

It’s time to show others what you have built! Work on a presentation and demo that you will present to other interns to showcase your work. You are also free to continue polishing and expanding on your project!
[STRETCH] User can render code it in-platform
[STRETCH] User can create multi-media (photos, videos) posts
[STRETCH] User can have create both business and personal accounts
[STRETCH]User has option of providing feedback via an integrated system
[STRETCH] User has option to experience a gamified social media experience (ie. badges, achievements, etc.)
[STRETCH] User can receive notifications
[STRETCH] User can log in with other authentications (i.e. Google, GitHub, etc.)
For this week, we have a bunch of extra activities prepared to give you a quick dive of what it is to work at Meta. You will find activities around using internal tools and frameworks, and even committing code to our internal repositories.
[STRETCH] User can render code it in-platform
[STRETCH] User can create multi-media (photos, videos) posts
[STRETCH] User can have create both business and personal accounts
[STRETCH]User has option of providing feedback via an integrated system
[STRETCH] User has option to experience a gamified social media experience (ie. badges, achievements, etc.)
[STRETCH] User can receive notifications
[STRETCH] User can log in with other authentications (i.e. Google, GitHub, etc.)







