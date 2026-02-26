# Ex9 Finding the Longest Length of Nested Set in a Permutation Array

## DATE: 25.02.2026

### Developed by
**Name:** VIJAY K

**Register Number:** 212223040236

## AIM:
To write a program that finds the length of the longest set s[k] defined as  
s[k] = { nums[k], nums[nums[k]], nums[nums[nums[k]]], … }  
where the iteration stops before a duplicate element occurs. The task is to return the maximum size among all such sets.

## Algorithm
1. Start the program.  
2. Read the number of elements and the permutation array.  
3. Create a boolean `visited` array initialized to false.  
4. For each index `i` not yet visited, follow the chain `x = nums[x]`, marking visited elements and counting steps until revisiting; this gives the size of s[i].  
5. Track the maximum size encountered.  
6. Output the maximum size.  
7. Stop the program.

## Program:
```java

import java.util.Scanner;

public class LongestNestedSet {
    static int arrayNesting(int[] nums) {
        int n = nums.length;
        boolean[] visited = new boolean[n];
        int maxSize = 0;
        for (int i = 0; i < n; i++) {
            if (!visited[i]) {
                int size = 0;
                int current = i;
                while (!visited[current]) {
                    visited[current] = true;
                    current = nums[current];
                    size++;
                }
                if (size > maxSize) maxSize = size;
            }
        }
        return maxSize;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter number of elements: ");
        int n = sc.nextInt();
        int[] nums = new int[n];
        System.out.println("Enter the permutation array elements (0-based indices):");
        for (int i = 0; i < n; i++) nums[i] = sc.nextInt();
        int result = arrayNesting(nums);
        System.out.println("Longest length of nested set: " + result);
        sc.close();
    }
}
```
## OUTPUT

<img width="1288" height="307" alt="image" src="https://github.com/user-attachments/assets/6802453d-3509-4f2b-9757-403adf7bb30c" />


## RESULT
The program successfully computes the longest length of the nested set s[k] for the given permutation array.
