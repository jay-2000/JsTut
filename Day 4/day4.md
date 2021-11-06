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

- String comparison

To see whether a string is greater than another, JavaScript uses the so-called “dictionary” or “lexicographical” order.

In other words, strings are compared letter-by-letter.

For example:

alert( 'Z' > 'A' ); // true

alert( 'Glow' > 'Glee' ); // true

alert( 'Bee' > 'Be' ); // true

The algorithm to compare two strings is simple:

Compare the first character of both strings.

If the first character from the first string is greater (or less) than the other string’s, then the first string is greater (or less) than the second. We’re done.

Otherwise, if both strings’ first characters are the same, compare the second characters the same way.

Repeat until the end of either string.

If both strings end at the same length, then they are equal. Otherwise, the longer string is greater.

In the first example above, the comparison 'Z' > 'A' gets to a result at the first step.

The second comparison 'Glow' and 'Glee' needs more steps as strings are compared character-by-character:

G is the same as G.

l is the same as l.

o is greater than e. Stop here. The first string is greater.

- Comparison of different types

When comparing values of different types, JavaScript converts the values to numbers.

For example:

alert( '2' > 1 ); // true, string '2' becomes a number 2

alert( '01' == 1 ); // true, string '01' becomes a number 1

For boolean values, true becomes 1 and false becomes 0.

For example:

alert( true == 1 ); // true

alert( false == 0 ); // true

- Strict equality

A regular equality check == has a problem. It cannot differentiate 0 from false:

alert( 0 == false ); // true

The same thing happens with an empty string:

alert( '' == false ); // true

This happens because operands of different types are converted to numbers by the equality operator ==. An empty string, just like false, becomes a zero.

What to do if we’d like to differentiate 0 from false?

A strict equality operator === checks the equality without type conversion.

In other words, if a and b are of different types, then a === b immediately returns false without an attempt to convert them.

Let’s try it:

alert( 0 === false ); // false, because the types are different

There is also a “strict non-equality” operator !== analogous to !=.

The strict equality operator is a bit longer to write, but makes it obvious what’s going on and leaves less room for errors.