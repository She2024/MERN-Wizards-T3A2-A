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
### Level 0: Context Diagram

1. **External Entities**
   - **Users**: Both regular users and admin users who interact with the system.
   - **JIRA System**: External API integration for ticket status updates.
   - **Email/SMS Notification Service**: Used for sending notifications.

2. **System**
   - **Discussion Board Application**: The core application facilitating the discussion platform.

### Level 1: Decomposition

1. **Processes**
   - **User Registration/Login (P1)**
     - **Inputs**: User registration data or credentials.
     - **Outputs**: Authentication tokens or error messages.
     - **Storage**: Updates to the User table.

   - **Create/Manage Posts (P2)**
     - **Inputs**: Post details such as title, content, priority, and category.
     - **Outputs**: Confirmation of creation, updates, or error messages.
     - **Storage**: Post data stored in the Posts table; linked to User table.
     - **External Influences**: Updates from JIRA reflecting changes to related posts (statuses).

   - **Participate in Discussions (P3)**
     - **Inputs**: Replies to posts.
     - **Outputs**: Reply confirmations or error messages.
     - **Storage**: Reply data linked to the appropriate post and user.

   - **Notifications (P4)**
     - **Inputs**: Event triggers such as new replies or post updates.
     - **Outputs**: Notification messages to users.
     - **External Systems**: Interaction with email/SMS services.

   - **Admin Functions (P5)**
     - **Inputs**: Admin actions like delete, archive, or update priorities.
     - **Outputs**: Confirmation messages or errors.
     - **Storage**: Modifications reflected in the database tables (Post, User).

2. **Data Stores**
   - **Users (D1)**
     - Stores user registration, authentication details, and admin status.
   - **Posts (D2)**
     - Contains post information, connected to reply data.
   - **Replies (D3)**
     - Houses individual replies linked back to posts.
   - **Notifications (D4)**
     - Manages user notifications and message logs.

3. **Data Flows**
   - Arrows indicating data flow between external entities and processes (e.g., Users -> User Registration/Login).
   - Arrows flowing into and out of data stores indicating storage and retrieval actions.

#### Main application Flow
[Link to Full App Dataflow Diagram](./docs/Flowchart/flowchart.png)
#### Home-Dashboard Flow
[Link to Home-Dashboard Dataflow Diagram](./docs/Flowchart/Home-dashboard.png)
#### Registration-Login Flow
[Link to Registration-Login Dataflow Diagram](./docs/Flowchart/Registration-login.png)
#### User Flow 
[Link to User Dataflow Diagram](./docs/Flowchart/user.png)
#### Admin Flow
[Link to Admin Dataflow Diagram](./docs/Flowchart/admin.png)
#### PostCreation-Reply-Details Flow
[Link to PostCreation-Reply-Details Dataflow Diagram](./docs/Flowchart/Postcreation-reply-details.png)
#### Notification Flow
[Link to Notifications Dataflow Diagram](./docs/Flowchart/notification.png)

### Entities and Relationships (ERD)

1. **Entity: User**
   - **Attributes:**
     - `userID`: ObjectId (Primary Key)
     - `username`: String
     - `passwordHash`: String
     - `email`: String
     - `userClass`: String (e.g., Admin, Regular User)
     - `userAdmin`: Boolean (Indicates if the user has admin privileges)
     - `registrationDate`: Date 

2. **Entity: Post**
   - **Attributes:**
     - `postID`: ObjectId (Primary Key)
     - `title`: String
     - `content`: String
     - `authorID`: ObjectId (Foreign Key referencing User)
     - `creationDate`: Date
     - `replies`: Array of ObjectId references to Reply
     - `priorityLabel`: String
     - `category`: String
     - `isArchived`: Boolean (Indicates if the post is archived)

3. **Entity: Reply**
   - **Attributes:**
     - `replyID`: ObjectId (Primary Key)
     - `content`: String
     - `authorID`: ObjectId (Foreign Key referencing User)
     - `creationDate`: Date
     - `postID`: ObjectId (Foreign Key linking to Post)

4. **Entity: Notification**
   - **Attributes:**
     - `notificationID`: ObjectId (Primary Key)
     - `recipientID`: ObjectId (Foreign Key referencing User)
     - `relatedPostID`: ObjectId (Optional, referencing Post)
     - `message`: String
     - `creationDate`: Date
     - `isRead`: Boolean 

5. **Relationships:**
   - **User to Post/Reply:**
     - One-to-Many relationship: A User can author multiple Posts and Replies.
   - **Post to Reply:**
     - One-to-Many relationship: Each Post can have multiple associated Replies.
   - **User to Notification:**
     - One-to-Many relationship: Each User can receive multiple Notifications.

