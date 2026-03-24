# Ex9 Finding the Longest Length of Nested Set in a Permutation Array
## DATE: 07.02.2026
## AIM:
To write a program that finds the length of the longest set s[k] defined as s[k] = { nums[k], nums[nums[k]], nums[nums[nums[k]]], … },where the iteration stops before a duplicate element occurs.

The task is to return the maximum size among all such sets.
## Algorithm
1.Start the program.
2.Input: An array nums representing a permutation of the numbers from 0 to n - 1.
3.Initialize a boolean array visited[] of size n to keep track of visited elements.
4.Initialize a variable maxLength = 0 to store the maximum length of any nested set.
5.For each index i in the array:
      i. If nums[i] is not visited:
      ii. Start from index i, and keep following nums[k] until a visited element is encountered.
      iii. Count the number of steps taken.
      iv. Update maxLength if the current count is greater than the existing value.
 6.Output the value of maxLength. End the program. 

## Program:
```
/*
Program to find the Longest Length of Nested Set in a Permutation Array
Developed by: SAI SANJAY R
RegisterNumber:  212223040178
*/
```
```
import java.util.*;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String input = sc.nextLine().trim();
        input = input.replace("nums =", "").replace("[", "").replace("]", "").trim();
        String[] parts = input.split(",");
        int[] nums = new int[parts.length];

        for (int i = 0; i < parts.length; i++) {
            nums[i] = Integer.parseInt(parts[i].trim());
        }

        Solution sol = new Solution();
        int result = sol.arrayNesting(nums);
        System.out.println(result);
        sc.close();
    }
}

class Solution {
    public int arrayNesting(int[] nums) {
        int n = nums.length;
        boolean[] visited = new boolean[n];
        int maxLen = 0;

        for (int i = 0; i < n; i++) {
            if (!visited[i]) {
                int count = 0;
                int curr = i;
                while (!visited[curr]) {
                    visited[curr] = true;
                    curr = nums[curr];
                    count++;
                }
                if (count > maxLen) {
                    maxLen = count;
                }
            }
        }
        return maxLen;
    }
}
```

## Output:
<img width="453" height="250" alt="image" src="https://github.com/user-attachments/assets/a7aa3503-db28-4b71-9b34-49c1f0c812e8" />

## Result:
The program successfully computes the longest length of the nested set s[k] for the given permutation array.
