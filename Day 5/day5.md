# Day 5

- Conditional branching: if, '?'

Sometimes, we need to perform different actions based on different conditions.

To do that, we can use the if statement and the conditional operator ?, that’s also called a “question mark” operator.

- The “if” statement

The if(...) statement evaluates a condition in parentheses and, if the result is true, executes a block of code.

For example:

```
let year = prompt('In which year was ECMAScript-2015 specification published?', '');

if (year == 2015) alert( 'You are right!' );
```

In the example above, the condition is a simple equality check (year == 2015), but it can be much more complex.

If we want to execute more than one statement, we have to wrap our code block inside curly braces:

```
if (year == 2015) {
  alert( "That's correct!" );
  alert( "You're so smart!" );
}
```

We recommend wrapping your code block with curly braces {} every time you use an if statement, even if there is only one statement to execute. Doing so improves readability.

- Boolean conversion

The if (…) statement evaluates the expression in its parentheses and converts the result to a boolean.

Let’s recall the conversion rules from the chapter Type Conversions:

A number 0, an empty string "", null, undefined, and NaN all become false. Because of that they are called “falsy” values.
Other values become true, so they are called “truthy”.
So, the code under this condition would never execute:

```
if (0) { // 0 is falsy
  ...
}
```

…and inside this condition – it always will:

```
if (1) { // 1 is truthy
  ...
}
```

We can also pass a pre-evaluated boolean value to if, like this:

```
let cond = (year == 2015); // equality evaluates to true or false

if (cond) {
  ...
}
```
- The “else” clause

The if statement may contain an optional “else” block. It executes when the condition is falsy.

For example:

```
let year = prompt('In which year was the ECMAScript-2015 specification published?', '');

if (year == 2015) {
  alert( 'You guessed it right!' );
} else {
  alert( 'How can you be so wrong?' ); // any value except 2015
}
```

- Several conditions: “else if”

Sometimes, we’d like to test several variants of a condition. The else if clause lets us do that.

For example:

```
let year = prompt('In which year was the ECMAScript-2015 specification published?', '');

if (year < 2015) {
  alert( 'Too early...' );
} else if (year > 2015) {
  alert( 'Too late' );
} else {
  alert( 'Exactly!' );
}
```

In the code above, JavaScript first checks year < 2015. If that is falsy, it goes to the next condition year > 2015. If that is also falsy, it shows the last alert.

There can be more else if blocks. The final else is optional.

- Conditional operator ‘?’

Sometimes, we need to assign a variable depending on a condition.

For instance:

```
let accessAllowed;
let age = prompt('How old are you?', '');

if (age > 18) {
  accessAllowed = true;
} else {
  accessAllowed = false;
}

alert(accessAllowed);
```

The so-called “conditional” or “question mark” operator lets us do that in a shorter and simpler way.

The operator is represented by a question mark ?. Sometimes it’s called “ternary”, because the operator has three operands. It is actually the one and only operator in JavaScript which has that many.

The syntax is:

```
let result = condition ? value1 : value2;
```

The condition is evaluated: if it’s truthy then value1 is returned, otherwise – value2.

For example:

```
let accessAllowed = (age > 18) ? true : false;
```

Technically, we can omit the parentheses around age > 18. The question mark operator has a low precedence, so it executes after the comparison >.

This example will do the same thing as the previous one:

```
// the comparison operator "age > 18" executes first anyway
// (no need to wrap it into parentheses)
let accessAllowed = age > 18 ? true : false;
```

But parentheses make the code more readable, so we recommend using them.

Please note:
In the example above, you can avoid using the question mark operator because the comparison itself returns true/false:

```
// the same
let accessAllowed = age > 18;
```

- Multiple ‘?’

A sequence of question mark operators ? can return a value that depends on more than one condition.

For instance:

```
let age = prompt('age?', 18);

let message = (age < 3) ? 'Hi, baby!' :
  (age < 18) ? 'Hello!' :
  (age < 100) ? 'Greetings!' :
  'What an unusual age!';

alert( message );
```

It may be difficult at first to grasp what’s going on. But after a closer look, we can see that it’s just an ordinary sequence of tests:

The first question mark checks whether age < 3.

If true – it returns 'Hi, baby!'. Otherwise, it continues to the expression after the colon ‘":"’, checking age < 18.

If that’s true – it returns 'Hello!'. Otherwise, it continues to the expression after the next colon ‘":"’, checking age < 100.

