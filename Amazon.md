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
- I took ownership of a ticket to add a section to the connection page, which I successfully completed. During the process, I noticed that the page became slow and unresponsive when users typed in certain fields, especially if the page was long. Understanding the impact on user experience, I spent 2-3 days investigating and fixing the issue in my section.

- Realizing that the problem affected other parts of the page, I proactively extended the fix to those areas as well. This caused over 50 WDIO tests to break. After consulting with a senior engineer, I took responsibility for fixing all the tests, despite the challenges of them passing locally but failing in the CI/CD pipeline. I worked through the weekend to resolve these issues, and the senior engineer was very pleased with the final result.
  
### Invent and Simplify
**- Drag and drop**
  - Took on a critical feature for Service Sandbox involving drag-and-drop functionality, initially assigned to a senior engineer due to its complexity and lack of precedent in Splunk.
  - After the senior engineer determined the feature was not feasible following a 2-3 week investigation, I offered to explore it further after completing my own tasks early.
  - Leveraged documentation on the D3 library and gradually implemented features such as node detection, mouse interaction, and canvas panning and zooming, demonstrating slow but steady progress to the team.
  - Despite initial estimates of a 2-week timeline, the feature required an additional month to fully develop. Successfully delivered the drag-and-drop functionality, allowing users to create service dependencies visually, which resulted in a patent and a SPOT award for my contribution.

**- Backbone to React:**
  - Upgraded the Service Definition preview page from Backbone to React, modernizing the UI and adding advanced features such as outlier detection and better user interactions.
  - The page was originally built with Backbone JS. The task involved a complete overhaul to React, which required understanding the current implementation and functionality.
  - Faced challenges in grasping the existing behavior, leading to many questions and thorough investigation to ensure a smooth transition.
  - Added more caching to improve more performance. 
  - Successfully completed the migration, which not only improved the page's performance and usability but also enabled further development and enhancements in line with modern framework capabilities.

### Are Right, A Lot
**Service Health Score**
- I used my judgment to create a feature that shows health scores for multiple service levels, even though it wasn't something customers asked for initially.
- I felt this feature would be really important for Service Sandbox, so I pushed for its development.
- I got input from both customers and the engineering team to make sure it was going to work well.
- By tackling the tricky parts of calculating and showing these scores and using feedback to improve things, I made sure the feature really met user needs and made the tool better overall.

### Learn and Be Curious
**Backbone to React, added Adaptive Thresholding**
- Actively engaged in demos and discussed ideas regarding Adaptive Thresholding algorithms.
- I dove into outlier detection as part of the ITSI Adaptive Thresholding project, which got me learning more about machine learning and how adaptive thresholding works.
- I wasn’t familiar with these concepts before, but I saw their potential to really boost our feature's effectiveness.
- I spent time understanding how to apply machine learning to predict anomalies and improve KPI monitoring.
- This curiosity helped me build a better feature and really pushed me to expand my skills beyond my usual scope.

### Hire and Develop the Best
- I took the lead in mentoring interns on the ITSI Service Sandbox project, guiding them through the setup of Splunk and ITSI itself. I met with them one-on-one to help with setting up their environments, answering any questions they had, and tackling any roadblocks they faced. These sessions were key in making sure they felt supported and confident, helping them quickly get up to speed with the project. By providing this guidance, I helped the interns contribute more effectively to the team and grow in their roles. They tend to bring things up that are blocking them. We talk about that and either I intervene directly or I give them advice on how to clear the roadblocks.

### Insist on the Highest Standards
When I took over the responsibility for improving the connection page in our application, I noticed that our WDIO tests were failing frequently, making it hard to trust the automated testing process. The connection page had become slow and unresponsive, leading to over 50 test failures. Some suggested ignoring the tests since they were flaky, but that didn’t sit well with me—I knew we needed reliable tests to maintain quality. I spent a weekend digging into the test failures, consulting with senior engineers to identify the root causes. By the end, I not only fixed the connection page but also made the WDIO tests more stable and reliable. As a result, our test suite now accurately reflects the system’s performance, ensuring we can confidently roll out updates without compromising on quality.

