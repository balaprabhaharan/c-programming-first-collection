# C Programming – My First Coding Collection

Hi! This is a small collection of 10 basic C programs I wrote while learning C in my first year of Computer Science and Engineering at KPR Institute of Engineering and Technology. Each one comes with a short explanation of how it works and a sample run, so you can see what it does before you try it yourself.

If you're also just starting out with C, I hope these help.

**Author:** Bala Prabhaharan E

---

## Contents

1. [Hello World](#1-hello-world)
2. [Sum of Two Numbers](#2-sum-of-two-numbers)
3. [Even or Odd](#3-even-or-odd)
4. [Largest of Three Numbers](#4-largest-of-three-numbers)
5. [Factorial of a Number](#5-factorial-of-a-number)
6. [Fibonacci Series](#6-fibonacci-series)
7. [Prime Number Check](#7-prime-number-check)
8. [Reverse a Number](#8-reverse-a-number)
9. [Simple Calculator](#9-simple-calculator)
10. [Multiplication Table](#10-multiplication-table)

---

## How to Run

Save any program as `program.c`, then compile and run it like this:

```bash
gcc program.c -o program
./program
```

(On Windows, type `program.exe` instead of `./program`.)

---

## 1. Hello World

**How it works:** This is where everyone starts. `main()` is the place every C program begins running, and `printf()` shows text on the screen.

```c
#include <stdio.h>

int main() {
    printf("Hello, World!\n");
    return 0;
}
```

**Output:**
```
Hello, World!
```

---

## 2. Sum of Two Numbers

**How it works:** The program asks for two numbers with `scanf()`, adds them up, and prints the answer.

```c
#include <stdio.h>

int main() {
    int a, b, sum;

    printf("Enter two numbers: ");
    scanf("%d %d", &a, &b);

    sum = a + b;
    printf("Sum = %d\n", sum);
    return 0;
}
```

**Sample Input / Output:**
```
Enter two numbers: 12 8
Sum = 20
```

---

## 3. Even or Odd

**How it works:** A number is even when you can divide it by 2 and nothing is left over. The `%` operator gives us that leftover (the remainder), and `if-else` decides which message to print.

```c
#include <stdio.h>

int main() {
    int n;

    printf("Enter a number: ");
    scanf("%d", &n);

    if (n % 2 == 0)
        printf("%d is Even\n", n);
    else
        printf("%d is Odd\n", n);
    return 0;
}
```

**Sample Input / Output:**
```
Enter a number: 7
7 is Odd
```
```
Enter a number: 10
10 is Even
```

---

## 4. Largest of Three Numbers

**How it works:** It checks each number against the other two using `if-else if` and the logical AND operator (`&&`). Whichever one is at least as big as both the others wins.

```c
#include <stdio.h>

int main() {
    int a, b, c;

    printf("Enter three numbers: ");
    scanf("%d %d %d", &a, &b, &c);

    if (a >= b && a >= c)
        printf("Largest = %d\n", a);
    else if (b >= a && b >= c)
        printf("Largest = %d\n", b);
    else
        printf("Largest = %d\n", c);
    return 0;
}
```

**Sample Input / Output:**
```
Enter three numbers: 25 78 43
Largest = 78
```

---

## 5. Factorial of a Number

**How it works:** The factorial of `n` (written `n!`) is `1 × 2 × 3 × … × n`. A `for` loop multiplies the numbers together one at a time. I used `unsigned long long` so that bigger results still fit.

```c
#include <stdio.h>

int main() {
    int n, i;
    unsigned long long fact = 1;

    printf("Enter a number: ");
    scanf("%d", &n);

    for (i = 1; i <= n; i++)
        fact = fact * i;

    printf("Factorial of %d = %llu\n", n, fact);
    return 0;
}
```

**Sample Input / Output:**
```
Enter a number: 5
Factorial of 5 = 120
```

---

## 6. Fibonacci Series

**How it works:** In this series, every number is the sum of the two before it: `0, 1, 1, 2, 3, 5, 8, …`. The loop prints the current number, then shifts the last two numbers forward to get the next one.

```c
#include <stdio.h>

int main() {
    int n, i, first = 0, second = 1, next;

    printf("Enter number of terms: ");
    scanf("%d", &n);

    printf("Fibonacci Series: ");
    for (i = 1; i <= n; i++) {
        printf("%d ", first);
        next = first + second;
        first = second;
        second = next;
    }
    printf("\n");
    return 0;
}
```

**Sample Input / Output:**
```
Enter number of terms: 8
Fibonacci Series: 0 1 1 2 3 5 8 13
```

---

## 7. Prime Number Check

**How it works:** A prime number can only be divided evenly by 1 and itself. The program tries every divisor from 2 up to `n/2`. If any of them divides `n` with no remainder, the number isn't prime and the loop stops early.

```c
#include <stdio.h>

int main() {
    int n, i, isPrime = 1;

    printf("Enter a number: ");
    scanf("%d", &n);

    if (n <= 1)
        isPrime = 0;

    for (i = 2; i <= n / 2; i++) {
        if (n % i == 0) {
            isPrime = 0;
            break;
        }
    }

    if (isPrime)
        printf("%d is a Prime number\n", n);
    else
        printf("%d is not a Prime number\n", n);
    return 0;
}
```

**Sample Input / Output:**
```
Enter a number: 17
17 is a Prime number
```
```
Enter a number: 21
21 is not a Prime number
```

---

## 8. Reverse a Number

**How it works:** Inside a `while` loop, `% 10` grabs the last digit and `/ 10` chops it off. Each digit grabbed gets added to the end of the reversed number, until nothing is left of the original.

```c
#include <stdio.h>

int main() {
    int n, rev = 0, digit;

    printf("Enter a number: ");
    scanf("%d", &n);

    while (n != 0) {
        digit = n % 10;
        rev = rev * 10 + digit;
        n = n / 10;
    }

    printf("Reversed number = %d\n", rev);
    return 0;
}
```

**Sample Input / Output:**
```
Enter a number: 12345
Reversed number = 54321
```

---

## 9. Simple Calculator

**How it works:** You type two numbers and an operator (`+ - * /`), and a `switch` statement picks the right calculation. It also checks for division by zero so the program doesn't break.

```c
#include <stdio.h>

int main() {
    float a, b;
    char op;

    printf("Enter first number, operator (+ - * /), second number: ");
    scanf("%f %c %f", &a, &op, &b);

    switch (op) {
        case '+': printf("Result = %.2f\n", a + b); break;
        case '-': printf("Result = %.2f\n", a - b); break;
        case '*': printf("Result = %.2f\n", a * b); break;
        case '/':
            if (b != 0)
                printf("Result = %.2f\n", a / b);
            else
                printf("Error: Division by zero\n");
            break;
        default:
            printf("Invalid operator\n");
    }
    return 0;
}
```

**Sample Input / Output:**
```
Enter first number, operator (+ - * /), second number: 15 * 4
Result = 60.00
```

---

## 10. Multiplication Table

**How it works:** A `for` loop counts from 1 to 10 and prints each line of the table for whatever number you enter.

```c
#include <stdio.h>

int main() {
    int n, i;

    printf("Enter a number: ");
    scanf("%d", &n);

    for (i = 1; i <= 10; i++)
        printf("%d x %d = %d\n", n, i, n * i);
    return 0;
}
```

**Sample Input / Output:**
```
Enter a number: 7
7 x 1 = 7
7 x 2 = 14
7 x 3 = 21
7 x 4 = 28
7 x 5 = 35
7 x 6 = 42
7 x 7 = 49
7 x 8 = 56
7 x 9 = 63
7 x 10 = 70
```

---

## What I Learned

Writing these programs taught me:

- How to take input and show output with `printf()` and `scanf()`
- How to make decisions in code with `if`, `else if`, and `switch`
- How to repeat things with `for` and `while` loops
- How arithmetic, relational, and logical operators work together
- That a big problem gets much easier once you break it into small steps

## What's Next

I want to learn these topics next:

- Arrays and strings
- Functions and recursion
- Pointers
- Structures and file handling

---

If this helped you, I'd really appreciate a ⭐ on the repo. Happy coding!
