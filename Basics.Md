System Design involves Figuring Out:
  1.  What are the requirement of the System Design?
  2.  Who are the Users and How many?
  3.  What components do we need in our design?
  4.  How these components should be organised?
  5.  How to make system scalable?
  6.  How to make system reliable>
  7.  How to make the system easy to maintain?

Kay Concepts:
  1.  Scalability
      How will system can handle more users or data without slowing down
      a. Verticle Scaling
      b. Horizontal Scaling
  2.  Performance
      a. Latency
      b. Throughput
  3. Availability
      Your system is doing what its supposed to do even if things go wrong.
      a. Replication
      b. Redundancy
      c. Fail over mechanisms
  4. Consistancy
      All Users see the same data at the same time no matterwhich part of the system they interact with


  5. CAP Thearem
     In a distrubuted system, you can only have 2 out of 3
     1.  Consistancy
     2. Availability
     3. Partition Tolerance
  6. Data storage and retrieval
  7. ACID transation
    A - atomicity
    C - Consistency
    I - Isolation
    D - Durability
 8. Constant Hashing
    Used To spread Data across a group of servers.
 9. Rate limiting
    Control the rate at which clients can make requests to a system
10. networking and communication
11. Security and privacy
    Putting in place method to keep important data safe and stop unwanted access
    Authentication, authorization, ENcryption

Building Blocks of System Design
  1. Application servers
      Computers that handle the business logic and processing required by the application.
  2. Load Balancers
      Distribute incoming requests to different servers to ensure no single server gets overwelmed
  3. DataBases
  4. Caching
  5. Message queues
  6. Storage
  7. Proxy servers
  8. CDN
Books reference
  1. Design data intensive Applications
Common System design interview questions
  1. Design a URL shortening service like TinyUrl
  2. Design a social media platform like twitter / instagram
  3. Design a chat application like whatsup/slack
  4. Design a web crawler
  5. Design a video streeming service like youtube / netflix
  6. Design a e commerce platform like amazon
  7. Design a ride sharing service like uber /lyft
  8. Design a Notification system
  9. Design a Key- value store like redis
  10. Design a scalable logging and monitoring system 

Expectation
  1. Clarify requirement including Functional and non- functional
  2. Estimate the capacity
  3. choose the right database
  4. Design API's and request/responce pattern
  5. sketch out thw high level diagram
  6. Deep dive into key component
  7. Discuss how the system will scale under the load 
  8. Discuss tradeoff
  9. discuss caching
  10. discuss stratergies for handing failures


Reference Github link
1. https://blog.algomaster.io/p/how-to-answer-a-system-design-interview-problem
2. https://github.com/binhnguyennus/awesome-scalability.git
3. https://github.com/donnemartin/system-design-primer.git
4. https://github.com/ashishps1/awesome-system-design-resources.git



