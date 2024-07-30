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


//CAP Thearem

In a distrubuted system, you can only have 2 out of 3
1.  Consistancy
2. Availability
3. Partition Tolerance


