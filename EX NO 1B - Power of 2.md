<h1 align="center">EX 1B Power of 2</h1>

### DATE: 10-08-2025

### AIM:
To write a Java program to for given constraints.Given an integer n, return true if it is a power of two. Otherwise, return false.

An integer n is a power of two, if there exists an integer x such that n == 2x.

### Algorithm

Start the program.

Read the integer value n from the user.

If n ≤ 0, return false (because powers of 2 are always positive).

Use a loop to check whether n becomes 1 when repeatedly divided by 2.

If n becomes 1, display true; otherwise display false.


### Program:
```
/*
Developed by: SHARMITHA V
Register Number:  212223110048
*/
import java.util.Scanner;

public class Solution {

    public boolean isPowerOfTwo(int n) {
        if(n==1) return true;
        long i=1;
        while((i<<1)<=n){
            if(i<<1 == n) return true;
            i = i<<1;
        }
        return false;
     
     
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Solution sol = new Solution();
        int n = scanner.nextInt();

        boolean result = sol.isPowerOfTwo(n);
        System.out.println(result);

        scanner.close();
    }
}
```
### OUTPUT:
<img width="1249" height="230" alt="image" src="https://github.com/user-attachments/assets/676aabd8-2b32-41b2-aa28-7a07ac0c7e91" />

### RESULT:

The program was successfully implemented and the expected output was verified.