If that’s true – it returns 'Greetings!'. Otherwise, it continues to the expression after the last colon ‘":"’, returning 'What an unusual age!'.

Here’s how this looks using if..else:

```
if (age < 3) {
  message = 'Hi, baby!';
} else if (age < 18) {
  message = 'Hello!';
} else if (age < 100) {
  message = 'Greetings!';
} else {
  message = 'What an unusual age!';
}
```

- Non-traditional use of ‘?’
Sometimes the question mark ? is used as a replacement for if:

```
let company = prompt('Which company created JavaScript?', '');

(company == 'Netscape') ?
   alert('Right!') : alert('Wrong.');
```

Depending on the condition company == 'Netscape', either the first or the second expression after the ? gets executed and shows an alert.

We don’t assign a result to a variable here. Instead, we execute different code depending on the condition.

It’s not recommended to use the question mark operator in this way.

The notation is shorter than the equivalent if statement, which appeals to some programmers. But it is less readable.

Here is the same code using if for comparison:

```
let company = prompt('Which company created JavaScript?', '');

if (company == 'Netscape') {
  alert('Right!');
} else {
  alert('Wrong.');
}
```

Our eyes scan the code vertically. Code blocks which span several lines are easier to understand than a long, horizontal instruction set.

The purpose of the question mark operator ? is to return one value or another depending on its condition. Please use it for exactly that. Use if when you need to execute different branches of code.

- Logical operators

There are four logical operators in JavaScript: || (OR), && (AND), ! (NOT), ?? (Nullish Coalescing). Here we cover the first three, the ?? operator is in the next article.

Although they are called “logical”, they can be applied to values of any type, not only boolean. Their result can also be of any type.

Let’s see the details.

|| (OR)
The “OR” operator is represented with two vertical line symbols:

```
result = a || b;
```

In classical programming, the logical OR is meant to manipulate boolean values only. If any of its arguments are true, it returns true, otherwise it returns false.

In JavaScript, the operator is a little bit trickier and more powerful. But first, let’s see what happens with boolean values.

There are four possible logical combinations:

```
alert( true || true );   // true
alert( false || true );  // true
alert( true || false );  // true
alert( false || false ); // false
```

As we can see, the result is always true except for the case when both operands are false.

If an operand is not a boolean, it’s converted to a boolean for the evaluation.

For instance, the number 1 is treated as true, the number 0 as false:

```
if (1 || 0) { // works just like if( true || false )
  alert( 'truthy!' );
}
```

Most of the time, OR || is used in an if statement to test if any of the given conditions is true.

For example:

```
let hour = 9;

if (hour < 10 || hour > 18) {
  alert( 'The office is closed.' );
}
```

We can pass more conditions:

```
let hour = 12;
let isWeekend = true;

if (hour < 10 || hour > 18 || isWeekend) {
  alert( 'The office is closed.' ); // it is the weekend
}
```

- OR "||" finds the first truthy value

The logic described above is somewhat classical. Now, let’s bring in the “extra” features of JavaScript.

The extended algorithm works as follows.

Given multiple OR’ed values:

```
result = value1 || value2 || value3;
```

The OR || operator does the following:

Evaluates operands from left to right.
For each operand, converts it to boolean. If the result is true, stops and returns the original value of that operand.
If all operands have been evaluated (i.e. all were false), returns the last operand.
A value is returned in its original form, without the conversion.

In other words, a chain of OR || returns the first truthy value or the last one if no truthy value is found.

For instance:

```
alert( 1 || 0 ); // 1 (1 is truthy)

alert( null || 1 ); // 1 (1 is the first truthy value)
alert( null || 0 || 1 ); // 1 (the first truthy value)

alert( undefined || null || 0 ); // 0 (all falsy, returns the last value)
```

This leads to some interesting usage compared to a “pure, classical, boolean-only OR”.

Getting the first truthy value from a list of variables or expressions.

For instance, we have firstName, lastName and nickName variables, all optional (i.e. can be undefined or have falsy values).

Let’s use OR || to choose the one that has the data and show it (or "Anonymous" if nothing set):

```
let firstName = "";
let lastName = "";
let nickName = "SuperCoder";

alert( firstName || lastName || nickName || "Anonymous"); // SuperCoder
```

If all variables were falsy, "Anonymous" would show up.

Short-circuit evaluation.

Another feature of OR || operator is the so-called “short-circuit” evaluation.

