#include <stdio.h>

int main() {
    float celsius, fahrenheit;

    printf("Enter temperature in Celsius: ");
    scanf("%f", &celsius);

    fahrenheit = (celsius * 1.8) + 32;

    printf("%.2f°C is equal to %.2f°F\n", celsius, fahrenheit);

    if (celsius < 0) {
        printf("Freezing!\n");
    } else if (celsius > 30) {
        printf("Hot!\n");
    }

    return 0;
}