### Think Big
When I noticed that users were waiting 7-14 days for data to become available in Service Sandbox, I realized we needed a faster solution. I proposed and implemented a backfilling feature that allowed users to populate data up to 7 days in the past instantly. This saved users a significant amount of time and allowed them to start analyzing and testing their services immediately, without the usual delays. By adding this feature, I improved the efficiency of the Sandbox, making it much more user-friendly and effective for quick iterations and testing.

### Bias for Action
We needed to enhance the Service Sandbox feature by adding a publish/validation page so users could check for errors before finalizing their services. A key aspect was ensuring that the service trees displayed correctly, with problematic nodes in red and others in light red. During development, we discovered that the page was incorrectly displaying parent nodes, which could prevent users from easily identifying issues.

Instead of delaying the rollout, I quickly identified that the problem was due to a configuration error involving the placement of the parent nodes. I updated the configuration, tested the fix, and deployed it to production. This swift action ensured that users could use the new feature effectively without disruption, maintaining project momentum and enhancing the user experience.

### Earn Trust
When reviewing MRs, I took a meticulous approach to verify that each change addressed all potential scenarios and edge cases. I worked closely with the engineers to discuss and understand their solutions, providing detailed feedback and suggesting improvements when necessary. This thorough review process not only ensured high-quality code but also demonstrated my commitment to the team's success and fostered trust in the quality and reliability of our shared work.

### Dive Deep
In the ITSI Service Sandbox project, I faced the challenge of rendering service trees that could contain up to 250 services. Full rendering was causing performance issues, so I dove deep into the data to find a solution. I analyzed how the service trees were being processed and realized that by implementing partial rendering, we could optimize the performance without sacrificing functionality. I fine-tuned the rendering logic to load only the visible parts of the tree first, allowing for smoother navigation and a better user experience. This deep dive into the rendering process significantly improved the system's responsiveness, making it more scalable for complex service structures.

### Have Backbone; Disagree and Commit
In our Service Sandbox project, I proposed adding a service lister on the Service pages to clearly indicate which services were created using the sandbox. This would help users differentiate between sandbox and production services at a glance. Initially, the team was hesitant, thinking it might clutter the interface and confuse users. I understood their concerns but believed this feature would add significant value by making it easier to manage and identify services.

To address their concerns, I designed two versions: one with the service lister and one without. I then conducted usability tests with actual users, demonstrating how the lister made navigation and service management more intuitive. The results showed that users found the service lister helpful and appreciated the added clarity. With this data in hand, I convinced the team to implement the feature, ensuring it was well-integrated and user-friendly.

### Deliver Results
We were nearing the General Availability (GA) release of the Service Sandbox, but as we gathered feedback from users, several additional feature requests emerged. Users wanted the ability to view service health scores within the sandbox, and many requested an option to revert or reset the sandbox environment easily.

These new suggestions were critical because they addressed real user needs and would greatly enhance the overall usability of the platform. Despite the tight timeline, I prioritized these features, working closely with the team to quickly design and implement them. We conducted rigorous testing to ensure that these additions didn't introduce new issues and that they integrated seamlessly with the existing functionality.

By focusing on delivering these key features before the GA release, we not only met our deadlines but also launched a product that was more aligned with user expectations, ultimately leading to greater customer satisfaction and adoption.

### Success and Scale Bring Broad Responsibility
I was working on improving real-time features for our Service Sandbox platform and proposed integrating socket.io to handle concurrent users more effectively. However, I quickly realized that our codebase wasn’t equipped to support this integration, and it hadn’t been tested extensively. Additionally, the number of users facing concurrency issues was relatively small, making it a tough sell for immediate implementation.

Instead of pushing forward with socket.io, I decided to implement a locking mechanism to manage concurrent access more reliably. This approach was more compatible with our existing infrastructure and addressed the immediate needs without requiring extensive changes. I also collected user feedback to ensure we prioritized the most pressing concerns. To avoid similar issues in the future, I now conduct thorough feasibility assessments before suggesting major changes, ensuring they align with both our technical capabilities and user needs.


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
Problem Statement: Design a rate limiter to control the number of requests a client can make to a service within a specific time frame.

