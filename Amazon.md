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




### 2 - Propose high-level design and get buy-in: 10 - 15 minutes



### 3 - Design deep dive: 10 - 25 minutes


  
### 4 -  Wrap: 3 - 5 minutes




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

