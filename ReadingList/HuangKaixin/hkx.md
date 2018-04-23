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

### Title 2

#### Summary

#### Strength

#### Weakness/Thought

## [2018 Former] Week 10

[Refer to Week 9]

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
