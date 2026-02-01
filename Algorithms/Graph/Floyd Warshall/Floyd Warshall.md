# Floyd Warshall Algorithm
- It is used to find shortest paths between all nodes
- It works for both directed and un-directed edges graph and also for graphs with both positive and negative edges
## Internal working
- If the shortest path exist from i to j through intermediate node k, then path from i to k and j to k, will also be the shortest
- This iterative approach ensures that by the time k is considered,all shortest path using vertices 0 to k-1 is already computed
### Time Complexity
- `O(V^3)`, V is vertices, three nested loop each of size V
### Space Complexity
- `O(1)`, same adjacency matrix is returned after updating short distances through each intermediate node k
### Code
```
// Solves the all-pairs shortest path
// problem using Floyd Warshall algorithm
function floydWarshall(dist)
{
    let V = dist.length;

    // Add all vertices one by one to
    // the set of intermediate vertices.
    for (let k = 0; k < V; k++) {

        // Pick all vertices as source one by one
        for (let i = 0; i < V; i++) {

            // Pick all vertices as destination
            // for the above picked source
            for (let j = 0; j < V; j++) {

                // shortest path from
                // i to j
                if (dist[i][k] != INF && dist[k][j] != INF) {
                    dist[i][j] = Math.min(dist[i][j], dist[i][k] + dist[k][j]);
                }
            }
        }
    }
}

let INF = 100000000;

// Driver Code
let dist = [
    [0, 4, INF, 5, INF], 
    [INF, 0, 1, INF, 6],
    [2, INF, 0, 3, INF],
    [INF, INF, 1, 0, 2],
    [1, INF, INF, 4, 0]
];

floydWarshall(dist);

for (let i = 0; i < dist.length; i++) {
    console.log(dist[i].join(" "));
}
``` 
## Real World Applications
- In networking to find shortest distances between nodes, which is know as network routing
- To find shortest distances between airports
- In geographic applications, finding shortest distances between locations by analyzing road networks.
### Sample problems
- [2976. Minimum Cost to Convert String I](https://leetcode.com/problems/minimum-cost-to-convert-string-i/solutions/5543985/very-easy-solution-with-explanation-by-a-gnoy/)

### References
- [Floyd Warshall Algorithm](https://www.geeksforgeeks.org/dsa/floyd-warshall-algorithm-dp-16/)