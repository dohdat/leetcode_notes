# Leadership Principles

### Customer Obsession
- Investigated and provided solutions for critical customer incidents
  - DTCC case:
    - Issue: Service templates broke after transferring from QA to Production; QA environment working fine.
    - Action: Stayed on call multiple times over 2 weeks with support engineer and senior engineers to investigate.
    - Troubleshooting: Examined logs and discovered the issue stemmed from using unsupported content packs for transfer.
    - Resolution: Advised the customer to use backup and restore instead to prevent further issues.
  - Progressive case:
    - Issue: Extreme lag on environment due to backfilled events after recent upgrade; stack unusable.
    - Action: Stayed on call for 5+ hours with support engineer, other engineers from different teams to investigate/search for logs for root cause. 
    - Troubleshooting: Restarted rules engines and the stack multiple times.
    - Resolution: Ran a script to restart everything, eliminating the backfilled events.

### Ownership
I took ownership of a ticket to add a section to the connection page, which I successfully completed. During the process, I noticed that the page became slow and unresponsive when users typed in certain fields, especially if the page was long. Understanding the impact on user experience, I spent 2-3 days investigating and fixing the issue in my section.

Realizing that the problem affected other parts of the page, I proactively extended the fix to those areas as well. This caused over 50 WDIO tests to break. After consulting with a senior engineer, I took responsibility for fixing all the tests, despite the challenges of them passing locally but failing in the CI/CD pipeline. I worked through the weekend to resolve these issues, and the senior engineer was very pleased with the final result.
  
### Invent and Simplify
- Drag and drop
  - Took on a critical feature for Service Sandbox involving drag-and-drop functionality, initially assigned to a senior engineer due to its complexity and lack of precedent in Splunk.
  - After the senior engineer determined the feature was not feasible following a 2-3 week investigation, I offered to explore it further after completing my own tasks early.
  - Leveraged documentation on the D3 library and gradually implemented features such as node detection, mouse interaction, and canvas panning and zooming, demonstrating slow but steady progress to the team.
  - Despite initial estimates of a 2-week timeline, the feature required an additional month to fully develop. Successfully delivered the drag-and-drop functionality, allowing users to create service dependencies visually, which resulted in a patent and a SPOT award for my contribution.

- Backbone to React:
  - Upgraded the Service Definition preview page from Backbone to React, modernizing the UI and adding advanced features such as outlier detection and better user interactions.
  - The page was originally built with Backbone JS. The task involved a complete overhaul to React, which required understanding the current implementation and functionality.
  - Faced challenges in grasping the existing behavior, leading to many questions and thorough investigation to ensure a smooth transition.
  - Added more caching to improve more performance. 
  - Successfully completed the migration, which not only improved the page's performance and usability but also enabled further development and enhancements in line with modern framework capabilities.

### Are Right, A Lot
- Diagnosed complex issues like KV store problems and ITSI search head overloads, providing effective solutions that resolved critical customer incidents.
- Led design discussions for Service Sandbox features, ensuring they met customer needs and were implemented with high quality.

### Learn and Be Curious
- Actively engaged in sprint demos and gathered feedback to improve development efforts and adapt to customer needs.
- Explored and integrated machine learning techniques into ITSI's Adaptive Thresholding project to enhance monitoring capabilities.

### Hire and Develop the Best
- Worked closely with other senior engineers, leading by example in the design and implementation of critical features.

### Insist on the Highest Standards
- Delivered high-quality, impactful features such as the drag-and-drop service builder and Adaptive Thresholding, which significantly improved user experience and product adoption.
- Implemented WDIO tests to prevent regression, maintaining high standards in code quality and functionality.

### Think Big
- Developed the Service Sandbox, a major feature that significantly reduced service decomposition time and improved adoption rates, impacting ITSI’s overall success.
- Led the transformation of key ITSI features, pushing for modernized, user-friendly interfaces and advanced functionality.

### Bias for Action
- Quickly addressed critical bugs and issues in Service Sandbox and ITSI, ensuring they were resolved before GA.
- Implemented a last-minute feature allowing users to revert published services back into the sandbox, addressing user requests in time for the GA release.

### Earn Trust
- Consistently delivered on commitments, leading the development of key features and resolving critical customer issues.
- Gained trust by presenting work in sprint demos and incorporating feedback to refine and improve deliverables.

### Dive Deep
- Investigated complex customer incidents involving ITSI and Puppet automation, identifying root causes and providing effective solutions.
- Led discussions and in-depth technical reviews of new features, ensuring they met technical and user requirements.
- 
### Have Backbone; Disagree and Commit
- Took the lead in design discussions, advocating for necessary features like drag-and-drop and Adaptive Thresholding, even when they added complexity to the project.

