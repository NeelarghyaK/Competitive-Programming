**Include files:**
```cpp
#include <ext/pb_ds/assoc_container.hpp>
#include <ext/pb_ds/tree_policy.hpp>
```
```cpp
using namespace __gnu_pbds;
typedef tree<int, null_type, less_equal<int>, rb_tree_tag, tree_order_statistics_node_update> pbds;// declaration // comparator can be greater, less, greater_equal...
```
**Declare pbds in this way:**    pbds A;

**Functions that can be used:**

A.insert(x);

A.erase(x);

Can iterate through A

Finding kth element: *A.find_by_order(k);

Finding number of element smaller than k: A.order_of_key(k);

Lower bound/Upper bound: *A.lower_bound(k);


To store duplicates: use less_equal as comparator... and use the following functions...
``` cpp
bool Exist(pbds &s, int x)
{
    if((s.upper_bound(x))==s.end()) return 0;
    return ((*s.upper_bound(x))==x);
 
}
 
void Erase(pbds &s, int x)
{
    if(Exist(s,x)) s.erase(s.upper_bound(x));
}
```

Source: https://youtu.be/IWyIwLFucU4
