# Roman Numeral to Integer Converter

This repository contains a simple C program that converts Roman numerals into their integer equivalents. The program efficiently processes Roman numeral strings by analyzing each character and applying the appropriate rules for subtraction and addition.

## Overview

Roman numerals are composed of the characters `I`, `V`, `X`, `L`, `C`, `D`, and `M`, representing the integers 1, 5, 10, 50, 100, 500, and 1000, respectively. This program:
- Converts Roman numerals to integers using a helper function to map values.
- Handles special subtraction cases (e.g., `IV = 4`, `IX = 9`).
- Ensures efficient processing with a time complexity of **O(n)**, where `n` is the length of the Roman numeral string.

## Example Inputs and Outputs

| Roman Numeral | Integer Value |
|---------------|---------------|
| `III`         | `3`           |
| `IV`          | `4`           |
| `MCMXCIV`     | `1994`        |
| `XLII`        | `42`          |

---

## Code Breakdown

### getvalue(char c)
A helper function that maps Roman numeral characters to their respective integer values:

```c
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
romanToInt(char* s)
This function converts a Roman numeral string into its integer value by:

Iterating through the string.
Checking if the current Roman numeral value is less than the next one.
Subtracting the current value if smaller, or adding it otherwise.
c
Copy code
int romanToInt(char* s) {
    int total = 0;
    for (int i = 0; s[i] != '\0'; i++) {
        int current = getvalue(s[i]);
        int next = getvalue(s[i + 1]);
        if (current < next) {
            total -= current;
        } else {
            total += current;
        }
    }
    return total;
}
