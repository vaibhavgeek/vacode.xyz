---
title: 'Dynamic Programming  '
date: 2020-04-09T06:04:00.004-07:00
draft: true
url: /2020/04/dynamic-programming-1.html
---

In this blog post we will discuss various dynamic programming questions. The idea is to have a same template to understand all the dynamic programming problems. All the problems that we discuss will be divided into four parts:-

  

*   What is the question?  (_read \* 2 times_) 
*   Why this problem can be solved with the help of Dynamic Programming? (_read once_)
*   What does dp\[i\]\[j\] or dp\[i\] mean with respect to the question? (_read once_)
*   What is the solution if the assumed dp array is to be constructed? (_read once_)
*   How the dp\[i\] or dp\[i\]\[j\] will be formulated? Along with the help of an example. (_read twice_)
*   Variations to the questions 

Once these algorithms are done, we will observe that even the new problems can be solved with the help of this template. I have used same terminology to make the questions easier. 

### 1\. Longest Common Subsequnce

**QUESTION** : Given two sequences, find the length of longest subsequence present in both of them. In the code given below we assume X,Y to be strings.  
  
WHY DP:  Notice that given problem can be broken down as smaller chunk problem. Let us just take the first character of both the strings and compare them. Then we take the next character of string 1 and compare it with string 2 and so on.  
  
DP\[i\]\[j\]:   
for the string s1\[0..i\] and string s2\[0..j\] what is the length of longest common subsequence with those specific substrings.  Example let string 1 be  "abcdefg" anf string 2 be "abcdgk"  
  

[![](https://1.bp.blogspot.com/-WVvvgv4S2Zc/XpCLQAAa_hI/AAAAAAAAEao/kqRyd5BTtmoBHycNm8CbVcrK3T0WFr5DQCLcBGAsYHQ/s320/2016-01-04-longest-common-subsequence2.png)](https://1.bp.blogspot.com/-WVvvgv4S2Zc/XpCLQAAa_hI/AAAAAAAAEao/kqRyd5BTtmoBHycNm8CbVcrK3T0WFr5DQCLcBGAsYHQ/s1600/2016-01-04-longest-common-subsequence2.png)

  
  
  
  
SOLUTION:   dp\[n\]\[m\] (initialized as  dp\[n+1\]\[m+1\]  
  
**CODE:**  
[https://github.com/vaibhavgeek/tompetitive/blob/master/dynamicProgramming/lcs.cpp](https://github.com/vaibhavgeek/tompetitive/blob/master/dynamicProgramming/lcs.cpp)  
  
  
```
 if (i == 0 || j == 0)    
            dp[i][j] = 0;    
  
        else if (X[i - 1] == Y[j - 1])    
            dp[i][j] = dp[i - 1][j - 1] + 1;    
  
        else  
            dp[i][j] = max(dp[i - 1][j], dp[i][j - 1]);
```

Variations:-

*   Printing Longest Common Subsequence
*   Longest Common Subsequence with at most k changes allowed

  

###  2. Maximum Sum Subarray

Tha maximum sum subarray is the task of finding the largest possible sum of a contagious subarray, within a given one-dimensional array A\[1..n\]. (No length specified)  
```
 dp[i] = max(dp[i-1] + a[i] , a[i])
```The maximum subarray problem is the task of finding the largest possible sum of a contiguous subarray, within a given one-dimensional array A\[1…n\] of numbers with k length.  
```
 dp[i] = dp[i-1] + a[i] - a[i-k-1]
```

### 3\. Longest Increasing Subsequence

The Longest Increasing Subsequence (LIS) problem is to find the length of the longest subsequence of a given sequence such that all elements of the subsequence are sorted in increasing order.  
  

  
```
 if(arr[j] < arr[i])  
        dp[i] = max(dp[i], dp[j] + 1)
```

### 4\. KnapSack Problem

  
Given weights and values of n items, put these items in a knapsack of capacity W to get the maximum total value in the knapsack. In other words, given two integer arrays val\[0..n-1\] and wt\[0..n-1\] which represent values and weights associated with n items respectively. Also given an integer W which represents knapsack capacity, find out the maximum value subset of val\[\] such that sum of the weights of this subset is smaller than or equal to W. You cannot break an item, either pick the complete item, or don’t pick it (0-1 property)  
In this problem we define dp\[i\]\[j\] as i value and for j knapsack capacity. That is for j capacity how much maximum value it can store.  
```
if( j < wt[i])   
        dp[i][j] = dp[i-1][j];  
    else   
        dp[i][j] = max(dp[i-1][j - wt[i]] + val[i] , dp[i-1][j]);  

```

### 5\. Coinchange Problem

Given a value N, if we want to make change for N cents, and we have infinite supply of each of S = { S1, S2, .. , Sm} valued coins, how many ways can we make the change? The order of coins doesn’t matter.  
```
 if(j >= coin[i])  
     {  
        dp[i][j] = min(1 + dp[i][j-coin[i]] , dp[i-1][j]);  
     }  
     else  
     {  
           dp[i][j] = dp[i-1][j];  
     }
```

### 5\. Wordbreak Problem