# CMPS 2200 Assignment 4
## Answers

**Name:** Marissa Vagnoni






- **1a.** Since a d-ary heap can have up to d children then the total amount of nodes essentially adds up to d^h, where h is the height. You can calculate the depth by setting a variable, such as n, equal to d^h and taking the log of both sides. This gives us the equation h = log_d * n. Therefore, the maximum depth is O(log_d(n)). 


- **1b.** 
**delete-min:** All d children must be accounted for to find the minimum and the entire height of log_d(n) might also be scanned. Therefore the total work would be O(d*log_d(n)).
**insert:** At each level the new element has to be compared with each parent node which could take the entire height of log_d(n). Therefore, the total work is O(log_d(n)).


- **1c.** delete-min happens once per vertex, so |V| times, and insert happens once per edge relaxtion, so |E| times. Using the work values from the previous questions the new bound can be written as |V| * O(d * log_d|V|) + |E| * O(log_d|V|). 

- **1d.** Since |E| = |V|^ 1 + E then choosing d = |V|^E would make the running time O(|E|). This is because this keeps log_d|V| constant and makes the dominating term |E|. 


- **2a.**
Solving by using formula: APSP(i,j,k) = min(APSP(i,j,k−1), APSP(i,k,k−1) + APSP(k,j,k−1))

k = 0
APSP(0,0,0) = 0 + 0 + 0 = 0
APSP(0,1,0) = 0 + -2 = −2
APSP(0,2,0) = 0 + 2 = 2
APSP(1,0,0) = -2 + 0 = −2
APSP(1,1,0) = -2 + -2 + 0 = −4
APSP(1,2,0) = -2 + 2 = 0
APSP(2,0,0) = 2 + 0 = 2
APSP(2,1,0) = 2 + -2 = 0
APSP(2,2,0) = 2 + 2 = 4

k = 1
Using APSP(0,1,0) = -2, APSP(1,0,0)=−2, APSP(1,1,0) =−4, APSP(1,2,0)=0, and APSP(2,1,0)=0
APSP(0,0,1) = -2 + -2 = −4
APSP(0,1,1) = -2 + -4 = −6
APSP(0,2,1) = -2 + 0 = −2
APSP(1,0,1) = -4 + -2 = −6
APSP(1,1,1) = -4 + -4 = −8
APSP(1,2,1) =-4 + 0 = −4
APSP(2,0,1) = 0 + -2 = −2
APSP(2,1,1) = 0 + -4 = −4
APSP(2,2,1) = 0 + 0 = 0

k = 2
Using APSP(0,2,1)=−2, APSP(1,2,1)=−4, APSP(2,0,1)=−2, APSP(2,1,1)=−4, and APSP(2,2,1)=0
APSP(0,0,2) = -2 + -2 = −4
APSP(0,1,2) = -2 + -4 = −6
APSP(0,2,2) = -2 + 0 = −2
APSP(1,0,2) = -4 + -2 = −6
APSP(1,1,2) = -4 + -4 = −8
APSP(1,2,2) = -4 + 0 = −4
APSP(2,0,2) = 0 + -2 = −2
APSP(2,1,2) = 0 + -4 = −4
APSP(2,2,2) = 0 + 0 = 0

- **2b.** The relationship between APSP(i,j,1) and APSP(i,j,2) is that the mimimum of APSP(i,j,1) and APSP(i,j,1) + APSP(2,j,1) is APSP(i,j,2). Yes, the values from APSP(i,j,2) are created from the results from k = 1 which were computed from k = 0. 


- **2c.** The optimal structure property for APSP(i,j,k) is for it to be the mimimum of APSP(i,j,k-1) and APSP(i,k,k-1) + APSP(k,j,k-1). This is due to the shortest path from i to j using vertices 0,1,..., k is the same as the shortest path using vertices 0,1,..,k-1 or the same as i to k and k to j using vertices 0,1,...,k-1. 

- **2d.** Each subproblem would only be computed from scratch once. The results would be stored for future use. The work is O(|V|^3) since there are three vertices and each subproblem can be solved in constant time.

- **2e.** The work of Johnson's algorithm is O(|V| * |E|log|E|) where as this would be O(|V|^3). If a graph has a lot of edges then the algorithm created would be better but if the graph has few edges Johnson's algorithm would be better since |E| would be small and O(|V||E|log|E|) is smaller than O(|V|^3).



- **3a.** Yes because an MST is always trying to find the shortest path to connect all nodes. To do so, it purposely avoids heavy weighted edges, so even the largest edge that ends up in the MST was as small as it could possibly be in the spanning tree. MST already minimizes the maximum edge weight. 



- **3b.** We can use Prim's algorithm once to get the MST and record total weight.
Prim works by using the light-edge property which chooses the lightest edge that connects a new vertext to the current tree. For the algorithm, first identify all edges that are connected to the tree and an outside vertex. Then, find the second-smallest edge which is what Prim did not take. Then, replace Prim's edge with this chosen edge and continue to re-run Prim until the tree is finished. Then, compute the weight of all the finished trees and return the tree with the smallest total weight that remains larger than the original MST weight. This would be the second-best spanning tree. In this case, we are choosing only one change but keeping the rest of the choices as small as possible, which makes it the closest but still worse than the original MST. 

- **3c.** From the notes, the work of prim is O(|E|log|E|) but we are searching for a new tree up to |V| times so the work of this algorithm would be O(|V| * (|E|log|E|)). 
