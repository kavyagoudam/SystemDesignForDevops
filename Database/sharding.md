# Database Sharding 

1 What is Sharding? 
Sharding is an architectural pattern that addresses the challenges of managing and querying large datasets in databases. It involves splitting a large database into smaller, more manageable parts called shards. 
 
The benefits of sharding are scalability, improved performance, and better availability. 

2 Types of Sharding 
Three main sharding strategies are as follows: 
 
- Range-based Sharding: Split database rows based on a range of values. 
- Key/Hash-based Sharding: Assign a particular key to a shard using a hash function 
- Directory-based Sharding: Relies on a lookup table to determine the distribution of records across shards.

3 Selecting the Shard Key 
- Choosing an appropriate shard key is crucial for an effective sharding strategy. Designers should consider several factors such as: 
- Cardinality: Number of possible values that a shard key can have. It’s better to have a shard key with high cardinality. 
- Frequency: Represents how often a particular shard key value appears. Higher frequency can result in hotspots. 
- Monotonic Change: Refers to the shard key value increasing or decreasing over time. Monotonic increases or decreases can result in unbalanced shards. 

4 Request Routing 
- With sharding, the most critical consideration is determining which query should go to which shard. There are three main approaches: 
- Shard-aware Node: The client can contact any node and the node will serve/redirect the request to the correct shard. 
- Routing Tier: Client requests go to a dedicated routing tier that determines the node responsible for handling the request. 
- Shard-aware Client: Clients are aware of the shard distribution across the nodes. 