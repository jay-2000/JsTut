# Day 0 

- Types of commenting :
// This is an in-line comment.

/* This is a
multi-line comment */

- JS data types :
undefined, null, boolean, string, symbol, bigint, number, and object.

- Declaring a variable( var is keyword)
 
 var ourName;

- semicolon (;) :
A semicolon may be ommitted in most caases when a line break exists
but putting a semicolon at the end of the statement is the best as well as safest practice for the programmers.

- use strict :
using "use strict" or 'use strict' the modern JS get recognised or modern mode is activated.

note: Make sure that "use strict" is at the top of your script , otherwise strict mode msy not be enabled.

- Variable :
It is used to store information . a variable is a "named storage" for data To create a variable in JS , use the let Keyword 

e.g.
let message;

we can put some data into it by using the assignment operator "=".

e.g.
let message;

message = "hello";

The string is now saved into the memory area associated with the variable we can access it using the variable name:

eg.
let message ;

message = 'hello';

alert(message); // shows the variable's content

To be concise, we can combine the variable declaration and assignment into a single line:

e.g.
let message = 'Hello!'; // define the variable and assign the value

alert(message); // Hello!

We can also declare multiple variables in one line:

e.g.
let user = 'John', age = 25, message = 'Hello';

Technically, all these variants do the same thing. So, it’s a matter of personal taste and aesthetics.

var instead of let
In older scripts, you may also find another keyword: var instead of let:

var message = 'Hello';

The var keyword is almost the same as let. It also declares a variable, but in a slightly different, “old-school” way.

There are subtle differences between let and var, but they do not matter for us yet. We’ll cover them in detail later.