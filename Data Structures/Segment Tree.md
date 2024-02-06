Submission Link: https://codeforces.com/contest/380/submission/237276013
Standard sum problem : https://codeforces.com/edu/course/2/lesson/4/1/practice/contest/273169/submission/245027097
```cpp
/* 1-based segment tree template */
 
const int ST_MAX = 1e6+5;
 
int _array[ST_MAX];
 
struct Node{
    // 0. add node variables and constructors according to needs
    int op, val, cl; 
    Node () { val=0; op=0; cl=0; }
    Node (int var) { val=0; op=max(0, var); cl=max(0, -var); }
    Node (int val, int op, int cl) { val=val; op=op; cl=cl;  }
};
 
/*
    int var
*/
 
int _n; // $ set _n 
class SegmentTree {
    public: 
        vector<Node> _t; 
    public:
        SegmentTree () {
            _t=vector<Node>(_n*4);  
        }
 
        Node combine (Node lc, Node rc){// Needs to be changed
            Node res;
            res.val=lc.val+rc.val+min(lc.op, rc.cl);
            res.op=lc.op+rc.op-min(lc.op, rc.cl);
            res.cl=lc.cl+rc.cl-min(lc.op, rc.cl);
            return res;
        }
 
        Node query (const int& l, const int& r, int v=1, int tl=1, int tr=_n){
            if (r<tl||l>tr) return Node (); 
            if (tl>=l && tr<=r) return _t[v]; 
            return combine (query(l, r, v<<1, tl, tm), 
                query(l, r, v<<1|1, tm+1, tr));
        }
 
        void build (int v=1, int tl=1, int tr=_n){
            if (tl==tr) _t[v] = Node(_array[tl]); 
            else {
                build (v<<1, tl, tm);
                build (v<<1|1, tm+1, tr); 
                _t[v] = combine (_t[v<<1], _t[v<<1|1]); 
            }
        }
 
        // point update 
        void update (const int& pos, const int& val, int v=1, int tl=1, int tr=_n){
            if (tl==tr) _t[v] = Node(val);  
            else {
                if (pos <= tm) update (pos, val, v<<1, tl, tm);
                else update (pos, val, v<<1|1, tm+1, tr); 
                _t[v] = combine (_t[v<<1], _t[v<<1|1]);  
            }
        }
};
```
