Here is a clean, well-formatted `README.md` file customized for these Dynamic Programming C implementations:

```markdown
# Dynamic Programming Algorithms in C

A collection of foundational Dynamic Programming (DP) algorithm implementations in C. This repository covers classic problems involving overlapping subproblems and optimal substructure.

---

## 📌 Table of Contents
- [Overview](#-overview)
- [How to Run](#-how-to-run)
- [Algorithms & Source Code](#-algorithms--source-code)
  - [1. Binomial Coefficient](#1-binomial-coefficient)
  - [2. Fibonacci Series](#2-fibonacci-series)
  - [3. Matrix Chain Multiplication](#3-matrix-chain-multiplication)

---

## 🚀 Overview

| Algorithm | Method | Time Complexity | Space Complexity |
| :--- | :--- | :---: | :---: |
| **Binomial Coefficient** | Dynamic Programming (2D Table) | O(n × r) | O(n × r) |
| **Fibonacci Series** | Dynamic Programming (1D Table) | O(n) | O(n) |
| **Matrix Chain Multiplication** | Dynamic Programming (2D Table) | O(n³) | O(n²) |

---

## 🛠 How to Run

1. **Compile using GCC:**
   ```bash
   gcc filename.c -o output

```

2. **Execute:**
```bash
./output

```



---

## 💻 Algorithms & Source Code

### 1. Binomial Coefficient

Computes $C(n, r)$ using Pascal's Triangle identity: $C(n, r) = C(n-1, r-1) + C(n-1, r)$.

```c
#include <stdio.h>

int n, r;

int bionomial() {
    int dp[n + 1][r + 1];
    for (int i = 0; i <= n; i++) {
        for (int j = 0; j <= r; j++) {
            if (j == 0 || j == i) {
                dp[i][j] = 1;
            } else if (j < i) {
                dp[i][j] = dp[i - 1][j - 1] + dp[i - 1][j];
            }
        }
    }
    return dp[n][r];
}

int main() {
    printf("Enter value of n: ");
    scanf("%d", &n);
    printf("Enter value of r: ");
    scanf("%d", &r);
    printf("Binomial coefficient C(%d, %d): %d\n", n, r, bionomial());
    return 0;
}

```

---

### 2. Fibonacci Series

Generates the Fibonacci sequence up to $N$ terms using bottom-up tabulating.

```c
#include <stdio.h>
#define max 100

int main() {
    int n, dp[max];
    printf("Enter value of n: ");
    scanf("%d", &n);
    
    dp[0] = 0;
    dp[1] = 1;
    for (int i = 2; i <= n; i++) {
        dp[i] = dp[i - 1] + dp[i - 2];
    }
    
    printf("Fibonacci series: ");
    for (int i = 0; i < n; i++) {
        printf("%d ", dp[i]);
    }
    printf("\n");
    return 0;
}

```

---

### 3. Matrix Chain Multiplication

Finds the most efficient way to multiply a chain of matrices by determining the minimum scalar multiplications needed.

```c
#include <stdio.h>
#define MAX 1000 

int arr[MAX], dp[MAX][MAX], n;

int matrix_chain() {
    int l, i, j, k, cost;
    for (i = 1; i <= n; i++) {
        dp[i][i] = 0;
    }
    for (l = 2; l <= n; l++) {
        for (i = 1; i <= n - l + 1; i++) {
            j = i + l - 1;
            dp[i][j] = 999999;
            for (k = i; k < j; k++) {
                cost = dp[i][k] + dp[k + 1][j] + arr[i - 1] * arr[k] * arr[j];
                if (cost < dp[i][j]) {
                    dp[i][j] = cost;
                }
            }
        }
    }
    return dp[1][n];
}

int main() {
    printf("Enter number of matrices: ");
    scanf("%d", &n);
    printf("Enter %d dimensions: ", n + 1);
    for (int i = 0; i <= n; i++) {
        scanf("%d", &arr[i]);
    }
    printf("Minimum multiplication cost = %d\n", matrix_chain());
    return 0;
}

```

```

```
