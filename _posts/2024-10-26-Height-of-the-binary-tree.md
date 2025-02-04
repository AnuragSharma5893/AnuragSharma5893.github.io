---
title: "2458. Height of the Binary Tree"
date: 2024-10-26 00:00:00 +0800
categories: [Leetcode]
tages: [Leetcode_potd, Binary Tree, Java]
link: "https://medium.com/@anuragsharma58693/2458-height-of-binary-tree-after-subtree-removal-queries-e558db0e6640"
---

# Height of Binary Tree After Subtree Removal Queries

## Leetcode 2458.

Today in the daily Leetcode problem of the day, we have a hard-level question related to trees.

But first Let’s understand the question

![Question Picture](https://miro.medium.com/v2/resize:fit:720/format:webp/1*jPm63ps3dlD6O6nQBhw0gA.png)


We have a Binary Tree with n nodes with unique values from 1 to n.

We have given queries[i] of size n which are independent. We have to perform queries[i] such that we Remove the subtree rooted at the node with the value queries[i] from the tree. Remember, It is guaranteed that queries[i] will not be equal to the value of the root.

Constraints:

    • The number of nodes in the tree is n.
    • 2 <= n <= 105
    • 1 <= Node.val <= n
    • All the values in the tree are unique.
    • m == queries.length
    • 1 <= m <= min(n, 104)
    • 1 <= queries[i] <= n
    • queries[i] != root.val

Our task is to Return an array answer of size m where answer[i] is the height of the tree after performing the ith query.

![image1](https://miro.medium.com/v2/resize:fit:640/format:webp/0*1yk3Iv0t29___UGc.png)

Input: root = [1,3,4,2,null,6,5,null,null,null,null,null,7], queries = [4]
Output: [2]
Explanation: The diagram above shows the tree after removing the subtree rooted at node with value 4.
The height of the tree is 2 (The path 1 -> 3 -> 2).

Let’s perform queries by taking an example:-

![image2](https://miro.medium.com/v2/resize:fit:602/format:webp/0*SXjjkmk9JmImvuWB.png)

Input: root = [5,8,9,2,1,3,7,4,6], queries = [3,2,4,8]
Output: [3,2,3,2]

Basically, we have to see after removing the queries node our tree height is disturbing or not. For that, we will calculate the maximum depth of the tree from both the left and right sides of the tree.

![image3](https://miro.medium.com/v2/resize:fit:720/format:webp/1*tW-kmQxtyx4iED9kjSLf4g.png)
![image4](https://miro.medium.com/v2/resize:fit:720/format:webp/1*nJN5dyLAxGvoJ8bFkju5pw.png)
![image5](https://miro.medium.com/v2/resize:fit:720/format:webp/1*KGt24gOVmA7KX25MV8Fskw.png)
![image6](https://miro.medium.com/v2/resize:fit:720/format:webp/1*nEZJEiRoIAjTqZyXwp53uQ.png)
![image7](https://miro.medium.com/v2/resize:fit:720/format:webp/1*B_qwz3SlmJ-hqI6dZG0hsw.png)


Now, Let's see through right side

![image8](https://miro.medium.com/v2/resize:fit:720/format:webp/1*c8jaiJJsnj2YFySX6WlU7Q.png)
![image9](https://miro.medium.com/v2/resize:fit:720/format:webp/1*GZHxPivqrYrajAhrpP3M-g.png)

Now we will put index 6 as max 2. And if we include 6 the height max. would be 3
![image10](https://miro.medium.com/v2/resize:fit:720/format:webp/1*1THsVwg8kc1vSItjWNiNhg.png)

Now, We will perform DFS traversal on both sides of the tree to perform the queries[i] by Remove and check whether after removing the form left can get the maximum height from the right side or vice versa just as mentioned in the problem statement.

Now let's write code in Java

```
class Solution {
    int max;
    public int[] treeQueries(TreeNode root, int[] queries) {
        int left[] = new int[100001];
        int right[] = new int[100001];   

        max = 0;
        leftFirst(root, left, 0);
        max = 0;
        rightFirst(root, right, 0);
        
        for(int i=0; i<queries.length; i++){
            queries[i] = Math.max(left[queries[i]], right[queries[i]]);
        }
        return queries;
    }

    private void leftFirst(TreeNode root, int[] left, int d) {
        if(root == null) return;
        left[root.val] = max;
        max = Math.max(max, d); // d = deapth
        leftFirst(root.left, left, d+1);
        leftFirst(root.right, left, d+1);
    }

    private void rightFirst(TreeNode root, int[] right, int d) {
        if(root == null) return;
        right[root.val] = max;
        max = Math.max(max, d); // d = deapth
        rightFirst(root.right, right, d+1);
        rightFirst(root.left, right, d+1);
    }
}
```

The Time and Space Complexity would be O(n).