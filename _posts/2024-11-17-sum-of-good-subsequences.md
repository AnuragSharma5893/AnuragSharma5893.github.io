---
title: "3351. Sum of Good Subsequences"
date: 2024-11-17 00:00:00 +0800
categories: [Leetcode]
tages: [Leetcode_potd]
---

# Sum of Good Subsequences
![image1](https://miro.medium.com/v2/resize:fit:720/format:webp/1*N0YN64RifWvDOPuG3VXf7A.png)

## Approach to the Problem
We are tasked with finding the sum of all possible good subsequences in a given array nums where a good subsequence satisfies the condition that the absolute difference between any two consecutive elements is exactly 1. Here's how we can systematically solve this problem.

Understand the Problem
1. Subsequences:
A subsequence is a sequence derived from an array by deleting some or no elements without changing the order of the remaining elements.
Example: [1, 2, 1] has subsequences: [1], [2], [1], [1, 2], [2, 1], [1, 2, 1].
2. Good Subsequences:
A subsequence is good if the absolute difference between consecutive elements is exactly 1.
3. Goal:
Compute the sum of all good subsequences modulo 10⁹+7.
Brute-Force Approach
1. Generating All the Subsequences:
Use recursion or bitmasking to generate all possible subsequences of the array.
Check if each subsequence is good by ensuring the condition ∣a[i]−a[i−1]∣ = 1 is satisfied for all consecutive elements.
Sum up all elements of the good subsequences.
2. Time Complexity:
Generating all subsequences takes O(2^n), where n is the length of the array.
Verifying each subsequence for the good property takes O(n) in the worst case.
Overall: O(n⋅2^n). This is infeasible for large n (up to 10⁵).
Optimal Approach
To handle the constraints efficiently, we use a dynamic programming approach with optimization based on frequencies of numbers in the array.

Algorithm We Use:-
1. Frequency Array:
Count the occurrences of each number in the array. This allows us to consider only the numbers present in the array, reducing unnecessary computation.
2. Dynamic Programming Arrays:
Using two arrays:

sum[c]: Tracks the sum of elements in all good subsequences ending with number c.
count[c]: Tracks the number of good subsequences ending with number c.
Transition:
For each number c in nums:

Add contributions from subsequences ending at c-1 (if c-1 exists in the array).
Add contributions from subsequences ending at c+1 (if c+1 exists in the array).
Add the number c itself as a single-element subsequence.
Modulo:
Since the answer can be large, perform all computations modulo 10⁹+7.
Final Sum:
Sum up all values in the sum array to get the result.

```
int sumOfGoodSubsequences(int[] nums) {
    int MOD = 1e9 + 7;
    int MAX = 1e5 + 1;

    long[] sum = new long[MAX];
    long[] count = new long[MAX];
    int[] freq = new int[MAX];

    // Count frequency of each number
    for (int num : nums) {
        freq[num]++;
    }

    for (int c = 0; c < MAX; c++) {
        if (freq[c] == 0) continue;

        if (c - 1 >= 0) {
            sum[c] += (count[c - 1] * c + sum[c - 1]) % MOD;
            count[c] += count[c - 1] % MOD;
        }

        sum[c] += c * freq[c];
        count[c] += freq[c];

        if (c + 1 < MAX) {
            sum[c] += (count[c + 1] * c + sum[c + 1]) % MOD;
            count[c] += count[c + 1] % MOD;
        }

        sum[c] %= MOD;
        count[c] %= MOD;
    }

    long result = 0;
    for (int c = 0; c < MAX; c++) {
        result = (result + sum[c]) % MOD;
    }

    return (int) result;
}
```

```
class Solution {
    public int sumOfGoodSubsequences(int[] nums) {
        long[] sum = new long[(int) (1e5 + 1)];
        long[] count = new long[(int) (1e5 + 1)];        
        int[] freq = new int[(int) (1e5 + 1)];
        long mod = (long) (1e9 + 7);
        for(int i: nums) freq[i]++;

        for(int i=0; i<nums.length; i++){
            int c = nums[i];
            if(c-1 >= 0 && count[c-1] > 0){
                sum[c] += (count[c-1] * c + sum[c-1]);
                count[c] += count[c-1];
            }
            sum[c] += c;
            count[c] += 1;

             if(c+1 < sum.length && count[c+1] > 0){
                sum[c] += (count[c+1] * c + sum[c+1]);
                count[c] += count[c+1];
            }
            sum[c] %= mod;
            count[c] %= mod;
        }
        long res = 0;
        for(int i=0; i < sum.length; ++i){
            if (sum[i] > 0){
                //system.out.println(i + "" + sum[i]);
            }
            res = (res % mod + sum[i] % mod) % mod;
        }

        return (int) (res % mod);
    } 
}
```

## Time Complexity

`Frequency Calculation: O(n), where n is the length of the array.`

`Dynamic Programming Update: O(range of numbers) = O(10⁵), as we iterate over the possible range of values.`

`Final Sum Computation: O(105)O(10⁵)O(105).`

`Overall Time Complexity: O(n+10⁵)≈ O(n) for n≤10⁵`

## Space Complexity
`Frequency array: O(10⁵).`

`DP arrays (sum and count): O(10⁵).`

`Overall Space Complexity: O(10⁵).`

How to Tackle Similar Problems

1. Break Down the Problem:
Identify properties of valid subsequences (like the condition `∣a[i]−a[i−1]∣=1|a[i] — a[i-1]| = 1∣a[i]−a[i−1]∣=1`).
2. Use Frequency Arrays:
Preprocess the array to avoid redundant computation.
3. Dynamic Programming:
Use DP to build solutions iteratively while maintaining the necessary conditions.
4. Modulo Arithmetic:
Always consider constraints like modulo 10⁹+7 for large results.