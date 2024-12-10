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

int getvalue(char c) {
    switch(c) {
        case 'I': return 1;
        case 'V': return 5;
        case 'X': return 10;
        case 'L': return 50;
        case 'C': return 100;
        case 'D': return 500;
        case 'M': return 1000;
        default: return 0;
    }
}

int romanToInt(char* s) {
    int total = 0;
    for(int i = 0; s[i] != '\0'; i++) {
        int current = getvalue(s[i]);
        int next = getvalue(s[i+1]);
        if(current < next) {
            total -= current; // Subtraction case (e.g., IV, IX)
        } else {
            total += current; // Regular case (e.g., VI, VII)
        }
    }
    return total;
}

int main() {
    char roman[] = "MCMXCIV";  // Example Roman numeral
    int result = romanToInt(roman);
    printf("The integer value of %s is: %d\n", roman, result);
    return 0;
}
