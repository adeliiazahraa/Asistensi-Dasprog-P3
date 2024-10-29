# Asistensi-Dasprog-P3
## Soal
### Kode
''' c

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int add(int a, int b) {
    return a + b;
}

int subtract(int a, int b) {
    return a - b;
}

int multiply(int a, int b) {
    return a * b;
}

float divide(int a, int b) {
    if (b == 0) {
        printf("Error: Pembagian tidak dapat dengan nol\n");
        return 0; 
    }
    return (float)a / b;
}

int factorial(int n) {
    if (n < 0) {
        printf("Error: Faktorial dari bilangan negatif tidak ada\n");
        return -1;
    }
    int result = 1;
    for (int i = 2; i <= n; i++) {
        result *= i;
    }
    return result;
}

int gcd(int a, int b) {
    while (b) {
        int temp = b;
        b = a % b;
        a = temp;
    }
    return a;
}

int lcm(int a, int b) {
    return (a * b) / gcd(a, b);
}

int main() {
    printf("Kalkulator Sederhana\n");
    printf("Format input: OPERATOR OPERAND1 OPERAND2 (contoh: ADD 4 5)\n");
    printf("Ketik 'EXIT' untuk keluar\n");

    char input[100]; 

    while (1) {
        printf("Masukkan perhitungan: ");
        fgets(input, sizeof(input), stdin); 
        
        input[strcspn(input, "\n")] = 0;

        if (strcmp(input, "EXIT") == 0) {
            break; 
        }

        char operator[10];
        int operand1, operand2;

        int count = sscanf(input, "%s %d %d", operator, &operand1, &operand2);

        if (count == 3) {
            if (strcmp(operator, "ADD") == 0) {
                printf("%d\n", add(operand1, operand2));
            } else if (strcmp(operator, "SUBTRACT") == 0) {
                printf("%d\n", subtract(operand1, operand2));
            } else if (strcmp(operator, "MULTIPLY") == 0) {
                printf("%d\n", multiply(operand1, operand2));
            } else if (strcmp(operator, "DIVIDE") == 0) {
                printf("%.2f\n", divide(operand1, operand2));
            } else if (strcmp(operator, "LCM") == 0) {
                printf("%d\n", lcm(operand1, operand2));
            } else if (strcmp(operator, "GCD") == 0) {
                printf("%d\n", gcd(operand1, operand2));
            } else {
                printf("Operator tidak dikenal.\n");
            }
        } else if (count == 2) {
            if (strcmp(operator, "FACTORIAL") == 0) {
                printf("%d\n", factorial(operand1));
            } else {
                printf("Operator tidak dikenal.\n");
            }
        } else {
            printf("Format input tidak valid.\n");
        }
    }

    printf("Kalkulator ditutup.\n");
    return 0;
}
