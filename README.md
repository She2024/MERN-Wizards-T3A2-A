# MERN-Wizards-T3A2-A
Documentation and planning for  Discussion Board 
## MERN Wizards, the team:
     Sheree Kunne
     Luke Harris
     Jessica Vaz Martins

## R1: Project Overview:
## Description:

A discussion board to allow staff or group members to discuss and set workflow priorities. Registered users and user classification will manage how users can interact, delete or archive threads. 

## Purpose:
**Easy collaboration:** An economic and efficient way for business to communicate and plan future workflow priorities.  
**Reduces subscription costs:** Increase the level of staff collaboration without the cost of increasing user subscriptions. 
**Reduce invalid service requests:** Reduce the number of invalid tickets being created by staff that are unsure which unit manages the asset or project in question.

## Functionality/features:

The discussion board will allow for an informal conversation across the business to map and prioritise workflow for the 12-month plan and allow priorities to pivot to accommodate work that may impact the planned deliverables. 
     •	Registered user authentication to restrict access 
     •	User classifications to manage levels of access
     •	Discussion topics with reply options
     •	Search function to locate topics
     •	Priority/category labels 
     •	Notification to alert relevant user of updates or new topics
     •	Admin functions to deleting, archiving and setting priority levels

## Target audience:
Companies or groups that need to collaborate on workflow planning and create open discussion channels. 

## Tech Stack: 
### Frontend
*Frontend:* React.js (UI) 
Insert details

## Backend
*Backend:* Node.js with Express
     •	Schemas: 
     •	postSchema: title, content, author, creation date, and reply array. 
     •	replySchema : content, author, creation date, and link to parent post.
     •	API Endpoints:  routes:
     •	get-all-posts
     •	get-post-by -ID
     •	create-new-posts
     •	create-reply-to-posts
     •	Replies: 
     •	 saved to the database
     •	reply ID is added to related post's replies array linking the post and its replies
     •	Fetching Posts and Replies: Retrieve posts with replies, frontend displays full discussions for improved UX.
     •	Error Handling: API method includes error handling, returning meaningful error messages to the user.

## Database: MongoDB Atlas Authentication: JWT for business accounts, OTPAuth library for TOTP generation and verification 
## Hosting: Netlify for the frontend
-----
## R2: Dataflow Diagram	
- Marking Guide:
CMP1003-4.1: Dataflow Diagram
    - HD: Provides dataflow diagram(s) that strictly follow the standard convensions to clearly identify the processes within your application. Clearly depicts where data is coming from, where it is going and how it is being stored.

-----
## R3:	Application Architecture Diagram	
- Marking Guide:
CMP1003-4.2: Application Architecture Diagram
    - HD: Shows almost flawless understanding of the high level structure of the app

-----
## R4:	User Stories	
- Marking Guide:
CMP1003-5.1: Provide UX/UI design documentation(user stories) that adequately show Agile methodology implementation.
    - HD: Provides multiple user stories that use ‘persona, what and why’ that outline meaningful features of project. Shows evidence of user story revision and refinement.

-----
## R5:	Wireframes for multiple standard screen sizes, created using industry standard software	  
- Marking Guide:
CMP1003-5.2: Provide UX/UI design documentation(wireframes)
    - HD: Provides wireframes that show exceptional planning of project flow and structure including but not limited to space distribution, content prioritisation, intended actions, functions, relationships between screens.

-----
## R6:	Screenshots of your Trello (or similar kanban system) board throughout the duration of the project
- Marking Guide:
CMP1003-6.1: Select and follow a commonly used planning methodology, such as Kanban, Trello, Jira, or Asana, that adequately show Agile methodology implementation.
    - HD: Simple and clear standards for planning methodology chosen and adhered to