# C++ STL for Competitive Programming — Quick Reference

Assume `using namespace std;` and `#include <bits/stdc++.h>` unless stated otherwise. These notes focus on syntax you can recall during a contest.

## 1. `set` — Unique elements, sorted

```
set<int> s = {4, 1, 3, 1};  // {1, 3, 4}

s.insert(2);       // O(log n)
s.erase(3);        // O(log n)
s.count(4);        // 0 or 1
s.find(5);         // iterator or s.end()
s.size();
s.empty();
```

Access elements

```
int mn = *s.begin();   // minimum
int mx = *s.rbegin();  // maximum

s.erase(s.begin());    // erase minimum
s.erase(prev(s.end())); // erase maximum
```

Bounds

```
auto it1 = s.lower_bound(x); // first element >= x
auto it2 = s.upper_bound(x); // first element > x

if (it1 != s.end()) cout << *it1;
```

Iteration

```
for (int x : s) cout << x << ' ';

for (auto it = s.begin(); it != s.end(); ++it)
    cout << *it << ' ';
```

Complexity: insertion, deletion, search and bounds are \\(O(\log n)\\).

## 2. `multiset` — Sorted elements, duplicates allowed

```
multiset<int> ms = {2, 2, 3, 5};

ms.insert(2);       // {2, 2, 2, 3, 5}
ms.count(2);        // 3
ms.find(2);         // iterator to one occurrence
```

Important gotcha: erase one vs all

```
ms.erase(2);        // removes ALL occurrences of 2
ms.erase(ms.find(2)); // removes only ONE occurrence
```

Only erase the iterator if it exists:

```
auto it = ms.find(x);
if (it != ms.end()) ms.erase(it);
```

Bounds and minimum/maximum

```
auto it = ms.lower_bound(x); // first >= x
auto jt = ms.upper_bound(x); // first > x

int mn = *ms.begin();
int mx = *ms.rbegin();
```

All standard searches, insertions and deletions are \\(O(\log n)\\). `count(x)` is \\(O(\log n + k)\\), where \\(k\\) is the number of occurrences found.

## 3. `map` — Sorted key-value pairs

```
map<int, int> mp;

mp[5] = 10;
mp[2] = 20;
mp[5]++;             // value becomes 11

cout << mp[5];       // 11
cout << mp[100];     // inserts key 100 with value 0!
```

Avoid accidental insertion

```
if (mp.find(x) != mp.end()) { /* exists */ }

if (mp.count(x)) { /* exists */ }

auto it = mp.find(x);
if (it != mp.end())
    cout << it->first << ' ' << it->second;
```

Use `mp.at(x)` to access an existing key without inserting one; it throws an exception if the key is missing.

Iteration and deletion

```
for (auto &[key, value] : mp)
    cout << key << ' ' << value << '\n';

mp.erase(x);         // erase by key
mp.erase(mp.begin()); // erase first key
mp.size();
```

Keys are traversed in ascending order by default.

Complexity: lookup, insertion and deletion \\(O(\log n)\\).

## 4. `unordered_set` and `unordered_map`

Hash-based alternatives without sorted ordering.

```
unordered_set<int> s;
s.insert(10);
s.erase(10);
s.count(10);
s.find(10);

unordered_map<int, int> mp;
mp[x]++;             // frequency counting
mp[x] = 100;
mp.erase(x);
```

| Operation                 | Average       | Worst case |
| ------------------------- | ------------- | ---------- |
| Insert / find / erase     | \\(O(1)\\)    | \\(O(n)\\) |
| Iteration in sorted order | Not supported | —          |

Useful for frequency counting and membership checks when ordering is unnecessary.

Gotchas

- Iteration order is unspecified.
- `unordered_map[x]` inserts a missing key.
- Rehashing can invalidate iterators.
- Adversarial inputs can cause poor performance; `map` offers predictable \\(O(\log n)\\).

## 5. Custom comparators

### Descending order in a set

```
set<int, greater<int>> s;
// Elements: largest to smallest
```

### Sort a vector using a lambda

```
sort(v.begin(), v.end(), [](int a, int b) {
    return a > b;
});
```

### Sort pairs by second element, then first

```
sort(v.begin(), v.end(), [](auto a, auto b) {
    if (a.second != b.second)
        return a.second < b.second;
    return a.first < b.first;
});
```

Critical rule: A comparator must define a strict ordering. Do not use `a <= b`; use `a < b`. For equal elements, return `false` in both directions.

## 6. `priority_queue` — Heaps

