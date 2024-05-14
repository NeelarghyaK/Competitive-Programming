https://codeforces.com/contest/1902/submission/235715242
```cpp
int nxt[1000005][28]={0};// nxt[i][j] gives the node value if node i is followed by character j
// int rep[1000005][28]={0}; // repetition
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

void cleartrie(){
    for(ll i=0;i<1e6+1;i++){
        for(ll j=0;j<26;j++){
            nxt[i][j]=0;
            rep[i][j]=0;
        }
    }
}
```
