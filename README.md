# Leetcode

class Solution {
    public boolean stoneGame(int[] piles) {
        int n = piles.length;
        int[][] dp = new int[n + 1][n + 1];
        int[] arr = new int[n + 1];
        for (int i = 1; i < arr.length; i++) {
            arr[i] = arr[i-1] + piles[i-1];
        }
        for (int len = 1; len <= n; len++) {
            for (int i = 1; i <= n - (len -1); i ++) {
                int b = 0;
                if (i + 1 <= n) {
                    b = dp[i + 1][i + len - 1];
                }
                dp[i][i+len-1] = arr[i + len - 1] - arr[i-1] - Math.min(dp[i][i + len - 2], b);
            }
        }
        return dp[1][n] > arr[n] - dp[1][n];
    }
}
