# Traversal using DFS

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
















  

