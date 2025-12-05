
<h1 align="center">EX NO 5 1E- Strassen’s algorithm.md</h1>

### DATE: 30-08-2025

### AIM:
To write a Java program to compute the multiplication of two large integers using a divide and conquer approach. Although Strassen’s algorithm is used for matrix multiplication, this program applies a similar divide-and-conquer strategy (Karatsuba's Algorithm) for fast integer multiplication.

The Karatsuba method reduces multiplication complexity from O(n³) to approximately O(n²·⁸¹).


### Algorithm

Read two large integer inputs as strings.

Remove leading zeros and pad the inputs if required.

Split each number into two halves: high and low parts.

Recursively compute:

z0 = low × low
z2 = high × high
z1 = (high + low) × (high + low) − z0 − z2
Combine the results using powers of 10 and return the final product.

Print the resulting multiplied value.



### Program:
```
/*
Developed by: SHARMITHA V
Register Number:  212223110048
*/
import java.util.Scanner;

public class KaratsubaBlockchain {

    public static String add(String x, String y) {
        StringBuilder result = new StringBuilder();
        int carry = 0;
        int i = x.length() - 1, j = y.length() - 1;
        while (i >= 0 || j >= 0 || carry > 0) {
            int sum = carry;
            if (i >= 0) sum += x.charAt(i--) - '0';
            if (j >= 0) sum += y.charAt(j--) - '0';
            result.append(sum % 10);
            carry = sum / 10;
        }
        return result.reverse().toString();
    }

    public static String subtract(String x, String y) {
        StringBuilder result = new StringBuilder();
        int borrow = 0;
        int i = x.length() - 1, j = y.length() - 1;
        while (i >= 0) {
            int diff = (x.charAt(i) - '0') - borrow - (j >= 0 ? (y.charAt(j--) - '0') : 0);
            if (diff < 0) {
                diff += 10;
                borrow = 1;
            } else {
                borrow = 0;
            }
            result.append(diff);
            i--;
        }
        return removeLeadingZeros(result.reverse().toString());
    }

    private static String pad(String s, int length) {
        while (s.length() < length)
            s = "0" + s;
        return s;
    }

    public static String removeLeadingZeros(String s) {
        int i = 0;
        while (i < s.length() - 1 && s.charAt(i) == '0') i++;
        return s.substring(i);
    }

    public static String karatsuba(String x, String y) {
        x = removeLeadingZeros(x);
        y = removeLeadingZeros(y);
        int n = Math.max(x.length(), y.length());

        if (n == 1) {
            return Integer.toString((x.charAt(0) - '0') * (y.charAt(0) - '0'));
        }

        x = pad(x, n);
        y = pad(y, n);
        int m = n / 2;

        String xHigh = x.substring(0, n - m);
        String xLow = x.substring(n - m);
        String yHigh = y.substring(0, n - m);
        String yLow = y.substring(n - m);

        String z0 = karatsuba(xLow, yLow);
        String z2 = karatsuba(xHigh, yHigh);
        String z1 = karatsuba(add(xHigh, xLow), add(yHigh, yLow));
        z1 = subtract(subtract(z1, z2), z0);
        z2 = z2 + "0".repeat(2 * m);
        z1 = z1 + "0".repeat(m);

        return removeLeadingZeros(add(add(z2, z1), z0));
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String A = sc.next();
        String B = sc.next();
        String hash = karatsuba(A, B);
        System.out.println("Product:");
        System.out.println(hash);
    }
}
```
### OUTPUT:
<img width="1035" height="322" alt="image" src="https://github.com/user-attachments/assets/66b1bd05-489c-41f0-96e6-400b05fa2d32" />

### RESULT:

The program was successfully implemented and the expected output was verified.