Requirements:

Types of Rate Limiting: Fixed window, sliding window, token bucket, or leaky bucket.
Granularity: Rate limiting per IP, user, API key, or globally.
Timeframe: Requests allowed per second, minute, hour, or day.
Actions on Limit Exceeding: Block, throttle, or delay requests.
Scalability: Should handle increasing loads across distributed systems.
Persistence: Should rate limits reset periodically or persist across time?
Performance: Should have minimal impact on the overall system latency.
Clarifying Questions:

What is the expected traffic load?
Should it be implemented at the API gateway level or within specific microservices?
Is it acceptable to have a small margin of error in request counting?
What type of storage system will be used (e.g., Redis, in-memory, database)?

### 2 - Propose high-level design and get buy-in: 10 - 15 minutes
**Functional Requirements:**
1. Limit the number of requests an entity can send to an API within a time window, e.g., 15 requests per second.
2. The APIs are accessible through a cluster, so the rate limit should be considered across different servers. The user should get an error message whenever the defined threshold is crossed within a single server or across a combination of servers.
**Non-Functional Requirements:**
1. The system should be highly available. The rate limiter should always work since it protects our service from external attacks.
2. Our rate limiter should not introduce substantial latencies affecting the user experience.

Rate Limiting is a process that is used to define the rate and speed at which consumers can access APIs. Throttling is the process of controlling the usage of the APIs by customers during a given period. Throttling can be defined at the application level and/or API level. **When a throttle limit is crossed, the server returns HTTP status “429 - Too many requests".**

Here are the three famous throttling types that are used by different services: 
**Hard Throttling:** The number of API requests cannot exceed the throttle limit.
**Soft Throttling:** In this type, we can set the API request limit to exceed a certain percentage. For example, if we have rate-limit of 100 messages a minute and 10% exceed-limit, our rate limiter will allow up to 110 messages per minute.
**Elastic or Dynamic Throttling:** Under Elastic throttling, the number of requests can go beyond the threshold if the system has some resources available. For example, if a user is allowed only 100 messages a minute, we can let the user send more than 100 messages a minute when there are free resources available in the system.


### 3 - Design deep dive: 10 - 25 minutes

