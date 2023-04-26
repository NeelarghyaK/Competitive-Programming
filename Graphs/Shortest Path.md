### Content: Djikstra, Bellman Ford, Floyd Warshall
**Shortest Path using bfs**
```cpp
if (!visited[u]) {
    cout << "No path!";
} else {
    vector<int> path;
    for (int v = u; v != -1; v = parent[v])
        path.push_back(v);
    reverse(path.begin(), path.end());
    cout << "Path: ";
    for (int v : path)
        cout << v << " ";
}

```

**Dijkstra algorithm for shortest path using priority queue**
```cpp

vector<int> dijkstra(int V, vector<vector<int>> adj[], int S){//adjacency list contains the vertices that are connected along with the weight
        priority_queue<pair<int, int>, vector<pair<int, int>>, greater<pair<int, int>>> pq;
        vector<int> distTo(V, INT_MAX);// set every distance to infinity
        distTo[S] = 0;
        pq.push({0, S});
        while (!pq.empty()){
            int node = pq.top().second;
            int dis = pq.top().first;
            pq.pop();
            for (auto it : adj[node]){
                int v = it[0];
                int w = it[1];
                if (dis + w < distTo[v]){
                    distTo[v] = dis + w;
                    pq.push({dis + w, v});
                }
            }
        }
        return distTo;
    }
    
```
Time Complexity:O(Elog(V))

Memory:O(E+V)

Dijkstra's algorithm does not work for negative weights. 
<br><br>
**Bellman Ford algorithm for shortest path**
<br><br>
Doesn't work if graph contains negative cycles.
Works with negative weights unlike Dijkstra.
```cpp
vector<int> bellman_ford(int V, vector<vector<int>>& edges, int S) {
		vector<int> dist(V, 1e8);
		dist[S] = 0;
		for (int i = 0; i < V - 1; i++) {
			for (auto it : edges) {
				int u = it[0];
				int v = it[1];
				int wt = it[2];
				if (dist[u] != 1e8 && dist[u] + wt < dist[v]) {
					dist[v] = dist[u] + wt;
				}
			}
		}
		// Nth relaxation to check negative cycle
		for (auto it : edges) {
			int u = it[0];
			int v = it[1];
			int wt = it[2];
			if (dist[u] != 1e8 && dist[u] + wt < dist[v]) {
				return { -1};
			}
		}


		return dist;
	}
```
Time Complexity:O(V*E)

Space Complexity:O(V)<br>

**Floyd Warshall Algorithm**
