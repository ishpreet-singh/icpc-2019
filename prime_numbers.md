# Prime Numbers

> A prime number is a natural number greater than 1 that cannot be formed by multiplying two smaller natural numbers.

## Finding all the prime numbers smaller than n

* eg: If number is 10, prime numbers are 2, 3, 5, 7

### Brute Force

**Time Complexity: O(n * √n)**

```
    // A function that predicts if number is prime in O(√n)
    bool isPrime(int n) {
        for(int i=2; i*i <= n; i++) {
            if(num %i == 0) {
                return false;
            }
        }
        return true;
    }

    void allPrimes(int n) {
        for(int i=2; i<n; i++) {
            if(isPrime(i)) {
                cout<<i<<endl;
            }
        }
    }
```

### Sieve of Eratosthenes

**Time Complexity: O(n * log(logn))**

_Approach_

* Create a list of consecutive integers from 2 to n: (2, 3, 4, …, n)
* Initially 2 is the first prime number(let say i = 2).
* Mark all multiples of 2(aka **i**) from as non prime starting from **i * i** (2*2 = 4).
* The numbers unmarked will be prime numbers.

```
    void sieveOfEratosthenes(int n) {
        // A boolean array, initialising all of them as prime
        bool prime[n + 1];
        for(int i=1; i <= n; i++) {
            prime[i] = true;
        }

        // Marking 0 and 1 as non-prime
        prime[0] = prime[1] = false;

        for(int i=2; i*i <= n; i++) {
            if(prime[i]) {
                for(int j=i*i; j <= n; j+= i) {
                    prime[j] = false;
                }
            }
        }

        // Printing Prime Numbers
        for(int i=2; i<=n; i++) {
            if(prime[i]) {
                cout<<p<< " is a prime Number"<<endl;
            }
        }
    }
```

Read more about [Sieve of Eratosthenes](https://en.wikipedia.org/wiki/Sieve_of_Eratosthenes)


### Segmented Sieve of Eratosthenes

**Time Complexity: O(n * log(logn))**

> The idea of segmented sieve is to divide the range [0..n-1] in different segments and compute primes in all segments one by one. Thsi works for **larger values of n**

_Approach_

* Use Sieve of Eratosthenes to find all primes upto √n.
* We need all primes in range [0..n-1]. We divide this range in different segments such that size of every segment is at-most √n.
* Do following for every segment [low..high]
Create an array mark[high-low+1]. Here we need only O(x) space where x is number of elements in given range.
Iterate through all primes found in step 1. For every prime, mark its multiples in given range [low..high].


```

void sieveOfEratosthenes(int n, vector<int> &prime) {
        // A boolean array, initialising all of them as prime
        bool prime[n + 1];
        for(int i=1; i <= n; i++) {
            prime[i] = true;
        }

        // Marking 0 and 1 as non-prime
        prime[0] = prime[1] = false;

        for(int i=2; i*i <= n; i++) {
            if(prime[i]) {
                for(int j=i*i; j <= n; j+= i) {
                    prime[j] = false;
                }
            }
        }

        // Printing Prime Numbers
        for(int i=2; i<=n; i++) {
            if(prime[i]) {
                prime.push_back(i);
            }
        }
    }
  
void segmentedSieve(int n) 
{ 
    int limit = floor(sqrt(n))+1; 
    vector<int> prime;  
    sieveOfEratosthenes(limit, prime);  
  
    // Divide the range [0..n-1] in different segments 
    int low = limit; 
    int high = 2*limit; 
  
    // process one segment at a time 
    while (low < n) 
    { 
        if (high >= n)  
           high = n; 
          
        bool mark[limit+1]; 
        for(int i=0; i <= limit; i++) {
            mark[i] = true;
        }
  
        for (int i = 0; i < prime.size(); i++) 
        { 
            int loLim = floor(low/prime[i]) * prime[i]; 
            if (loLim < low) {
                loLim += prime[i]; 
            }
  
            for (int j=loLim; j<high; j+=prime[i]){
                mark[j-low] = false; 
            }
        } 
  
        for (int i = low; i<high; i++) {
            if (mark[i - low] == true) {
                cout << i << " "; 
            }
        }
  
        // Update low and high for next segment 
        low = low + limit; 
        high = high + limit; 
    } 
} 
```


Read more about [Segmented Sieve of Eratosthenes](https://www.geeksforgeeks.org/segmented-sieve/)

