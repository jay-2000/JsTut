# Day 4

- Comparisons
We know many comparison operators from maths.

In JavaScript they are written like this:

Greater/less than: a > b, a < b.
Greater/less than or equals: a >= b, a <= b.
Equals: a == b, please note the double equality sign == means the equality test, while a single one a = b means an assignment.
Not equals: In maths the notation is ≠, but in JavaScript it’s written as a != b.

- Boolean is the result

All comparison operators return a boolean value:

true – means “yes”, “correct” or “the truth”.
false – means “no”, “wrong” or “not the truth”.
For example:

alert( 2 > 1 );  // true (correct)

alert( 2 == 1 ); // false (wrong)

alert( 2 != 1 ); // true (correct)

A comparison result can be assigned to a variable, just like any value:

let result = 5 > 4; // assign the result of the comparison

alert( result ); // true