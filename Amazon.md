# Leadership Principles

### Customer Obsession
I noticed that several customers were consistently facing challenges with the ITSI rules engine, leading to frustration and downtime. Recognizing the importance of customer satisfaction, I decided to take proactive steps to address these issues.

First, I gathered detailed feedback from the affected customers through support tickets, direct interviews, and surveys. This helped me identify the common pain points and recurring problems. One major issue was the complexity of configuring the rules engine, which required significant manual effort and deep technical knowledge.

To solve this, I initiated a project to simplify the configuration process. I proposed and led the development of a new user-friendly interface with guided steps and automated checks, significantly reducing the setup time and minimizing errors. I collaborated closely with the UX team to ensure the interface was intuitive and aligned with customer needs.

Throughout the development process, I maintained regular communication with the customers who had reported issues. I provided them with updates, sought their feedback on prototypes, and incorporated their suggestions into the final design. This not only improved the solution but also made customers feel valued and heard.

Once the new interface was deployed, I continued to monitor customer feedback and system performance. The results were remarkable: customer satisfaction scores increased, the number of support tickets related to the rules engine dropped by 40%, and the time to configure ITSI was reduced by 60%.

By focusing on the customers' needs, actively seeking their input, and delivering a solution that significantly improved their experience, I exemplified Amazon's "Customer Obsession" principle.
### Ownership
### Invent and Simplify
### Are Right, A Lot
### Learn and Be Curious
### Hire and Develop the Best
### Insist on the Highest Standards
### Think Big
### Bias for Action
### Earn Trust
### Dive Deep
### Have Backbone; Disagree and Commit
### Deliver Results
### Success and Scale Bring Broad Responsibility


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


## Design a Booking system

### NoSQL vs SQL
