https://docs.google.com/document/d/1l4jEJ_977HtiZet7xE-d_xIBjiJ9XDpYccv1bDKTJMk/edit
```cpp
  int query(int i, int n, vector<ll> &fen){
      int ans = 0;
      for (;i>0;i-=i&-i) ans += fen[i];
      return ans;
  }
  void update(int i,int val, int n, vector<ll> &fen){
      for(;i<=n;i+=i&-i) fen[i] += val;
  }
                  
  void clean(int i, int n, vector<ll> &fen){ // This step is important for multiple test case. You clean only things you touched avoiding TLE
      for(;i<=n;i+=i&-i) fen[i]=0;
  }
```
