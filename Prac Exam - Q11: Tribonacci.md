Question 11 (●●●●):
# The Trouble with Tribonacci

The Tribonacci series is very similar to the Fibonacci series. 
The only difference between the two is that in the Tribonacci series, 
you add the previous three terms instead of the previous two.

The first three values in the Tribonacci series are, by definition, 1.
After the first three values each value is the sum of the previous three.
Hence, the Tribonacci series commences: 1,1,1,3,5,9,17,31,57,105, ...

Unfortunately, the Tribonacci series grows quickly and your program may be asked to calculate any of the first 5000 Tribonacci values.
This means the values that your program must calculate are far too large to fit in any standard C numeric data type.

So how to do?
The orignal ieda is to declare 4 integer, 3 nums to calculate and 1 "temp".
BUT...It does not work...

Why?

C cannot handle such long number!

Solution:

```C
#include <stdio.h>
#include <stdlib.h>

#define MAX_DIGITS 1500

void add_big_numbers(int *result, int *a, int *b, int *c) {
    int carry = 0;
    for (int i = MAX_DIGITS - 1; i >= 0; i--) {
        int sum = a[i] + b[i] + c[i] + carry;
        result[i] = sum % 10;
        carry = sum / 10;
    }
}

void print_big_number(int *number) {
    int start = 0;
    while (start < MAX_DIGITS && number[start] == 0) {
        start++;
    }
    if (start == MAX_DIGITS) {
        printf("0");
    } else {
        for (int i = start; i < MAX_DIGITS; i++) {
            printf("%d", number[i]);
        }
    }
    printf("\n");
}

int main(void) {
    int count;
    scanf("%d", &count);

    int trib1[MAX_DIGITS] = {0};
    int trib2[MAX_DIGITS] = {0};
    int trib3[MAX_DIGITS] = {0};
    int trib_next[MAX_DIGITS] = {0};

    trib1[MAX_DIGITS - 1] = 1;
    trib2[MAX_DIGITS - 1] = 1;
    trib3[MAX_DIGITS - 1] = 1;

    if (count == 1 || count == 2 || count == 3) {
        printf("1\n");
        return 0;
    }

    for (int i = 4; i <= count; i++) {
        add_big_numbers(trib_next, trib1, trib2, trib3);

        for (int j = 0; j < MAX_DIGITS; j++) {
            trib1[j] = trib2[j];
            trib2[j] = trib3[j];
            trib3[j] = trib_next[j];
        }
    }

    print_big_number(trib3);

    return 0;	
}

```







