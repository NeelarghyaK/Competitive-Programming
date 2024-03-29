### Content: Traversals, Searches, Cyclicity, no of Connected components


**Traversal using DFS**

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
  //use tree-> for In-order traversal (left-right-current)
  traversal(tree->right);
  //use tree-> for Post-order traversal (left-current-right)
}

```
**DFS using adjacency list for tree**

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
**DFS using adjacency list for graph**
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
<br><br>
**Number of connected components**
<br><br>
https://cses.fi/paste/ba4286c414fbddb14df5d8/
<br><br>
**Strongly connected component**
Problem: https://codeforces.com/contest/427/problem/C
Submission: https://codeforces.com/contest/427/submission/225806261

**Checking cyclicity of graph**<br>

If we find a node that is already visited but it is not the parent of the current node, then there is a cycle.
CSES:Round trip
https://ideone.com/eH95Cc
<br><br>
**BFS on a graph**
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
<br>
