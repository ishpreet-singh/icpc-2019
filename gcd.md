# GCD - Greatest Common Divisor

> GCD or HCF (Highest Common Factor) of two numbers is the largest number that divides both of them.

For example GCD of 20 and 28 is 4 and GCD of 98 and 56 is 14.

```
    int gcd(int a, int b) {
        if(b == 0) {
            return a;
        }
        return gcd(b, a % b);
    }
```

**Time Complexity is O(Log(Max(a, b)))**

Also Lcm of two numbers:

> hcf * lcm = product of numbers

