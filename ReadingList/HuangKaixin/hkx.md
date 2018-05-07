# Readings of Huang Kaixin

## [2018 Former] Week 9 

### My Own Research - EFLightPM: An Efficient, Friendly and Lightweight Persistent Memory Library


EFLightPM is a user-mode persistent memory library, which integrates persistent memory abstraction, allocation, recycling and recovery.
It exposes easy-to-use APIs to programmers and supports fast persistent memory allocation, recycling with hash-based mechanism.
It reduces the transaction overhead for data consistency by exploting a novel logging mechanism called Write Behind Logging.
We develop EFLightPM on real PM environment, which is called AEP/Apache Pass. We build it on App-Direct Mode for solid data persistence.
We aslo build two big data applications on EFLightPM (A Trajectory Store and a KV-Store).

This work is supposed to be optimzed during May and June. The target conference is ASPLOS/HPCA/PPoPP.

### Towards the Design of Efficient and Consistent Index Structure with Minimal Write Activities for Non-Volatile Memory 

#### Summary

The researchers found that traditional index structures such as B+-Tree may not be appropriate for NVM in terms of the requirements for high-performance and high-endurance.
This paper studies what is the best index structure for NVM-based system and how to design such index structures. They point out that there are a lot of challenges to design NVM-friendly index structures.
First, the write activities on NVM should be minimized, which implies that index structure should be as simple as possible.
Second, the simple structure brings challenges to achieve high-performance data retrieval operations.
Third, data consistency issues should be carefully considered due to partial write and reordered write.
This paper proposes an index structure based on the simplest data structure (i.e., linked list);
to overcome the challenge of performance effect, the researchers design a novel technique by explicitly building up a contiguous virtual address space on the linked list.
Farthermore, this paper devises a novel indexing scheme called VLAB and implements it in a storage engine.
Evaluations are conducted on an NVDIMM workstation using YCSB
workloads and real-world traces. Results show that write activities of the state-of-the-art indexes are 6.98 times more than ours;


#### Strength

- They conduct an in-depth investigation to understand what is the best index structure for NVM and how to design an NVM-friendly index structure.
- They develop a novel technique, called Dual-VA, to organize linked lists using contiguous virtual address spaces, on which they can conduct efficient searches.
- They propose an efficient and consistent index scheme based on Dual-VA list; the scheme can reduce a significant number of NVM writes while achieving high overall performance.
- They implement VLAB in an experimental storage engine and plug it into MySQL for evaluations; comprehensive experiments are conducted using YCSB workloads and real-world traces on an NVDIMM workstations.

#### Weakness/Thought

Although the idea to extract useful index structures for NVM is quite interesting, the key fundamentation of this research is not solid.
The wear-out problem seems to be a slight point in real NVM platform (e.g., AEP developed by Intel).

Besides, data consistency is an important problem to be solved while in this paper, I can't obtain any tricky method for consistency guarantee for proposed index sturcture and indexing scheme.

### Soft Updates Made Simple and Fast on Non-volatile Memory (Mingkai Dong and Haibo Chen)

#### Summary

This work revists Soft-update, which is a metadata update mechanism in traditional disk-oriented file systems, into non-volatile memory with NVM-optimized design.
Soft-update is an intriguing idea that eliminates most synchronous metadata updates through delayed writes and dependency tracking.
Since the logging/journaling persistence procedure is removed from the critical path, SoupFS obtains elevant performace improvement.

#### Strength
- It has a detailed analysis of the complexity of soft updates and the argument that soft updates can be made simple for NVM.
- It gives a detailed review of the update dependencies of filesystems on NVM with a lot of figures and abundant explanation.
- It uses multiple benchmarks to prove the performance advantage of SoupFS, including microbenchmarks (filetest, dirtest) and macrobenchmarks(Filebench, Postmark).

#### Weakness/Thought

Soft-upate is an old method in file systems and the researchers just make the old thing "great" again. The inspiration is: how can I utilize some old "fashions" in persistent memory system design?
I want to exploit hybrid logging in Daisy to minimize the logging overhead in critical path. The concrete methodology is: recognize workload with insert/update to use redo or undo.
We can adaptively choose one logging method with the changing of writing workloads. 

## [2018 Former] Week 10

### A High Performance File System for Non-Volatile Main Memory

### Summary

They revisit current state-of-the-art NVMM-aware file systems and draw a key observation that the slow NVM writes incur the most of performance degrading. 
To remove the write overhead from critical path, they propose a novel NVM-based file system, named HiNFS.
It uses a DRAM write buffer to support lazy-persistent file writes to DRAM, which avoids the slow writes to NVM.
To solve the double write problem, they propose a new consistency mechanism to reduce double writes and inconsistency between DRAM and NVM.

### Strength

- They reveal the problem of the direct access overheads by quantifying the copy overheads of state-of-the-art NVMM-aware file systems on a simulated NVMM device, which shows credible information and motivation.
- They propose an NVMM-aware Write Buffer policy to hide the long write latency of NVMM by buffering the lazy-persistent
file writes in DRAM temporarily.
- They ensure read consistency by using a combination of the DRAM Block Index and Cache-line Bitmap to track the
latest data between DRAM and NVMM.
- They implement HiNFS as a kernel module in Linux kernel 3.11.0 and evaluate it on software NVMM emulators using extensive workloads to enhance the variety of results.

### Weakness

- The basement of this paper is the long write latency of NVM, which may not be a critical problem for current NVM hardwares.
- The key assumption that OS is aware of DRAM space and NVM, which is contradictory with the Intel Apache Pass.
- It only compares itself to two NVM-based file systems? What about comparing to NOVA and ...?
- The overhead of managing DRAM buffer and more complicated consistency mechanism is not discussed much.

### RFP: When RPC is Faster than Server-Bypass with RDMA

#### Summary

In this paper, they introduce two interesting observations about RDMA. 
First, RDMA has asymmetric performance characteristics, which can be used to improve server-reply’s performance. 
Second, the performance of server-bypass is not as good as expected in many cases, because more rounds of RDMA may be needed if the server is totally bypassed.

Based on these two observations, they therefore introduce a new RDMA paradigm called Remote
Fetching Paradigm (RFP). 
It supports the legacy RPC interfaces and hence avoids the need of redesigning application-specific data
structures. With proper parameters, it can achieve even higher IOPS than that of the previous paradigms. We have designed and implemented an in-memory key-value store based on RFP to evaluate its effectiveness.

#### Strength

- They report two key observations about RDMA and its usage paradigms by credible experiments;
- They propose a new RDMA-based RPC paradigm called RFP that provides higher performance but with moderate porting cost; 
- They design and implement an in-memory key-value store to validate the effectiveness of RFP.

#### Thought

- The asymmetry of RDMA is a good challenge and we should also care for this in our project.
- RFP may be directly utilized or with slight modification for better performance.
- Distributed transaction consistency should be introduced when considering RDMA communication.


## [2018 Former] Week 11

## [2018 Former] Week 12 

## [2018 Former] Week 13

## [2018 Former] Week 14

## [2018 Former] Week 15 

## [2018 Former] Week 16

## [2018 Former] Week 17

## [2018 Former] Week 18 

## [2018 Former] Week 19

## [2018 Former] Week 20
