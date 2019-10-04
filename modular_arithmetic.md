# Modular Arithmetic

When we divide two integers we will have an equation that looks like the following:

A / B = Q % R

* A is the dividend
* B is the divisor
* Q is the quotient
* R is the remainder
* % is called the modulo Operator(mod)

    ```13 mod 5 = 3```

* There are negatice Modulo operators also like:

    ```−5 mod 3 = 1```

* Modular Addition

    ```(A + B) mod C = (A mod C + B mod C) mod C```

* Modular Subtraction
 
    ```(A - B) mod C = (A mod C - B mod C) mod C```

* Modular Multiplication

    ```(A * B) mod C = (A mod C * B mod C) mod C```

* Moludar Exponentiation

    ```A^B mod C = ( (A mod C)^B ) mod C```

* Fast Moludar Exponentiation

    Given three numbers a, b and c, we need to find (a^b) % c

```
long power(int a, int b, int c) {
    // Set answer to 1
    long ans = 1;

    // If a > c 
    a = a % c;

    while(b > 0) {
        
        // if b is odd
        if(b%2 != 0) {
            ans = (ans * a) % c;
        }

        b /= 2;
        a *= 2;
    }

    return ans;
}
```

> Time Complexity : O(Log b)

References:

  * https://www.geeksforgeeks.org/modular-exponentiation-power-in-modular-arithmetic/
  * https://www.khanacademy.org/computing/computer-science/cryptography/modarithmetic
  * 