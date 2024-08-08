# Scalability

Scalability is the property of a system to handle a growing amount of load by adding resources to the system.

A system that can continuously evolve to support a growing amount of work is scalable.

We will explore different ways a system can grow and common ways to make a system scalable.

### How can a System Grow?

1.  Growth in user Base
    More users started using the system, leading to increased number of requests.

2.  Growth in Features
    More feature were introduced to expand the system's capabilities.

3.  Growth in Data Volume.
    Growth in the amount of data the system stores and manages due to user activity or logging.

4.  Growth in Data Volume
    Growth in the amount of data the system stores and manages due to user activity or logging

5.  Growth in complexity
    The system's Architecture evolves to accomodate new features, scale or integrations, resulting in additional components and dependencies.

6.  Growth in Geographic Reach
    The system is expanded to serve userd in new regions or countries.


### How to Scale a system?

Here are 10 common ways to make a system scalable.

1.  Vertical Scaling(Scaleup)
    This means adding more power to your existsing machines by upgrading server with more RAM, Faster CPU's additional storage. It's good approach for simpler architectures but has limitations in how far you can go.

2.  Horizontal Scaling(scale out)
    Adding more machines to your system to spread the workload across multiple server it's often considered the most effective way to scale for large systems.
    ```
    Netflix uses horizontal scaling for its streaming service, adding more servers to their clusters to handle the growing number of users and data traffic.
    ```
3.  Load Balancing
    Load Balancing is the process of Distributing traffic accros multiple servers to ensure no single server becomes overwhelmed.
    ```
    Google employs load balancing extensively across its global infrastructure to distribute search queries and traffic evenly across its massive server farms.
    ```
4.  Caching
    Store frequently accessed data in-memory to reduce the load on the server or database. Implementation caching can dramatically improve response times.
    ```
    Reddit uses caching to store frequently accessed content like hot posts and comments so that they can be served quickly without querying the database each time
    ```
5.  Content Delivery Networks(CDN's)
    Distribute static asstes closer to the users, it will reduce the latency and result in faster load times.

    ```
    Cloudflare provides CDN services, speeding up website access for users worldwide by caching content in servers located close to users.
    ```
6.  Partitioning
    Split data or functionality across multiple nodes / servers to distribute workload avoid bottlenecks.
    ```
    Amazon DynamoDB uses partitioning to distribute data and traffic for its NoSQL database service across many servers, ensuring fast performance and scalability.
    ```

7.  Asynchronous communication
    Defer long- running or non-criticle tasks to background queues or message brokers. This ensures your main application remains responsive to users.
    ```
    Slack uses asynchronous communication for messaging. When a message is sent, the sender's interface doesn't freeze; it continues to be responsive while the message is processed and delivered in the background.
    ```

8.  Microservices Architecture
    Break Down your applicaion into smaller, independent services the can be scaled independently. This imporves resilience and allows teams to work on specific components in parallel
    ```
    Uber has evolved its architecture into microservices to handle different functions like billing, notifications, and ride matching independently, allowing for efficient scaling and rapid development.
    ```

9.  Auto-Scaling
    Automatically adjust the number of active servers based on the current load. This ensures that the system can handle spikes in traffic without manual intervention.
    ```
    AWS Auto Scaling monitors applications and automatically adjusts capacity to maintain steady, predictable performance at the lowest possible cost.
    ```
10. Multi-region Deployment
    Deploy the application in multiple data centers or cloud tor educe latency and improve redundancy.
    ```
    Example: Spotify uses multi-region deployments to ensure their music streaming service remains highly available and responsive to users all over the world, regardless of where they are located.
    ```