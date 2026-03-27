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

### The "Prefix Count" Trick
To do this in one pass, we use a single sliding window and a count variable.

Here is the secret sauce:

- When your window has exactly `k` odd numbers, you shrink the left side (i++) as much as possible, counting how many times you can shrink it before losing an odd number. (This is essentially counting the leading even numbers).

- You store that number in a `count` variable and add it to your answer.

- If your right pointer `j` hits another even number later, you don't need to recalculate anything! You just add that exact same count to your answer again, because trailing evens create the exact same number of valid subarrays as the core window.

```
class Solution {
public:
    int numberOfSubarrays(vector<int>& nums, int k) {
        int i = 0, j = 0, odd_count = 0, count = 0, ans = 0;

        while (j < nums.size()) {
            if (nums[j] % 2 != 0) {
                odd_count++;
                count = 0; // Reset our valid subarray counter when we hit a new odd number
            }

            // When we have exactly 'k' odds, count how many valid left-boundaries exist
            while (odd_count == k) {
                count++; // Count this valid window configuration
                
                if (nums[i] % 2 != 0) {
                    odd_count--; // If we drop an odd number, we break out of the while loop
                }
                i++; // Shrink from the left
            }

            // Add the valid subarrays found for this specific right edge (j)
            ans += count; 
            j++;
        }

        return ans;
    }
};
```