### Additional Actions for User Administration

- Admin users (`userAdmin` = true) will have additional capabilities, such as:
  - **Deleting Posts**: Admins can remove inappropriate or obsolete posts.
  - **Archiving Posts**: Admins can archive posts that are no longer active but may need future reference.
  - **Updating Priority/Status**: Admins can adjust the priority label of posts to reflect their importance in current workflows.


### Diagram Structure

- **User Table**:
  - ID: `userID` (PK)
  - Username: `username`
  - Password Hash: `passwordHash`
  - Email: `email`
  - User Class: `userClass`
  - Is Admin: `userAdmin`
  - Registration Date: `registrationDate`

- **Post Table**:
  - ID: `postID` (PK)
  - Title: `title`
  - Content: `content`
  - Author: `authorID` (FK to User)
  - Created On: `creationDate`
  - Replies: `replies` (array of Reply IDs)
  - Priority Label: `priorityLabel`
  - Category: `category`
  - Is Archived: `isArchived`

- **Reply Table**:
  - ID: `replyID` (PK)
  - Content: `content`
  - Author: `authorID` (FK to User)
  - Created On: `creationDate`
  - Linked Post: `postID` (FK to Post)

- **Notification Table**:
  - ID: `notificationID` (PK)
  - Recipient: `recipientID` (FK to User)
  - Related Post: `relatedPostID` (Optional FK to Post)
  - Message: `message`
  - Created On: `creationDate`
  - Is Read: `isRead`

[Link to ER Diagram for Discussion Board app](./docs/ERD/er_diagramv2.drawio.png)

-----
## R3:	Application Architecture Diagram	
1. **Frontend Layer**
   - **User Interface (React.js)**
     - **Components**
       - Login/Registration Forms
       - Post Creation and Listing
       - Reply Management
       - Notifications Display
       - Web Assets and PDFs Display
       - JIRA Ticket Status Indicator (showing In Progress, Awaiting Support, Complete)
     - **Routing**
       - Dashboard
       - Post Details Page
       - User Profile Page
       - Assets and Services Page 

2. **Backend Layer**
   - **Server (Node.js with Express.js)**
     - **Authentication Middleware**
     - **API Endpoints**
       - **User Routes**
         - POST `/users/register`
         - POST `/users/login`
         - GET `/users/:id` (Profile)
       - **Post Routes**
         - POST `/posts` (create discussion)
         - GET `/posts` (fetch all posts)
         - GET `/posts/:id` (retrieve specific posts)
         - PUT `/posts/:id` (update discussion)
         - DELETE `/posts/:id` (delete discussion)
         - **JIRA Integration Endpoint**
           - POST `/jira/update-status` (updates discussion card with JIRA ticket status)
       - **Reply Routes**
         - POST `/replies` (create a reply)
         - GET `/posts/:postId/replies` (fetch replies for a post)
       - **Web Assets Routes**
         - GET `/assets` (fetch web assets and PDFs related to discussions)
       - **Notification Routes**
         - GET `/notifications/:userId` (retrieve user notifications)

3. **Database Layer**
   - **MongoDB**
     - **Collections**
       - `Users`: Stores user profiles with classifications.
       - `Posts`: Contains discussion topics.
       - `Replies`: Links replies to their parent posts.
       - `Assets`: Stores metadata for web assets and PDFs.
       - `Notifications`: Manages user notification data.

4. **Business Logic Layer**
   - Handles user input, processes data, and integrates with the JIRA API to automatically update discussion statuses based on JIRA ticket progress.

5. **Integration Layer**
   - **JIRA API Integration**
     - Links JIRA tickets to discussions, updating the discussion card status based on ticket updates.
   - **External Services**
     - Email/SMS service (We can use SendGrid or Twilio) for notifications.

6. **Hosting & Deployment**
   - **Frontend Deployment**: Hosted on Netlify for performance and scalability.
   - **Backend Deployment**: Hosted on Render for efficient backend service management.
   - **CI/CD Pipelines**: Automated deployment and testing (e.g., GitHub Actions).

7. **Security Layer**
   - Uses HTTPS for secure data transmission.
   - Implements JWT (JSON Web Tokens) for user sessions.
   - Input validation and sanitisation to prevent vulnerabilities.  

### A.A.Diagram
[Link to A.A.D Diagram](./docs/A.A.D/A.A.D.png)

-----
## R4:	User Stories	
- Marking Guide:
CMP1003-5.1: Provide UX/UI design documentation(user stories) that adequately show Agile methodology implementation.
    - HD: Provides multiple user stories that use ‘persona, what and why’ that outline meaningful features of project. Shows evidence of user story revision and refinement.


