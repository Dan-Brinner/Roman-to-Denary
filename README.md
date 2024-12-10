# Roman to Denary Converter

**Description:**
This C program converts a Roman numeral string to its equivalent decimal (denary) integer value.

**How it Works:**

The `roman_to_denary` function:

1. Iterates through the Roman numeral string character by character.
2. Determines the value of the current Roman numeral character.
3. Compares the current value with the next character's value.
4. Handles subtractive notation: If the current value is less than the next, subtracts the current value from the total.
5. Handles additive notation: Otherwise, adds the current value to the total.

**Code Implementation:**

```c
#include <stdio.h>
#include <string.h>

int value(char r) {
    if (r == 'I')
        return 1;
    if (r == 'V')
        return 5;
    if (r == 'X')
        return 10;
    if (r == 'L')
        return 50;
    if (r == 'C')
        return 100;
    if (r == 'D')
        return 500;
    if (r == 'M')
        return 1000;
    return -1;
}

int romanToDecimal(char* str) {
    int res = 0;
    int i = 0;
    for (; str[i]; i++) {
        int s1 = value(str[i]);
        if (i + 1 < strlen(str)) {
            int s2 = value(str[i + 1]);
            if (s1 < s2) {
                res -= s1;
            } else {
                res += s1;
            }
        } else {
            res += s1;
        }
    }
    return res;
}

int main() {
    char str[15];
    printf("Enter Roman Numeral: ");
    scanf("%s", str);
    printf("Integer form of Roman Numeral is %d \n", romanToDecimal(str));
    return 0;
}
