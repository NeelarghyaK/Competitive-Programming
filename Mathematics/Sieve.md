Problem link: https://codeforces.com/contest/1766/submission/236803250

This sieve finds out the least prime factor for all i from 2 to N

O(N(log(logN)))

```cpp

const int N=1e7+1;
vector<ll> lpf(N);
void prime(){
    for(ll i=2;i<N;i++){
        if(lpf[i]) continue;
        lpf[i]=i;
        for(ll j=i*i;j<N;j+=i){
            if(lpf[j]==0)
            lpf[j]=i;
        }
    }
}

```
