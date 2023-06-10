
// DSU w/o Rank Compression and using randomized Union + Path Compression

```cpp
const int MAXN = 1005;
int par[MAXN], members[MAXN];
 
void init(){
	for (int i=1;i<=n;i++){
		par[i] = i;
		members[i] = 1; 
	}
}
 
int root(int u){
	if(par[u]==u) return u;
	return par[u] = root(par[u]);	
}
 
void unite(int u,int v){
	if(rand()&1) swap(u,v);
	par[root(u)] = v; 
	members[root(v)] += members[root(u)];
}
```
