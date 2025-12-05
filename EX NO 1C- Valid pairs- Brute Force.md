<h1 align="center">EX 1C Valid Pairs using Brute Force Approach</h1>

### DATE: 21-08-2025

### AIM:

To write a Java program that counts the number of valid pairs (i, j) such that i < j and |nums[i] – nums[j]| = k, using the brute force method.

### Algorithm

Start the program.

Read the value of n and then read n elements into the array.

Read the value of integer k.

Use two nested loops to compare every pair (i, j) where i < j.

Count the pair if the absolute difference equals k, then print the result.


### Program:
```
/*
Developed by: SHARMITHA V
Register Number:  212223110048
*/
import java.util.Scanner;
import java.util.*;
public class CountPairsWithDifference {
    public static int countKDifference(int[] nums, int k) {
        
        Map<Integer,Integer> map = new HashMap<>();
        int res = 0;
        
        for(int i = 0;i< nums.length;i++){
            if(map.containsKey(nums[i]-k)){
                res+= map.get(nums[i]-k);
            }
            if(map.containsKey(nums[i]+k)){
                res+= map.get(nums[i]+k);
            }
            map.put(nums[i],map.getOrDefault(nums[i],0)+1);
        }
        
        
        return res;
    }   
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] nums = new int[n];
        for (int i = 0; i < n; i++) {
            nums[i] = sc.nextInt();
        }
        int k = sc.nextInt();
        int result = countKDifference(nums, k);
        System.out.println(result);
        sc.close();
    }
}
```
### OUTPUT:
<img width="1203" height="379" alt="image" src="https://github.com/user-attachments/assets/e8b904e7-1734-4b45-932b-9d92b8fff994" />

### RESULT:

The program was successfully implemented and the expected output was verified.

