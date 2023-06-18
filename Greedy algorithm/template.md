
#include <vector>
#include <algorithm>
#include <string>
#include <climits>
#include <stack>
#include <queue>
#include <map>
#include <cmath>
#include <iostream>
#include <unordered_map>
#include <cstring>
#include <iomanip>
#include <array>
#include <set>
#include <iterator>
#define ll long long
#define ub upper_bound 
#define lb lower_bound  
#define mod 1000000007
#define endl '\n'
#define debug(x) cout<< #x<< " "<< x<< endl;

using namespace std;
// class Compare {
// public:
//     bool operator()(pair<pair<ll,ll>,ll> below, pair<pair<ll,ll>,ll> above)
//     {
//         if (below.first.second < above.first.second) { // Descending order
//             return true;
//         }
//         return false;
//     }
// };// Comparator for priority queue

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

int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    ll t;  cin >> t;
    while (t--) {
        ll n, m; cin>> n>> m;
        vector<pair<ll,ll>> v(n);
        pair<ll,ll> p1, p2;
        ll x,y; 
        for(int i=0;i<n;i++){
            cin>> v[i].first>> v[i].second;
            if(v[i].first> v[x].first) 
        }



    }
    return 0;
}
