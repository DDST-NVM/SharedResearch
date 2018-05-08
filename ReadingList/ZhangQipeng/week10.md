# Readings of ZhangQipeng

## [2018 Former] Week 10

### Distributed Shared Persistent Memory (Yizhou Shan, Yiying Zhang)

####Summary
The research focus on the application of NVM in distributed, datacenter environments. In the paper, Distributed Shared Persistent Memory(DSPM) and Hotpot are introduced. 
1. DSPM incorporates distributed memory and storage in one layer to eliminate data marshaling and unmarshaling. It provides persistent naming and data reliability.
2. Hotpot exposes a global virtual memory address space to each user application and provides a new persistent naming mechanism.
3. Hotpot two data reliability ideas: 
   Intergrate distributed memory caching and data replication by imposing morphable states on PM pages.
   Define data commit points to specify making what data persistent.
4. Type of nodes
   ON: owner node. maintains data and metadata of chunk
   DN: data node. fetch data from ON
   CN: commit node.
   ON serves both page read and data commit requests belonging to the chunk it owns.
5. Define different conditions of crash, including node, PM, time, provide corresponding actions for recovery.

####Strength
1. Support distributed, datacenter environment.
2. Provides data reliability and high availability that Octopus does not provide.
3. Access data with memory instructions and make data durable explicitly.
4. Design clear data orgnization and management strategy.
5. Apply MongoDB on existing filesystems to compare the performance.

####Thought