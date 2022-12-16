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
# Number of connected components

https://cses.fi/paste/ba4286c414fbddb14df5d8/

# Checking cyclicity of graph
If we find a node that is already visited but it is not the parent of the current node, then there is a cycle.
CSES:Round trip
https://ideone.com/eH95Cc












  

