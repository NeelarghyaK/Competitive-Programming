```cpp
#include <bits/stdc++.h>
// #include <ext/pb_ds/assoc_container.hpp>
// #include <ext/pb_ds/tree_policy.hpp>
#include <cstdio>
#define ll long long
#define ub upper_bound  // last occurrence
#define lb lower_bound  // first occurrence
#define mod 1000000007
#define endl '\n'
#define debug(x) cout<< #x<< " "<< x<< endl;

using namespace std;

// using namespace __gnu_pbds;
// typedef tree<int, null_type, less<int>, rb_tree_tag, tree_order_statistics_node_update> pbds;
 
// inline int mul(int x,int y){    ll z = 1ll; z=z*x*y;   z%=mod; return (int)z; }
// inline int add(int x,int y){    ll z = 0ll; z=z+x+y;   z%=mod; return (int)z; }
// inline int sub(int x,int y){    ll z = 0ll;   z=x+mod-y; z%=mod; return (int)z; }

// inline pair<ll,ll> operator+ (const pair<ll,ll> &a, const pair<ll,ll> &b) {
//     pair<ll,ll> temp; 
//     temp.first = a.first + b.first;
//     temp.second = a.second + b.second; 
//     return temp; 
// }
// inline pair<ll,ll> operator- (const pair<ll,ll> &a, const pair<ll,ll> &b) {
//     pair<ll,ll> temp; 
//     temp.first = a.first - b.first;
//     temp.second = a.second - b.second; 
//     return temp; 
// }
 
// struct grp {
//     ll fi;
//     ll sec;
// };
 
// ll binpow(ll a, ll b) {
//     ll result = 1;
//     while (b > 0) {
//         if (b & 1)
//             result *= a;
//         a *= a;
//         a %= mod;
//         b /= 2;
//         result %= mod;
//     }
//     return result;
// }
// // add %mod to prevent overflow
// int inv(int x) {
//     return binpow(x, mod - 2); // use the inverse as normal multiplication
// }
 
// bool comp(struct grp a, struct grp b) {
//     return (b.fi > a.fi);
// }
// // for asccending order
// struct grp arr[1005];
// int query(int i, int n, vector<ll> &fen){
//     int ans = 0;
//     for (;i>0;i-=i&-i) ans += fen[i];
//     return ans;
// }
// void update(int i,int val, int n, vector<ll> &fen){
//     for(;i<=n;i+=i&-i) fen[i] += val;
// }
                
// void clean(int i, int n, vector<ll> &fen){ // This step is important for multiple test case. You clean only things you touched avoiding TLE
//     for(;i<=n;i+=i&-i) fen[i]=0;
// } 

int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    // freopen("Input.txt", "r", stdin);
    // freopen("Output.txt", "w", stdout);
    ll t;  cin >> t;
    while (t--){
        
    } 
    return 0;
}
```
