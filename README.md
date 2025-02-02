# MERN-Wizards-T3A2-A
Documentation and planning for  Discussion Board 
## MERN Wizards, the team:
     Sheree Kunne
     Luke Harris
     Jessica Vaz Martins

## R1: Project Overview:
### Description
The platform is a discussion board designed to enable staff or group members to discuss and set workflow priorities. It incorporates user registration and classification to manage permissions for interacting with, deleting, or archiving threads. 

### Purpose
The aim is to facilitate easy collaboration by providing an economical and efficient way for businesses to communicate and plan future workflow priorities. By increasing collaboration without increasing subscription costs, it helps reduce invalid service requests, as staff can better understand which unit manages specific assets or projects. 

### Functionality/Features
The discussion board will support informal conversations across the business to map and prioritise workflows for a 12-month plan while allowing flexibility to accommodate changes. Key features include:
- **Registered User Authentication**: Restricts access to authorised users.
- **User Classifications**: Manages levels of access and permissions.
- **Discussion Topics with Replies**: Users can create and participate in topic discussions.
- **Search Function**: Allows easy location of topics.
- **Priority/Category Labels**: Helps in organising discussions.
- **Notifications**: Alerts users to updates or new topics.
- **Admin Functions**: Includes options to delete, archive, and set priority levels for discussions.
- **JIRA API Link to the Cards**: Integrate with JIRA via its API, allowing users to link discussion threads directly to JIRA cards. This facilitates a seamless transition between planning and execution phases by maintaining direct access to task details and status updates within the JIRA platform.

### Target Audience
The platform targets companies or groups that need to collaborate on workflow planning and establish open discussion channels.
- **Project Managers**: To oversee and prioritise project discussions and workflows.
- **Team Leads**: To engage their teams in collaborative discussions and contribute to setting priorities.
- **Staff Members**: To participate in discussions, offer insights, and help in decision-making processes related to workflow priorities.
- **IT Administrators**: To manage user roles and ensure secure and efficient platform usage

### Tech Stack

- **Frontend**: Built using React.js to provide a dynamic and intuitive user interface.

- **Backend**: Developed with Node.js and Express, featuring:
  - **Schemas**:
    - **postSchema**: Includes title, content, author, creation date, and a reply array.
    - **replySchema**: Comprises content, author, creation date, and links to parent posts.
  - **API Endpoints**:
    - `get-all-posts`: Fetches all posts.
    - `get-post-by-ID`: Retrieves specific posts by ID.
    - `create-new-posts`: Allows the creation of new discussions.
    - `create-reply-to-posts`: Facilitates replying to posts.
  - **Replies Management**:
    - Replies are saved to the database and linked to the parent post.
    - Posts with replies are fetched to display full discussions on the frontend.
  - **Error Handling**: Returns meaningful error messages to users when exceptions occur.

- **Database**: Utilises MongoDB to efficiently store and manage data.

- **Hosting**: The application is hosted on Netlify, ensuring reliable availability and scalability.
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