** Traversal using DFS **

```cpp

struct Tree{
  string value;
  Tree *left;
  Tree *right;
}

void traversal(Tree *tree){
  if(tree==NULL) return;
  //use tree-> for Pre-order traversal (current-left-right)
  traversal(tree->left);
  //use tree-> for Post-order traversal (left-current-right)
  traversal(tree->right);
  //use tree-> for In-order traversal (left-right-current)
}

```
# DFS using adjacency list for tree

```cpp
void dfs(int u=1,int p=-1){
//use for top down
  for (int child:adj[u]){
     if(child==p) continue;
     dfs(child,u);
  }
  //use for bottom up
}

```
# DFS using adjacency list for graph
```cpp
 vector<vector<int>> adj;
 int n;
 vector<bool> visited;
 void dfs(int v){
   visited[v]=true;
   for(int u:adj[v]){
     if(!visited[u]) 
       dfs(u);
   }
}

void main(){
  for(int i=0;i<n;i++){ // n= no of nodes
    if(!visited[i])
      dfs(i);
  }
} 
  
```
Time Complexity=O(V+E)

Space complexity=O(V) 
# Number of connected components

https://cses.fi/paste/ba4286c414fbddb14df5d8/

# Checking cyclicity of graph
If we find a node that is already visited but it is not the parent of the current node, then there is a cycle.
CSES:Round trip
https://ideone.com/eH95Cc
# BFS on a graph
```cpp


int n; // number of nodes
int root; // root vertex

queue<int> q;
vector<bool> visited(n);
vector<int> level(n), parent(n);

q.push(root);
visited[root] = true;
parent[root] = -1;
while (!q.empty()) {
    int v = q.front();
    q.pop();
    for (int u : adj[v]) {
        if (!visited[u]) {
            visited[u] = true;
            q.push(u);
            level[u] = level[v] + 1;
            parent[u] = v;
        }
    }
}


```
Time Complexity=O(V+E)
# Shortest Path using bfs

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
# Topological Sorting (just use dfs and insert values in ans from leaves to root)
```cpp
int n; // number of vertices
vector<vector<int>> adj; // adjacency list of graph
vector<bool> visited;
vector<int> ans;

void dfs(int v) {
    visited[v] = true;
    for (int u : adj[v]) {
        if (!visited[u])
            dfs(u);
    }
    ans.push_back(v);
}

void topological_sort() {
    visited.assign(n, false);
    ans.clear();
    for (int i = 0; i < n; ++i) {
        if (!visited[i])
            dfs(i);
    }
    reverse(ans.begin(), ans.end());
}
```
# Dijkstra algorithm for shortest path using priority queue
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
# Bellman Ford algorithm for shortest path
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

Space Complexity:O(V)

# Floyd Warshall Algorithm


    
















  