It means that || processes its arguments until the first truthy value is reached, and then the value is returned immediately, without even touching the other argument.

The importance of this feature becomes obvious if an operand isn’t just a value, but an expression with a side effect, such as a variable assignment or a function call.

In the example below, only the second message is printed:

```
true || alert("not printed");
false || alert("printed");
```

In the first line, the OR || operator stops the evaluation immediately upon seeing true, so the alert isn’t run.

Sometimes, people use this feature to execute commands only if the condition on the left part is falsy.

- && (AND)

The AND operator is represented with two ampersands &&:

```
result = a && b;
```

In classical programming, AND returns true if both operands are truthy and false otherwise:

```
alert( true && true );   // true
alert( false && true );  // false
alert( true && false );  // false
alert( false && false ); // false
```

An example with if:

```
let hour = 12;
let minute = 30;

if (hour == 12 && minute == 30) {
  alert( 'The time is 12:30' );
}
```

Just as with OR, any value is allowed as an operand of AND:

```
if (1 && 0) { // evaluated as true && false
  alert( "won't work, because the result is falsy" );
}
```

- AND “&&” finds the first falsy value

Given multiple AND’ed values:

```
result = value1 && value2 && value3;
```

The AND && operator does the following:

Evaluates operands from left to right.
For each operand, converts it to a boolean. If the result is false, stops and returns the original value of that operand.
If all operands have been evaluated (i.e. all were truthy), returns the last operand.
In other words, AND returns the first falsy value or the last value if none were found.

The rules above are similar to OR. The difference is that AND returns the first falsy value while OR returns the first truthy one.

Examples:

```
// if the first operand is truthy,
// AND returns the second operand:
alert( 1 && 0 ); // 0
alert( 1 && 5 ); // 5

// if the first operand is falsy,
// AND returns it. The second operand is ignored
alert( null && 5 ); // null
alert( 0 && "no matter what" ); // 0
```

We can also pass several values in a row. See how the first falsy one is returned:

```
alert( 1 && 2 && null && 3 ); // null
```

When all values are truthy, the last value is returned:

```
alert( 1 && 2 && 3 ); // 3, the last one
```

- ! (NOT)

The boolean NOT operator is represented with an exclamation sign !.

The syntax is pretty simple:

```
result = !value;
```

The operator accepts a single argument and does the following:

Converts the operand to boolean type: true/false.
Returns the inverse value.
For instance:

```
alert( !true ); // false
alert( !0 ); // true
```

A double NOT !! is sometimes used for converting a value to boolean type:

```
alert( !!"non-empty string" ); // true
alert( !!null ); // false
```

That is, the first NOT converts the value to boolean and returns the inverse, and the second NOT inverses it again. In the end, we have a plain value-to-boolean conversion.

There’s a little more verbose way to do the same thing – a built-in Boolean function:

```
alert( Boolean("non-empty string") ); // true
alert( Boolean(null) ); // false
```

The precedence of NOT ! is the highest of all logical operators, so it always executes first, before && or ||.

- Nullish coalescing operator '??'

A recent addition
This is a recent addition to the language. Old browsers may need polyfills.
The nullish coalescing operator is written as two question marks ??.

As it treats null and undefined similarly, we’ll use a special term here, in this article. We’ll say that an expression is “defined” when it’s neither null nor undefined.

The result of a ?? b is:

if a is defined, then a,
if a isn’t defined, then b.
In other words, ?? returns the first argument if it’s not null/undefined. Otherwise, the second one.

The nullish coalescing operator isn’t anything completely new. It’s just a nice syntax to get the first “defined” value of the two.

We can rewrite result = a ?? b using the operators that we already know, like this:

```
result = (a !== null && a !== undefined) ? a : b;
```

Now it should be absolutely clear what ?? does. Let’s see where it helps.

The common use case for ?? is to provide a default value for a potentially undefined variable.

For example, here we show user if defined, otherwise Anonymous:

```
let user;

alert(user ?? "Anonymous"); // Anonymous (user not defined)
```

Here’s the example with user assigned to a name:

```
let user = "John";

alert(user ?? "Anonymous"); // John (user defined)
```

We can also use a sequence of ?? to select the first value from a list that isn’t null/undefined.

Let’s say we have a user’s data in variables firstName, lastName or nickName. All of them may be not defined, if the user decided not to enter a value.

We’d like to display the user name using one of these variables, or show “Anonymous” if all of them aren’t defined.

