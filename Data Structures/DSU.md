
// DSU w/o Rank Compression and using randomized Union + Path Compression

```cpp
void init(ll n, vector<ll> &par, vector<ll> &members){
	for (int i=1;i<=n;i++){
		par[i] = i;
		members[i] = 1; 
	}
}
 
int root(int u, vector<ll> &par){
	if(par[u]==u) return u;
	return par[u] = root(par[u], par);	
}
 
void unite(int u,int v, vector<ll> &members, vector<ll> &par){
	if(rand()&1) swap(u,v);
	members[root(v, par)] += members[root(u, par)];
	par[root(u, par)] = v; 
}
```
Randomized union might not work in case there is no path compression. Refer to Codeforces EDU Pilot Course DSU Practice Problem 3 for this.
