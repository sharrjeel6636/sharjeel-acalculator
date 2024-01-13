#include <stdio.h>
#include <math.h>

// Basic Operations
float add(float a, float b) { return a + b; }
float subtract(float a, float b) { return a - b; }
float multiply(float a, float b) { return a * b; }
float divide(float a, float b) { return (b != 0) ? a / b : 0; }

// Trigonometric Operations
float trigOperation(float angle, char operation) {
    switch (operation) {
        case 's': return sin(angle);
        case 'c': return cos(angle);
        case 't': return tan(angle);
        case 'a': return asin(angle);
        case 'b': return acos(angle);
        case 'n': return atan(angle);
        default: return 0;
    }
}

// Algebraic Operations
float algebraicOperation(float num, char operation) {
    switch (operation) {
        case 'e': {
            float exponent; printf("Enter exponent: "); scanf("%f", &exponent);
            return pow(num, exponent);
        }
        case 'q': return sqrt(num);
        case 'u': return cbrt(num);
        case 'r': {
            float n; printf("Enter root index (n): "); scanf("%f", &n);
            return pow(num, 1.0 / n);
        }
        case 'f': return (num >= 0) ? tgamma(num + 1) : 0;
        case 'v': return fabs(num);
        default: return 0;
    }
}

// Logarithmic Operations
float logarithmicOperation(float num, char operation) {
    switch (operation) {
        case '1': return log10(num);
        case 'n': return log(num);
        case 'g': {
            float base; printf("Enter logarithm base: "); scanf("%f", &base);
            return log(num) / log(base);
        }
        default: return 0;
    }
}

int main() {
    float num1, num2, result;
    char operationType, operation;

    // Take input from the user
    printf("Enter first number: "); scanf("%f", &num1);
    printf("Enter operation type (b for Basic, t for Trigonometric, a for Algebraic, l for Logarithmic): "); scanf(" %c", &operationType);

    // Perform the selected operation type
    switch (operationType) {
        case 'b': // Basic Operations
            printf("Enter operation (+, -, *, /): "); scanf(" %c", &operation);
            printf("Enter second number: "); scanf("%f", &num2);
            switch (operation) {
                case '+': result = add(num1, num2); break;
                case '-': result = subtract(num1, num2); break;
                case '*': result = multiply(num1, num2); break;
                case '/': result = divide(num1, num2); break;
                default: printf("Invalid operation\n"); return 1;
            }
            break;

        case 't': // Trigonometric Operations
            printf("Enter trigonometric operation (s, c, t, a, b, n): "); scanf(" %c", &operation);
            result = trigOperation(num1, operation);
            break;

        case 'a': // Algebraic Operations
            printf("Enter algebraic operation (e, q, u, r, f, v): "); scanf(" %c", &operation);
            result = algebraicOperation(num1, operation);
            break;

        case 'l': // Logarithmic Operations
            printf("Enter logarithmic operation (1, n, g): "); scanf(" %c", &operation);
            result = logarithmicOperation(num1, operation);
            break;

        default:
            printf("Invalid operation type\n");
            return 1;
    }

    // Display the result
    printf("Result: %.2f\n", result);

    return 0;
}