### Persona: Wade Warren

What? I need a service where I can change the priority of tasks when a task becomes urgent. Why? So critical marketing tasks get completed on time.

What? I need a service where my team and I can reply to submitted requests with additional marketing notes or materials. Why? So the Web Services team has all the necessary assets and information to complete the work.

What? I need a service where I can edit my request after submitting it.
Why? So I can correct mistakes or update details without submitting a new request.

What? I need a service where my requests are securely stored. Why? So I don’t lose important information and can reference past submissions.

What? I need a service where my team can see all submitted requests and their priorities.Why? So everyone knows what tasks are being worked on and which ones are the highest priority.


Persona: Anna Williamson

What? I need a service where I can submit requests for event updates on the discussion board.Why? So the Web Services team can update event details efficiently without needing a Jira ticket for every change.

What? I need a service where I can set priority levels for event-related requests.Why? So urgent updates, like last-minute schedule changes such as event cancellation, are addressed quickly.

What? I need a service where I can reply to task requests.Why? So I don’t have to submit a new request every time minor adjustments are needed.

What: I need a service where I get a notification when someone replies to my post.
Why? So I can stay updated on my request without constantly checking the discussion board.

What? I need a service where I can overview the discussion board before posting a request.Why? So I don’t duplicate an existing request.

[Link to customer stories folder](./docs/Customer%20Stories/)  

-----
## R5:	Wireframes for multiple standard screen sizes, created using industry standard software	    
1. **Home/Dashboard Screen**
   - **Purpose**: Provide an overview of current discussions, recent notifications, and quick access to key functions.
   - **Key Features**: Post list with filtering options, notifications sidebar, quick links to create a post or access user profile.

2. **Registration/Login Screen**
   - **Purpose**: Allow users to sign up or log in to access the platform.
   - **Key Features**: Simple, clean login form with fields for email/username, password, and buttons for login, registration, and password recovery.

3. **Post Creation Screen**
   - **Purpose**: Enable users to create new discussion posts.
   - **Key Features**: Form fields for title, content, priority level, category, and optional JIRA ticket linking. Clear submit and cancel actions.

4. **Post Detail & Discussion Screen**
   - **Purpose**: Display full details of a post along with all replies.
   - **Key Features**: Post content, list of replies, option to reply, like or follow the post, and admin functionalities if applicable (edit or delete).

5. **Reply Creation Screen (Modal)**
   - **Purpose**: Allow users to respond to posts.
   - **Key Features**: Simple text area for content, submit button. Can be a modal overlay to streamline the user experience.

6. **Notifications Screen**
   - **Purpose**: Provide a centralised view of all notifications.
   - **Key Features**: List of notifications with marks for read/unread status, links to the relevant posts, and settings for notification preferences.

7. **User Profile Screen**
   - **Purpose**: Display user information and settings.
   - **Key Features**: User details, edit profile options, view past posts and replies, and an admin area for eligible users.

8. **Admin Functions Screen**
   - **Purpose**: Enable admin users to manage posts and users.
   - **Key Features**: List and controls to archive, delete, or update priority for posts, user management options.

### Responsive Layouts
   - **Desktop Version**: Display full version of screens with all features accessible.
   - **Tablet Version**: Compact arrangement to maintain functionality with adjusted layouts.
   - **Mobile Version**: Streamlined design focusing on core functions, optimised for vertical scrolling and touch interactions.

[Link to wireframes folder](./docs/Wireframes/)  
[Link to colour choices folder](./docs/Colour%20selection/)

-----
## R6:	Screenshots of your Trello (or similar kanban system) board throughout the duration of the project
- Marking Guide:
CMP1003-6.1: Select and follow a commonly used planning methodology, such as Kanban, Trello, Jira, or Asana, that adequately show Agile methodology implementation.
    - HD: Simple and clear standards for planning methodology chosen and adhered to  
### Trello Board
Our project utilised Trello as our chosen Kanban system to implement Agile methodology effectively throughout the project duration. Trello's visual interface allowed us to maintain clear and simple standards for task management and prioritized efficient workflows.

#### Planning Methodology
- **Columns Setup**: Our Trello board was organised into columns representing key stages of development: * add collumn names here *

#### Agile Implementation
- **Task Cards**: Each task card included detailed descriptions, due dates, assignees, and relevant attachments or links. This level of detail maintained clarity and transparency, ensuring all team members could contribute effectively.

#### Project Progression
- **Screenshots**: Throughout the project, we captured screenshots of our Trello board to document the evolution of our task management. These screenshots demonstrate how the board aided in visualising progress.

[Link to project screenshot folders](./docs/Project%20screenshots/)
