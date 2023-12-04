https://codeforces.com/contest/1902/submission/235715242
```cpp
int nxt[1000005][28]={0};
// int rep[1000005][28]={0};
ll nc=1;
void buildtrie(string str){
    ll parent=1;
    for(auto u: str){
        if(nxt[parent][u-'a']==0){
            nxt[parent][u-'a']=++nc;
        }
        //rep[parent][u-'a']++;
        parent=nxt[parent][u-'a'];
    }
}
```