Let’s use the ?? operator for that:

```
let firstName = null;
let lastName = null;
let nickName = "Supercoder";

// shows the first defined value:
alert(firstName ?? lastName ?? nickName ?? "Anonymous"); // Supercoder
```

- Comparison with ||

The OR || operator can be used in the same way as ??, as it was described in the previous chapter.

For example, in the code above we could replace ?? with || and still get the same result:

```
let firstName = null;
let lastName = null;
let nickName = "Supercoder";

// shows the first truthy value:
alert(firstName || lastName || nickName || "Anonymous"); // Supercoder
```

Historically, the OR || operator was there first. It exists since the beginning of JavaScript, so developers were using it for such purposes for a long time.

On the other hand, the nullish coalescing operator ?? was added to JavaScript only recently, and the reason for that was that people weren’t quite happy with ||.

The important difference between them is that:

|| returns the first truthy value.
?? returns the first defined value.
In other words, || doesn’t distinguish between false, 0, an empty string "" and null/undefined. They are all the same – falsy values. If any of these is the first argument of ||, then we’ll get the second argument as the result.

In practice though, we may want to use default value only when the variable is null/undefined. That is, when the value is really unknown/not set.

For example, consider this:

```
let height = 0;

alert(height || 100); // 100
alert(height ?? 100); // 0
```

The height || 100 checks height for being a falsy value, and it’s 0, falsy indeed.

so the result of || is the second argument, 100.

The height ?? 100 checks height for being null/undefined, and it’s not,
so the result is height “as is”, that is 0.

In practice, the zero height is often a valid value, that shouldn’t be replaced with the default. So ?? does just the right thing.

- Precedence

The precedence of the ?? operator is about the same as ||, just a bit lower. It equals 5 in the MDN table, while || is 6.

That means that, just like ||, the nullish coalescing operator ?? is evaluated before = and ?, but after most other operations, such as +, *.

So if we’d like to choose a value with ?? in an expression with other operators, consider adding parentheses:

```
let height = null;
let width = null;

// important: use parentheses
let area = (height ?? 100) * (width ?? 50);

alert(area); // 5000
```

Otherwise, if we omit parentheses, then as * has the higher precedence than ??, it would execute first, leading to incorrect results.

```
// without parentheses
let area = height ?? 100 * width ?? 50;

// ...works the same as this (probably not what we want):
let area = height ?? (100 * width) ?? 50;
```

- Using ?? with && or ||

Due to safety reasons, JavaScript forbids using ?? together with && and || operators, unless the precedence is explicitly specified with parentheses.

The code below triggers a syntax error:

```
let x = 1 && 2 ?? 3; // Syntax error
```

The limitation is surely debatable, it was added to the language specification with the purpose to avoid programming mistakes, when people start to switch from || to ??.

Use explicit parentheses to work around it:

```
let x = (1 && 2) ?? 3; // Works

alert(x); // 2
```

- Loops: while and for

We often need to repeat actions.

For example, outputting goods from a list one after another or just running the same code for each number from 1 to 10.

Loops are a way to repeat the same code multiple times.

The “while” loop
The while loop has the following syntax:

```
while (condition) {
  // code
  // so-called "loop body"
}
```

While the condition is truthy, the code from the loop body is executed.

For instance, the loop below outputs i while i < 3:

```
let i = 0;
while (i < 3) { // shows 0, then 1, then 2
  alert( i );
  i++;
}
```

A single execution of the loop body is called an iteration. The loop in the example above makes three iterations.

If i++ was missing from the example above, the loop would repeat (in theory) forever. In practice, the browser provides ways to stop such loops, and in server-side JavaScript, we can kill the process.

Any expression or variable can be a loop condition, not just comparisons: the condition is evaluated and converted to a boolean by while.

For instance, a shorter way to write while (i != 0) is while (i):

```
let i = 3;
while (i) { // when i becomes 0, the condition becomes falsy, and the loop stops
  alert( i );
  i--;
}
```

- The “do…while” loop

The condition check can be moved below the loop body using the do..while syntax:

```
do {
  // loop body
} while (condition);
```

The loop will first execute the body, then check the condition, and, while it’s truthy, execute it again and again.

For example:

```
let i = 0;
do {
  alert( i );
  i++;
} while (i < 3);
```

This form of syntax should only be used when you want the body of the loop to execute at least once regardless of the condition being truthy. Usually, the other form is preferred: while(…) {…}.