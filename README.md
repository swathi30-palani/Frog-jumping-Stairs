// Frog Jump
// 2024 Amazon interview question

// Base case
// dp[0] = 0
// dp[1] = |height[1] - height[0]|

// Dry run for heights = [10, 20, 30, 10]

// dp[0] = 0
// dp[1] = |20 - 10| = 10
// dp[2] = min(dp[1] + |30 - 20|, dp[0] + |30 - 10|)
//        = min(10 + 10, 0 + 20) = min(20, 20) = 20
// dp[3] = min(dp[2] + |10 - 30|, dp[1] + |10 - 20|)
//        = min(20 + 20, 10 + 10) = min(40, 20) = 20

// Final Answer: Minimum energy to reach last stone = 20
public class Frogjumps {
    public static int frogjump(int[] heights, int n){
        int [] dp = new int[n];
        dp [0] = 0;
        for(int i =1 ; i < n ; i++){
            int jumpOne = dp[i - 1] + Math.abs(heights[i] - heights[i - 1]);
            int jumpTwo = Integer.MAX_VALUE;
            if ( i > 1){
                jumpTwo = dp[i - 2] + Math.abs(heights[i] - heights[i - 2]);
            }
            dp[i] = Math.min(jumpOne, jumpTwo);
        }
        return dp[n - 1];
    }
    public static void main(String[] args){
        int[] heights = {10, 20, 30, 40};
        int n = heights.length;
        
        System.out.println("Minimum energy to reach last stone: " + frogjump(heights, n));
    }
}