### Deliver Results
- Successfully launched major features like the Service Sandbox and Adaptive Thresholding, delivering significant improvements to ITSI’s functionality and user experience.
- Resolved critical customer incidents, ensuring that ITSI environments remained operational and met customer expectations.

### Success and Scale Bring Broad Responsibility
- Played a key role in launching features that improved ITSI’s scalability and usability, ensuring broader success for Splunk and its customers.


# System Design
## Design Youtube

### 1 - Understand the problem and establish design scope: 3 - 10 minutes

**Functional requirements:**
- Users can upload videos
- Users can like, comment, share videos
- Users can subscribe to channels
- Search functionality

**Non-functional requirements:**
- Scalability to handle millions of concurrent users
- High availability and reliability
- Low latency video streaming
- Secure user data management
- Efficient content delivery network (CDN) for global reach



### 2 - Propose high-level design and get buy-in: 10 - 15 minutes
![image](https://github.com/user-attachments/assets/cab2f5e7-e53e-4121-b415-dc6b7c8c8bd6)

**Client-side application:**
- Web and mobile interfaces
- Video player for streaming
- User interaction features (likes, comments, subscriptions)

**Backend services:**
- User management services: authentication, authorization, user profiles, subscriptions.
- Video upload and encoding services: handles video uploads, encode into multiple formats, storing in a video storage system.
- CDN: distributes video content globally to reduce latency and improve streaming quality.
- Recommendation system: suggests video based on user activity, history and trends.
- Search service: allows users to search for videos, channels.
- Notification service: Sends notifications for new videos, comments.

**Database system:**
- Metadata database: stores video metadata, user information, comments, likes
- NoSQL database: Used for storing large amounts of unstructured data like comments, likes
- Search index: for fast retrieval of search results
- Cache: for storing frequently accessed data to reduce database load.

**Storage sytem:**
- Blob storage (S3): for storing raw video files
- Transcode video storage: for storing videos in different formats and resolutions

**Load balancer:**
- Distributes incoming traffic across multiple servers to ensure high availability and reliability.

### 3 - Design deep dive: 10 - 25 minutes

![image](https://github.com/user-attachments/assets/3e1fcf57-f41a-4386-993c-531b51ed17c6)

**Web Server:**
- Handles incoming HTTP requests from the client like serving web pages, handling video playback requests.

**Load balancer:**
- Distributes incoming requests across multiple web servers to ensure no single server is overwhelmed. This helps in managing high traffic and provides fault tolerance.

**API Server**
- Manages communication between the Web Server and various backend services, including metadata storage and retrieval. This server might also handle user authentication, comments, likes, and other API-related tasks.

**Metadata Storage:**
- Stores metadata related to videos such as titles, descriptions, tags, and other attributes. This database is queried whenever a user searches for a video or when recommendations are generated.

**Metadata:**
- Refers to the information about videos that is used to categorize, search, and recommend videos. It is crucial for the functionality of the platform, enabling efficient data retrieval and processing.

**Transcoding Server:**
- Converts uploaded videos into different formats and resolutions. This allows YouTube to serve videos at various quality levels depending on the user's device and network conditions.

**Video Storage:**
- Where the actual video files are stored. After transcoding, the videos are stored here in different formats and resolutions.

**CDN:**
- A distributed network of servers that delivers video content to users from a location geographically closest to them. This reduces latency and improves video streaming quality.

**Data types:**

**User:**
- userId: UUID unique id for the user.
- email (string)
- username (string)
- profilePictureUrl (string)

**Video:**
- videoID: UUID
- title (string)
- description (string)
- uploaderId (string)
- uploadedDate (DateTime)

**Comment**
- commentID (UUID)
- videoID
- userID
- commentText
- timestamp (datetime)
  
### 4 -  Wrap: 3 - 5 minutes

**Handles locking**
- Pessimistic locking:
  - Locks the data when a transaction begins to prevent other transactions from accessing it until the lock is released. Performance bottlenecks.
- Optimistic locking:
  - Allows multiple transactions to read the same data, but checks for conflicts before committing changes. If a conflict is detected, the transaction is rolled back.
 
**Sharding:**
- Sharding divides a large database into smaller, more manageable pieces, each called a shard.
  - Range-Based Sharding: Distributes data based on a range of values (e.g., user IDs 1-1000 in one shard).
  - Hash-Based Sharding: Uses a hash function on the shard key to evenly distribute data.
  - Geographical Sharding: Divides data based on geographic location to reduce latency.


## Design a Rate Limiter
### 1 - Understand the problem and establish design scope: 3 - 10 minutes




### 2 - Propose high-level design and get buy-in: 10 - 15 minutes



### 3 - Design deep dive: 10 - 25 minutes


  
### 4 -  Wrap: 3 - 5 minutes