![Screenshot 2024-08-06 at 10 28 44 PM](https://github.com/user-attachments/assets/54ae22fc-bee1-4580-b5f6-57763391ddce)

#### 1. Fixed Window Algorithm
Overview:

The fixed window algorithm divides time into fixed intervals (e.g., every minute) and counts the number of requests within each interval. If the number of requests exceeds the allowed limit within a window, subsequent requests are blocked until the next window starts.
Implementation:

For each client (IP, user, API key), maintain a counter and a timestamp of the current window.
When a request arrives:
Check if the current time is within the same window.
If yes, increment the counter.
If the counter exceeds the limit, block the request.
If the current time is outside the window, reset the counter and timestamp.
Trade-offs:

Pros: Simple to implement, lightweight.

Cons: Can cause burst traffic at the boundary of windows, leading to potential overloading.

Use Case: Suitable for scenarios with low to moderate traffic where strict request control isn't critical.

#### 2. Sliding Window Log Algorithm
Overview:

The sliding window log algorithm maintains a log of all incoming requests and only considers those within a specific sliding window (e.g., last 60 seconds) to determine the rate.
Implementation:

For each client, maintain a list (or queue) of timestamps for each request.
When a request arrives:
Remove timestamps that are outside the sliding window.
Check the size of the remaining list.
If the size exceeds the limit, block the request.
Otherwise, add the current timestamp to the list and proceed.
Trade-offs:

Pros: Smooths out the traffic, no burst at window boundaries.

Cons: Higher memory usage due to storing all timestamps; more complex due to dynamic checking.

Use Case: Suitable for environments where request patterns are bursty and require more even distribution over time.

#### 3. Sliding Window Counter Algorithm
Overview:

A variation of the sliding window approach, this algorithm divides time into multiple smaller segments within the sliding window (e.g., 10 seconds in a 60-second window). It keeps track of request counts in each segment, allowing more granular control over the rate.
Implementation:

For each client, maintain counters for each time segment within the sliding window.
When a request arrives:
Determine which segment the current time falls into.
Add up the counts of the segments that fall within the sliding window.
If the sum exceeds the limit, block the request.
Update the current segment's counter.
Trade-offs:

Pros: Provides more accurate rate limiting compared to fixed window.

Cons: Requires maintaining multiple counters; may need adjustments for different time granularities.

Use Case: Useful for scenarios where a more accurate distribution of requests over time is needed, balancing between fixed and sliding windows.

#### 4. Token Bucket Algorithm
Overview:

The token bucket algorithm controls the flow of requests by using tokens. A bucket holds tokens, and each incoming request consumes a token. Tokens are replenished at a steady rate. If the bucket is empty, requests are either throttled or blocked.
Implementation:

For each client, maintain a counter for tokens and a timestamp for the last refill.
When a request arrives:
Calculate the number of tokens to add based on the time elapsed since the last refill.
Add tokens to the bucket, ensuring it doesn’t exceed the bucket capacity.
If there are enough tokens, proceed with the request and decrement the token count.
If not, block or queue the request.
Trade-offs:

Pros: Can handle burst traffic; maintains steady request flow.

Cons: Slightly more complex to implement; needs careful configuration of token refill rate and bucket size.

Use Case: Ideal for APIs that need to handle bursty traffic followed by steady processing.

#### 5. Leaky Bucket Algorithm
Overview:

The leaky bucket algorithm is similar to token bucket but with a twist: it processes requests at a constant rate. The bucket leaks tokens at a steady rate, and any excess requests are queued. If the queue is full, new requests are dropped.
Implementation:

For each client, maintain a queue for incoming requests.
When a request arrives:
If the bucket has space, add the request to the queue.
The queue processes requests at a fixed rate, "leaking" them out of the system.
If the queue is full, drop or reject new requests.
Trade-offs:

Pros: Smooths out burst traffic; consistent processing rate.
Cons: May introduce latency for legitimate requests during high traffic; requires careful management of queue size.
Use Case: Best for systems where consistent processing rates are critical, and the system can’t handle bursty loads.

Data Storage Considerations
**In-Memory Storage (e.g., Redis):**

Pros: Fast access, supports TTL (Time to Live) for automatic counter resets, good for distributed systems.

Cons: Requires additional infrastructure, potential issues with data consistency across distributed instances.

**Local Cache:**

Pros: Simpler to implement for single-instance applications, lower latency.

Cons: Not suitable for distributed environments; limits scalability.
Scalability and Consistency

**Sharding:**

Distribute clients across multiple nodes or shards to balance the load.
Use consistent hashing to ensure that each client's rate limit is managed by a specific shard.

**Consistency Models:**

Eventual Consistency: Accepts some delay in propagating the rate limit status across distributed systems, trading off consistency for performance.
Strong Consistency: Ensures that rate limits are uniformly enforced across all nodes, but may introduce latency.
Failover and Fault Tolerance
Redundancy:

Use replica nodes or clusters to ensure availability even if one node fails.
Implement fallback mechanisms if the primary rate-limiting store is unavailable.
Graceful Degradation:

If the rate-limiting system is down, allow requests to go through but monitor the rate closely to avoid overwhelming the service.

  
### 4 -  Wrap: 3 - 5 minutes

IP-Based Throttling: Controls requests per IP, but can cause issues in shared environments (e.g., internet cafes) and is vulnerable to memory exhaustion from IPv6 address spoofing.

Token-Based Throttling: Limits API requests after user authentication, but can be problematic for login APIs, where incorrect attempts could lock out legitimate users.

Hybrid Approach: Combines both IP and user-based rate limiting to mitigate individual weaknesses, though it increases memory and storage requirements.



# OOD questions
## Library Management System

```javascript
// Book Class
class Book {
    constructor(id, title, author, available = true) {
        this.id = id;
        this.title = title;
        this.author = author;
        this.available = available;
    }
    checkOut() { this.available = !this.available; return !this.available; }
    returnBook() { this.available = true; }
}

// Member Class
class Member {
    constructor(id, name) {
        this.id = id;
        this.name = name;
        this.borrowedBooks = [];
    }
    borrowBook(book) {
        if (book.checkOut()) {
            this.borrowedBooks.push(book);
            return true;
        }
        return false;
    }
    returnBook(book) {
        book.returnBook();
        this.borrowedBooks = this.borrowedBooks.filter(b => b.id !== book.id);
    }
}

// Library Class
class Library {
    constructor() {
        this.books = [];
        this.members = [];
    }
    addBook(book) { this.books.push(book); }
    removeBook(bookId) { this.books = this.books.filter(b => b.id !== bookId); }
    addMember(member) { this.members.push(member); }
    findBookById(bookId) { return this.books.find(b => b.id === bookId); }
    findMemberById(memberId) { return this.members.find(m => m.id === memberId); }
}

// Transaction Class
class Transaction {
    static checkOutBook(member, book) {
        return member.borrowBook(book);
    }
    static returnBook(member, book) {
        member.returnBook(book);
    }
}

// Example Usage
const library = new Library();
const book1 = new Book(1, '1984', 'George Orwell');
const book2 = new Book(2, 'To Kill a Mockingbird', 'Harper Lee');
library.addBook(book1);
library.addBook(book2);

const member = new Member(1, 'John Doe');
library.addMember(member);

console.log(Transaction.checkOutBook(member, book1)); // true
console.log(member.borrowedBooks); // [Book { id: 1, title: '1984', author: 'George Orwell', available: false }]
console.log(Transaction.checkOutBook(member, book2)); // true

Transaction.returnBook(member, book1);
console.log(member.borrowedBooks); // [Book { id: 2, title: 'To Kill a Mockingbird', author: 'Harper Lee', available: false }]
```

## Design Online Stock Brokerage System

```javascript
// Class Definitions
class User {
    constructor(userId, name, email) {
        this.userId = userId;
        this.name = name;
        this.email = email;
        this.accounts = [];
    }

    addAccount(account) {
        this.accounts.push(account);
    }
}

class Account {
    constructor(accountId, userId, balance) {
        this.accountId = accountId;
        this.userId = userId;
        this.balance = balance;
        this.holdings = {};
    }

    addHolding(stock, quantity) {
        this.holdings[stock.ticker] = (this.holdings[stock.ticker] || 0) + quantity;
    }

    updateBalance(amount) {
        this.balance += amount;
    }
}

class Stock {
    constructor(ticker, price) {
        this.ticker = ticker;
        this.price = price;
    }

    updatePrice(newPrice) {
        this.price = newPrice;
    }
}

class Order {
    constructor(orderId, userId, stock, quantity, price, type) {
        this.orderId = orderId;
        this.userId = userId;
        this.stock = stock;
        this.quantity = quantity;
        this.price = price;
        this.type = type; // 'Buy' or 'Sell'
        this.status = 'Pending';
    }

    executeOrder(account) {
        if (this.type === 'Buy') {
            if (account.balance >= this.quantity * this.price) {
                account.updateBalance(-this.quantity * this.price);
                account.addHolding(this.stock, this.quantity);
                this.status = 'Executed';
            } else {
                this.status = 'Failed - Insufficient Funds';
            }
        } else if (this.type === 'Sell') {
            if (account.holdings[this.stock.ticker] >= this.quantity) {
                account.updateBalance(this.quantity * this.price);
                account.addHolding(this.stock, -this.quantity);
                this.status = 'Executed';
            } else {
                this.status = 'Failed - Insufficient Holdings';
            }
        }
    }
}

// Example Usage
const user = new User(1, 'Alice', 'alice@example.com');
const account = new Account(101, 1, 10000);
const stock = new Stock('AAPL', 150);
user.addAccount(account);

const order1 = new Order(1, 1, stock, 10, 150, 'Buy');
order1.executeOrder(account);

console.log(`Order Status: ${order1.status}`);
console.log(`Account Balance: $${account.balance}`);
console.log(`Account Holdings: `, account.holdings);
```

