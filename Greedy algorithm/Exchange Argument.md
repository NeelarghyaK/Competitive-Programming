## Exchange Argument
You consider an optimal solution O and then see if you can convert O to a sorted solution O* such that optimality still holds.
For problems where we need to find the optimal structure, we need to look for all permutations.This would take exponential time. We can instead use Exchange Argument and sort
array using a comparator of some sort and claim that each of the sub structure in the sorted structure will be optimal. This reduces the time by a considerable amount.
We might have to use dp later. In a lot of cases the solution will have O(N2) time complexity. The dp should be dp[pref][used] — best possible result (balance) if we choose used items so far (in the prefix pref).

Refer to this link(author:Errichto)-
https://codeforces.com/blog/entry/63533
