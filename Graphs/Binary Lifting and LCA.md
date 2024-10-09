https://youtu.be/oib-XsjFa-M?si=a-BKxVKtZAKXuRb6
https://youtu.be/dOAxrhAUIhA?si=ibvBJEJzm7PFDU2c
**Code for finding distance between two nodes in a tree**
```cpp
#include <bits/stdc++.h>
#include <cstdio>
#define ll long long
#define popc __builtin_popcountll
#define mod 998244353
#define endl '\n'
#define debug(x) cout<< #x<< " "<< x<< endl;
using namespace std;

const int LOG=25;
const int N=2*1e5+5;

vector<ll> depth(N);
vector<vector<ll>> up(N, vector<ll>(LOG));

void dfs(int u, vector<vector<ll>> &adj, vector<ll> &vis){
    vis[u]++;
    for(auto v: adj[u]){
        if(vis[v]) continue;
        else {
            depth[v]=depth[u]+1;
            up[v][0]=u;
            for(int i=1;i<LOG;i++){
                up[v][i]=up[up[v][i-1]][i-1];
            }
            dfs(v, adj, vis);
        }
    }
}
int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    // freopen("inp4.txt", "r", stdin);
    // freopen("Output.txt", "w", stdout);
    ll t; t=1;
    ll cn=0;
    while(t--){
        ll n, q; cin>> n>> q;
        vector<vector<ll>> adj(n+1);
        vector<ll> vis(n+1);
        for(int i=0;i<n-1;i++){
            ll x, y; cin>> x>> y;
            adj[x].push_back(y);
            adj[y].push_back(x);
        }
        dfs(1, adj, vis);
        while(q--){
            ll x, y; cin>> x>> y;
            ll ans=0;
            if(depth[x]>depth[y]){
                swap(x, y);
            }
            ll diff=depth[y]-depth[x];
            for(int i=LOG-1;i>=0;i--){
                if((diff>>i)&1ll){
                    y=up[y][i];
                }
            }
            ans+=diff;
            if(x==y) cout<< ans<< endl;
            else {

                for(int i=LOG-1;i>=0;i--){
                    if(up[x][i]!=up[y][i]){
                        x=up[x][i];
                        y=up[y][i];
                        ans+=(1ll<<(i+1));
                    }
                }
                ans+=2;
                cout<< ans<< endl;
            }
        }   
    }
    return 0;
}
```
