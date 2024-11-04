Algorithm:
1.Initialize Variables: Create a variable to count the number of two-digit prime numbers.
2.Extract Two-Digit Numbers: Traverse the digits of the number 
n and, for each pair of adjacent digits, form a two-digit number.
3.Check for Primality: For each two-digit number, check if it’s prime.
a.A prime number has no divisors other than 1 and itself.
4.Increment Counter: If a two-digit number is prime, increment the counter.
5.Output the Result: Print the count of two-digit prime numbers.

C Program
Below is a C program that implements this logic.

#include <stdio.h>
#include <stdbool.h>

// Function to check if a number is prime
bool isPrime(int num) {
    
    if (num < 2) return false;
    for (int i = 2; i * i <= num; i++) {
        if (num % i == 0) return false;
    }
    return true;
}

// Function to count two-digit prime numbers formed by adjacent digits
int countTwoDigitPrimes(int n) {
   
    int count = 0;
    int prev_digit = n % 10;  // Last digit
    n /= 10;

    while (n > 0) {
        int current_digit = n % 10;  // Extract current digit
        int two_digit_num = current_digit * 10 + prev_digit;  // Form two-digit number
        if (isPrime(two_digit_num)) {
            count++;
        }
        prev_digit = current_digit;  // Move to the next pair
        n /= 10;
    }
    return count;
}

int main() {
   
    int n;
    printf("Enter a number: ");
    scanf("%d", &n);

    int result = countTwoDigitPrimes(n);
    printf("Count of two-digit prime numbers: %d\n", result);

    return 0;
}

Explanation:

1.isPrime Function: This helper function checks if a given integer is prime. It returns true if the number is prime and false otherwise.

a.It iterates from 2 up to the square root of the number to check for factors. If any factor is found, it returns false.

2.countTwoDigitPrimes Function:
a.This function takes the integer n and processes it to count two-digit prime numbers.
b.It extracts pairs of adjacent digits to form two-digit numbers. For example, given n = 114, it will first form 14 and then 11.
c.For each two-digit number formed, it checks if it is prime using isPrime. If the number is prime, it increments the count.

3.main Function:

a.Prompts the user to enter a number and calls the countTwoDigitPrimes function to count the two-digit primes.
b.Outputs the result.

Example Walkthrough
If the input is 114:

a.Adjacent two-digit numbers: 11, 14.
b.11 is prime, 14 is not.
c.Output will be 1 since there is one two-digit prime.
