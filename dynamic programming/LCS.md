# Longest Common subsequence

```cpp
int dp[m+1][n+1];
for (int i=0;i<=m;i++){
     for (int j=0;j<=n;j++){
            if (i==0||j==0)
                dp[i][j]=0;
            else if (X[i-1]==Y[j-1])
                dp[i][j]=dp[i-1][j-1]+1;
            else
                dp[i][j]=max(dp[i-1][j],dp[i][j-1]);
        }
    }
    //To get the string traverse from dp[m+1][n+1] and check if max(dp[i-1][j],dp[i][j-1])==dp[i][j] and go to dp[i-1][j-1] if true else go to the max of dp[i-1][j] and dp[i][j-1]
     //Traverse till 0 is reached
 
```
