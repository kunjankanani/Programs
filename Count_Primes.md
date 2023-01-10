# Count Primes

Given an integer n, return the number of prime numbers that are strictly less than n.

 

Example 1:
```
Input: n = 10
Output: 4
Explanation: There are 4 prime numbers less than 10, they are 2, 3, 5, 7.
```
Example 2:
```
Input: n = 0
Output: 0
```
Example 3:
```
Input: n = 1
Output: 0
```

Constraints:

- 0 <= n <= 5 * 10^6

## Solution

### Sieve of Eratosthenes Explanation with Example: 

Let us take an example when n = 50. So we need to print all prime numbers smaller than or equal to 50. 

We create a list of all numbers from 2 to 50.  

![Add](https://media.geeksforgeeks.org/wp-content/uploads/SieveofEratosthenes1.jpg)

According to the algorithm we will mark all the numbers which are divisible by 2 and are greater than or equal to the square of it. 

![Add](https://media.geeksforgeeks.org/wp-content/uploads/SieveofEratosthenes2.jpg)

Now we move to our next unmarked number 3 and mark all the numbers which are multiples of 3 and are greater than or equal to the square of it.  

![Add](https://media.geeksforgeeks.org/wp-content/cdn-uploads/SieveofEratosthenes3.jpg)

We move to our next unmarked number 5 and mark all multiples of 5 and are greater than or equal to the square of it.  

![Add](https://media.geeksforgeeks.org/wp-content/uploads/SieveofEratosthenes4.jpg)

We continue this process and our final table will look like below:  

![Add](https://media.geeksforgeeks.org/wp-content/uploads/SieveofEratosthenes5.jpg)

So the prime numbers are the unmarked ones: 2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37, 41, 43, 47.



```c++
int countPrimes(int n) 
{
        int k=0;
        vector<bool> prime(n+1,true);
        
        prime [0] = prime [1] = false ; 
        for(int i=2 ; i<n ; i++)
            if(prime[i])
            {
                k++;
                for(int j=2*i ; j<n ; j=j+i)
                {
                    prime[j]=false;
                }
            }
            return k; 
}

```