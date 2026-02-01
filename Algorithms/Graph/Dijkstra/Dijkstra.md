# Dijkstra's Algorithm
- It is used to find shortest path from src to all nodes in a weighted undirected graph with no negative edges
## Internal Working
- Once we pop a node from priority queue, we finalize its distance and never consider it again
- Assuming there is no negative edge, if another path exist to the node, it would have to go through nodes with equal or greater curr distances
## Negative Weight
- Suppose total cost to u is finalized
- It may be possible that there is path with less cost through some node v, processed later due to negative weight
- It will nullify the earlier assumption, so it doesn't work with negative weights    
### Time Complexity
- `O(V+E)*logV`, V is vertices, E is edges
- All the vertices in priority queue are rearranged when new vertices or its neighbors are added
### Space Complexity
- `O(V+E)` 
- distance array + priority queue for vertices and its neighbors
### Internal structure
- It will consist of graph created using adjacency list, which will have node-> node,weight for each edge
- It will have min heap which will give next nearest node to source
- It will have dist array to keep track of min distance of each node from source
- It will apply BFS, to find shortest distances for all nodes
### Code
```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.PriorityQueue;

class GFG {

    static ArrayList<Integer> dijkstra(ArrayList<ArrayList<int[]>> adj, int src) {
        int V = adj.size();

        // Min-heap (priority queue) storing pairs of (distance, node)
        PriorityQueue<int[]> pq = new PriorityQueue<>((a, b) -> a[0] - b[0]);

        // Distance array: stores shortest distance from source
        int[] dist = new int[V];
        Arrays.fill(dist, Integer.MAX_VALUE);

        // Distance from source to itself is 0
        dist[src] = 0;
        pq.offer(new int[]{0, src});

        // Process the queue until all reachable vertices are finalized
        while (!pq.isEmpty()) {
            int[] top = pq.poll();
            int d = top[0];
            int u = top[1];

            // If this distance is not the latest shortest one, skip it
            if (d > dist[u])
                continue;

            // Explore all adjacent vertices
            for (int[] p : adj.get(u)) {
                int v = p[0];
                int w = p[1];

                // If we found a shorter path to v through u, update it
                if (dist[u] + w < dist[v]) {
                    dist[v] = dist[u] + w;
                    pq.offer(new int[]{dist[v], v});
                }
            }
        }

        ArrayList<Integer> result = new ArrayList<>();
        for (int d : dist)
            result.add(d);

        // Return the final shortest distances from the source
        return result;
    }
    
    
    static void addEdge(ArrayList<ArrayList<int[]>> adj, int u, int v, int w) {
        adj.get(u).add(new int[]{v, w});
        adj.get(v).add(new int[]{u, w});
    }

    public static void main(String[] args) {
        int V = 5;
        int src = 0;

        // graph creation
        ArrayList<ArrayList<int[]>> adj = new ArrayList<>();
        for (int i = 0; i < V; i++) {
            adj.add(new ArrayList<>());
        }

        addEdge(adj, 0, 1, 4);
        addEdge(adj, 0, 2, 8);
        addEdge(adj, 1, 4, 6);
        addEdge(adj, 1, 2, 3);
        addEdge(adj, 2, 3, 2);
        addEdge(adj, 3, 4, 10);

        ArrayList<Integer> result = dijkstra(adj, src);
        for (int d : result)
            System.out.print(d + " ");
        System.out.println();
    }
}
```
### Sample problems
- [3650. Minimum Cost Path with Edge Reversals](https://github.com/abhineshchandra1234/LeetCode_Solutions_Java/blob/587285c98721e1b5a90089d75b05e11e586f4dc1/leetcode%20solutions/3650.%20Minimum%20Cost%20Path%20with%20Edge%20Reversals/Solution.java#L30)
- [2976. Minimum Cost to Convert String I](https://leetcode.com/problems/minimum-cost-to-convert-string-i/solutions/5543985/very-easy-solution-with-explanation-by-a-gnoy/)

### References
- [Dijkstra's Algorithm](https://www.geeksforgeeks.org/dsa/dijkstras-shortest-path-algorithm-greedy-algo-7/)