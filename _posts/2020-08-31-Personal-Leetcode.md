---
layout: post
date: 2020-08-31 03:00
title:  "Personal leetcode gist"
description: leetcode code
comments: false
category: 
- docs
- help
tags:
- documentation
- leetcode
- Java
---
### 09/19/2020 Leetcode weekly contest

> 1594-> Maximum Non Negative Product in a Matrix
[📜problem](https://leetcode.com/problems/maximum-non-negative-product-in-a-matrix/)
<!--more-->
- Solution 1 (DP):
{% highlight ruby linenos %}

        public int maxProductPath(int[][] grid) {
                int n = grid.length;
                int m = grid[0].length;
                double[][] curMax = new double[n][m];
                double[][] curMin = new double[n][m];
                curMax[0][0] = grid[0][0];
                curMin[0][0] = grid[0][0];
                for (int i = 1; i < grid.length; i++) {
                    curMax[i][0] = grid[i][0] * curMax[i - 1][0];
                    curMin[i][0] = grid[i][0] * curMin[i - 1][0];
                }
                for (int i = 1; i < grid[0].length; i++) {
                    curMax[0][i] = grid[0][i] * curMax[0][i - 1];
                    curMin[0][i] = grid[0][i] * curMin[0][i - 1];
                }

                for (int i = 1; i < n; i++) {
                    for (int j = 1; j < m; j++) {
                        if (grid[i][j] >= 0) {
                            curMax[i][j] = Math.max(curMax[i][j - 1] * grid[i][j], curMax[i - 1][j] * grid[i][j]);
                            curMin[i][j] = Math.min(curMin[i][j - 1] * grid[i][j], curMin[i - 1][j] * grid[i][j]);
                        } else {
                            curMax[i][j] = Math.max(curMin[i][j - 1] * grid[i][j], curMin[i - 1][j] * grid[i][j]);
                            curMin[i][j] = Math.min(curMax[i][j - 1] * grid[i][j], curMax[i - 1][j] * grid[i][j]);
                        }
                    }
                }

                if (curMax[n - 1][m - 1] < 0) {
                    return -1;
                } else {
                    return (int)(curMax[n - 1][m - 1] % 1000000007);
                }
         }

{% endhighlight %}


- Solution 2 (DFS):

{% highlight ruby linenos %}

        class Solution {
            int mod = 1000000007;
            double res = -1;
            public int maxProductPath(int[][] grid) {
                if(grid.length == 0 || grid[0].length == 0) return -1;
                dfs(0,0,grid,grid[0][0]);
                return (int)(res%mod);
            }
            public void dfs(int i, int j, int[][] grid, double curr){
                if(i == grid.length -1 && j == grid[0].length -1 ){
                    res = Math.max(res, curr);
                    return;

                }
                if(grid[i][j] == 0){
                    res = Math.max(res, 0);
                    return;
                }

                if(i+1 < grid.length){
                    dfs(i+1, j, grid, curr * grid[i+1][j]);
                }
                if(j + 1 < grid[0].length){
                    dfs(i, j+1, grid, curr * grid[i][j+1]);
                }
            }
        }

{% endhighlight %}

> 159-> Longest Substring with At Most Two Distinct Characters


| Problem Link | Solution Link |
| --- | --- |
| [📜problem](https://leetcode.com/problems/longest-substring-with-at-most-two-distinct-characters/) | [`solution`](https://gist.github.com/LoneRan/2cdd40d62f5f391660e1f6cafdbac5ef)|



> 438-> Find All Anagrams in a String


| Problem Link | Solution Link |
| --- | --- |
| [📜problem](https://leetcode.com/problems/find-all-anagrams-in-a-string/) | [`solution`](https://gist.github.com/LoneRan/f696afb961895af1f93e75764fa0122a)|


> 72-> Edit Distance


| Problem Link | Solution Link |
| --- | --- |
| [📜problem](https://leetcode.com/problems/edit-distance/) | [`solution`](https://gist.github.com/LoneRan/4835cb1cdebabeb3349c4ca8466c1fd2)|
