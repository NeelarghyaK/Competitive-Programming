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

vector<ll> par(100005, 1);
vector<ll> dijkstra(ll V, vector<vector<pair<ll,ll>>> adj, ll S){//adjacency list contains the vertices that are connected along with the weight
    priority_queue<pair<ll, ll>, vector<pair<ll, ll>>, greater<pair<ll, ll>>> pq;
    vector<ll> distTo(V, 1e18);// set every distance to infinity
    distTo[S] = 0;
    pq.push({0, S});
    while (!pq.empty()){
        ll node = pq.top().second;
        ll dis = pq.top().first;
        pq.pop();
	if(distTo[node] < dis) continue;
        for (auto it : adj[node]){
            ll v = it.first;
            ll w = it.second;
            if (dis + w < distTo[v]){
                par[v]=node;
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

```cpp
for (int k = 0; k < n; ++k) {
    for (int i = 0; i < n; ++i) {
        for (int j = 0; j < n; ++j) {
            if (d[i][k] < INF && d[k][j] < INF)
                d[i][j] = min(d[i][j], d[i][k] + d[k][j]); 
        }
    }
}
```