### Max-heap (default)

```
priority_queue<int> pq;

pq.push(3);
pq.push(10);
pq.push(5);

pq.top();  // 10
pq.pop();  // removes 10
pq.size();
pq.empty();
```

### Min-heap

```
priority_queue<int, vector<int>, greater<int>> pq;

pq.push(3);
pq.push(10);
pq.push(5);

pq.top();  // 3
```

### Pair heap

```
priority_queue<pair<int,int>> pq;
pq.push({2, 5});
pq.push({3, 1});

pq.top(); // {3, 1}
```

Pairs use lexicographic ordering: first by `.first`, then `.second`. The default is a max-heap.

For a min-heap of pairs:

```
priority_queue<
    pair<int,int>,
    vector<pair<int,int>>,
    greater<pair<int,int>>
> pq;
```

### Custom comparator for a struct

```
struct Node {
    int cost, id;
};

struct Compare {
    bool operator()(const Node& a, const Node& b) const {
        return a.cost > b.cost;
    }
};

priority_queue<Node, vector<Node>, Compare> pq;
```

This creates a min-heap by `cost`. For `priority_queue`, the comparator's direction can feel counterintuitive: `a.cost > b.cost` puts the smallest cost at the top.

Complexity: `top()` \\(O(1)\\), `push()` and `pop()` \\(O(\log n)\\).

## 7. Ordered set (PBDS) — Rank and k-th element

GNU C++ extension, commonly available with Codeforces' GNU C++ compiler.

```
#include <ext/pb_ds/assoc_container.hpp>
#include <ext/pb_ds/tree_policy.hpp>
using namespace __gnu_pbds;

using ordered_set = tree<
    int,
    null_type,
    less<int>,
    rb_tree_tag,
    tree_order_statistics_node_update
>;

ordered_set s;
s.insert(10);
s.insert(30);
s.insert(20);
```

Two powerful operations

```
s.order_of_key(25); // number of elements strictly < 25: 2

auto it = s.find_by_order(1); // iterator to 2nd smallest: 20
if (it != s.end()) cout << *it;
```

`find_by_order(k)` uses zero-based indexing.

Both operations take \\(O(\log n)\\).

### Ordered multiset trick

PBDS `tree` does not directly support duplicates. Store `{value, unique_id}` pairs instead:

```
using ordered_multiset = tree<
    pair<int,int>,
    null_type,
    less<pair<int,int>>,
    rb_tree_tag,
    tree_order_statistics_node_update
>;

ordered_multiset s;
int id = 0;

s.insert({5, id++});
s.insert({5, id++});
s.insert({8, id++});

s.order_of_key({5, -1}); // count of values < 5
s.order_of_key({6, -1}); // count of values <= 5

auto it = s.find_by_order(1); // second element
```

To erase one occurrence, retain its exact pair and call `s.erase({value, id})`.

Note: PBDS is a GNU extension, not standard C++. Its availability depends on the compiler.

## 8. Quick complexity cheat sheet

| Container        | Find              | Insert          | Erase             |
| ---------------- | ----------------- | --------------- | ----------------- |
| `set`            | \\(O(\log n)\\)   | \\(O(\log n)\\) | \\(O(\log n)\\)   |
| `multiset`       | \\(O(\log n)\\)\* | \\(O(\log n)\\) | \\(O(\log n)\\)\* |
| `map`            | \\(O(\log n)\\)   | \\(O(\log n)\\) | \\(O(\log n)\\)   |
| `unordered_set`  | \\(O(1)\\)\*      | \\(O(1)\\)\*    | \\(O(1)\\)\*      |
| `unordered_map`  | \\(O(1)\\)\*      | \\(O(1)\\)\*    | \\(O(1)\\)\*      |
| `priority_queue` | Top \\(O(1)\\)    | \\(O(\log n)\\) | \\(O(\log n)\\)   |
| PBDS ordered set | \\(O(\log n)\\)   | \\(O(\log n)\\) | \\(O(\log n)\\)   |

\*Average/amortized or operation-specific qualifications apply. For `multiset`, erasing by key takes \\(O(\log n + k)\\) when \\(k\\) occurrences are removed. Hash containers have \\(O(n)\\) worst-case operations.

Three things worth remembering before your next contest:

1. `multiset.erase(x)` removes every copy; erase an iterator to remove one.
2. `map[x]` and `unordered_map[x]` insert missing keys.
3. PBDS gives you rank and k-th element queries that ordinary `set` cannot provide.
