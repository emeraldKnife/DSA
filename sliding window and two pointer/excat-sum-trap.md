Standard sliding windows are built to find the Maximum or Minimum length of something. They are fundamentally terrible at finding an Exact amount when zeroes/negatives are involved, because the window size can shrink without the sum changing.

### The "At Most" Math Trick
Instead of tearing your hair out trying to count exact subarrays with leading zeros, you change the rules of the game:
- Write a simple sliding window that finds the total number of subarrays where the sum is at most `goal` (<= goal).
- Write a sliding window that finds the total number of subarrays where the sum is at most `goal - 1` (<= goal - 1).
- Subtract the two!
```
Exact(goal) = AtMost(goal) - AtMost(goal - 1)
```

For example:-
```
class Solution {
private:
    // Helper function to find count of subarrays with sum <= k
    int subarraysWithSumAtMost(vector<int>& nums, int k) {
        if (k < 0) return 0; // Negative sum is impossible with 0s and 1s
        
        int i = 0, j = 0, sum = 0, count = 0;
        
        while (j < nums.size()) {
            sum += nums[j];
            
            // Standard sliding window shrink!
            while (sum > k) {
                sum -= nums[i];
                i++;
            }
            
            // If the window [i, j] is valid, then every subarray ending at j 
            // and starting anywhere between i and j is ALSO valid.
            // The number of such subarrays is exactly the length of the window!
            count += (j - i + 1); 
            
            j++;
        }
        
        return count;
    }

public:
    int numSubarraysWithSum(vector<int>& nums, int goal) {
        // The magic formula
        return subarraysWithSumAtMost(nums, goal) - subarraysWithSumAtMost(nums, goal - 1);
    }
};
```
