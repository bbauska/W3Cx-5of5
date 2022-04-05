#### Module 2: Adding interactivity to HTML documents   2.1 Introduction - Module 2   Module 2 outline
# Module 2 outline
### What you will learn in Module 2

* Conditional statements and logical operators: if...then...else, etc.
* Loops: iterating on collections, doing things repeatedly
* Events: detect keys, mouse clicks or moves, window resize events, etc.
* DOM: interacting with the content of the HTML page (selecting elements, modifying them, adding and removing new ones)
* HTML5 canvas intro: learn how to draw and animate simple shapes in a HTML5 canvas



#### Module 2: Adding interactivity to HTML documents   2.2 Conditional statements, loops and logical operators   Boolean values and logical operators

# Boolean values and logical operators

### Live coding video: boolean value,, if...else statement and comparison operators


>! missing video/transcript

### Boolean values and logical operators

Introduction

Before talking about how your JavaScript program can make decisions, such as **if this condition is fulfilled then I'll do this, 
otherwise I'll do that...**, we need to define a few more concepts.

We will start with **boolean values** and **logical operators**.

#### Boolean values

The boolean type represents a logical entity having two values: **true** and **false**.

Use of the keywords true and false:

```javascript
var b = true; 
 
var b = false;
```

A boolean variable should not be enclosed in quotation marks, otherwise it becomes a string variable:
```javascript
var b = 'true'; // b is not a boolean but a string
```

#### Undefined and null values

#### Undefined

undefined is returned when a variable has not been assigned:

```javascript
var foo;
> foo
undefined
 
> typeof foo;
'undefined'
 
>if (foo === undefined) {
    console.log('The variable foo has no value and is undefined');
}
'The variable foo has no value and is undefined'
```
The above example shows how we can test whether a variable has a value (line 8 uses a conditional statement).

The keyword "undefined" is part of the JavaScript language, so you can assign the undefined value to a variable:

```javascript
> var foo = undefined; // equivalent to var foo; without giving any value
undefined
 
> foo;
undefined
```

`var foo;` and `var foo = undefined;` are equivalent but we recommend that you use the first version to declare the variable (it is shorter, and that reduces the code).

If you try to access a variable that has not been declared before, a `ReferenceError` will be raised. But the `typeof` operator will return "undefined":

```javascript
> bar;
ReferenceError
 
> typeof bar;
'undefined'
Logical operators
```

#### Logical operators

The logical operators are as follows: 

*  && (AND)  

```javascript 
if ((x  > 0) && (x < 10)) { 
	console.log('x is strictly positive and less than 10'); 
}
```

*  || (OR) 

```javascript
if ((x  > 0) || (x == -5)) { 
	console.log('x is positive or equal to -5'); 
}
```

*  ! (NOT) 

```javascript
if (!(x  > 0)) { 
	console.log('x is not positive (x is less or equal to 0'); 
}
```
			 
`&&`, `||` operators are binary, `!` is unary. 


```javascript
var b = !true; 
b; //false
 
var b = !!true;
b; //true
 
var b = "one"; 
!b;   false // implicit conversion of "one" to a boolean value
 
var b = "one"; // implicit conversion of "one" to a boolean value
!!b; //true

```

In an expression with logical operators, as shown in lines 8 and 11 of the previous example, non-boolean values are implicitly converted to boolean.

#### Lazy evaluation or short-circuit evaluation:

Logical expressions are evaluated from left to right. JavaScript uses a mechanism known as **short-circuit evaluation** to prevent 
the second, third, and nth conditions from being tested in certain cases: 

* **false && something (an expression)**  is always false, and the part to the right of `&&` operator is not tested.
* **true || something (an expression)** is evaluated to true, and the part to the right of the `||` operator is not tested.

Examples:

```javascript
var b = 5;
var c = 6;
 
if ((b === 5) || (b === 6))  { //the second part is never tested
    console.log('b is equal to 5 or equal to 6');
}
 
if ((b === 5) && (c === 6)) {  // second part is evaluated
    console.log('b  is equal to 5 and c is equal to 6');
}
 
if ((b === 15) && (c === 6)) {  // second part is never evaluated
    console.log('b  is equal to 5 and c is equal to 6');
} else {
    console.log('b not equal to 15 or c not equal to 6');
}

```

### Implicit conversions of non boolean values in expressions

Used with logical operators or within statements, non-boolean values are implicitly converted to booleans.  

### All the following values are evaluated as false :

1. false
2. undefined
3. null
4. 0
5. NaN
6. the empty string ''

### Everything else is evaluated as true!


```javascript
var boo = 'hello' && 'world';

```
***Great example***
boo equals 'world' because 'hello' is a string value that is evaluated as true.


```javascript
var boo2 = (0/0) || 43.2 ;

```
boo2 equals `43.2` because the expression 0/0 equals `NaN`, which is evaluated as `false`.

Question:

What is the value of the variable myNumber after the execution of this code? 

```javascript
var myNumber = !1;
 
if(myNumber == null){
   myNumber = 3;
}
 
myNumber = myNumber || 2;

```

### Comparison Operators

* Equal ==
* Not equal !=
* Greater than >
* Greater than or equal >=
* Less than <
* Less than or equal to <=
* Strict equal ===
* Strict not equal !==

### What is the difference between == and === in JavaScript?

### Equal (==)

Returns true if the operands are strictly equal with type conversion.

### Strict equal (===)

Returns true if the operands are strictly equal with no type conversion.

The triple-equals operator never does type coercion. It returns true if both operands reference the same object, or in the case of 
value types, have the same value.

Some examples :

```javascript
1 == 1 ;
//true
 
1 == 2 ;
//false
 
/* Here, the interpreter will try to convert the string ‘1’
into a number before doing the comparison */
 
1 == '1';
//true :
 
 
//with strict equal, no conversion:
 
1 === 1;
//true
1 === '1';
//false

```

### Depending on the context, generally strict equal (or strict not equal) is preferred. 

### Best practice for beginners: always use === or !== for comparisons.



Here's an interesting article about this question:

"Why you should use strict equal" (Impressive Webs, March 1st, 2012)
https://www.impressivewebs.com/why-use-triple-equals-javascipt/

#### Specific case of NaN

As we have already seen, JavaScript has some special values. One of them is NaN: **Not-a-Number**. 

NaN has this special property : 

```javascript
NaN == NaN;
// false
 
NaN === NaN;
// false

```

`Nan` is equal to nothing - not even to itself!  But you do have a function to check the `NaN` value:  `isNaN(expr)` 

* `isNaN`: returns true if the argument coerces to `NaN`, and otherwise returns `false`.


```javascript
isNaN(NaN);
// true
 
isNaN(0/0);
// true
 
isNaN(12);
// false
 
isNaN('foo');
// true

```

A reliable way for ECMAScript code to test if a value X is a `NaN`, is an expression of the form `X !== X`. The result will be `true` if, 
and only if, `X` is a `NaN`. (see the isNan documentation).


```javascript
var num =0/0;
 
if(isNaN(num)){
   num = 0;
}
//shortened version with the conditional operator
var num = isNaN(num) ? 0 : num
 
//version with logical operator (implicit conversion)
var num = num || 0;
 
/*
   <=> num = NaN || 0
 
   <=> num = false || 0
*/
 
num;
//returns 0 in this three cases

```


Of course 0/0 rarely happens, but there are other cases where NaN can appear, for example:

* `parseInt('foo');`  returns `NaN`   //parseInt tries to convert a String to a Number 
* `Math.sqrt(-1);` return `NaN` 


---

#### Module 2: Adding interactivity to HTML documents   2.2 Conditional statements, loops and logical operators  Conditional statements: if...then...else, switch

# Conditional statements: if...then...else, switch

### Live coding video: switch statement

>! Missing video/trasncript

#### Example from the video

CodePen example from the video
https://codepen.io/w3devcampus/pen/jmoJRZ

### Conditional statements

What are statements?

JavaScript source code is a set of statements. There are a couple of different statement types. We have already seen one of them, the variable statement:
```javascript

var myVar = 'hello ' + 'world';

```
We've also seen the expression statement:
```javascript

3 + 4;

// more often like this
var x = (3 + 4);
var y = (5 + x);
```

A statement closes with a semicolon, but we will see later that missing semicolons are automatically inserted (for readability reasons, we highly recommend systematically adding a semicolon at the end of all statements).

Statements are generally executed sequentially from top to bottom of the script. However, this flow can be modified by statements such as conditional statements and iteration statements.

### The block statement

The block statement is a simple statement which allows us to group a set of statements wrapped in curly braces. 

Block statement:
```javascript
{
    var i = 0;
    var result = false;
    console.log('i = ' + i);
}
```

The block statement is used by other statements such as the if-statement or for-statement. We will see these statements below.

### Conditional statements

All the examples for this section are in this codepen (to run it: click on the "edit on CodePen" label, and once in CodePen, open the devtool console to see the outputs of this program):


```javascript
/*CONDITIONAL STATEMENTS*/
/*if statement*/

var num = 10;
if (num == 10) {
    num = 20;
}

console.log('if statement,\n num>> ' + num);

/*if-else statement*/

var num = 10;
if (num > 10) {
    num = 20;
} else {
    num = 0;
}

console.log('if-else statement,\n num>> ' +num);

/*
Question 1 
how to replace this code by an expression including one operator?
*/
var max; 
var min;
//var min=1;
if (min){
    max = min + 10;
} else {
    max = 10;
}
console.log('question1, \n max>> ' + max);
//Answer is at the end of the document


/*switch statement*/

//this example is equivalent to the previous if-else example
var num = 10;
switch(num){
  case(num>10): num=20;
    break;
  default: num = 0;
}
console.log('switch1,\n num> ' + num);

//switch statement behaviour when break keyword is missing
//comment and uncomment cloudColor variable to see the different results

var gear = '';
//var cloudColor;
//var cloudColor = 'green';
var cloudColor = 'black';
switch(cloudColor) {
    case 'green': gear += 'spacesuit';
        break;
    case 'black': gear += 'boots, ';
    case 'grey': gear += 'umbrella, ';
    case 'white': gear += 'jacket, ';
    default: gear += 'watch';
}

console.log('switch2,\n gear >> ' + gear);

//The above example with break; 

var gear = '';
//var cloudColor;
//var cloudColor = 'green';
var cloudColor = 'black';
switch(cloudColor) {
    case 'green': 
      gear += 'spacesuit';
      break;
    case 'black': 
      gear += 'boots, ';
      break;
    case 'grey': 
      gear += 'umbrella, ';
      break;
    case 'white': 
      gear += 'jacket, ';
      break;
    default: 
      gear += 'watch';
}

console.log('swtich3,\n gear >> ' + gear);



/*
Question 1 
how to replace this code by an expression including one operator?
var max;
var min;
if (min){
    max = min + 10;
} else {
    max = 10;
}
*/

//Answer
var max;
var min;
max = (min)? min+10 : 10;
//console.log('question 1,\n max >> ' + max);



```
#### Conditional statements are used to execute a unit of code 
#### only if a condition is evaluated as true.
The if statement

Syntax:

```javascript

if ( Expression ) Statement else Statement

if ( Expression ) Statement

```
The expression may include:

* logical operators ( `!` `&&` `||` )
* comparison operators ( `==`, `===`, `>`, `>=`, `<`, `<=` )
* any values or expressions which can be converted to boolean

#### Example: if-statement

```javascript
var num = 10;
 
if (num === 10) {
    num = 20;
}
 
// num equals 20

```
#### Example: if-else statement

```javascript
var num = 10;
 
if (num > 10) {
    num = 20;
} else {
    num = 0;
}
 
// num equals 0

```

#### Reminder:

#### The following values will evaluate to false:

* false
* undefined
* null
* 0
* NaN
* "" (empty string)

#### All other values, including all objects, evaluate to true when passed to a conditional statement.

### The if-then-else ternary operator

This ternary operator is a shortcut version of if...then...else.

Let's look at this code example:

```javascript

var max;
var min = 2;
 
if (min < 10) {
    max = min + 10;
} else {
    max = min;
}
```
Explanation: You can replace this "if-then-else" statement with the ternary operator that uses a syntax with "?" and ":"


```javascript
var max;
var min;
max = (min < 10)? min+10 : min;

```
Line 3 can be read as if (min < 10) then max = min+10, else max = min. The "then" part is after the "?" and the "else" part is after the ":" part.

This "short" version is not recommended except for very simple statements that involve a very obvious block of instructions for the "then" and the "else". Usually this syntax is much harder to read for beginners.

#### Curly braces

Should we use them in if-then-else statements? There are examples without curly braces on the Web: what does this mean?

Here are two versions of the same code.

Version 1: no curly braces

```javascript
if (a > 2)
    result = 'a is bigger than 2';
else
    result = 'a is not bigger than 2';

```

Version 2: with curly braces for delimiting the "then" and "else" blocks

```javascript
if (a > 2) {
    result = 'a is bigger than 2';
} else {
    result = 'a is not bigger than 2';
}
```

Version 1 and version 2 are equivalent. Indeed, version 1 is correct: you can omit curly braces if the "then" or "else" blocks 
are made of only one statement (one line of code).

But version 2 is cleaner and more readable, and, in particular, it is much better for maintainability 
(because you can add a statement just by pressing the enter key. And you can add some extra lines of code without 
worrying about adding curly braces because you broke the **1 line statement rule**).

#### So it is strongly recommended that you always use if-statements enclosed in curly braces. 

Of course, one-line if-statements like this :
```javascript
if (true) doSomething();
```
...are really fast to write, but if you want to add a second statement later it will become more time consuming.

#### Conclusion: always use curly braces!

### The switch statement

In order to avoid having a series of ifs and elses, it is possible to use a switch statement. 

The syntax of the switch statement is:

```javascript
switch (expression) {
    case value1:
        statement
        break;       // break can be omitted in that case
                     // the second test case will be executed
                     // most of the time we add a break; at the end
                     // of a "case"
 
    case value2:
        statement
        break;
 
    case value3:
        statement
        break;
 
    default:         // if no case tested true
        statement
        break;
}
```
If the value of an expression equals one of the cases (the equality operator evaluated is `===`), all the statements next to this case block are executed sequentially until the keyword break is reached.

Example 1: a common switch/case/default example.

```javascript
var gear = '';
 
switch (cloudColor) {
    case 'green':
        gear = 'spacesuit';
        break;
 
    case 'black':
        gear = 'boots';
        break;
 
    case 'grey':
        gear = 'umbrella';
        break;
 
    case 'white':
        gear = 'jacket';
        break;
 
    default:
        gear = 'watch';
        break; // useless if in the last case
} // end of the switch statement

```
In this example, if the clouds are grey, then my gear will be just an umbrella. If they are white, I'll wear only a 
jacket, if they are black I'll be nude with just boots (!), and if they are green I'll get a spacesuit. And if the 
cloud color is none of these, then I'll only wear a watch. The presence of the break keyword at the end of the different 
cases make the choices 100% exclusive. Only one case can be executed!

Example 2: a switch without "breaks" at the end of each case.


```javascript
var gear = '';
 
switch (cloudColor) {
    case 'green':
        gear += 'spacesuit';
        break;
 
    case 'black':
        gear += 'boots, ';
 
    case 'grey':
        gear += 'umbrella, ';
 
    case 'white':
        gear += 'jacket, ';
 
    default:
        gear += 'watch';
} // end of the switch statement

```
Explanation: if the clouds are black, then my gear will be 'boots, umbrella, jacket, watch'. If the clouds are green, my gear 
is a spacesuit (because of the lack of the break keyword, other cases will not be tested). If the cloud color is not in the 
listed colors, then my gear is only a watch (default case).

To finish up this section, here is a complete example: three ways to do condition statements (to run it: click on 
the **edit on codepen** label and once in codepen, open the devtool console to see the outputs of this program):


```javascript
/*CONDITIONAL STATEMENTS*/
/*3 examples which are equivalent*/

//try to change foo value 
var foo=1;
//var foo=2; 
//var foo=1000;
//var foo=0;
//var foo='1';

var bar1,bar2,bar3;

//example 1 
if(foo===1){
  bar1='one';
}
else if(foo===2){
  bar1='two';
}
else{
  bar1='something';
}

//example 2
bar2 = (foo===1)?'one':(foo===2)?'two':'something';

//example 3
switch(foo){
  case 1 :
    bar3='one';
    break;
  case 2 : 
    bar3 ='two';
    break;
  default:
    bar3 ='something';
}

//now we print results :

console.log('example1,\n bar1 >> ' + bar1);
console.log('example2,\n bar2 >> ' + bar2);
console.log('example3,\n bar3 >> ' + bar3);

```



```javascript
var x = 2;
var y = 5;

if(y > 0) {
    if ((x > 2) && (y < 10)) {
        if(x === 2) console.log("YES");
    } else {
        if((y === 5) && (x > 10)) console.log("NO");
    }
} else {
    console.log("MAYBE");
}
console.log(" THE END");

```

> THE END

---

#### Module 2: Adding interactivity to HTML documents   2.2 Conditional statements, loops and logical operators   Loop statements

# Loop statements

### Live coding video: loop statements

>! missing video/transcript

Example from the video

Example on CodePen
https://codepen.io/w3devcampus/pen/qmGeYZ?editors=0012

### Loops

A loop is used to run the same block of code several times while a condition is satisfied.

If you have trouble with loops, the online tool [slowmoJS](http://toolness.github.io/slowmo-js/) can be really useful: you just have to copy and paste an example into it to run it step by step and see how your program executes loops.

### The while statement

With a while statement, a block of code is executed repeatedly while the specified condition is satisfied (evaluates to true).

Syntax:
```javascript
while ( condition ) statement

```
The condition is an expression, and the statement can be a block statement.

Typical example of a while statement:

```javascript
var i = 1, j = 1;
 
while ( i < 4 ) {
    j += i;
    i += 1; 
}

```
### The do-while statement

The do-while statement is very similar to the while statement, but its syntax is different:

```javascript
do statement while ( condition )

```

Typical example:

```javascript
var i = 0;
 
do {
    console.log('i = ' + i);
    i++;
} while(i < 20);
 
console.log('Value of i after the do-while statement: ' + i);

```

The **do-while statement executes the content of the loop once before checking the condition of the while**, 
whereas a **while statement will check the condition first before executing the content**.

A do-while is used for a block of code that must be executed at least once.These situations tend to be relatively rare, thus the simple while-statement is more commonly used. 

If you want to see the difference, look at the `do-while` statement with slowmoJS and the `while` statement slowmoJS. 

### The for statement

This statement adds some things to the while and do-while statements: an initialization expression and an incrementing expression.

Its syntax is:

```javascript
for (initialization; condition; incrementation) statement

```
The three expressions within the parentheses are optional. If the condition is omitted, it is replaced by true (infinite loop).

Typical example (counting from 0 to 10):

```javascript
for (var i = 0; i <= 10; i++) {
   console.log('i = ' + i);
}

```
We can have more than one instruction in the **initialization part**, and more than one instruction in the **incrementation part**. 
Here is another example:

```javascript
for (var i = 1, j = 1; i <= 10; i++, j+=2) {
    console.log('i = ' + i + ' j = ' + j);
}

```
In this example, two variables are defined and assigned within the initialization expression. Before each execution of the block statement, 
the condition is checked; here we need `i <=10`. After each execution of the block statement, the incrementation expression is executed 
to increment the variables i by 1 and j by 2.

Open the devtool console of your browser and copy and paste the above code, or look at the slowmoJS execution.

### The for-in statement

The for-in statement is used to iterate through an object (or through an array, which is also an object). 

Its syntax is:

```javascript
for ( variable in expression ) statement

```


```javascript
var michel = {              // michel is an object
    familyName:'Buffa',     // familyName, givenName, age
                            // are its properties
    givenName: 'Michel',
    age: 51
}
 
for(var property in michel) {   // the for-in will
                                // enumerate properties
    console.log(property);      // will print "familyName",
                                // "givenName",
                                // "age"
    console.log(michel[property]);  // michel['givenName'] same 
                                    // as michel.givenName
}

```
Before each execution of the block statement, the variable named `property` is assigned with the name of one of the properties (the keys) 
of the object.

We will see further examples of this statement in module 4, which is devoted to the study of JavaScript objects.

### [ADVANCED] Other statements

The continue statement

The continue statement is used to stop the execution of a block and start the next iteration of the loop. The difference from the "break" statement is that the loop continues.

Syntax:

```javascript
continue [label]

```
The label is optional.

Typical example:Typical example:

```javascript
for(var i = 1, k = 0; i < 5; i++) {
    if (i === 3) {
        continue;
    }
 
    k += 2*i;
    console.log('k += ' + (2*i));
}
console.log('Final k value:' + k)

```

Copy and paste this example in your devtool console, but first, try to guess what the value of k will be!

Hint: lines 2-4 mean that line 6 will never be executed for i = 3. That means that i*2 will only be added to k for i = 1, 2 and 4...

### The break statement

The break statement is used to stop an iteration, a switch or a labelled statement.

Syntax:
```javascript
break [label]

```
break [label]

```javascript
var tab = ['michel', 'john', 'donald', 'paul']; // johh at index = 1
 
function isNameInTheArray(name, theArray) {
    console.log("Number of elements in the array : " + theArray.length);
    for(var i=0; i < theArray.length; i++) {
        console.log('comparing with element in the array at pos ' + i);
 
        if(theArray[i] === name) {
           console.log('the name ' + name +
                       ' is in the array at pos: ' + i);
           break;
        } else {
           console.log(name + ' is not at pos ' + i);
        }
    }
}
 
// Execute the function
isNameInTheArray('john', tab);

```

Copy and paste in the devtool console. You'll see that the function that compares each element in the array passed as the second parameter with the name 'john', will stop looping after 'john' has been found at index = 1.


---

#### Module 2: Adding interactivity to HTML documents   2.2 Conditional statements, loops and logical operators   Discussion and projects

# Discussion and projects

### Discussion and projects

Here is the discussion forum for this part of the course. Please either post your comments/observations/questions or share your creations.

See below for suggested topics of discussion and optional projects.

#### Suggested topic of discussion:

Did you know about the === and !== operators we recommend you to use?

#### Optional projects:

If not allergic to High School math: try to write a piece of code that solves second degree equations. You pass the a, b, c parameters of: ax2 + bx + c, and the solve function will compute delta = b2 - 4a*c. Test the sign of delta, and if it's equal to zero, then display (in the console, or better, in the page) the roots of the equation.
Try to write a small program that asks you to guess a number. It will choose randomly a number, and will ask you to enter a value in an input field. Then it will display "too small" or "too big", until you find the number.

Hint: use the Math.random and Math.round methods, such as in let randomNumber = Math.round(Math.random() * 10); to get a random value between 0 and 10.

For working with input fields, look at section 1.4 from the first module, the math function plotter example used input fields. Or look at the section about DOM in this module.


---

#### Module 2: Adding interactivity to HTML documents   2.3 Functions (part2): callbacks   Functions and callbacks

# Functions and callbacks

#### Two ways to declare a function


#### 1 - Standard function declaration

We've already seen that functions can be **declared** using this syntax:
```javascript
function functionName(parameters) {
// code to be executed
}
```

A function declared this way can be **called** like this:

```javascript
functionName(parameters);
```

Notice that we do not add a semicolon at the end of a function declaration. **Semicolons are used to separate executable JavaScript statements**, 
and a function declaration is not an executable statement.

Here is an example:

```javascript
function sum(a, b) {
  // this function returns a result
  return (a + b);
}

function displayInPage(message, value) {
  // this function does not return anything
  document.body.innerHTML += message + value + "<br>";
}

var result = sum(3, 4);
displayInPage("Result: ", result);

// we could have written this
displayInPage("Result: ", sum(10, 15));
```

In the above example, the sum function returns a value, and the displayInPage function does not return anything.

#### 2 - Use a function expression

A JavaScript function can also be defined using an expression that can be stored in a variable. Then, the variable can be used as a function:

Here is a typical example:
```javascript
var sum = function(a, b) {
  return (a + b);
};

var displayInPage = function(message, value) {
  // this function does not return anything
  document.body.innerHTML += message + value + "<br>";
};

var result = sum(3, 4);
displayInPage("Result: ", result);

// we could have written this
displayInPage("Result: ", sum(10, 15));
```

Notice how the `sum` and `displayInPage` functions have been declared. **We used a variable to store the function expression**, then we 
can call the functions using the variable name. And we **added a semicolon at the end, since we executed a JavaScript instruction, giving 
a value to a variable**.

The **function expression* is an ***anonymous function***, a function without a name, that represents a value that can be assigned to a 
variable. Then, the variable can be used to execute the function.

We say that functions are **first class objects** which can be manipulated like any other object/value in JavaScript.

This means that functions can also be used as parameters to other functions. In this case they are called `callbacks`.

### Callbacks

ndeed, as functions are first-class objects, we can pass a function as an argument, as a parameter to another function and later execute that passed-in function or even return it to be executed later. When we do this, we talk about callback functions in JavaScript: a function passed to another function, and executed inside the function we called.

All the examples of event listeners that you've seen used callback functions. Here is another one that registers mouse click listeners on the window object (the window objects represent the whole HTML document):

```javascipt
// Add a click event listener on the whole document
// the processClick function is a callback:
// a function called by the browser when a click event
// is detected
window.addEventListener('click', processClick);

function processClick(event) {
  document.body.innerHTML += "Button clicked<br>";
}

// We could have written this, with the body of the callback as an argument of the addEventListener function
window.addEventListener('click', function(evt) {
  document.body.innerHTML += "Button clicked version 2<br>";
});
```

In this case, the `processClick` function is passed as a parameter to the `addEventListener` method/function.

Callback functions are derived from a programming paradigm known as **functional programming**. They are very, very common in JavaScript. We'll use them a lot in the next section of the course, called **Handling events**.

---

### Module 2: Adding interactivity to HTML documents   2.4 Handling events   Introduction

# Handling events  

### Introduction

Adding interactivity to a Web application can only be achieved with CSS, using the :hover pseudo CSS class, for instance. For example:


```html
<!DOCTYPE html>
<html lang="en">
<head>
  <title>Mouse over</title>
  <meta charset="utf-8"/>
</head>
<body> 
   <button>Put the mouse cursor over me</button>
</body>
</html>  
```

```css
button:hover {
  color:red;
  border:2px solid;
}
```
However, firing a specific action when the button is clicked, knowing which mouse button has been used, computing the (x, y) mouse 
pointer position in the button system coordinate, or executing more complex tasks can only be done through JavaScript.

With JavaScript, a button click, a move of the mouse, a resized window, and many other interactions create what are called `events`.  
The timing and order of events cannot be predicted in advance. We say that **event processing* is asynchronous. Web browsers detect 
events as they occur, and may pass them to JavaScript code. They do this by allowing you to register functions as event listeners, 
also called handlers or callbacks for specific events.

Each time an event occurs, the browser puts it in a **queue of events*.

Then the browser looks at a list of "Event Listeners" and calls the ones that correspond to the type of event *they listen to*.


---

#### Module 2: Adding interactivity to HTML documents   2.4 Handling events   Adding and removing event listeners

# Adding and removing event listeners

### Live coding video: adding an event listener to a document

>! missing video/transcript

Online example used in the above video:
https://codepen.io/w3devcampus/pen/zzOVGB?editors=1000


### Live coding video: adding an event listener to a specific HTML element

>! missing video/transcript

Online example used in the above video
https://codepen.io/w3devcampus/pen/pwzXqb?editors=1000

#### Adding and removing event listeners

Event listeners: a typical example

Here is one possible syntax for registering an event listener that listens to `click` events on any part of the window 
(clicks anywhere on a web document will be processed by this event handler):

```javascipt
<script>
    addEventListener('click', function(evt) {
        document.body.innerHTML += 'Button clicked!';
    });
</script>
```
The addEventListener function is one possible syntax for registering a function to be called when a given type of event occurs.


```javascipt
addEventListener(type_of_elem, callback_function)
```

In the example below, the type of event is a 'click', and the callback function is the part in bold:

```javascipt
function(evt) {
   console.log("Button clicked!");
}
```

When this function is small (a few lines of code), it's common practice to put its body as the second parameter of the addEventListener function.

In other words, this:


```javascipt
<script>
addEventListener('click', function(evt) {
    document.body.innerHTML += 'Button clicked!';
});
</script>
```
... is the same as this (the function called when a click occurs has its body "outside" of the addEventListener parameters, and we use its name as the second parameter):

```javascipt
<script>
addEventListener('click', processClick);
function processClick(evt) {
    console.log("Button clicked!");
}
</script>
```
### Adding an event listener to specific HTML elements

Instead of listening to event on the whole document (using `addEventListener` is the same as using `window.addEventListener`), we can 
listen to specific DOM elements.

For example, here is how we can listen to clicks on a specific button (whereas clicks on the rest of the document will be ignored).

```html
<!DOCTYPE html>
<html lang="en">
  <head>
  <title>Second example of an event listener</title>
    <meta charset="utf-8">
</head>
<body>
  <button id="myButton">Click me!</button>
  <p></p>
  <script>
    var b = document.querySelector("#myButton");
    b.addEventListener('click', function(evt) {
      alert("Button clicked");
    });
  </script> 
</body>
</html>
```

In this example, instead of using the `addEventListener` method directly, we used it on a DOM object (the button):

Get a reference of the HTML element that can fire the events you want to detect. This is done using the DOM API that we'll cover 
in detail later this week. In this example we used one of the most common/useful methods: `var b = document.querySelector("#myButton");`

Call the `addEventListener` method on this object. In the example: `b.addEventListener('click', callback)`
Every DOM object has an `addEventListener` method. Once you get a reference of  any HMTL element from JavaScript, you can start 
listening to events on it.

An alternative method for adding an event listener to an HTML element: use an `on` attribute (ex: `onclick = "...."`)

Instead of using `b.addEventListener('click', callback)`, it's possible to use an `onclick='doSomething();'` attribute directly 
in the HTML tag of the element:

In this example, instead of using the addEventListener method directly, we used it on a DOM object (the button):

Get a reference of the HTML element that can fire the events you want to detect. This is done using the DOM API that we'll cover in detail later this week. In this example we used one of the most common/useful methods: var b = document.querySelector("#myButton");
Call the addEventListener method on this object. In the example: b.addEventListener('click', callback)
Every DOM object has an addEventListener method. Once you get a reference of  any HMTL element from JavaScript, you can start listening to events on it.

An alternative method for adding an event listener to an HTML element: use an `on` attribute (ex: `onclick = "...."`)

Instead of using `b.addEventListener('click', callback)`, it's possible to use an `onclick='doSomething();'` attribute directly 
in the HTML tag of the element:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
  <title>Third example of an event listener</title>
    <meta charset="utf-8">
      <script>
         function processClick(evt) {
          alert("Button clicked");
        };
  </script> 
</head>
<body>
  <button id="myButton" onclick="processClick(event);">Click me!</button>
</body>
</html>
```
This syntax:


```javascipt
<button id="myButton" onclick="processClick(event);">Click me!</button>
```
... is ok when you only need a single event listener to click events for this button, as there can be **only one `onclick` attribute per element**.

Using the `b.addEventListener('click', callback)` syntax,  you can register more than one event listener. You'll need rarely to do this, so in my 
opinion it's fine to choose whichever syntax you like.

Remember that for big projects, it's always better to separate the HTML, CSS and JavaScript code. In this case, I'd recommend that 
you put all your event listener definitions in a separate JavaScript file, and use the addEventListener syntax in preference to the `on` 
attributes syntax.

### Removing event listeners

When we click on the button, we execute the `processClick(evt)` callback function, and inside we remove the listener we previously 
registered. Consequence: if we click on the button again, nothing happens as there is no longer a click event listener attached to it.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
  <title>Removing an event listener</title>
    <meta charset="utf-8">
</head>
<body>
  <button id="myButton">Click me, this will work only once!</button>
  <p></p>
  <script>
    var b = document.querySelector("#myButton");
    b.addEventListener('click', processClick);
    
    function processClick(evt) {
     alert("Button clicked, event listener removed, try to click on the button again: nothing will happen anymore!"); 
      b.removeEventListener('click', processClick);
    }
  </script> 
</body>
</html>
```
Note that to remove an event listener, you should have added it with its named function, so that we can pass it to both `addEventListener` 
and `removeEventListener`.


#### Knowledge check 2.4.1 (not graded)

What precaution should you take when adding an event listener to a given HTML element?

I need to be sure that the element is in the DOM before selecting it using the DOM API or the selector API correcto

Explanation
Indeed, we need to be sure that the element is in the DOM before quering it. You can do that by locating the JavaScript 
code after the HTML tag that corresponds to the element, or do this in a JavaScript function that is called only when the 
DOM is ready, for example using `<body onload="init()">`, and put the code in the init function.


---

#### Module 2: Adding interactivity to HTML documents   2.4 Handling events   The event object

# The event object

### The event object is the only parameter passed to event listeners

Typical example:

```javascript
function processClick(evt) {
    alert("Button clicked!");
}
```
Each event listener has a single parameter that is  a "DOM event object". It has various properties and methods that can be very useful.

For example, with a `keyup`, `keydown` or `keypress` event, the event object contains the code of the key that has been 
pressed/released, with a `mousemove` listener we can get the relative position of the mouse in the DOM element that has generated 
the event, etc.

The event object contains some important properties and methods that are common to all types of events:

* `evt.type`: the name of the event
* `evt.target`: for example, is the HTML element that has fired the event. In our previous examples with the click listeners on a 
button, `evt.target` in the event listener is the button itself.
* `evt.stopPropagation()`: will not propagate the event to all other elements that listen to it. If several elements are registered 
for a click event - for example, you have a click listener on a button and on the window (the whole page). If you click on the button, 
and if in its click event listener you call `evt.stopPropagation();` then the click event listener on the window object will never be 
called.
* `evt.preventDefault()`: the default browser behavior will not be executed. For example, in a `contextmenu` event listener attached 
to an object, if you call `evt.preventDefault()`, instead of having the right click default context menu of your browser displayed, 
you'll be able to display your own context menu, like in this [example](http://jsbin.com/kuyorac/edit?html,css,js,console,output).

It also contains properties that are associated with the type of the event, for example:

* `evt.button`: the mouse button that has been used in the case of a mouse event listener
* `evt.keyCode`: the code of the key that has been used
* `evt.pageX`: coordinate of the mouse relative to the page
* etc.

In the subsequent sections of this course we will look at the most common types of events in detail.

### Reference table

The most useful common properties are:

| Property  | Action performed    							|
|-----------|-----------------------------------------------|
|**type**	|Returns the name of the event.					|
|**target**	|Returns the element that triggered the event.	|




The most useful common methods are:

| Property              | Action performed    							|
|-----------------------|-----------------------------------------------|
|**preventDefault()**	|Cancels the event if it is "cancelable", meaning that the default action that belongs to the event will not occur. It is useful for cancelling the default browser behavior. For example: if you want to create a context menu that pops up with a right click, you must prevent the default behavior of the browser that will pop up its default context menu.					|
|**stopPropagation()**	|Prevents further propagation of an event during event flow.	|

---

#### Module 2: Adding interactivity to HTML documents   2.4 Handling events   Page lifecycle events

# Page lifecycle events

### Live coding video: page 'load' event and the event object

>! misssing video/transcript

Online example used in the above video
https://codepen.io/w3devcampus/pen/XgrveY?editors=0001
	
### Page lifecycle events

These events detect when the page is loaded and when the DOM is ready.

Events related to the page lifecycle

There are many other events related to the page life cycle. The most useful ones for an introduction course are shown below:

| Event     | occurs when ...    							|
|-----------|-----------------------------------------------|
|**load**	|This event occurs when an object has loaded (including all its resources: images, etc.). This event is very useful when you want to run JS code and be sure that the DOM is ready (in other words, be sure that a `document.getElementById(...)` or `document.querySelector(...)` will not raise an error because the document has not been loaded and elements you are looking for are not ready).				|
|**target**	|The event occurs when the document view is resized. Usually, we get the new size of the window inside the event listener using `var w = window.innerWidth;` and `var h = window.innerHeight;`	|
|**scroll**	|The event occurs when an element's scrollbar is being scrolled. Usually in the scroll event listener we use things such as: `var max = document.body.scrollHeight - innerHeight;` `var percent = (pageYOffset / max);` ...to know the percentage of the scroll in the page.	|

### Page event properties

There are no particular properties that need to be mentioned here. Usually, the load event listener corresponds to a JavaScript function that 
can be seen as **the main** function of your Web application. It is a best practice to start everything after the page has been completely loaded. 
In the resize listener, you get the new size of the window, or the new size of some HTML elements in the page (as they might have been resized 
too when the window was resized), and then you do something (redraw a graphic in an HTML canvas that takes into account the new canvas size, 
for example).

#### Example 1: wait until the page is loaded (when the DOM is ready) before doing something

This first variant that uses `<body onload="init();">`
	
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>Example1 of the 'load' event</title>
</head>
<body onload='init();'>
  <p>This page uses <code>&lt;body onload='init();'&gt;</code> in the JS code  to execute the init function ONLY WHEN THE PAGE HAS BEEN LOADED!</p>
  
  <p>This is important as very often we cannot do important things before the DOM is ready (all HTML elements have been created and can be manipulated from JavaScript).</p>
  
  <p>PAGE STATUS: <span id="pageStatus">NOT LOADED YET</span></p>
</body>
</html>

```


```css
#pageStatus {
  border:1px solid red;
  padding: 2px;
  color:red;
}
```


```javascript
function init() {
  var status = document.querySelector('#pageStatus');
  status.innerHTML = 'LOADED!';
  
  // start working!
  // ....
}
```

This second variant: using `window.onload = init;` in the JavaScript code...

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>Example1 of the 'load' event</title>
</head>
<body>
  <p>This page uses <code>window.onload = init;</code> in the JS code  to execute the init function ONLY WHEN THE PAGE HAS BEEN LOADED!</p>
  
  <p>This is important as very often we cannot do important things before the DOM is ready (all HTML elements have been created and can be manipulated from JavaScript).</p>
  
  <p>PAGE STATUS: <span id="pageStatus">NOT LOADED YET</span></p>
</body>
</html>
```


```css
#pageStatus {
  border:1px solid red;
  padding: 2px;
  color:red;
}
```


```javascript
window.onload = init;

function init() {
  var status = document.querySelector('#pageStatus');
  status.innerHTML = 'LOADED!';
  
  // start working!
  // ....
}
```

#### Example 2: detect a resize of the window

In this example, we're listening to page load and page resize events. When the window is loaded for the first time, or resized, we call the `resize()` 
callback function. The `window.innerWidth` and `window.innerHeight` properties are used to display the updated size of the window. We also use `screen.width` 
and `screen.height` to display the screen size.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>Example1 of the 'resize' event</title>
</head>
<body>
  <p>This page uses <code>window.onresize = resize;</code> in the JS code  to execute the resize function. Try to change the size of your window now!</p>
 
  <p>Curent page size: <span id="pageSize"></span></p>
  <p>Screen size: <span id="screenSize"></span></p>
</body>
</html>
```


```css
#pageSize, #screenSize {
  border:1px solid red;
  padding: 2px;
  color:red;
}
```


```javascript
window.onload = resize;
window.onresize = resize;

function resize(evt) {
  console.log("resize");
  var pageSizeSpan = document.querySelector('#pageSize');
  pageSizeSpan.innerHTML = "Width: " + window.innerWidth + " Height: " + window.innerHeight;
  
 // screen size
var screenSizeSpan = document.querySelector('#screenSize');
  screenSizeSpan.innerHTML = "Width: " + screen.width + " Height: " + screen.height;
  
}
```

Example 3: do something as the page is being scrolled up or down
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>Example of the 'scroll' event</title>
</head>
  <body>
<div class="progress">
  <div>Percentage</div>
    </div>
    <p id="text">Scroll me and the progress bar on the right will show 
  the percentage of scroll. Look also at the CSS
  code (body is 2000px height, for example)...</p>
  </body>
</html>
```


```css
.progress {
  border: 1px solid blue;
  width: 100px;
  position: fixed;
  top: 10px; right: 10px;
}

.progress > div {
  height: 12px;
  background: lightBlue;
  width: 0%;
  font-size:8px;
}

#text {
  margin-top:50px;
}
body {
  height: 2000px;
}
```


```javascript
window.onload = init;

var progressBar;

function init() {
  progressBar = document.querySelector(".progress div");

  window.addEventListener("scroll", function() {
      var max = document.body.scrollHeight - window.innerHeight;
      var percent = (window.pageYOffset / max) * 100;
      progressBar.style.width = percent + "%";
  });
}
```

#### Knowledge check 2.4.2 (not graded)


```javascript
function init(evt) {
   console.log("Page loaded! DOM Ready!");
   // access the DOM using the DOM API or the selector API
   var elem = document.querySelector(...);
   elem.innerHTML = ....;
```

Check the correct ways to call the function init only when the page has loaded and the DOM is ready:
<body onload="init();"/> correcto
In a JS code, add window.onload = init; correcto
in a JS code, add window.addEventListener('load', init); correcto

#### Explanation
All answers are correct. All of these syntaxes have the same effect: call init once the page is loaded.


---

#### Module 2: Adding interactivity to HTML documents   2.4 Handling events   Key events: legacy API

# Key events: legacy API

### Dealing with key events

#### Introduction

This has been a bit of a nightmare for years, as different browsers have had different ways of handling key events and key codes (read [this](http://unixpapa.com/js/key.html) if you are fond 
of JavaScript archeology). Fortunately it's much better today, and we are able to rely on methods that should work on any browser.

When you listen to keyboard related events (`keydown`, `keyup` or `keypressed`), the event parameter passed to the listener function will contain 
the code of the key that fired the event. Then it is possible to test which key has been pressed or released, like this:



```javascript
window.addEventListener('keydown', function(event) {
   if (event.keyCode === 37) {
     //left arrow was pressed
   }
});
```

At line 2, the value `37` is the key code that corresponds to the left arrow. It might be difficult to know which codes represent which real keyboard keys, so here are some handy pointers:

Try key codes with this interactive example: http://www.asquare.net/javascript/tests/KeyCode.html
And find a list of keyCodes (taken from: http://css-tricks.com/snippets/javascript/javascript-keycodes/) below:

![JSKeyCodes](https://courses.edx.org/asset-v1:W3Cx+HTML5.1x+4T2015+type@asset+block@JSKeyCodes.jpg)


### The different key events

Event types related to keyboard

| key events    | 					   																|
|---------------|-----------------------------------------------------------------------------------|
|**keydown**	|The event occurs when the user is pressing a key.									|
|**keyup**		|The event occurs when the user releases a key.										|
|**keypress**	|(now deprecated)	The event occurs when the user presses a key (up and release).	|

	
### keyboardEvent properties

These are legacy properties, still used by many JavaScript code around the world. However, we do not recommend that you use them if you are targeting 
modern browsers. `keyCode` has a more powerful/easy to use replacement called `code` (not yet supported by all browsers), that comes with a new `key` 
property (see the following pages of the course).
 
| keyboardEvent | 					   																|
|---------------|-----------------------------------------------------------------------------------|
|**keyCode**	|Returns the Unicode character code of the key that triggered the onkeypress ,onkeydown or onkeyup event.|
|**shiftKey**	|Returns whether the "shift" key was pressed when the key event was triggered.	|
|**ctrlKey**	|Returns whether the "ctrl" key was pressed when the key event was triggered.	|
|**altKey**		|Returns whether the "alt" key was pressed when the key event was triggered.	|

	
#### Example 1: use keyup and keydown on the window object
https://codepen.io/w3devcampus/pen/wJZJZp
 	
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>Example of the 'keyup' and 'keydown' events on the window object</title>
</head>
  <body>
    <p>Please type some keys and see what happens</p>
    <div id="keys"></div>
  </body>
</html>
```
	

```javascript
window.onkeyup = processKeyUp;
window.onkeydown = processKeyDown;

/* or we could have written:
   window.addEventListener('keyup', processKeyUp);
   window.addEventListener('keydown', processKeyDown);
*/

function processKeyUp(evt) {
  var keys = document.querySelector('#keys');
  keys.innerHTML += "keydown: " + evt.key + " code: " + evt.keyCode + "<br>";
}
```

#### Example 2: see  keypress on the window object

See the Pen keyup and keydown events on window by W3Cx (@w3devcampus) on CodePen.
https://codepen.io/w3devcampus/pen/WpWjey
https://codepen.io/w3devcampus/pen/BWERyY

#### Example 3: detect a combination of keys + modifier keys (shift, ctrl, alt)

https://codepen.io/w3devcampus/pen/BWERyY

Try to type shift-a for example, ctrl-shift-b or alt-f...

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>Example of the 'keypress' event on the window object, awith shift, meta and alt</title>
</head>
  <body>
    <p>Please type some keys and see what happens. Try typing key modifiers at the same time: shift, alt, control</p>
    <div id="keys"></div>
  </body>
</html>
```

```javascript
window.onkeydown = processKeyDown;

/* or we could have written:
   window.addEventListener('keypress', processKeyPress);
*/

function processKeyDown(evt) {
  var keys = document.querySelector('#keys');
  
   keys.innerHTML += "keypress: " + evt.key + 
                   " code: " + evt.keyCode + " Modifiers : ";

  var modifiers = "";
  
  if(event.shiftKey)
    modifiers += "SHIFT ";

  if(event.altKey)
    modifiers += "ALT ";

  if(event.ctrlKey)
    modifiers += "CTRL ";

  if(modifiers === "")
    modifiers = "NONE";
  
  keys.innerHTML += modifiers + "<br>";
}

```


---

#### Module 2: Adding interactivity to HTML documents   2.4 Handling events   Dealing with different keyboard layouts

# Dealing with different keyboard layouts

### Internationalize your keyboard controls

#### Introduction

Please do not assume that each key is at the same location on the keyboard in every country!

We've shown how to detect keyup, keydown and keypress events using the DOM API, and how to use the keyCode property of the DOM event.

Be careful when you use the key events in your application, as keyboard layouts vary from one country to another. Most first person shooter games (FPS) use three keys located on the top left of your keyboard to move your character. French AZERTY keyboards will use ZQSD for this (Z = up/move forward, Q and D are for left/right and S is for down/move backward), while US keyboards will use WASD, for example. So keep in mind that keys are not located at the same place on keyboards from different countries.

Extract from the "Internationalise your keyboard controls" article on MDN, by Julien Wajsberg:

> "Recently I came across two lovely new graphical demos, and in both cases, the controls would not work on my French AZERTY keyboard.

> There was the wonderful WebGL 2 technological demo After The Flood, and the very cute Alpaca Peck. Shaw was nice enough to fix the latter when I told him about the issue. It turns out the Web browser actually exposes a useful API for this."

#### One keyboard, many layouts

For details, see Wikipedia’s keyboard layout page!
https://en.wikipedia.org/wiki/Keyboard_layout

QWERTY layout, used in US, GB, etc.:

![QWERTY keyboard layout](https://d37djvu3ytnwxt.cloudfront.net/assets/courseware/v1/90b06977ee3a3e0a40aea0a7d0b4adbd/asset-v1:W3Cx+JS.0x+1T2017+type@asset+block/QWERTY.png)

AZERTY layout, used in some French-speaking countries:

![AZERTY keyboard layout](https://d37djvu3ytnwxt.cloudfront.net/assets/courseware/v1/7cfadb8f6dd3bb3e51277685a1e3b4fa/asset-v1:W3Cx+JS.0x+1T2017+type@asset+block/AZERTY.png)

In addition, QWERTZ keyboards are in use in Germany and other European countries, and DVORAK is another alternative to QWERTY:

DVORAK:

![DVORAK keyboard layout](https://d37djvu3ytnwxt.cloudfront.net/assets/courseware/v1/9ff392064dff40eb73ff18574fbe08db/asset-v1:W3Cx+JS.0x+1T2017+type@asset+block/DVORAK.png)



---

#### Module 2: Adding interactivity to HTML documents   2.4 Handling events   Key and code properties

# Key and code properties

### New recommended properties you can use with modern browsers: key and code

You may have noticed that in some examples from the previous course page about key events, we used event.key in order to display the character that has been typed. The key property has been introduced with a new W3C API called UI Events (or DOM level 3 events), that has been discussed since 2000.  All major browsers have implemented this very practical key property. It comes with another property named code, which is what keyCode should have been. The value of the code property corresponds to a code that is more readable than the value of the old keyCode property.

* **key**: when the pressed key is a printable character, you get the character in string form. When the pressed key is not a printable character (for example: Backspace, Control, but also Enter or Tab which actually are printable characters), you get a multi-character descriptive string, like 'Backspace', 'Control', 'Enter', 'Tab'.
* **code**: Gives you the physical key that was pressed, in string form. This means it’s totally independent of the keyboard layout that is being used. So let’s say the user presses the Q key on a QWERTY keyboard. Then event.code gives you 'KeyQ' while event.key gives you 'q'.

> But when an AZERTY keyboard user presses the A key, he also gets `KeyQ` as event.code, yet event.key contains `a`. This happens because the A key 
> on a AZERTY keyboard is at the same location as the Q key on a QWERTY keyboard.

As for numbers, the top digit bar yields values like 'Digit1', while the numeric pad yields values like 'Numpad1'.

Unfortunately this feature is not yet implemented by Microsoft IE/Edge but support is coming soon to Edge.
List of codes, the reference keyboard

### List of codes, the reference keyboard

There’s no existing keyboard with all the possible keys. That’s why the W3C published a specification just for this. You can read about the 
existing mechanical layouts around the world, as well as their reference keyboard. For instance here is their reference 
keyboard for the alphanumerical part:
https://www.w3.org/TR/uievents-code/
https://www.w3.org/TR/uievents-code/#keyboard-layout
https://www.w3.org/TR/uievents-code/#code-value-tables

![layout](https://d37djvu3ytnwxt.cloudfront.net/assets/courseware/v1/e103f259d85894158e15443dd13b6802/asset-v1:W3Cx+JS.0x+1T2017+type@asset+block/keyboard-codes-alphanum1.png)

You can also read this document published by the W3C with explanations about all the possible values for the code property.

Also read through the examples given in the specification. They show very clearly what happens when the user presses various types of keys, both for code and key.
https://www.w3.org/TR/uievents-key/
https://w3c.github.io/uievents/#code-examples

#### Example that displays the key and code values with your current keyboard

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>key and keyCode</title>
    <meta charset="utf-8"/>
  </head>
  <body>
   <p>Press some keys on your keyboard and see the corresponding evt.key and evt.code values. If you are not using a QWERTY keyboard, notice that the values might be different. This is because an 'a' on an AZERTY keyboard, will correspond to the KeyQ code on the reference keyboard.</p>
    <p>  You typed:</p>
  </body>
</html>
```



```javascript
window.onkeydown = function(evt) {
  document.body.innerHTML += "key = " + evt.key + "<br>";
 document.body.innerHTML += "code = " + evt.code + "<br><br>";
}
```
I encourage you to take a look and get at least an overview of this specification.

Please note that the W3C has also published a sibling specification describing the values for the key property.

Before looking at examples, let's see the current Web browser support for these properties:

As of April 2017:

http://caniuse.com/#feat=keyboardevent-code

---

#### Module 2: Adding interactivity to HTML documents   2.4 Handling events   Mouse events

# Mouse events

### Mouse interaction, mouse events

Important note: Remember that many people do not use the mouse and rely on the keyboard to interact with the Web. This requires keyboard access to all functionality, including form controls, input, and other user interface components (learn more).

Detecting mouse events in a canvas is quite straightforward: you add an event listener to the canvas, and the browser invokes that listener when the event occurs.

The example below is about listening to mouseup and mousedown events (when a user presses or releases any mouse button):



```javascript
canvas.addEventListener('mousedown', function (evt) {
   // do something with the mousedown event
});
 
canvas.addEventListener('mouseup', function (evt) {
   // do something with the mouseup event
});
```

The event received by the listener function will be used for getting the button number or the coordinates of the mouse cursor. Before looking at different examples, let's look at the different event types we can listen to.

#### Mouse events

#### Event types related to mouse


| Mouse events    | 					   																|
|---------------|-----------------------------------------------------------------------------------|
|**click**	    |The event occurs when the user clicks on an element (presses a button and releases it).									|
|**dblclick**	|The event occurs when the user double-clicks on an element.										|
|**mousedown**	|The event occurs when the user presses a key (up and release).	|
|**mouseup**	|The event occurs when a user releases a mouse button over an element.	|
|**mousemove**	|The event occurs when the pointer is moving while it is over an element.									|
|**mouseenter**	|The event occurs when the pointer is moved onto an element.										|
|**mouseleave**	|The event occurs when the pointer is moved out of an element.	|
|**mouseover**	|The event occurs when the pointer is moved onto an element, or onto one of its children.									|
|**contextmenu**		|The event occurs when the user right-clicks on an element to open a context menu.										|


#### MouseEvent properties	
	
	
| MouseEvent properties    | 					   																|
|---------------|-----------------------------------------------------------------------------------|
|**button**	    | Returns which mouse button was pressed when the mouse event was triggered.									|
|**clientX and clientY**	| Returns the coordinates of the mouse pointer, relative to the element coordinate system that triggered the event. If you click in the left top corner the value will always be (0,0) independent of scroll position, these coordinates are relative to the VIEWPORT (the visible part of the document page).										|
|**pageX and pageY**	| Returns the coordinates of the mouse pointer, relative to the document, when the mouse event was triggered. They are relative to the complete document/page, and will always be relative to the very beginning of the document/page, even if the top of the page is not visible because you've scrolled down. They will change when the page scrolls and the mouse does not move!.	|
|**screenX and screenY**	| Returns the coordinates of the mouse pointer, relative to the screen, when an event was triggered.	|
|**altKey, ctrlKey, shiftKey**	| Returns whether the "alt, ctrl and shif" key was pressed when an event was triggered.									|
|**detail**	| Returns a number that indicates how many times the mouse was clicked.										|

	
Examples

Example 1: detect a click on an element
	

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>detect mouse clicks on elements</title>
</head>
  <body>
    <button id="button1" onclick="processClick(event)">Button1</button>
    <div id="myDiv" onclick="processClick(event)">Click also on this div!</div>
    <div id="clicks"></div>
  </body>
</html>
```


```css
#myDiv {
  color:red;
  background-color: pink;
  width:100px;
  height:100px;
  text-align:center;
  margin:20px;
}
```


```javascript
window.onclick = processClick;

function processClick(evt) {
  var clicks = document.querySelector('#clicks');

  var target = evt.target.id;
  
  if(target === "") {
    clicks.innerHTML += "You clicked on the window, not on a particular element!<br>";
  } else {
    clicks.innerHTML += "Element clicked id: " + target + "<br>";
   
  }
  
  evt.stopPropagation(); // try commenting it and click on the button or div
}
```

#### Example 2: see the differences between clientX/clientY and pageX/pageY

The source code is not meant to be understood. It uses the jQuery lib and comes from a stackOverflow thread. But it's interesting: move the mouse pointer, look at the different properties. Then scroll the page (the table at the top will not move), and look at the properties again; notice how pageX/pageY change, since they are relative to the top of the page, even if they are not visible. Click on the codePen label on top right and run this example! It does not work when embedded in this page!

https://codepen.io/w3devcampus/pen/bqJWJJ

```html
<!DOCTYPE html>
<html lang="en">
<head>
<script src="https://ajax.googleapis.com/ajax/libs/jquery/1/jquery.min.js"></script>
<meta charset=utf-8 />
<title>client - page - screen</title>
</head>
<body>
    <table>
      <tr>
        <td>Mouse position inside:</td>
        <td>X &nbsp;&nbsp;&nbsp; Y</td>
      </tr>
      <tr>
        <td>- client:</td>
        <td id="client"></td>
        <td>Client Viewport</td>
      </tr>
      <tr>
        <td>- page:</td>
        <td id="page"></td>
        <td>Document Page (scroll down to see the difference)</td>
      </tr>
      <tr>
        <td>(scrollTop:</td>
        <td id="scrollTop"></td>
        <td>Scroll top [pageY-clientY] )</td>
      </tr> 
      <tr>
        <td>- screen:</td>
        <td id="screen"></td>
        <td>Screen</td>
      </tr>
    </table>
</body>
</html>
```


```css
body{
  height:4000px;
  font-family:Arial,"Helvetica Neue",Helvetica,sans-serif;
}


table{
  position:fixed;
  width:100%;
  padding:10px 20px;
  background:#eee;
  border-spacing:5px 0; 
}
table td{
  vertical-align:bottom;
  border:1px dashed #ddd;
  padding:3px 10px;
}
table tr:first-child{
  background:#ddd;
}
```


```javascript


var m = ['client','page','screen']; // mods
$(document).mousemove(function(e){
  for(var i=0; i<3; i++){
    $('#'+m[i]).text((e[m[i]+'X'])+' '+ (e[m[i]+'Y']));
  }
  $('#scrollTop').text(
    $('html, body').scrollTop()
  );
});
```

#### Example 3: detect a mousemove event and get the mouse position relative to the page

https://codepen.io/w3devcampus/pen/OpGmjE

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>mousemove events relative to page</title>
</head>
  <body>
    <h1>Please move the mouse on this window!"</h1>
    <div id="mousePositions"></div>
    <p>Yep! The above values are the same  when we're listening on the window and we did not scrolled the page!</p>
        <div id="mouseScreenPositions"></div>

  </body>
</html>
```

```javascript
window.onmousemove = processMouseMouve;

function processMouseMouve(evt) {
  var mousePositions = document.querySelector('#mousePositions');
  mousePositions.innerHTML = "clientX: " + evt.clientX +
                              " clientY: " + evt.clientY + "<br>" +
                             " pageX : " + evt.pageX +
                              "  pageY : " + evt.pageY +
                              "<br>";

  var mouseScreenPositions = document.querySelector('#mouseScreenPositions');
  mouseScreenPositions.innerHTML = "screenX: " + evt.screenX +
                             " screenY: " + evt.screenY + 
                             "<br>";
 }
```


#### Example 4: detect a mousemove and get the mouse position relative to the element that fired the event

Here is a first version that does not work well due to a naive use of clientX/PageX and clientY/pageY mouse event properties:

https://codepen.io/w3devcampus/pen/oZryVL

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>mousemove events relative to page</title>
</head>
  <body>
    <h1>Please move the mouse on the grey canvas below!</h1>
    <p>The mouse position is not correct (try to move the cursor at the top left corner of the cavas: it should be 0,0 but it isn't. And if you scroll the page it's worse). clientX and clientY cannot be used "as is".</p>
    <canvas id="myCanvas" width=300 height=50></canvas>
    <div id="mousePositions"></div>
    
        <div id="mouseScreenPositions"></div>

  </body>
</html>
```


```css
canvas {
  border:4px solid;
  margin-left:20px;
  background-color:lightGrey;
}

body {
  height:2000px;
}
```


```javascript
window.onload = init;

function init() {
  // page has been loaded
  canvas = document.querySelector('#myCanvas');
  
  canvas.addEventListener('mousemove', processMouseMouve)
}

function processMouseMouve(evt) {
  var mousePositions = document.querySelector('#mousePositions');
  
  mousePositions.innerHTML = "mouse pos X: " + evt.clientX +
                              " mouse pos Y: " + evt.clientY + 
                              "<br>" 
 }
```
Here is another version that uses clientX/clientY and the e.target.getBoundingClientRect() method that returns the bounding rectangle that contains the element that fired the event. The return value has top, left, width, and height properties that describe this rectangle. We can use the top and left properties along with evt.clientX and evt.clientY to fix the mouse position and to get a real position relative to the top left corner of the canvas:

	
	

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>mousemove events relative to page</title>
</head>
  <body>
    <h1>Please move the mouse on the grey canvas below!</h1>
    <p>You'll see that there is a no more a problem:  (0, 0) is now at the top left corner of the canvas, even if we scroll the page!</p>
    <canvas id="myCanvas" width=300 height=50></canvas>
    <div id="mousePositions"></div>
    
        <div id="mouseScreenPositions"></div>

  </body>
</html>
```


```css
canvas {
  border:4px solid;
  margin-left:20px;
  background-color:lightGrey;
}

body {
  height:2000px;
}
```


```javascript
window.onload = init;

function init() {
  // page has been loaded
  canvas = document.querySelector('#myCanvas');
  
  canvas.addEventListener('mousemove', processMouseMouve)
}

function processMouseMouve(evt) {
  var mousePositions = document.querySelector('#mousePositions');
  var rect = evt.target.getBoundingClientRect()
  var mouseX = evt.clientX - rect.left;
  var mouseY = evt.clientY - rect.top;
  
  mousePositions.innerHTML = "mouse pos X: " + mouseX +
                              " mouse pos Y: " + mouseY + 
                              "<br>" 
 }
```

JavaScript source code extract:


```javascript
function processMouseMouve(evt) {
    var mousePositions = document.querySelector('#mousePositions');
    // adjust mouse position relative to the canvas
    var rect = evt.target.getBoundingClientRect()
    var mouseX = evt.clientX - rect.left;
    var mouseY = evt.clientY - rect.top;
    mousePositions.innerHTML = "mouse pos X: " + mouseX +
                               " mouse pos Y: " + mouseY +
                               "<br>"
}
```

#### Example 5: combine mouseup, mousedown, mousemove to implement a click and drag behavior

https://codepen.io/w3devcampus/pen/bqJRMV

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>mousemove events relative to page</title>
</head>
  <body>
    <h1>Please click and drag the div below.</h1>
   <div id="dragMe" class='draggable'>Drag me!</div>
  </body>
</html>
```


```css
body {
  padding:10px
}

.draggable {
  width:100px;
  height:100px;
  background-color:#666;
  color:white;
  padding:10px 12px;
  cursor:move;
  position:absolute; /* important (all position that's not `static`) */
}
```


```javascript
window.onmousemove = moveElem;
window.onmouseup = stopMovingElem;
window.onload = init;

var selected = null; // element to be moved
var oldMouseX, oldMouseY; // Stores x & y coordinates of the mouse pointer
var elemX, elemY;

function init() {
    document.querySelector('.draggable').onmousedown = function (evt) {
        dragInit(evt);
    };
}
  
// Will be called when user starts dragging an element
function dragInit(evt) {
    // Store the elem
    selected = evt.target;
    elemX = selected.offsetLeft;
    elemY = selected.offsetTop;
  
    oldMouseX = evt.clientX;
    oldMouseY = evt.clientY;
}

// Will be called when user dragging an element
function moveElem(e) {
    // new mouse ps
    var newMouseX = e.clientX;
    var newMouseY = e.clientY;
  
    if(oldMouseX !== undefined) {
        // how many pixels did we move the mouse?
        var dx = newMouseX - oldMouseX;
        var dy = newMouseY - oldMouseY;
     }
    
    if (selected !== null) {  
        // move the selected element dx, dy pixels hozontally/vertically
        changePosOfSelectedElement(dx, dy);
    }
  
    // update the old position of the mouse
    oldMouseX = newMouseX;
    oldMouseY = newMouseY;
}

function changePosOfSelectedElement(dx, dy) {
  // update the old position of the selected element
  elemX += dx;
  elemY += dy;
  
  // change the pos on screen of the element
  // by modifying its CSS left/top properties
  selected.style.left = elemX + 'px';
  selected.style.top = elemY + 'px';
}

// Destroy the object when we are done
function stopMovingElem() {
    selected = null;
}

```

#### Example 6: create  and attach a right-click context menu to any element

https://codepen.io/w3devcampus/pen/oZOweM


```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>Example of right click context menu in pure JS</title>
</head>
<body>
    <div>
      <nav id="context-menu" class="context-menu">
        <ul class="context-menu__items">
          <li class="context-menu__item" id="context-menu-learn" onclick="menuItem1();">
            Learn
          </li>
          <li class="context-menu__item" onclick="menuItem2();">
            Clear
          </li>
          <li class="context-menu__item" onclick="toggleMenuOff();">
            Close
          </li>
        </ul>
      </nav>
    </div>
  <p>Try to right click on this div:</p>
  <div id="div1" class="div">A Div with a context menu</div>
<p>  This one does not have a context menu attached, try also a right click:  </p>
  <div id="div2" class="div">Another Div without a context menu</div>
</body>
</html>
```


```css
          /* CONTEXT MENU */
      /* context menu */

.context-menu {
  display: none;
  position: absolute;
  z-index: 10;
  padding: 12px 0;
  width: 240px;
  background-color: #fff;
  border: solid 1px #dfdfdf;
  box-shadow: 1px 1px 2px #cfcfcf;
}

.context-menu--active {
  display: block;
}

.context-menu__items {
  list-style: none;
  margin: 0;
  padding: 0;
}

.context-menu__item {
  display: block;
  margin-bottom: 4px;
  padding: 4px 12px;
  color: #0066aa;
  text-decoration: none;
}

.context-menu__item:last-child {
  margin-bottom: 0;
}


.context-menu__item:hover {
  color: #fff;
  background-color: #0066aa;
}

#div1 {
  background-color:red;
  height:100px;
}

#div2 {
  background-color:green;
  height:100px;
}
```


```javascript
window.onload = init;

var menu, menuIsVisible;

function init() {
   menu = document.querySelector("#context-menu"); 
  menuIsVisible = false;
  /* to attach a context menu to all divs, you can do this:
     var divs = document.querySelectorAll(".div");

     divs.forEach(function(d) {
          addContextMenu(d);
     });
  */

  // attache the context menu to the first div
  var div1 = document.querySelector("#div1");
  addContextMenu(div1);

  // Clicking anywhere on the window toggle the menu off
  window.addEventListener('click', toggleMenuOff);
}

function addContextMenu(elem) {
    elem.addEventListener("contextmenu", function(e) {
            //console.log("contextmenu activated");
            e.preventDefault(); // avoids default right click menu
            toggleMenuOn();
            positionMenu(e);
    });
}
      
function toggleMenuOn() {
   if(!menuIsVisible) {
       menuIsVisible = true;
        menu.classList.add("context-menu--active"); // see further in the DOM section of the course
    }
}

function toggleMenuOff() {
    if(menuIsVisible) {
       menuIsVisible = false;
        menu.classList.remove("context-menu--active");
     }
}


function positionMenu(e) {
     // Mouse position is relative to the element clicked
  
     // We make the coords absolute in the page
     var clickCoordsX = e.pageX;
     var clickCoordsY = e.pageY;
  

     var menuWidth = menu.offsetWidth + 1;
     var menuHeight = menu.innerHeight + 1;

     var elementWidth = e.target.offsetWidth;
     var elementHeight = e.target.offsetHeight;

     if ((elementWidth - clickCoordsX) < menuWidth) {
       menu.style.left = elementWidth - menuWidth + "px";
     } else {
       menu.style.left = clickCoordsX + "px";
     }

     if ((elementHeight - clickCoordsY) < menuHeight) {
       menu.style.top = elementHeight - menuHeight + "px";
     } else {
       menu.style.top = clickCoordsY + "px";
     }
   }

// Actions called when a menu item is choosen

function menuItem1() {
  console.log('learn');
  toggleMenuOff();
}

function menuItem2() {
  console.log('clear');
  toggleMenuOff();
}

```

---

#### Module 2: Adding interactivity to HTML documents   2.4 Handling events   Form and input field events

# Form and input field events

### Forms

#### Events related to forms

|event |-------|
|------|-------|
|input	|The event occurs when an element gets user input (e.g., a key is typed on an input field, a slider is moved, etc.)|
|change	|The event occurs when the content of a form element, the selection, or the checked state have changed (for `<input>`, `<select>`, and `<textarea>`). A change event listener on a slider will generate an event when the drag/move ends, while input events will be useful to do something as the slider is being moved.|
|focus	|The event occurs when an element gets focus (e.g., the user clicks in an input field)|
|blur	|The event occurs when an element loses focus (e.g., the user clicks on another element)|
|select	|The event occurs after the user selects some text (for `<input>` and `<textarea>`)|
|submit	|The event occurs when a form is submitted|

### FormEvent properties

There are no particular properties that need to be mentioned here. Usually, on a form event listener, we check the content of the different input fields, using their value property. See examples in the part of the course that deals with form events.

#### Example 1: validating on the fly as the user types in a text input field

First variant: using the `input` event:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>Simple input field validation</title>
</head>
<body>
  <h1>Simple input field validation using the 'input' event</h1>
  <p>Just type a name in the input field and see what happens!</p>
<label>
  <span>Name (required):</span>
  <input type="text" 
         name="nom" 
         maxlength="32" 
         required
         oninput = "validateName(this)">
</label>
  <p>
  <span id="nameTyped"></span>
</p>  
</body>
</html>
```


```javascript
function validateName(field) {
  // this is the input field text content
  var name = field.value;  
  
  // get the output div
  var output = document.querySelector('#nameTyped');
  // display the value typed in the div 
  output.innerHTML = "Valid name: " + name;
  
  // You can do validation here, set the input field to
  // invalid is the name contains forbidden characters
  // or is too short
  // for example, let's forbid names with length < 5 chars
  if(name.length < 5) {
    output.innerHTML = "This name is too short (at least 5 chars)";
  }
}
```

#### Second variant: using the 'keyup' event:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>Simple input field validation using keyup events</title>
</head>
<body>
  <h1>Simple input field validation using the 'input' event</h1>
  <p>Just type a name in the input field and see what happens! <span style="color:red"> TRY TO TYPE A "!" too</span></p>
<label>
  <span>Name (required):</span>
  <input type="text" 
         name="nom" 
         maxlength="32" 
         required
         onkeyup = "validateName(event)">
</label>
  <p>
  <span id="keyTyped"></span>
</p>  
</body>
</html>
```



```javascript
function validateName(evt) {
  // this is the input field text content
  var key = evt.key;  
  
  // get the output div
  var output = document.querySelector('#keyTyped');
  // display the value typed in the div 
  output.innerHTML = "Valid key: " + key;
  
  // You can do validation here, set the input field to
  // invalid is the name contains forbidden characters
  // or is too short
  // for example, let's forbid names with length < 5 chars
  if(key === "!") {
    output.innerHTML = "This key is forbidden!";
    // remove the forbodden char
    // current typed value
    var name = evt.target.value;
    // we use the substring JavaScript function
    // to remove the last character
    // first parameter = start index
    // second = last index
    evt.target.value = name.substring(0, name.length-1);
  }
}
```
Note that HTML5 forms and the multiple facets of form and input field validation are covered in depth in the HTML5 fundamentals course, which dedicates a whole week to this topic.

#### Example 2: do something while a slider is being moved


```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>JavaScript slider use</title>
</head>
<body>
  <h1>Simple <code>&lt;input type=range&gt;</code> field validation using the 'input' event</h1>
  <p>Just move the slider</p>
<label>
 1 <input type="range" 
         min=1
         max=12
          step=0.1
         oninput = "doSomething(event)"> 12
</label>
  <p>
  <span id="sliderValue"></span>
</p>  
</body>
</html>
```


```javascript
function doSomething(evt) {
  // this is the slider value
  var val = evt.target.value;  
  
  // get the output div
  var output = document.querySelector('#sliderValue');
  // display the value typed in the div 
  output.innerHTML = "Value selected: " + val;
}
```

#### Example 3: detect value changes in a number input field


```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>JavaScript number input use</title>
</head>
<body>
  <h1>Simple <code>&lt;input type=number&gt;</code> field validation using the 'input' event</h1>
  <p>type a number or use the small vertical arrows</p>
<label>
  Type a number: 
<input type="number" 
         min=1
         max=12
          step=0.1
         oninput = "doSomething(event)">
</label>
  <p>
  <span id="numberValue"></span>
</p>  
</body>
</html>
```


```javascript
function doSomething(evt) {
  // this is the slider value
  var val = evt.target.value;  
  
  // get the output div
  var output = document.querySelector('#numberValue');
  // display the value typed in the div 
  output.innerHTML = "Value selected: " + val;
}
```

#### Example 4: choose a color and do something


```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>JavaScript color chooser use</title>
</head>
<body>
  <h1>Simple <code>&lt;input type=color&gt;</code> use</h1>
  <p>Pick a color to change the background color of the page</p>
<label>
<input type="color" 
         onchange = "changePageBackgroundColor(this.value);">
  <!-- we could have used oninput= in the previous line -->
</label>
  <p>
  <span id="choosedColor"></span>
</p>  
</body>
</html>
```


```javascript
function changePageBackgroundColor(color) {
document.body.style.backgroundColor = color;  
  // get the output div
  var output = document.querySelector('#choosedColor');
  // display the value typed in the div 
  output.innerHTML = "Color selected: " + color;
}
```


---

#### Module 2: Adding interactivity to HTML documents   2.4 Handling events   Reference tables

# Reference tables

### Quick summary of event management in JavaScript

#### HTML5 EVENTS

There is no input or output in JavaScript. We treat events caused by user actions as inputs, and we manipulate the DOM structure as output. Usually in a JavaScript application, we will get info such as the key strokes, the mouse button clicks and the mouse position, and we will refer to these variables when determining what action to perform.

In any case, the events are called DOM events, and we use the DOM APIs to create ***event handlers***.

#### HOW TO LISTEN TO EVENTS

There are three ways to manage events in the DOM structure. You could attach an event inline in your HTML code like this:

#### Method 1: declare an event handler in the HTML code

```javascript
<div id="someDiv" onclick="alert('clicked!')"> content of the div </div>
```

This method is very easy to use, but it is not the recommended way to handle events. Indeed, although it currently works, it is deprecated 
(will probably be abandoned in the future). Mixing 'visual layer' (HTML) and 'logic layer' (JavaScript) in one place is really bad practice 
and causes a host of problems during development.

#### Method 2: attach an event handler to an HTML element in JavaScript

```javascript
document.getElementById('someDiv').onclick = function() {
   alert('clicked!');
}
```
This method is fine, but  you will not be able to attach multiple listener functions. If you need to do this, use the version shown below.

#### Method 3: register a callback to the event listener with the addEventListener method (preferred  method)

```javascript
document.getElementById('someDiv').addEventListener('click', function() {
   alert('clicked!');
}, false);
```
Note that the third parameter describes whether the callback has to be called during the captured phase. This is not important for now, just 
set it to `false` or ignore it (you can even pass only two parameters to the addEventListener function call and do not set this boolean parameter 
at all).

#### Details of the DOM event are passed to the event listener function

When you create an event listener and attach it to an element, the listener will create an event object to describe what happened. 
This object is provided as a parameter of the callback function:

```javascript
element.addEventListener('click', function(event) {
   // now you can use event object inside the callback
}, false);
```
Depending on the type of event you are listening to, you will consult different properties from the event object in order to obtain useful information such as: "which keys are pressed down?", "what is the location of the mouse cursor?", "which mouse button has been clicked?", etc.

In the following lessons, we will remind you how to deal with the keyboard and the mouse.

Further reading

In Method 1 (above), we mentioned that "mixing 'visual layer' (HTML) and 'logic layer' (JavaScript) ... is bad practice", and this is similarly reflected in many style features being deprecated in HTML5 and moved into CSS3. The management philosophy at play here is called "the separation of concerns" and applies in several ways to software development - at the code level, through to the management of staff. It's not part of the course, but professionals may find the following references useful:

* Separation of concerns - Wikipedia, the free encyclopedia - https://en.wikipedia.org/wiki/Separation_of_concerns
* Chapter 5. Separation of Concerns from Programming JavaScript Applications, by Eric Elliott, O'Reilly, 2013. - http://chimera.labs.oreilly.com/books/1234000000262/ch05.html
* The Art of Separation of Concerns by derekgreer, January 3, 2008 - http://aspiringcraftsman.com/2008/01/03/art-of-separation-of-concerns/

#### Reference tables for events and properties/methods

These tables are provided as a reference. They are a compilation of the most common event types sorted by domain (key, mouse, forms, etc.). For each domain you will see the most useful event types and their properties.

In the following sections, we will show  examples that use most of the events displayed in these tables.

### Event object

Most useful common properties:

|properties|     |
|----------|-----|
|type	|Returns the name of the event |
|target	|Returns the element that triggered the event |


Most useful common methods:

|methods|     |
|----------|-----|
|preventDefault()	|Cancels the event if it is cancelable, meaning that the default action that belongs to the event will not occur |
|stopPropagation()	|Prevents further propagation of an event during event flow |


### Page

Events related to the page lifecycle

There are many other events related to the page life cycle. Below are the most useful ones for an intro course:

|properties|     |
|----------|-----|

|load	| This event occurs when an object has loaded (including all its resources: images, etc.) This event is very useful when you want to run JS code and be sure that the DOM is ready (in other words, be sure that a document.getElementById(...) or document.querySelector(...) will not raise an error because the document has not been loaded and elements you are looking for are not ready.|
|resize	| The event occurs when the document view is resized. Usually we get the new size of the window inside the event listener using `var w = window.innerWidth;` and `var h = window.innerHeight;`|
|scroll	| The event occurs when an element's scrollbar is being scrolled. Usually, in the scroll event listener, we use things such as: `var max = document.body.scrollHeight - innerHeight;` `var percent = (pageYOffset / max);` ...to know the percentage of the scroll in the page.|

### Page event properties

There are no particular properties that need to be mentioned here. Usually, the load event listener corresponds to a JavaScript function 
that can be seen as **the main** function of your Web Application. It is good practice to start everything after the page has been completely 
loaded. In the resize listener, you get the new size of the window, or the new size of some HTML elements in the page (as they might have been resized too when the window was resized) and then you do something (redraw a graphic in an HTML canvas that takes into account the new canvas size, for example).

### Keyboard

#### Event types related to keyboard

| Event  |                    |
|--------|--------------------|
|keydown	|The event occurs when the user is pressing a key|
|keyup		|The event occurs when the user releases a key|
|keypress	|The event occurs when the user presses a key (up and release)|

keyboardEvent properties

| Property  |                    |
|-----------|--------------------|
|keyCode	|Returns the Unicode character code of the key that triggered the onkeypress ,onkeydown or onkeyup event |
|shiftKey	|Returns whether the "shift" key was pressed when the key event was triggered |
|ctrlKey	|Returns whether the "ctrl" key was pressed when the key event was triggered |
|altKey		|Returns whether the "alt" key was pressed when the key event was triggered |


### Mouse

#### Event types related to mouse

| Event  |                    |
|--------|--------------------|
|click		|The event occurs when the user clicks on an element (presses a button and releases it)|
|dblclick	|The event occurs when the user double-clicks on an element|
|mousedown	|The event occurs when the user presses a key (up and release)|
|mouseup	|The event occurs when a user releases a mouse button over an element|
|mousemove	|The event occurs when the pointer is moving while it is over an element|
|mouseenter	|The event occurs when the pointer is moved onto an element|
|mouseleave	|The event occurs when the pointer is moved out of an element|
|mouseover	|The event occurs when the pointer is moved onto an element, or onto one of its children|
|contextmenu	|The event occurs when the user right-clicks on an element to open a context menu|


#### MouseEvent properties

| Property  |                    |
|-----------|--------------------|
|button					|Returns which mouse button was pressed when the mouse event was triggered|
|clientX and clientY	|Returns the coordinates of the mouse pointer, relative to the element coordinate system that triggered the event|
|pageX and pageY		|Returns the coordinates of the mouse pointer, relative to the document, when the mouse event was triggered|
|screenX and screenY	|Returns the coordinates of the mouse pointer, relative to the screen, when an event was triggered|
|altKey, ctrlKey, shiftKey	|Returns whether the "alt, ctrl and shift" key was pressed when an event was triggered|
|detail					|Returns a number that indicates how many times the mouse was clicked|


### Forms

#### Events related to forms

| Event  |                    |
|--------|--------------------|
|input	|The event occurs when an element gets user input (e.g., a key is typed on an input field, a slider is moved, etc.)|
|change	|The event occurs when the content of a form element, the selection, or the checked state have changed (for <input>, <select>, and <textarea>). A change event listener on a slider will generate an event when the drag/move ended, while input events will be useful to do something as the slider is being moved.|
|focus	|The event occurs when an element gets focus (e.g., the user clicks in an input field)|
|blur	|The event occurs when an element loses focus (e.g., the user clicks on another element)|
|select	|The event occurs after the user selects some text (for <input> and <textarea>)|
|submit	|The event occurs when a form is submitted|


#### FormEvent properties

There are no particular properties that need to be mentioned here. Usually, on a form event listener, we check the content of the different input fields, using their value property. See examples in the course, in the part dealing with form events.


---

#### Module 2: Adding interactivity to HTML documents   2.4 Handling events   Discussion topics

# Discussion topics

Discussion topics and projects

Here is the discussion forum for this part of the course. Please either post your comments/observations/questions or share your creations.

See below for suggested topics of discussion.

Suggested topics

* Did you know the differences between clientX, pageX, etc. when dealing with mousemove events? Did you know the method we showed for getting the mouse position relative to the elements you're moving the mouse on?
* Did you know the different keyboard layouts, and the code and key event properties?

---

#### Module 2: Adding interactivity to HTML documents   2.5 The DOM API   Introduction

# Introduction

### The DOM standard - exploring the DOM of a document

When a user clicks on a link or enters a URL in the address of your Web browser, it downloads the page’s HTML text and builds up a model of the document’s structure called the DOM (Document Object Model). This model is used to render the HTML page on the screen.

The DOM is a standard  that describes how a document must be manipulated. It defines a “language- and platform neutral interface”. So, every browser offers the same JavaScript DOM API.

The DOM API is a programming interface the JavaScript programmer can use to modify the HTML content or the CSS style of HTML elements on the fly.

The DOM API provides the document object as a structured object, a group of nodes represented as a tree. We saw this in Module 1 when we revised the basic principles of HTML .

The document object also exposes a large set of methods to access and manipulate the structured document. Through the DOM, look for nodes (html elements that compose the page), move nodes, delete nodes, modify nodes (attributes, content), and also handle their associated events.

In JavaScript, the DOM is accessible through the property document of the global object window. We rarely manipulate the window object directly as it is implicit: window.document is the same as document. 

So by using this object, we can access and manipulate our page from JavaScript as a structured document.

Reminder from Module 1: HTML and the DOM

'Elements' are the pieces themselves, i.e., a paragraph, a header, and even the body are elements. Most elements can contain other elements - for example, the body element would contain header elements, paragraph elements, in fact pretty much all of the visible elements of the Document Object Model (developers call it the "DOM").

Let's take, for example, a simplified version of the last HTML code we showed you:

### There are different types of nodes in the DOM

There are different types of nodes, but don't worry - the most useful ones are highlighted in bold.

* Element (example: <ul></ul>)
* Text (example: <p>the text within the element p is a node of type text</p>)
* Document, DocumentFragment, DocumentType (example: <!doctype html> for html5), Comment (example: <!-- left column -->), ProcessingInstruction (example: <?php echo $name ?>)

#### Exploring the DOM with the devtool console

You can explore the DOM with the devtool console. This time we used Firefox for exploring the DOM, as it proposes a good structured view of the DOM and of its properties/methods:

---


#### Module 2: Adding interactivity to HTML documents   2.5 The DOM API   A warning about the DOM API

# A warning about the DOM API

The DOM and the DOM API can be cumbersome and complicated. There are many methods and properties for manipulating the DOM tree, that are not "very JavaScript". There are historical reasons for this: the DOM wasn’t designed exclusively for JavaScript. Rather, it tries to define a language-neutral interface that can be used in other systems as well — not just HTML but also XML, which is a generic data format with an HTML-like syntax.

HTML5 made some additions that are not in the DOM API but which greatly help the JavaScript programmer (we'll see this in a minute with the "selector API", for example).

So we've decided to focus on only 20% of the DOM API and on the selector API (for selecting elements in the DOM). These are the most useful parts and it will give you enough knowledge to solve nearly every problem where you need to manipulate the DOM.


--- 

#### Module 2: Adding interactivity to HTML documents   2.5 The DOM API   Accessing HTML elements

# Accessing HTML elements

>! missing video/transcript

### Accessing HTML elements

#### 1 - With the selector API (recommended)

Extract from HTML5 selectors API – It’s like a Swiss Army Knife for the DOM : "One of the many reasons for the success of JavaScript libraries like jQuery and Prototype, on top of their easing the pain of cross-browser development was how they made working with the DOM far less painful than it had previously been, and indeed how it was with the standard DOM. Being able to use arbitrary CSS selector notation to get matching elements from a document made the standard DOM methods seem antiquated, or at the very least, far too much like hard work.

Luckily, the standards and browser developers took notice. The W3C developed the Selectors API, a way of easily accessing elements in the DOM using standard CSS selector concepts, and browser developers have baked these into all modern browsers, way back to IE8."

The `querySelector(CSSSelector)` and `querySelectorAll(CSSSelector)` methods

Ah... these methods owe a lot to jQuery! They introduce a way to use CSS selectors (including CSS3 selectors) for requesting the DOM, like jQuery introduced ages ago.

Any CSS  selector can be passed as a parameter for these methods.

* While `querySelector(selector)` will return the first element in the DOM that matches the selector (and you will be able to work with it directly),
* `querySelectorAll(selector)` returns a collection of HTML elements corresponding to all elements matching the selector. To process the results, it will be necessary to loop over each of the elements in the collection.

Typical use:

Looking for an element in the whole document (the whole HTML page): call the querySelector method (or querySelectorAll) on the document object, that corresponds to the whole DOM tree of your web page:



```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>querySelector and querySelector example 1</title>
</head>
<body>
  <button onclick="addBorderToFirstImage();">
    Add a border to the first image
  </button>
  <br>
  <button onclick="resizeAllImages();">
    Resize all images
  </button>
  <br>
  <p>Click one of the buttons above!</p>
<img src="http://mainline.i3s.unice.fr/mooc/Ntvj5rq.png" 
     id="img1"
     width=200 alt="image #1">
<img src="http://mainline.i3s.unice.fr/mooc/yiU59oi.gif" 
     width=200 alt="image #2">
<img src="http://mainline.i3s.unice.fr/mooc/6FstYbc.jpg" 
     width=200 alt="image #3">
<img src="http://mainline.i3s.unice.fr/mooc/L97CyS4.png" 
     width=200 alt="image #4">
</body>
</html>
```


```javascript
window.onload = init;

function init() {
  // we're sure that the DOM is ready
  // before querying it
  
  // add a shadow to all images
  // select all images
  var listImages = document.querySelectorAll("img");

  // change all their width to 100px
  listImages.forEach(function(img) {
    // img = current image
    img.style.boxShadow = "5px 5px 15px 5px grey";
    img.style.margin = "10px";
  });  
  
}

function addBorderToFirstImage() {
  // select the first image with id = img1
  var img1 = document.querySelector('#img1');

  // Add a red border, 3px wide
  img1.style.border = '3px solid red';  
}

function resizeAllImages() {
  // select all images
  var listImages = document.querySelectorAll("img");

  // change all their width to 100px
  listImages.forEach(function(img) {
    // img = current image
    img.width = 100;
  });
}
```
Source code from the above example:

HTML part: we have two buttons that will call a JavaScript function (lines 2 and 6) where we will manipulate the DOM), and we have four images, the first one with an id equal to "img1" (lines 11, 14, 16 and 18). 

JavaScript part: the init function is executed as soon as the page is loaded (and the DOM is ready), in this function we add a shadow and margins to all images (lines 3-21). The two other functions are called when one of the HTML buttons is clicked (line 23 and line 31).


```javascript
window.onload = init; // run init once the page is loaded
 
function init() {
    // we're sure that the DOM is ready
    // before querying it
    // this function runs once the page is loaded
    // add a shadow to all images
    // select all images
    var listImages = document.querySelectorAll("img");
 
    // change all their width to 100px
    listImages.forEach(function(img) {
        // img = current image
        // add a shadow 5px left, 5 pixel down, 15px blur, 5px spread
        // grey
        img.style.boxShadow = "5px 5px 15px 5px grey";
        // add a margin 10px on each side
        img.style.margin = "10px";
    });
}
 
function addBorderToFirstImage() {
    // select the first image with id = img1
    var img1 = document.querySelector('#img1');
 
    // Add a red border, 3px wide
    img1.style.border = '3px solid red';
}
 
function resizeAllImages() {
    // select all images
    var listImages = document.querySelectorAll("img");
 
    // change all their width to 100px
    listImages.forEach(function(img) {
        // img = current image, we resize it by changing its
        // width attribute
        img.width = 100;
    });
}
```

Miscellanous examples of use of querySelector(CSSSelector) and querySelectorAll(CSSselector)

Here are some other examples that use more complicated CSS selectors. If you are not familiar with their syntax, we recommend that you follow the CSS basics, and HTML5 and CSS fundamentals courses from W3Cx.

#### Example 1: get all `<li>` directly in a `<ul>` of class nav:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>querySelector and querySelector example 1</title>
</head>
<body>
  <button onclick="firstLiClassRedInUl();">Select first li of class red and color it in red</button>
  <br>
  <button onclick="allLisInUlOfClassNav();">Underline All li in a ul of class nav</button>
  
<ul class="nav">
    <li>Home</li>
    <li class="red">Products</li>
    <li>About</li>
</ul>
  Another list:
  <ul>
    <li>Apple</li>
    <li class="red">Cherries</li>
    <li>Oranges</li>
</ul>
</body>
</html>

```


```javascript
function firstLiClassRedInUl() {
  // first li of class="red" in a ul
  var elm = document.querySelector("ul li.red");
  elm.style.color = 'red';
}

function allLisInUlOfClassNav() {
  // get all li directly in a ul of class nav
  var list = document.querySelectorAll("ul.nav > li");
  
  list.forEach(function(elm) {
    elm.style.textDecoration = "underline";
  })
}
```

#### Example 2: display all checked <input type="checkbox"> elements located inside an element of a given id:


```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>querySelector and querySelector example 1</title>
</head>
<body>
  <button onclick="displayListOfCheckedItems();">Show Checked items</button>
  <br>
<ul id="fruits">
    <li>
       <input type="checkbox" name="fruit" value="apples">Apples
    </li>
    <li>
       <input type="checkbox" name="fruit" value="oranges">
        Oranges
    </li>
    <li>
       <input type="checkbox" name="fruit" value="bananas">   
        Bananas
    </li>
    <li>
       <input type="checkbox" name="fruit" value="grapes">
        Grapes
    </li>
</ul>
</body>
</html>

```

```javascript
function displayListOfCheckedItems() {
  // all inputs that have been checked
  var listOfSelectedValues="";
  
  var list = document.querySelectorAll("#fruits input:checked");  
  list.forEach(function(elm) {
    listOfSelectedValues += elm.value + " ";
    
    // Put the li in red.
    // the li is the parent of the current input elem stored
    // in the elm variable
    elm.parentNode.style.color = 'green';
  });
  document.body.append("You selected: " + listOfSelectedValues);
}
```

JavaScript code: we select all elements of type input that have an attribute checked equal to true, and located inside an element whose id is "fruits". Notice the use of document.querySelectorAll, for selecting more than one element (line 6), then, we iterate on the list (line 8) and concatenate to the string variable listOfSelectedValues the value of each element (located in its value attribute). This is done in line 9.

Lines 9-12 use the parentNode property of the selected nodes in order to change the color of the <li> (parents of <input> elements selected) in red. In the DOM tree, we selected input elements that are each a child of a <li> element. The text displayed: "Apples", "Oranges" etc. belong to the <li> element. In order to access it from the <input> child we selected, we use elm.parentNode.

#### Example 3: change the background of all paragraphs <p> in an element of a given id:


```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>Change background color of p under an element whose id is known</title>
</head>
<body>
  <button onclick="changeBackGroundOfPs('firstDiv');">Change backgrounds of p under a given element known by id</button>
  <br>
<div id="firstDiv">
  <p>First paragraph.</p>
  <p>Second paragraph.</p>
</div>
</body>
</html>

```

```javascript
function changeBackGroundOfPs(id) {
  var paragraphs = document.querySelectorAll("#" + id + " p");

  // Another way to iterate on all elements in a collection
  for (var i = 0; i < paragraphs.length; i++ ) {
    paragraphs[i].style.backgroundColor = "lightGreen";
  }
}
```

JavaScript code: we build a CSS selector using the id passed as a parameter. In this example, the id is 'firstDiv', the id of the div at line 3 in the above code.

So, the variable CSS selector at line 2 in the JavaScript code below will have a value equal to "#firstDiv p", that means: select all <p> under an element whose id is "firstDiv". The paragraphs variable is a list that contains the paragraphs selected. Then we iterate on this list (this time using a for loop, which is an alternative method to using the forEach method used in previous examples) (line 5-7), and we change the background of all selected paragraphs (line 6).

```javascript
// all elements li in ul elements in an element of id=nav
var el = document.querySelector('#nav ul li');

// all li in a ul, but only even elements
var els = document.querySelectorAll('ul li:nth-child(even)');

// all td directly in tr in a form of class test
var els = document.querySelectorAll('form.test > tr > td');

// all paragraphs of class warning or error
querySelectorAll("p.warning, p.error");

// first element of id=foo or id=bar
querySelector("#foo, #bar");

// first p in a div
var div = document.getElementById("bar");
var p = div.querySelector("p");
```

### 2 - With the DOM API (old fashioned)

These methods are from the DOM API and can all be replaced by the `querySelector` and `querySelectorAll` methods that we've discussed. 
They are still used in many JavaScript applications, and are very simple to understand.

From the document we can access the elements composing our web page in a few ways:

* `document.getElementById(identifier)` returns the element which has the id `identifier`.
This is equivalent to `document.querySelector("#identifier');` (just add a `#` before the id when using a CSS selector). 

Example: `var elm = document.getElementById('myDiv');` is equivalent to `document.querySelector('#myDiv');`

* `document.getElementsByTagName(tagName)` returns a list of elements which are named `tagName`.
This is equivalent to `document.querySelectorAll(tagName);`

Example: `var list = document.getElementByTagName('img');` is equivalent to `document.querySelector('img');`

* `document.getElementsByClassName(className)` returns a list of elements which have the class `className`.
This is equivalent to `document.querySelectorAll('.className');` 

Example: `var list = document.getElementByClassName('important');` is equivalent to `document.querySelector('.important');` (just add a `.` before the class name when using a CSS selector). 

Notice that identifier, tagName and className must be of type String. 

---

#### Module 2: Adding interactivity to HTML documents   2.5 The DOM API   Changing the style of selected HTML elements

# Changing the style of selected HTML elements

### Changing the style of selected HTML elements

The style attribute: how to modify an HTML element's CSS properties from JavaScript

The most common way to modify the CSS style of one of several elements you selected using the DOM or Selector API, is to use the style attribute.

Typical use:

```javascript
// select the paragraph with id = "paragraph1"
var p = document.querySelector('#paragraph1');
 
// change its color
p.style.color = 'red';
```

### Warning: with the style attribute, you can modify (or read) any CSS property, but be careful: the syntax changes a little due to the fact that in JavaScript the "-" is a math operator, while in CSS it is used to separate properties made of multiple words, such as background-color.

#### When using such properties from JavaScript, the rule is simple:

1. Remove the `-` sign,
2. Capitalize the word after the "-" sign!

### Simple, isn't it?

Examples:

* `text-align` becomes `style.testAlign`
* `margin-left` becomes `style.marginLeft`
* etc.

The most useful CSS properties (we do recommend that you follow the W3Cx courses CSS basics, CSS and HTML5 fundamentals from W3Cx to 
learn more about CSS):

* `color`: changing the color of the text content of selected element(s),
* `background-color`: same but this time the background color,
* `margin` and `padding` properties (external and internal margins), including their variants: `margin-left`, `margin-top`, `margin-right`, `margin-bottom`, also `padding-left`, etc.
* `border` and `border-radius`: change the border, type (plain, dashed), color, thickness, rounded corners etc.
* `box-shadow` to add shadows to selected elements, 
* `font`, `font-style`: font characters and style (italic, bold, plain)
* `text-align` (centered, etc.)


Here are some examples:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>Change background color of p under an element whose id is known</title>
</head>
<body>
  <button onclick="changeCSSStyle();">Change different properties of the paragraphs, using the style attribute</button>
  <br>
<div id="firstDiv">
  <p id="p1">Paragraph 1.</p>
  <p id="p2">Paragraph 2.</p> 
  <p id="p3">Paragraph 3.</p>
  <p id="p4">Paragraph 4.</p>
  <p id="p5">Paragraph 5.</p>
  <p id="p6">Paragraph 6.</p>

</div>
</body>
</html>

```


```javascript
function changeCSSStyle(id) {
  var p = document.querySelector("#p1");

  p.style.color = 'red';
  p.innerHTML = 'style.color used to change the color';

  p = document.querySelector("#p2");

  p.style.backgroundColor = 'lightGreen';
  p.innerHTML = 'style.backgroundColor used';

  p = document.querySelector("#p3");

  p.style.marginLeft = '100px';
  p.innerHTML = 'style.leftMargin used to shift this paragraph 100px to the right';
  
  p = document.querySelector("#p4");

  p.style.border = '2px solid blue';
  p.style.padding = "20px";
  p.innerHTML = 'style.border and style.padding (internal margins) used';


  p = document.querySelector("#p6");

  p.style.textAlign = 'center';
  p.style.border = "1px dashed red";
  // for boxShadow: h-shadow v-shadow blur spread color
  p.style.boxShadow = "2px 2px 5px 0px grey";
  p.innerHTML = 'style.textAlign, style.border, style.bowShadow used';

}
```
#### Using the ClassList interface to change more than one CSS property simultaneously

External resources:

* The W3C specification about the classList DOM interface - https://www.w3.org/TR/dom/#dom-element-classlist
* An article from the Mozilla Developer's web site - https://hacks.mozilla.org/2010/01/classlist-in-firefox-3-6/

Until now, to manipulate CSS classes of an HTML element was a bit complex, both for verifying the presence of a class name in an element, and for adding or removing classes associated with a given element.

The ClassList interface simplifies it all by acting as a container object and by providing a set of methods to manipulate its content.

The classList property applies to an HTML element, and returns a collection of class names:


```javascript
var elem= document.querySelector("#id1");
 
var allClasses = elem.classList;
```

### The classList API

The list of methods usable on a classList object are add(), remove(), toggle() and contains().

```javascript
// By default, start without a class in the div: <div class=""/>
// Set "foo" as the class by adding it to the classList
div.classList.add('foo'); // now <div class="foo"/>

// Check that the classList contains the class "foo"
div.classList.contains('foo'); // returns true

// Remove the class "foo" from the list
div.classList.remove('foo'); // now <div class=""/>

// Check if classList contains the class "foo"
div.classList.contains('foo'); // returns false: "foo" is gone

// Check if class contains the class "foo",
// If it does, "foo" is removed, if it doesn't, it's added
div.classList.toggle('foo'); // class set to <div class="foo"/>
div.classList.toggle('foo'); // class set to <div class=""/>
```

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>querySelector and querySelector example 1</title>
</head>
<body>
  <button onclick="displayListOfCheckedItems();">Show Checked items</button>
  <button onclick="reset();">Reset list</button>
  <br>
<ul id="fruits">
    <li>
       <input type="checkbox" name="fruit" value="apples">Apples
    </li>
    <li>
       <input type="checkbox" name="fruit" value="oranges">
        Oranges
    </li>
    <li>
       <input type="checkbox" name="fruit" value="bananas">   
        Bananas
    </li>
    <li>
       <input type="checkbox" name="fruit" value="grapes">
        Grapes
    </li>
</ul>
</body>
</html>

```


```css
.checked {
    border: 2px dashed #000;
    background-color: green;
    color:yellow;
}

```


```javascript
function displayListOfCheckedItems() {
  // all inputs that have been checked
  var listOfSelectedValues="";
  
  var list = document.querySelectorAll("#fruits input:checked");  
  list.forEach(function(elm) {
    listOfSelectedValues += elm.value + " ";
    
    // get the li parent of the current selected input
    var liParent = elm.parentNode;
    // add the CSS class .checked
    liParent.classList.add("checked");
  });
  document.body.append("You selected: " + listOfSelectedValues);
}

function reset() {
  var list = document.querySelectorAll("#fruits input");  
  list.forEach(function(elm) {
    // uncheck
    elm.checked = false;
    
    // remove CSS decoration
    var liParent = elm.parentNode;
    liParent.classList.remove("checked");
  });
}
```

... and the `classList.add(CSS_class)` and `classList.remove(CSS_class)` methods on the `<li>` elements

---


#### Module 2: Adding interactivity to HTML documents   2.5 The DOM API   Changing the content of selected HTML elements

# Changing the content of selected HTML elements

### Modifying selected HTML elements

We've already seen many examples (even during week 1) in which we selected one or more elements, and modified their content. Let's summarise all the methods we've seen, and perhaps introduce a few new things...

Properties that can be used to change the value of selected DOM node

Using the innerHTML property

This property is useful when you want to change all the children of a given element. It can be used to modify the text content of an element, or to insert a whole set of HTML elements inside another one.

Typical use:


```javascript
var elem = document.querySelector('#myElem');
 
elem.innerHTML = 'Hello '; // replace content by Hello
 
elem.innerHTML += '<b>Michel Buffa</b>', // append at the end
                                         // Michel Buffa in bold
 
elem.innerHTML = 'Welcome' + elem.innerHTML; // insert Welcome
                                             // at the beginning
 
elem.innerHTML = ''; // empty the elem
```

Using the textContent property

It's also possible, with selected nodes/elements that contain text, to use the textValue property to read the text content or to modify it. There are subtle differences that can be seen in the above example (click the 'edit on CodePen" part on the top left, and once in codePen, open the devtool console):

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>Modifying content of selected DOM nodes</title>
</head>
<body>
  <h1>Open the console and look at the JavaScript code!</h1>
<p id="first">first paragraph</p>
<p id="second"><em>second</em> paragraph</p>
</body>
</html>

```


```javascript
window.onload = init;

function init() {
  // DOM is ready
  var firstP = document.querySelector("#first");
  console.log(firstP.textContent);
  console.log(firstP.innerHTML);

  firstP.textContent = "Hello I'm the first paragraph";
  console.log(firstP.textContent);

  var secondP = document.querySelector("#second");
  console.log(secondP.textContent);
  console.log(secondP.innerHTML);
  
  secondP.textContent = "Hello I'm the second paragraph";
  console.log(secondP.textContent);
  console.log(secondP.innerHTML);
}
```

#### Changing the attributes of selected elements

It's very common to modify the attributes of selected elements: the width of an image, CSS style with the style attribute, value of an input field, etc.

This example shows some of the things we can do:
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>Modifying content of selected DOM nodes</title>
</head>
<body>
  <h1>Try these</h1>
<p>What is your name: <input type="text" id="name" value="Michel"> <button onclick="resetName();">Reset (click to empty the input field)</button></p>
  <p>Pick a color: <input id="color" type="color" value='#FF0000'><button onclick="setToGreen();">Set color chooser to green</button></p>
  <p>In the next example, click on the input field and use the small vertical arrows to increase the value. Notice that the numbers go 1 by 1 and that the maximum value is 20. Then click the button and do the same thing!</p>
    <p>Pick a number between 0 and 20: <input id="number" type="number" min=0 max=20 step = 1 value='10'><button onclick="changeStep();">Change step and max attribute values </button></p>
  <p>Click the next image to change its url and size:</p>
<img src="https://www.paris-web.fr/2013/assets_c/2013/08/michel-buffa-thumb-143x143-372.jpg" onclick="changeAndResize(this)" alt="Michel Buffa">
</body>
</html>
```


```javascript
function resetName() {
  var inputField = document.querySelector("#name");
  inputField.value = "";
}

function setToGreen() {
  var colorChooser = document.querySelector("#color");
  colorChooser.value = "#00FF00";
}

function changeStep() {
  var number = document.querySelector("#number");
  number.value = 10;
  number.step = "0.1";
  number.max = 11;
}

function changeAndResize(img) {
    img.src="https://pbs.twimg.com/profile_images/110455194/n666194627_2302_400x400.jpg";
  img.width=250;
  img.style.border = "4px solid red";
}
```

---

#### Module 2: Adding interactivity to HTML documents   2.5 The DOM API   Adding new elements to the DOM

# Adding new elements to the DOM

### Adding new elements to the DOM

The DOM API comes with a set of methods you can use on DOM elements.

In general, to add new nodes to the DOM we follow these steps:

#### 1. Create a new element by calling the createElement() method, using a syntax like:
```javascript
var elm = document.createElement(name_of_the_element).
```

```javascript
var li = document.createElement('li');
var img = document.createElement('img'); etc.
```

#### 2. Set some attributes / values  / styles for this element. 


```javascript
li.innerHTML = '<b>This is a new list item in bold!</b>'; // can add HTML in it
li.textContent = 'Another new list item';
li.style.color = 'green'; // green text
img.src = "http://..../myImage.jpg"; // url of the image
img.width = 200;
```

#### 3. Add the newly created element to another element in the DOM, using append(), appendChild(), insertBefore() or the innerHTML property


```javascript
var ul = document.querySelector('#myList');
ul.append(li); // insert at the end, appendChild() could also be used (old)
ul.prepend(li); // insert at the beginning
ul.insertBefore(li, another_element_child_of_ul);// insert in the middle
document.body.append(img); // adds the image at the end of the document
```

### A warning about append vs appendChild, prepend, etc...

#### If the examples do not run on your browser (Edge, IE, old browsers), read this!

The DOM specification recently added some jQuery like methods that are similar to the ones proposed by the jQuery library 
(that was designed a long time ago to simplify DOM manipulations).

For a long time, developers used `document.appendChild` to add an element to the DOM. Now you can use document.append, 
which is shorter, along with some other methods such as `document.prepend` etc. All these methods are supported by recent 
browsers except Microsoft Edge (but support is coming soon). See this table for compatibility.

> In the course, we recommend that you use document.append, but if you are looking for maximum compatibility, you can either use document.appendChild instead of document.append (just search and replace all occurrences of document.append with document.appendChild in the examples), or add to your JavaScript code this polyfill.

Just copy and paste the 10 lines of JavaScript from the polyfill to your code and append will work on browsers that do not yet 
implement it.

Here is an example in JsBin that uses all these new methods, and that includes the polyfill for append and prepend at the end 
of the JavaScript code.

#### Example 1: use of the createElement(), append() methods and of the textContent attribute:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>Adding new elements to the DOM</title>
</head>
<body>
<label for="newNumber">Please enter a number</label>
<input type="number" id="newNumber" value=0>
<button onclick="add();">Add to the list</button>
<br>
<button onclick="reset();">Reset list</button>
 
<p>You entered:</p>
<ul id="numbers"></ul>
</body>
</html>
```


```css
input:invalid {
  color:pink;
}
```


```javascript
function add() {
  // get the current value of the input field
  var val = document.querySelector('#newNumber').value;
  if((val !== undefined) && (val !== "")) {
    // val exists and non empty
    // get the list of numbers. It's a <ul>
    var ul = document.querySelector("#numbers");
    // add it to the list as a new <li>
    var newNumber = document.createElement("li");
    newNumber.textContent = val;
    // or newNumber.innerHTML = val
    ul.append(newNumber);
  }
}
 
function reset() {
  // get the list of numbers. It's a <ul>
  var ul = document.querySelector("#numbers");
  // reset it: no children
  ul.innerHTML = ""; 
}
```

HTML code extract: we use an `<input type="number">` for entering a number (line 2). Then if one clicks on the **Add to the list** button, 
the add() JavaScript function is called (line 3), this will add the typed number to the empty list at line 7. If one presses the **reset** 
button, it will empty this same list by calling the `reset()` JavaScript function.

JavaScript code extract: notice at line 25 the use of the innerHTML property for resetting the content of the `<ul>` list. `innerHTML` 
corresponds to all the sub DOM contained inside the `<ul>...</ul>`. `InnerHTML` can be used for adding/deleting/modifying a DOM node's content.

#### Example 2: using the innerHTML property to add new elements

This is the same example, but in an abbreviated form, using the innerHTML property:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>Adding new elements to the DOM</title>
</head>
<body>
  <label for="newNumber">Please enter a number</label>
  <input type="number" id="newNumber" value=0>
  <button onclick="add()">Add to the list</button>
  <br>
  <button onclick="reset();">Reset list</button>

<p>You entered:</p>
<ul id="numbers"></ul>
</body>
</html>
```


```css
input:invalid {
  color:pink;
}
```


```javascript
function add() {
  // get the current value of the input field
  var val = document.querySelector('#newNumber').value;
  
  if((val !== undefined) && (val !== "")) {
    // val exists and non empty
    
    // get the list of numbers. It's a <ul>
    var ul = document.querySelector("#numbers");
     
    ul.innerHTML += "<li>" + val + "</li>";
  }
}

function reset() {
  document.querySelector("#numbers").innerHTML = "";
}
```

---

#### Module 2: Adding interactivity to HTML documents   2.5 The DOM API   Moving HTML elements in the DOM

# Moving HTML elements in the DOM


The `append()`, `appendChild()` methods normally adds  a new element to an existing one, as shown in this example:

```javascript
var li = createElement('li');
ul.append(li); // adds the new li to the ul element
```

One interesting thing to know is that if we do not create the new element, but rather get it from somewhere else in the 
document, it is then removed from its parents and added to the new parent.

In other words: it moves from its original location to become a child of the targetElem.

Let's see a very simple example:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>Moving elements using appendChild()</title>
</head>
<body>
  <p>Click on a browser image to move it to the list of cool browsers:</p><br/>
  <img src="http://mainline.i3s.unice.fr/mooc//ABiBCwZ.png" id="cr" 
       onclick="move(this)" alt="Logo Chrome">
  <img src="http://mainline.i3s.unice.fr/mooc//n7xo93U.png" id="ff" 
       onclick="move(this)" alt="Logo Firefox">
  <img src="http://mainline.i3s.unice.fr/mooc//ugUmuGQ.png" id="ie" 
       onclick="move(this)" alt="Logo IE">
  <img src="http://mainline.i3s.unice.fr/mooc//jfrNErz.png" id="op" 
       onclick="move(this)" alt="Logo Opera">
  <img src="http://mainline.i3s.unice.fr/mooc//gDJCG0l.png" id="sf" 
       onclick="move(this)" alt="Logo Safari"><br/>
  <div class="box" id="coolBrowsers">
      <p>Cool Web browsers</p>
  </div>
</body>
</html>
```


```css
.box {
  border: silver solid;
  width: 256px;
  height: 128px;
  margin: 10px;
  padding: 5px;
  float: left;
}
```


```javascript
function move(elem) {
  var targetList = document.querySelector('#coolBrowsers');
  targetList.append(elem);
  
  // trick to remove the click listener once
  // the image has been moved into the list
  elem.onclick = null;
}
```

### Another, more significant example, that also uses drag'n'drop

Notice that this example comes from the HTML5 advanced course. Our plan here is not to explain drag'n'drop in detail, but to show how 
`append()` can be used to move an element.

In this example, when a user starts to drag an element, the `drag()` JavaScript function is called. In this function we use the 
drag'n'drop clipboard to store the id of the image that is being dragged.

When the image is dropped, the `drop()` method is called. As the drop event listener is declared on the two divs (on the left and 
the right), we just call `append()` on the target div element, and this will add the dragged image to the div, while removing it 
from its original location.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Drag and drop</title>
     <meta charset="utf-8">
  </head>
<body>
  <p id="text" ondragstart="drag(this, event)">Drag and drop browser images in a zone:</p><br/>
  <img src="http://mainline.i3s.unice.fr/mooc/ABiBCwZ.png" id="cr" 
       ondragstart="drag(this, event)" alt="Logo Chrome">
  <img src="http://mainline.i3s.unice.fr/mooc/n7xo93U.png" id="ff" 
       ondragstart="drag(this, event)" alt="Logo Firefox">
  <img src="http://mainline.i3s.unice.fr/mooc/ugUmuGQ.png" id="ie" 
       ondragstart="drag(this, event)" alt="Logo IE">
  <img src="http://mainline.i3s.unice.fr/mooc/jfrNErz.png" id="op" 
       ondragstart="drag(this, event)" alt="Logo Opera">
  <img src="http://mainline.i3s.unice.fr/mooc/gDJCG0l.png" id="sf" 
       ondragstart="drag(this, event)" alt="Logo Safari"><br/>

  <div class="box" ondragover="return false" ondrop="drop(this, event)">
      <p>Cool Web browsers</p>
  </div>
  
  <div class="box" ondragover="return false" ondrop="drop(this, event)">
      <p>Web browsers from the 90's</p>
  </div>
</body>
</html>
```


```css
.box {
  border: silver solid;
  width: 256px;
  height: 128px;
  margin: 10px;
  padding: 5px;
  float: left;
}
```


```javascript
function drag(target, evt) {
    // When dragged, copy into the drag'n'drop clipboard
    // the id of the dragged elem (it's target.id)
        evt.dataTransfer.setData("browser", target.id);
    }

function drop(target, evt) {
    // get the id of the element being dragged
        var id = evt.dataTransfer.getData("browser");
  
        target.appendChild(document.getElementById(id));
      // prevent default behavior
      evt.preventDefault();
}
```

---

#### Module 2: Adding interactivity to HTML documents   2.5 The DOM API   Removing elements from the DOM

# Removing elements from the DOM

Let's take an example that we've already encountered. This time, you will check the elements you want to remove from the list!
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>RemoveChild example</title>
</head>
<body>
  <button onclick="removeSelected();">Remove selected items</button>
  <button onclick="reset();">Reset in initial configuration</button>
  <br>
<ul id="fruits">
    <li>
       <input type="checkbox" name="fruit" value="apples">Apples
    </li>
    <li>
       <input type="checkbox" name="fruit" value="oranges">
        Oranges
    </li>
    <li>
       <input type="checkbox" name="fruit" value="bananas">   
        Bananas
    </li>
    <li>
       <input type="checkbox" name="fruit" value="grapes">
        Grapes
    </li>
</ul>
</body>
</html>
```


```javascript
function removeSelected() {  
  var list = document.querySelectorAll("#fruits input:checked"); 
  var ul = document.querySelector("#fruits");
  
  list.forEach(function(elm) {
    // elm is an <input type="checkbox">, its parent is a li
    // we want to remove from the <ul> list
    // when we remove the <li>, the <input> will also
    // be removed, as it's a child of the <li>
    var li = elm.parentNode;
    ul.removeChild(li);
  });
}

function reset() {
  var ul = document.querySelector("#fruits");
  // Empty the <ul>
  ul.innerHTML = "";
  
  // Adds each list item to the <ul> using innerHTML += ...
  ul.innerHTML += "<li><input type='checkbox' name='fruit' value='apples'>Apples</li>";

  ul.innerHTML += "<input type='checkbox' name='fruit' value='oranges'>Oranges</li><br>";

    ul.innerHTML += "<input type='checkbox' name='fruit' value='bananas'>Bananas</li><br>";

    ul.innerHTML += "<input type='checkbox' name='fruit' value='grapes'>Grapes</li>";
}
```

JavaScript code extract: we need to get the `<ul>` that contains all the `<li><input type="checkbox"></li>` elements (line 3). 
This is the element we will use for calling `removeChild(...)`. The loop on the checked element (lines 5-12) iterates on a list 
of checked input elements. In order to make both the text (Apples, Oranges, etc.) AND the checkbox disappear, we need to access 
the different `<li>` elements that contain the selected checkboxes. This is done in line 10. Then, we can call `ul.removeChild(li)` 
on the `<ul>` for removing the `<li>` that contains the selected element (line 11). 

### Remove all children of an element using the innerHTML property

In the same example, if you look at the reset() JavaScript function, we use the ul's `innerHTML` property both for emptying the 
list (lines 3-4) and for appending to it all the initial HTML code (lines 6-17):


```javascript
function reset() {
  var ul = document.querySelector("#fruits");
  // Empty the <ul>
  ul.innerHTML = "";
  // Adds each list item to the <ul> using innerHTML += ...
  ul.innerHTML += "<li><input type='checkbox' name='fruit'   
                   value='apples'>Apples</li>";
 
  ul.innerHTML += "<input type='checkbox' name='fruit' 
                   value='oranges'>Oranges</li><br>";
 
  ul.innerHTML += "<input type='checkbox' name='fruit'
                   value='bananas'>Bananas</li><br>";
 
  ul.innerHTML += "<input type='checkbox' name='fruit'
                   value='grapes'>Grapes</li>";
}
```

---

#### Module 2: Adding interactivity to HTML documents   2.5 The DOM API   Discussion topics

# Discussion topics

### Discussion topics

Here is the discussion forum for this part of the course. Please either post your comments/observations/questions or share your creations.

See below for suggested topics of discussion.

Suggested topics

* Did you know there were different keyboard layouts?
* Did you know the best practices in order to make a Web application compatible with different keyboard layouts?
* Did you know there were different properties for getting the mouse coordinates?
* Did you know the method we proposed for getting the mouse coordinate relative to the element the mouse is being moved on?
* Sometimes, detecting key events on a canvas HTML element is tricky. Do not forget to visit the HTML5 Coding essentials and Best practices MOOC at W3Cx, as we cover these in details in the section about the HTML5 canvas element.

---

#### Module 2: Adding interactivity to HTML documents   2.6 Let's write a small game   Introduction to drawing/animating

# Introduction to drawing/animating

### Live coding video: basic example showing how to draw in a canvas


>! Missing video/trasncript

### Introduction to drawing/animating

[Note: drawing and animating within a canvas is presented in detail in the W3C HTML5 Coding Essentials and Best Practices course, in modules 3 and 4.

#### HTML5 Canvas basic usage

The HTML5 canvas is a transparent element that is useful for drawing and animating. We'll see some simple examples here, as we're going to finish this week by writing a small, simple game together, that will use most of what we've learnt so far: loops, conditional statements, events, functions, callbacks, simple objects, a few input fields, etc.

A typical HTML code for adding a canvas to a Web page:

```javascript
<!DOCTYPE html>
<html lang="en">
 <head>
  <meta charset="utf-8">
  <title>Draw a monster in a canvas</title>
 </head>
 <body>
  <canvas id="myCanvas" width="200" height="200"></canvas>
 </body>
</html>
```
The canvas declaration is at line 8. Use attributes to give it a `width` and a `height`, but unless you add some CSS properties, you will 
not see it on the screen because it's transparent!

Let's use CSS to reveal the canvas, for example, add a 1px black border around it:
```css
canvas {
   border: 1px solid black;
}
```
And here is a reminder of best practice when using the canvas:

1. **Use a function that is called AFTER the page is fully loaded** (and the DOM is ready), select the canvas in the DOM (this is the `init` function (as in `window.onload = init`) we already saw many times).
2. **Then, get a 2D graphic context for this canvas **(the context is an object we will use to draw on the canvas, to set global properties such as color, gradients, patterns and line width).
3. **Only then can you can draw something**,
4. **Do not forget to use global variables for the canvas and context objects**. I also recommend keeping the `width` and `height` of the canvas somewhere. These might be useful later.
5. **For each function that will change the context (color, line width, coordinate system, etc.), start by saving the context, and end by restoring it**.

#### Example 1: some drawing examples (wireframe and filled rectangle, filled circle, filled text, changing colors)
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>Draw a monster in a canvas</title>
</head>
<body>
  <canvas id="myCanvas"  width="200" height="200"></canvas>
</body>
</html>
```


```css
canvas {
  border: 1px solid black;
}
```


```javascript
/ useful to have them as global variables
var canvas, ctx;

window.onload = function init() {
    // called AFTER the page has been loaded
    canvas = document.querySelector("#myCanvas");
    // important, we will draw with this object
    ctx = canvas.getContext('2d');
  
    // ready to go !
    // filled rectangle
    ctx.fillStyle = 'red';
    ctx.fillRect(10, 10, 30, 30);
  
    // wireframe rectangle
    ctx.strokeStyle = 'green';
    ctx.lineWidth = 4;
    ctx.strokeRect(100, 40, 40, 40);
  
    // fill circle, will use current ctx.fillStyle
    ctx.beginPath();
    ctx.arc(60, 60, 10, 0, 2*Math.PI);
    ctx.fill();
  
    // some text
    ctx.fillStyle = "purple";
    ctx.font = "20px Arial";
    ctx.fillText("Hello!", 60, 20);
}
```

#### Explanations:

1. We use a function (line 4) called after the page is loaded (we say **after the DOM is ready*), so that the querySelector at line 6 will return the canvas.  If the page was not completely loaded and if this code had been run before it had finished loading, the canvas value would have been **undefined**.
2. Once we have the canvas, we request a **graphic context* (line 8). This is a variable for 2D or 3D  drawing on a canvas (in our case: 2D!) that we will use for drawing or setting colors, line widths, text fonts, etc.
3. Then we can draw. Here we show only a few things you can do with the canvas API, but believe me, you can do much more (draw images, gradients, textures, etc.)! At line 15, we draw a filled rectangle. Parameters are the x and y coordinates of the top left corner (x goes to the right, y to the bottom of your screen), and the width and the height of the rectangle. At line 14, we used the `fillStyle` property of the context to set the color of filled shapes. This means: *now, all filled shapes you are going to draw will be in red!*. It's like a global setting.
4. Lines 17-20 draw a green wireframe rectangle, with a line width equal to 4 pixels. Notice the use of `stroke` instead of `fill` in the property name `strokeStyle/fillStyle` and in the context method for drawing a rectangle `strokeRect/fillRect`.
5. Lines 23-25 draw a filled circle. The syntax is a bit different as circles are parts of a `path` (see the HTML5 fundamentals course, we explain the concept of `path` in the canvas API). Just keep in mind for now that before drawing a circle you need to call `beginPath()`. The call to `arc(x, y, radius, start_angle, end_angle)` does not draw the circle, it defines it. The next instruction `ctx.fill()` at line 25 will draw all shapes that have been defined since a new path began, as filled shapes. Calling `ctx.stroke()` here, instead of `ctx.fill()` would have drawn a wireframe circle instead of a filled one. Also note that the filled circle is red even if we did not specify the color. Remember that we set `ctx.fillStyle = 'red'` at line 14. Unless we change this, all filled shapes will be red.
6. Lines 28-30 draw a filled text. The call to `filltext(message, x, y)` draws a filled text at the x,y position; this time in purple as we called `ctx.fillStyle='purple'` before calling `fillText(...)`

#### Example 2: functions that save and restore the context before drawing

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>Draw a monster in a canvas</title>
</head>
<body>
  <canvas id="myCanvas"  width="200" height="200"></canvas>
</body>
</html>
```


```css
canvas {
  border: 1px solid black;
}
```


```javascript
// useful to have them as global variables
var canvas, ctx, w, h; 

window.onload = function init() {
    // called AFTER the page has been loaded
    canvas = document.querySelector("#myCanvas");
  
    // often useful
    w = canvas.width; 
    h = canvas.height;  
  
    // important, we will draw with this object
    ctx = canvas.getContext('2d');
  
    // ready to go !
    drawFilledRectangle(10, 10, 20, 20, "red");
  
    drawFilledCircle(100, 100, 15, "green");
};

function drawFilledRectangle(x, y, width, height, color) {
    // GOOD practice: save the context, use 2D trasnformations
    ctx.save();
  
    // translate the coordinate system, draw relative to it
    ctx.translate(x, y);
  
    ctx.fillStyle = color;
    // (0, 0) is the top left corner of the monster.
    ctx.fillRect(0, 0, width, height);
  
    // GOOD practice: restore the context
    ctx.restore();
}

function drawFilledCircle(x, y, radius, color) {
    // GOOD practice: save the context, use 2D trasnformations
    ctx.save();
  
    // translate the coordinate system, draw relative to it
    ctx.translate(x, y);
  
    ctx.fillStyle = color;
    // (0, 0) is the top left corner of the monster.
    ctx.beginPath();
    ctx.arc(0, 0, radius, 0, 2*Math.PI);
    ctx.fill();
 
    // GOOD practice: restore the context
    ctx.restore();
}
```

### Explanations:

This time we've written two functions for a cleaner code: one function that draws a filled rectangle with a given color, and one function that draws a filled circle, with a given color.

The values for `x`, `y`, `width`, `height`, `radius`, `color` can be passed as parameters to these functions.

When a function changes anything to the **global context**: filled or stroke color, line width, or the position of the coordinate system (located by default in 0, 0, at the top left of the canvas), then it is good practice to save this context at the beginning of the function, with a call to `ctx.save()`, and to restore it at the end of the function, with a call to `ctx.restore()`. In this way, any change to the **global context** won't have any effect outside of the function.

We used also `ctx.translate(x, y)` in order to move the rectangle and the circle (look, they have been drawn at `x=0`, `y=0`, but as we translate the origin of the coordinate system with `ctx.translate`, the shapes are located in x, y on in the canvas). This is also a good practice: indeed, if we add more shapes (like eyes in the rectangle, in order to draw a monster), using coordinates relative to 0, 0, the whole set of shapes will be translated by the call to `ctx.translate(x, y)`. This will make it easier to draw characters, monsters, etc. as we will see in a third example.

#### Example 3: draw a monster instead of a simple rectangle or circle

This is where you reap the benefits of your good habits of saving/restoring the context and using ctx.translate(x, y)!

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>Draw a monster in a canvas</title>
</head>
<body>
  <canvas id="myCanvas"  width="200" height="200"></canvas>
</body>
</html>
```

```javascript
/ useful to have them as global variables
var canvas, ctx, w, h; 


window.onload = function init() {
    // called AFTER the page has been loaded
    canvas = document.querySelector("#myCanvas");
  
    // often useful
    w = canvas.width; 
    h = canvas.height;  
  
    // important, we will draw with this object
    ctx = canvas.getContext('2d');
  
    // ready to go !
    // Try to change the parameter values to move
    // the monster
    drawMyMonster(10, 10);
};

function drawMyMonster(x, y) {
    // draw a big monster !
    // head
  
    // GOOD practice: save the context, use 2D trasnformations
    ctx.save();
  
    // translate the coordinate system, draw relative to it
    ctx.translate(x, y);
  
    // (0, 0) is the top left corner of the monster.
    ctx.strokeRect(0, 0, 100, 100);
  
    // eyes, x=20, y=20 is relative to the top left corner
    // of the previous rectangle
    ctx.fillRect(20, 20, 10, 10);
    ctx.fillRect(65, 20, 10, 10);
  
    // nose
    ctx.strokeRect(45, 40, 10, 40);
  
    // mouth
   ctx.strokeRect(35, 84, 30, 10);
  
   // teeth
   ctx.fillRect(38, 84, 10, 10);
   ctx.fillRect(52, 84, 10, 10);
  
   // GOOD practice: restore the context
   ctx.restore();
}
```

In this small example, we used the context object to draw a monster using the default color (black) and wireframe and filled modes:

* `ctx.fillRect(x, y, width, height`): draws a rectangle whose top left corner is at (x, y) and whose size is specified by the width 
and height parameters; and both outlined by, and filled with, the default color.
* `ctx.strokeRect(x, y, width, height)`: same but in wireframe mode.
* Note that we use (line 30) `ctx.translate(x, y)` to make it easier to move the monster around. So, all the drawing instructions 
are coded as if the monster was in (0, 0), at the top left corner of the canvas (look at line 33). We draw the body outline with a 
rectangle starting from (0, 0). Calling `context.translate` **changes the coordinate system** by moving the **old (0, 0)** to (x, y) 
and keeping other coordinates in the same position relative to the origin.
* Line 19: we call the `drawMonster` function with (10, 10) as parameters, which will cause the original coordinate system to be 
translated by (10, 10).
* And if we change the coordinate system (this is what the call to `ctx.translate(...)` does) in a function, it is good practice 
to always save the previous context at the beginning of the function and restore it at the end of the function (lines 27 and 50).

---

#### Module 2: Adding interactivity to HTML documents   2.6 Let's write a small game   Animating

# Animating

### Live coding video: basic animation techniques

>! missing video/transcript


A typical animation loop will do the following at regular intervals:

1. Clear the canvas
2. Draw graphic objects / shapes
3. Move graphic shapes / objects
4. Go to step 1

Optional steps can be:

* Look at the keyboard / mouse / gamepad if we need to do something according to their status (i.e. if the left arrow is pressed: move the player to the left)
* Test collisions: the player collided with an enemy, remove one life
* Test game states: if there are no more lives, then go to the **game over** state and display a **game over** menu.
* Etc.

#### Example 1: let's do some animation

There are different methods for coding an animation loop in JavaScript, that are described in the above video, and detailed both 
in the HTML5 Coding Essentials and Best Practices W3Cx course (week 4), and in the HTML5 Apps and Games W3Cx course 
(Week 2 is for learning how to code HTML5 games).

In this intro course, we'll only use the recommended one, without going into advanced use.

The trick is to write a function, and at the end of this function, to ask the browser to call it again in 1/60th of a second if possible.

Here is an example:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>Draw a monster in a canvas</title>
</head>
<body>
  <canvas id="myCanvas"  width="200" height="200"></canvas>
</body>
</html>
```


```javascript
// useful to have them as global variables
var canvas, ctx, w, h; 
var xMonster = 10;
var yMonster = 10;
var monsterSpeed = 1;

window.onload = function init() {
    // called AFTER the page has been loaded
    canvas = document.querySelector("#myCanvas");
  
    // often useful
    w = canvas.width; 
    h = canvas.height;  
  
    // important, we will draw with this object
    ctx = canvas.getContext('2d');
  
    // ready to go !
    mainLoop();
};

function mainLoop() {
  // 1 - clear the canvas. We told you that w, and h will be useful!
  ctx.clearRect(0, 0, w, h);
  
  // 2 - draw the monster
  drawMyMonster(xMonster, yMonster);
  
  // 3 - move the monster
  xMonster += monsterSpeed;
  
  // 4 - test collisions with vertical boundaries
   if (((xMonster + 100)> w) || (xMonster < 0))  {
     // collision with left or right wall
    // change the direction of movement
    monsterSpeed = -monsterSpeed;
  }
  
  // 5 - request a new frame of animation in 1/60s
  requestAnimationFrame(mainLoop);
}

function drawMyMonster(x, y) {
    // draw a big monster !
    // head
  
    // GOOD practice: save the context, use 2D trasnformations
    ctx.save();
  
    // translate the coordinate system, draw relative to it
    ctx.translate(x, y);
  
    // (0, 0) is the top left corner of the monster.
    ctx.strokeRect(0, 0, 100, 100);
  
    // eyes, x=20, y=20 is relative to the top left corner
    // of the previous rectangle
    ctx.fillRect(20, 20, 10, 10);
    ctx.fillRect(65, 20, 10, 10);
	
	// nose
    ctx.strokeRect(45, 40, 10, 40);
  
    // mouth
    ctx.strokeRect(35, 84, 30, 10);
  
    // teeth
    ctx.fillRect(38, 84, 10, 10);
    ctx.fillRect(52, 84, 10, 10);
  
   // GOOD practice: restore the context
   ctx.restore();
}
```

#### Example 2: animating a ball that bounces on the sides of the canvas (walls)


```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>Draw a monster in a canvas</title>
</head>
<body>
  <canvas id="myCanvas"  width="200" height="200"></canvas>
</body>
</html>

```

```javascript
// useful to have them as global variables
var canvas, ctx, w, h; 
var ball = {
  x: 100,
  y:100,
  radius: 15,
  color:'green',
  speedX:2,
  speedY:1
}

var player = {
  x:10,
  y:10,
  width:20,
  height:20,
  color:'red'
}

window.onload = function init() {
    // called AFTER the page has been loaded
    canvas = document.querySelector("#myCanvas");
  
    // often useful
    w = canvas.width; 
    h = canvas.height;  
  
    // important, we will draw with this object
    ctx = canvas.getContext('2d');
  
    // ready to go !
    mainLoop();
};

function mainLoop() {
  // 1 - clear the canvas
  ctx.clearRect(0, 0, w, h);
  
  // draw the ball and the player
  drawFilledRectangle(player);
  drawFilledCircle(ball);

  // animate the ball that is bouncing all over the walls
  moveBall(ball);
  
  // ask for a new animation frame
  requestAnimationFrame(mainLoop);
}

function moveBall(b) {
  b.x += b.speedX;
  b.y += b.speedY;
  
  testCollisionBallWithWalls(b);
}

function testCollisionBallWithWalls(b) {
    // COLLISION WITH VERTICAL WALLS ?
    if((b.x + b.radius) > w) {
    // the ball hit the right wall
    // change horizontal direction
    b.speedX = -b.speedX;
    
    // put the ball at the collision point
    b.x = w - b.radius;
  } else if((b.x -b.radius) < 0) {
    // the ball hit the left wall
    // change horizontal direction
    b.speedX = -b.speedX;
    
    // put the ball at the collision point
    b.x = b.radius;
  }
  
  // COLLISIONS WTH HORIZONTAL WALLS ?
  // Not in the else as the ball can touch both
  // vertical and horizontal walls in corners
  if((b.y + b.radius) > h) {
    // the ball hit the right wall
    // change horizontal direction
    b.speedY = -b.speedY;
    
    // put the ball at the collision point
    b.y = h - b.radius;
  } else if((b.y -b.radius) < 0) {
    // the ball hit the left wall
    // change horizontal direction
    b.speedY = -b.speedY;
    
    // put the ball at the collision point
    b.Y = b.radius;
  }  
}

function drawFilledRectangle(r) {
    // GOOD practice: save the context, use 2D trasnformations
    ctx.save();
  
    // translate the coordinate system, draw relative to it
    ctx.translate(r.x, r.y);
  
    ctx.fillStyle = r.color;
    // (0, 0) is the top left corner of the monster.
    ctx.fillRect(0, 0, r.width, r.height);
  
    // GOOD practice: restore the context
    ctx.restore();
}

function drawFilledCircle(c) {
    // GOOD practice: save the context, use 2D trasnformations
    ctx.save();
  
    // translate the coordinate system, draw relative to it
    ctx.translate(c.x, c.y);
  
    ctx.fillStyle = c.color;
    // (0, 0) is the top left corner of the monster.
    ctx.beginPath();
    ctx.arc(0, 0, c.radius, 0, 2*Math.PI);
    ctx.fill();
 
    // GOOD practice: restore the context
    ctx.restore();
}
```

#### Explanations:

This time we've used "simple objects" for the circle and the rectangles, and we've called them "player" and "ball":


```javascript
var ball = {
  x: 100,
  y:100,
  radius: 15,
  color:'green',
  speedX:2,
  speedY:1
}
 
var player = {
  x:10,
  y:10,
  width:20,
  height:20,
  color:'red'
}
```

With this syntax, it's easier to manipulate **the x pos of the ball** - you just have to use `ball.x`. we added two properties to the 
ball object: `speedX` and `speedY`. Their value is the number of pixels that will be added to the current `ball.x` and `ball.y` position, 
at each frame of animation.

Let's look at the animation loop:

```javascript
function mainLoop() {
  // 1 - clear the canvas
  ctx.clearRect(0, 0, w, h);
  // draw the ball and the player
  drawFilledRectangle(player);
  drawFilledCircle(ball);
 
  // animate the ball that is bouncing all over the walls
  moveBall(ball);
  // ask for a new animation frame
  requestAnimationFrame(mainLoop);
}
```

Now, let's decompose the animation loop in some external functions to make it more readable. At each frame of animation, we will 
clear the canvas, draw the player as a rectangle, draw the ball as a circle, and move the ball. 

You can take a look at the new versions of drawFilledRectangle that now take only one parameter named r, instead of x, y, width, 
height and a color. We've only changed a few things in its code (changed x to `r.x`, y to `r.y`, color to `r.color` etc.)

Let's look at the moveBall function:

```javascript
function moveBall(b) {
    b.x += b.speedX;
    b.y += b.speedY;
    testCollisionBallWithWalls(b);
}
```

This function is called 60 times per second. So, 60 times per second we modify the `b.x` and `b.y` positions of the ball passed as 
parameter by adding to them the `b.speedX` and `b.speedY` property values.

Notice that we call `moveBall(ball)` from `mainLoop`. In the `moveBall` function, the ball passed as a parameter becomes the b parameter. 
So when we change the `b.x` value inside the function, we are in reality changing the x value of the global object ball! 

Ok, and at line 5 we call `testCollisionBallWithWalls(b)`, which will test if the ball b hits a vertical or horizontal wall. Let's see 
an extract of this function now:

```javascript
function testCollisionBallWithWalls(b) {
    // COLLISION WITH VERTICAL WALLS?
    if((b.x + b.radius) > w) {
        // the ball hit the right wall
        // change horizontal direction
        b.speedX = -b.speedX;
        // put the ball at the collision point
       b.x = w - b.radius;
    } ...
    ...
}
```

At line 3 you can see the test that checks if the ball b hits the right side of the canvas. The right wall is at w (the width of the canvas)
on the X-axis. If we compare `(b.x + b.radius)` with w, we can check if a part of the ball extends beyond the right wall. 

Remember that each 1/60th of a second, the ball moves a certain number of pixels to the right (the exact value is `b.speedX`). Imagine 
that the ball moves 10 pixels to the right at each frame of animation. At some point, it will **cross the right wall**. We cannot just 
change the sign of `b.speedX` to make it go to the other side. If we did this, it may stay stuck against the side with one half of the 
ball on either side of the wall. 

If we now remove `b.speedX` to the `ball.x` position, we return the ball to the position it was in before it hit the wall. If we then 
reverse `speedX`, the ball will indeed start moving with a reverse horizontal speed. This will work but can give a strange visual effect 
if the balls moves, say, 20 pixels per frame or more. The ball will never be in a position where the eye can ***see it against the wall***. 
This is why experienced game coders know that you just need to put the ball at the contact position, not to its previous position, 
before reversing the speed value. This is done at lines 8-9. Try changing speedX to say, 20, and you'll see what we mean.


---

#### Module 2: Adding interactivity to HTML documents   2.6 Let's write a small game   Animating multiple objects

# Animating multiple objects

Here, we have ball1, ball2 and ball3. In the animation loop we draw and move these three balls. Here is the result:


```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>Draw a monster in a canvas</title>
</head>
<body>
  <canvas id="myCanvas"  width="400" height="400"></canvas>
</body>
</html>

```


```javascript
// useful to have them as global variables
var canvas, ctx, w, h; 
var ball1 = {
  x: 100,
  y:100,
  radius: 30,
  color:'blue',
  speedX:2,
  speedY:1
}

var ball2 = {
  x: 60,
  y:130,
  radius: 55, 
  color:'purple',
  speedX:3,
  speedY:1
}

var ball3 = {
  x: 200,
  y:250,
  radius: 15,
  color:'green',
  speedX:3,
  speedY:5
}

var player = {
  x:10,
  y:10,
  width:20,
  height:20,
  color:'red'
}

window.onload = function init() {
    // called AFTER the page has been loaded
    canvas = document.querySelector("#myCanvas");
  
    // often useful
    w = canvas.width; 
    h = canvas.height;  
  
    // important, we will draw with this object
    ctx = canvas.getContext('2d');
  
    // ready to go !
    mainLoop();
};

function mainLoop() {
  // 1 - clear the canvas
  ctx.clearRect(0, 0, w, h);
  
  // draw the ball and the player
  drawFilledRectangle(player);
  drawFilledCircle(ball1);
  drawFilledCircle(ball2);
  drawFilledCircle(ball3);

  // animate the ball that is bouncing all over the walls
  moveBall(ball1);
  moveBall(ball2);
  moveBall(ball3);
  
  // ask for a new animation frame
  requestAnimationFrame(mainLoop);
}

function moveBall(b) {
  b.x += b.speedX;
  b.y += b.speedY;
  
  testCollisionBallWithWalls(b);
}

function testCollisionBallWithWalls(b) {
    // COLLISION WITH VERTICAL WALLS ?
    if((b.x + b.radius) > w) {
    // the ball hit the right wall
    // change horizontal direction
    b.speedX = -b.speedX;
    
    // put the ball at the collision point
    b.x = w - b.radius;
  } else if((b.x -b.radius) < 0) {
    // the ball hit the left wall
    // change horizontal direction
    b.speedX = -b.speedX;
    
    // put the ball at the collision point
    b.x = b.radius;
  }
  
  // COLLISIONS WTH HORIZONTAL WALLS ?
  // Not in the else as the ball can touch both
  // vertical and horizontal walls in corners
  if((b.y + b.radius) > h) {
    // the ball hit the right wall
    // change horizontal direction
    b.speedY = -b.speedY;
    
    // put the ball at the collision point
    b.y = h - b.radius;
  } else if((b.y -b.radius) < 0) {
    // the ball hit the left wall
    // change horizontal direction
    b.speedY = -b.speedY;
    
    // put the ball at the collision point
    b.Y = b.radius;
  }  
}

function drawFilledRectangle(r) {
    // GOOD practice: save the context, use 2D trasnformations
    ctx.save();
  
    // translate the coordinate system, draw relative to it
    ctx.translate(r.x, r.y);
  
    ctx.fillStyle = r.color;
    // (0, 0) is the top left corner of the monster.
    ctx.fillRect(0, 0, r.width, r.height);
  
    // GOOD practice: restore the context
    ctx.restore();
}

function drawFilledCircle(c) {
    // GOOD practice: save the context, use 2D trasnformations
    ctx.save();
  
    // translate the coordinate system, draw relative to it
    ctx.translate(c.x, c.y);
  
    ctx.fillStyle = c.color;
    // (0, 0) is the top left corner of the monster.
    ctx.beginPath();
    ctx.arc(0, 0, c.radius, 0, 2*Math.PI);
    ctx.fill();
 
    // GOOD practice: restore the context
    ctx.restore();
}
```

#### Extract of the source code: the mainLoop function

```html
function mainLoop() {
    // 1 - clear the canvas
    ctx.clearRect(0, 0, w, h);
    // draw the balls and the player
    drawFilledRectangle(player);
    drawFilledCircle(ball1);
    drawFilledCircle(ball2);
    drawFilledCircle(ball3);
 
    // animate the balls bouncing all over the walls
    moveBall(ball1);
    moveBall(ball2);
    moveBall(ball3);
    // ask for a new animation frame
    requestAnimationFrame(mainLoop);
}
```

And what if we have 100 balls? We're not going to copy and paste the lines that draw and move the balls 100 times!

Using arrays and loops for creating any number of balls, for animating and moving any number of balls!

New version: look at the createBalls, drawBalls and moveBalls functions now!


```javascript
// useful to have them as global variables
var canvas, ctx, w, h; 
// an empty array!
var balls = []; 

var player = {
  x:10,
  y:10,
  width:20,
  height:20,
  color:'red'
}

window.onload = function init() {
    // called AFTER the page has been loaded
    canvas = document.querySelector("#myCanvas");
  
    // often useful
    w = canvas.width; 
    h = canvas.height;  
  
    // important, we will draw with this object
    ctx = canvas.getContext('2d');
  
    // create 10 balls
    balls = createBalls(10);
  
    // ready to go !
    mainLoop();
};

function mainLoop() {
  // 1 - clear the canvas
  ctx.clearRect(0, 0, w, h);
  
  // draw the ball and the player
  drawFilledRectangle(player);
  drawAllBalls(balls);

  // animate the ball that is bouncing all over the walls
  moveAllBalls(balls)
  
  // ask for a new animation frame
  requestAnimationFrame(mainLoop);
}

function createBalls(n) {
  // empty array
  var ballArray = [];
  
  // create n balls
  for(var i=0; i < n; i++) {
     var b = {
        x:w/2,
        y:h/2,
        radius: 5 + 30 * Math.random(), // between 5 and 35
        speedX: -5 + 10 * Math.random(), // between -5 and + 5
        speedY: -5 + 10 * Math.random(), // between -5 and + 5
        color:getARandomColor(),
      }
     // add ball b to the array
     ballArray.push(b);
    }
  // returns the array full of randomly created balls
  return ballArray;
}

function getARandomColor() {
  var colors = ['red', 'blue', 'cyan', 'purple', 'pink', 'green', 'yellow'];
  // a value between 0 and color.length-1
  // Math.round = rounded value
  // Math.random() a value between 0 and 1
  var colorIndex = Math.round((colors.length-1)*Math.random()); 
  var c = colors[colorIndex];
  
  // return the random color
  return c;
}

function drawAllBalls(ballArray) {
    ballArray.forEach(function(b) {
      drawFilledCircle(b);
    });
}

function moveAllBalls(ballArray) {
  // iterate on all balls in array
  ballArray.forEach(function(b) {
      // b is the current ball in the array
      b.x += b.speedX;
      b.y += b.speedY;
  
      testCollisionBallWithWalls(b); 
  });
}

function testCollisionBallWithWalls(b) {
    // COLLISION WITH VERTICAL WALLS ?
    if((b.x + b.radius) > w) {
    // the ball hit the right wall
    // change horizontal direction
    b.speedX = -b.speedX;
    
    // put the ball at the collision point
    b.x = w - b.radius;
  } else if((b.x -b.radius) < 0) {
    // the ball hit the left wall
    // change horizontal direction
    b.speedX = -b.speedX;
    
    // put the ball at the collision point
    b.x = b.radius;
  }
  
  // COLLISIONS WTH HORIZONTAL WALLS ?
  // Not in the else as the ball can touch both
  // vertical and horizontal walls in corners
  if((b.y + b.radius) > h) {
    // the ball hit the right wall
    // change horizontal direction
    b.speedY = -b.speedY;
    
    // put the ball at the collision point
    b.y = h - b.radius;
  } else if((b.y -b.radius) < 0) {
    // the ball hit the left wall
    // change horizontal direction
    b.speedY = -b.speedY;
    
    // put the ball at the collision point
    b.Y = b.radius;
  }  
}

function drawFilledRectangle(r) {
    // GOOD practice: save the context, use 2D trasnformations
    ctx.save();
  
    // translate the coordinate system, draw relative to it
    ctx.translate(r.x, r.y);
  
    ctx.fillStyle = r.color;
    // (0, 0) is the top left corner of the monster.
    ctx.fillRect(0, 0, r.width, r.height);
  
    // GOOD practice: restore the context
    ctx.restore();
}

function drawFilledCircle(c) {
    // GOOD practice: save the context, use 2D trasnformations
    ctx.save();
  
    // translate the coordinate system, draw relative to it
    ctx.translate(c.x, c.y);
  
    ctx.fillStyle = c.color;
    // (0, 0) is the top left corner of the monster.
    ctx.beginPath();
    ctx.arc(0, 0, c.radius, 0, 2*Math.PI);
    ctx.fill();
 
    // GOOD practice: restore the context
    ctx.restore();
}
```
Let's look at the new functions we've added: 

createBalls(numberOfBalls), returns an array of balls:


```javascript
function createBalls(n) {
  // empty array
  var ballArray = [];
  // create n balls
  for(var i=0; i < n; i++) {
      var b = {
          x:w/2,
          y:h/2,
          radius: 5 + 30 * Math.random(), // between 5 and 35
          speedX: -5 + 10 * Math.random(), // between -5 and + 5
          speedY: -5 + 10 * Math.random(), // between -5 and + 5
          color: getARandomColor(),
      }
      // add ball b to the array
      ballArray.push(b);
  }
  // returns the array full of randomly created balls
  return ballArray;
}
```

#### Explanations:

* Line 3: we declare an empty array that will contain the balls,
* Lines 7-14: we create a new ball object with random values. Note the use of `Math.random()`, a predefined JavaScript function that returns a decimal value between 0 and 1. We call another function named `getARandomColor()` that returns a color taken randomly.
* Line 16: we add the newly created ball b to the array,
* Line 19: we return the array to the caller.

The getARandomColor function

```javascript
function getARandomColor() {
    var colors = ['red', 'blue', 'cyan', 'purple',
                  'pink', 'green', 'yellow'];
    // a value between 0 and color.length-1
    // Math.round = rounded value
    // Math.random() a value between 0 and 1
    var colorIndex = Math.round((colors.length-1)*Math.random());
    var c = colors[colorIndex];
    // return the random color
    return c;
}
```

#### Explanations:

* Line 2: in this function, we use an array of random color names named colors (you can go on the codePen example and change these colors or add new ones).
* Line 7: then we compute an index with a random value between 0 and colors.length-1. Remember that in an array of n elements, the index of the first is always 0 and the index of the last one is always equal to the length of the array -1. For example: var myArray = ['red', 'blue', 'green'], red is at index 0, green at index 2, while myArray.length = 3, the number of elements in the array.
* Lines 8 and 11: once we get a random index in the correct range, we can return the corresponding color.

Functions `drawAllBalls` and `moveAllBalls`:

```javascript
function drawAllBalls(ballArray) {
    ballArray.forEach(function(b) {
        drawFilledCircle(b);
    });
}
 
function moveAllBalls(ballArray) {
    // iterate on all balls in array
    ballArray.forEach(function(b) {
        // b is the current ball in the array
        b.x += b.speedX;
        b.y += b.speedY;
        testCollisionBallWithWalls(b);
    });
}
```

#### Explanations:

These two functions use an iterator on the array of balls (using the `forEach` method that looked the best fit here). The code inside 
the iterator is the same as in the previous example. We did not have to modify the `testCollisionBallWithWalls` code, for example.


--- 

#### Module 2: Adding interactivity to HTML documents   2.6 Let's write a small game   Mouse interactions, mouse events

# Mouse interactions, mouse events

### Mouse interactions, mouse events in a canvas

Mouse interactions, mouse events

INTRODUCTION

Detecting mouse events in a canvas is quite straightforward: you add an event listener to the canvas, and the browser invokes that listener when the event occurs.

The example below is about listening to `mouseup` and `mousedown` events (when a user presses or releases any mouse button):


```javascript
canvas.addEventListener('mousedown', function (evt) {
    // do something with the mousedown event
});
 
canvas.addEventListener('mousedup', function (evt) {
    // do something with the mouseup event
});
```

The event received by the listener function will be used for getting the button number or the coordinates of the mouse cursor. Before 
looking at different examples, let's look at the different event types we can listen to.

### The different mouse events (reminder)

In the last example, we saw how to detect the `mouseup` and `mousedown` events.

There are other events related to the mouse:

* `mouseleave`: similar to `mouseout`, fired when the mouse leaves the surface of the element. The difference between `mouseleave` and `mouseout` is that mouseleave does not fire when the cursor moves over descendant elements, and mouseout is fired when the element the cursor moves to is outside the bounds of the original element or is a child of the original element.
* `mouseover`: the mouse cursor is moving over the element that listens to that event. A mouseover event occurs on an element when you are over it - coming from either its child OR parent element, but a mouseenter event only occurs when the mouse moves from the parent element to the child element.
* `mousedown`: fired when a mouse button is pressed.
* `mouseup`: fired when a mouse button is released.
* `mouseclick`: fired after a mousedown and a mouseup have occured.
* `mousemove`: fired while the mouse moves over the element. Each time the mouse moves, a new event is fired, unlike with mouseover or mouseenter, where only one event is fired.

#### The tricky part: getting the position of the mouse relative to the canvas

When you listen to any of the above events, the event object (we call it a "DOM event"), passed to the listener function, has properties 
that correspond to the mouse coordinates: `clientX` and `clientY`.

> However, these are what we call "viewport coordinates". Instead of being relative to the canvas itself, they are relative to the 
> viewport (the visible part of the page).

Most of the time you need to work with the mouse position relative to the canvas, not to the viewport, so you must convert the coordinates between the viewport and the canvas. This will take into account the position of the canvas in the viewport, and the CSS properties that may affect the canvas position (margin, etc.).

Fortunately, there is a method for getting the position and size of any element in the viewport: `getBoundingClientRect()`.

Here is an example that shows the problem:

```html
<!DOCTYPE HTML>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>Wrong way to get the mouse
    position in a canvas</title>
    <style>
      body {
        margin: 20px;
        padding: 0px;
      }
    </style>
  </head>
  <body>
    Move the mouse cursor to the
    top left corner of the canvas:<p></p>
    <p>Instead of (0, 0), you will see coordinates relative to the window object (page)</p>
    <canvas id="myCanvas" width="300" height="200"></canvas>
  </body>
</html>
```


```javascript
var canvas, ctx, mousePos, mouseButton;

window.onload = function init() {
    canvas = document.getElementById('myCanvas');
    ctx = canvas.getContext('2d');

    canvas.addEventListener('mousemove', function (evt) {
        mousePos = getMousePos(canvas, evt);
        var message = 'Mouse position: ' + mousePos.x + ',' + mousePos.y;
        writeMessage(canvas, message);
    }, false);

      canvas.addEventListener('mousedown', function (evt) {
        mouseButton = evt.button;
        var message = "Mouse button " + evt.button + " down at position: " + mousePos.x + ',' + mousePos.y;
        writeMessage(canvas, message);
    }, false);

    canvas.addEventListener('mouseup', function (evt) {
        var message = "Mouse up at position: " + mousePos.x + ',' + mousePos.y;
        writeMessage(canvas, message);
    }, false);
};



function writeMessage(canvas, message) {
    ctx.save();
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    ctx.font = '18pt Calibri';
    ctx.fillStyle = 'black';
    ctx.fillText(message, 10, 25);
    ctx.restore();
}

function getMousePos(canvas, evt) {
    // WRONG !
    return {
        x: evt.clientX,
        y: evt.clientY
    };
}

```

#### WRONG code used in this example:


```javascript
...
canvas.addEventListener('mousemove', function (evt) {
    mousePos = getMousePos(canvas, evt);
    var message = 'Mouse position: ' + mousePos.x + ',' + mousePos.y;
    writeMessage(canvas, message);
}, false);
 
...
function getMousePos(canvas, evt) {
   // WRONG!!!
   return {
      x: evt.clientX,
      y: evt.clientY
   };
}
```

Here is the result, when the mouse is approximately at the top left corner of the canvas:
![WRONG](https://courses.edx.org/asset-v1:W3Cx+HTML5.1x+4T2015+type@asset+block@badMouseCoords.jpg)

A good version of the code: 


```javascript
var canvas, ctx, mousePos, mouseButton;

window.onload = function init() {
    canvas = document.getElementById('myCanvas');
    ctx = canvas.getContext('2d');

    canvas.addEventListener('mousemove', function (evt) {
        mousePos = getMousePos(canvas, evt);
        var message = 'Mouse position: ' + mousePos.x + ',' + mousePos.y;
        writeMessage(canvas, message);
    }, false);

      canvas.addEventListener('mousedown', function (evt) {
        mouseButton = evt.button;
        var message = "Mouse button " + evt.button + " down at position: " + mousePos.x + ',' + mousePos.y;
        writeMessage(canvas, message);
    }, false);

    canvas.addEventListener('mouseup', function (evt) {
        var message = "Mouse up at position: " + mousePos.x + ',' + mousePos.y;
        writeMessage(canvas, message);
    }, false);
};



function writeMessage(canvas, message) {
    ctx.save();
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    ctx.font = '18pt Calibri';
    ctx.fillStyle = 'black';
    ctx.fillText(message, 10, 25);
    ctx.restore();
}

function getMousePos(canvas, evt) {
   // necessary to take into account CSS boundaries
   var rect = canvas.getBoundingClientRect();
   return {
      x: evt.clientX - rect.left,
      y: evt.clientY - rect.top
   };
}

```

And here is the fixed version of the getMousePos function:

```javascript
function getMousePos(canvas, evt) {
   // necessary to take into account CSS boundaries
   var rect = canvas.getBoundingClientRect();
   return {
      x: evt.clientX - rect.left,
      y: evt.clientY - rect.top
   };
}
```
Result (the cursor is approximately at the top left corner):

![Result](https://courses.edx.org/asset-v1:W3Cx+HTML5.1x+4T2015+type@asset+block@mouseZeroZero.jpg)


#### A good example that shows how to display the mouse position, and the mouse button that has been pressed or released

This example uses the previous function for computing the mouse position correctly. It listens to `mousemove`, `mousedown` and `mouseup` events,
 and shows how to get the mouse button number using the `evt.button` property.

Example:


```javascript
<!DOCTYPE HTML>
<html lang="en">
  <head>
    <title>Wrong way to get the mouse
    position in a canvas</title>
    <meta charset="utf-8">
    <style>
      body {
        margin: 20px;
        padding: 0px;
      }
    </style>
  </head>
  <body>
   <p> Move the mouse cursor and click anywhere!</p>
    <canvas id="myCanvas" width="300" height="200"></canvas>
  </body>
</html>
```




```html
var canvas, ctx, mousePos, mouseButton;

window.onload = function init() {
    canvas = document.getElementById('myCanvas');
    ctx = canvas.getContext('2d');

    canvas.addEventListener('mousemove', function (evt) {
        mousePos = getMousePos(canvas, evt);
        var message = 'Mouse position: ' + mousePos.x + ',' + mousePos.y;
        writeMessage(canvas, message);
    }, false);

      canvas.addEventListener('mousedown', function (evt) {
        mouseButton = evt.button;
        var message = "Mouse button " + evt.button + " down at position: " + mousePos.x + ',' + mousePos.y;
        writeMessage(canvas, message);
    }, false);

    canvas.addEventListener('mouseup', function (evt) {
        var message = "Mouse up at position: " + mousePos.x + ',' + mousePos.y;
        writeMessage(canvas, message);
    }, false);
};

```

---

#### Module 2: Adding interactivity to HTML documents   2.6 Let's write a small game   Moving a player with the mouse

# Moving a player with the mouse

This time, we've added a mousemove event listener to the canvas in the init function, and reused the trick that you saw in the previous section to get the correct mouse position:

Working example:


```javascript
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>Draw a monster in a canvas</title>
</head>
<body>
  <canvas id="myCanvas"  width="400" height="400"></canvas>
</body>
</html>
```




```html
// useful to have them as global variables
var canvas, ctx, w, h; 
var mousePos;

// an empty array!
var balls = []; 

var player = {
  x:10,
  y:10,
  width:20,
  height:20,
  color:'red'
}

window.onload = function init() {
    // called AFTER the page has been loaded
    canvas = document.querySelector("#myCanvas");
  
    // often useful
    w = canvas.width; 
    h = canvas.height;  
  
    // important, we will draw with this object
    ctx = canvas.getContext('2d');
  
    // create 10 balls
    balls = createBalls(10);
  
    // add a mousemove event listener to the canvas
    canvas.addEventListener('mousemove', mouseMoved);

    // ready to go !
    mainLoop();
};

function mouseMoved(evt) {
    mousePos = getMousePos(canvas, evt);
}

function getMousePos(canvas, evt) {
    // necessary work in the canvas coordinate system
    var rect = canvas.getBoundingClientRect();
    return {
        x: evt.clientX - rect.left,
        y: evt.clientY - rect.top
    };
}

function movePlayerWithMouse() {
  if(mousePos !== undefined) {
    player.x = mousePos.x;
    player.y = mousePos.y;
  }
}

function mainLoop() {
  // 1 - clear the canvas
  ctx.clearRect(0, 0, w, h);
  
  // draw the ball and the player
  drawFilledRectangle(player);
  drawAllBalls(balls);

  // animate the ball that is bouncing all over the walls
  moveAllBalls(balls);
  
  movePlayerWithMouse();
  
  // ask for a new animation frame
  requestAnimationFrame(mainLoop);
}


function createBalls(n) {
  // empty array
  var ballArray = [];
  
  // create n balls
  for(var i=0; i < n; i++) {
     var b = {
        x:w/2,
        y:h/2,
        radius: 5 + 30 * Math.random(), // between 5 and 35
        speedX: -5 + 10 * Math.random(), // between -5 and + 5
        speedY: -5 + 10 * Math.random(), // between -5 and + 5
        color:getARandomColor(),
      }
     // add ball b to the array
     ballArray.push(b);
    }
  // returns the array full of randomly created balls
  return ballArray;
}

function getARandomColor() {
  var colors = ['red', 'blue', 'cyan', 'purple', 'pink', 'green', 'yellow'];
  // a value between 0 and color.length-1
  // Math.round = rounded value
  // Math.random() a value between 0 and 1
  var colorIndex = Math.round((colors.length-1)*Math.random()); 
  var c = colors[colorIndex];
  
  // return the random color
  return c;
}

function drawAllBalls(ballArray) {
    ballArray.forEach(function(b) {
      drawFilledCircle(b);
    });
}

function moveAllBalls(ballArray) {
  // iterate on all balls in array
  ballArray.forEach(function(b) {
      // b is the current ball in the array
      b.x += b.speedX;
      b.y += b.speedY;
  
      testCollisionBallWithWalls(b); 
  });
}

function testCollisionBallWithWalls(b) {
    // COLLISION WITH VERTICAL WALLS ?
    if((b.x + b.radius) > w) {
    // the ball hit the right wall
    // change horizontal direction
    b.speedX = -b.speedX;
    
    // put the ball at the collision point
    b.x = w - b.radius;
  } else if((b.x -b.radius) < 0) {
    // the ball hit the left wall
    // change horizontal direction
    b.speedX = -b.speedX;
    
    // put the ball at the collision point
    b.x = b.radius;
  }
  
  // COLLISIONS WTH HORIZONTAL WALLS ?
  // Not in the else as the ball can touch both
  // vertical and horizontal walls in corners
  if((b.y + b.radius) > h) {
    // the ball hit the right wall
    // change horizontal direction
    b.speedY = -b.speedY;
    
    // put the ball at the collision point
    b.y = h - b.radius;
  } else if((b.y -b.radius) < 0) {
    // the ball hit the left wall
    // change horizontal direction
    b.speedY = -b.speedY;
    
    // put the ball at the collision point
    b.Y = b.radius;
  }  
}

function drawFilledRectangle(r) {
    // GOOD practice: save the context, use 2D trasnformations
    ctx.save();
  
    // translate the coordinate system, draw relative to it
    ctx.translate(r.x, r.y);
  
    ctx.fillStyle = r.color;
    // (0, 0) is the top left corner of the monster.
    ctx.fillRect(0, 0, r.width, r.height);
  
    // GOOD practice: restore the context
    ctx.restore();
}

function drawFilledCircle(c) {
    // GOOD practice: save the context, use 2D trasnformations
    ctx.save();
  
    // translate the coordinate system, draw relative to it
    ctx.translate(c.x, c.y);
  
    ctx.fillStyle = c.color;
    // (0, 0) is the top left corner of the monster.
    ctx.beginPath();
    ctx.arc(0, 0, c.radius, 0, 2*Math.PI);
    ctx.fill();
 
    // GOOD practice: restore the context
    ctx.restore();
}
```

Extract from the JavaScript source code:

Line 9 defines a mousemove event listener: the `mouseMoved` callback function will be called each time the user moves the mouse on the 
canvas.

The `mouseMoved(evt)` function uses the trick from the previous section and puts the correct mouse position in the `mousePos` variable. 

With this code, as soon as we move the mouse on top of the canvas, we'll have this `mousePos` global variable (line1) that will 
contain the mouse position (in the form of the `mousePos.x` and `mousePos.y` properties).

And here is the new `mainLoop` function. We added a call to the `mousePlayerWithMouse` function:

```javascript
function mainLoop() {
    // 1 - clear the canvas
    ctx.clearRect(0, 0, w, h);
    // draw the ball and the player
    drawFilledRectangle(player);
    drawAllBalls(balls);
 
    // animate the ball that is bouncing all over the walls
    moveAllBalls(balls);
    movePlayerWithMouse();
    // ask for a new animation frame
    requestAnimationFrame(mainLoop);
}
```

And here is the code of the movePlayerWithMouse function:


```javascript
function movePlayerWithMouse() {
    if(mousePos !== undefined) {
        player.x = mousePos.x;
        player.y = mousePos.y;
    }
}
```

If the mouse position is defined, the player's x and y position will equal to the positions of the mouse pointer.

The mouse position may be undefined if the animation loop started without the mouse cursor being on top of the canvas. 
Remember that the `mainLoop` starts as soon as the page is loaded.

Perhaps it's occurred to you that it might be better to move the player **from its center** instead of from its top left 
corner. We leave this improvement to you! :-)


---

#### Module 2: Adding interactivity to HTML documents   2.6 Let's write a small game   Making it a game! Adding collision detection

# Making it a game! Adding collision detection

New version! Try to move the player to all the balls as fast as you can !


```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>Draw a monster in a canvas</title>
</head>
<body>
  <canvas id="myCanvas"  width="400" height="400"></canvas>
</body>
</html>
```


```javascript
// useful to have them as global variables
var canvas, ctx, w, h; 
var mousePos;

// an empty array!
var balls = []; 

var player = {
  x:10,
  y:10,
  width:20,
  height:20,
  color:'red'
}

window.onload = function init() {
    // called AFTER the page has been loaded
    canvas = document.querySelector("#myCanvas");
  
    // often useful
    w = canvas.width; 
    h = canvas.height;  
  
    // important, we will draw with this object
    ctx = canvas.getContext('2d');
  
    // create 10 balls
    balls = createBalls(10);
  
    // add a mousemove event listener to the canvas
    canvas.addEventListener('mousemove', mouseMoved);

    // ready to go !
    mainLoop();
};

function mouseMoved(evt) {
    mousePos = getMousePos(canvas, evt);
}

function getMousePos(canvas, evt) {
    // necessary work in the canvas coordinate system
    var rect = canvas.getBoundingClientRect();
    return {
        x: evt.clientX - rect.left,
        y: evt.clientY - rect.top
    };
}

function movePlayerWithMouse() {
  if(mousePos !== undefined) {
    player.x = mousePos.x;
    player.y = mousePos.y;
  }
}

function mainLoop() {
  // 1 - clear the canvas
  ctx.clearRect(0, 0, w, h);
  
  // draw the ball and the player
  drawFilledRectangle(player);
  drawAllBalls(balls);
  drawNumberOfBallsAlive(balls);

  // animate the ball that is bouncing all over the walls
  moveAllBalls(balls);
  
  movePlayerWithMouse();
  
  // ask for a new animation frame
  requestAnimationFrame(mainLoop);
}

// Collisions between rectangle and circle
function circRectsOverlap(x0, y0, w0, h0, cx, cy, r) {
   var testX=cx;
   var testY=cy;
   if (testX < x0) testX=x0;
   if (testX > (x0+w0)) testX=(x0+w0);
   if (testY < y0) testY=y0;
   if (testY > (y0+h0)) testY=(y0+h0);
   return (((cx-testX)*(cx-testX)+(cy-testY)*(cy-testY))< r*r);
}

function createBalls(n) {
  // empty array
  var ballArray = [];
  
  // create n balls
  for(var i=0; i < n; i++) {
     var b = {
        x:w/2,
        y:h/2,
        radius: 5 + 30 * Math.random(), // between 5 and 35
        speedX: -5 + 10 * Math.random(), // between -5 and + 5
        speedY: -5 + 10 * Math.random(), // between -5 and + 5
        color:getARandomColor(),
      }
     // add ball b to the array
     ballArray.push(b);
    }
  // returns the array full of randomly created balls
  return ballArray;
}

function getARandomColor() {
  var colors = ['red', 'blue', 'cyan', 'purple', 'pink', 'green', 'yellow'];
  // a value between 0 and color.length-1
  // Math.round = rounded value
  // Math.random() a value between 0 and 1
  var colorIndex = Math.round((colors.length-1)*Math.random()); 
  var c = colors[colorIndex];
  
  // return the random color
  return c;
}

function drawNumberOfBallsAlive(balls) {
  ctx.save();
  ctx.font="30px Arial";
  
  if(balls.length === 0) {
    ctx.fillText("YOU WIN!", 20, 30);
  } else {
    ctx.fillText(balls.length, 20, 30);
  }
  ctx.restore();
}

function drawAllBalls(ballArray) {
    ballArray.forEach(function(b) {
      drawFilledCircle(b);
    });
}

function moveAllBalls(ballArray) {
  // iterate on all balls in array
  ballArray.forEach(function(b, index) {
      // b is the current ball in the array
      b.x += b.speedX;
      b.y += b.speedY;
  
      testCollisionBallWithWalls(b); 
    
      testCollisionWithPlayer(b, index);
  });
}

function testCollisionWithPlayer(b, index) {
  if(circRectsOverlap(player.x, player.y,
                     player.width, player.height,
                     b.x, b.y, b.radius)) {
    // we remove the element located at index
    // from the balls array
    // splice: first parameter = starting index
    //         second parameter = number of elements to remove
    balls.splice(index, 1);
  }
}

function testCollisionBallWithWalls(b) {
    // COLLISION WITH VERTICAL WALLS ?
    if((b.x + b.radius) > w) {
    // the ball hit the right wall
    // change horizontal direction
    b.speedX = -b.speedX;
    
    // put the ball at the collision point
    b.x = w - b.radius;
  } else if((b.x -b.radius) < 0) {
    // the ball hit the left wall
    // change horizontal direction
    b.speedX = -b.speedX;
    
    // put the ball at the collision point
    b.x = b.radius;
  }
  
  // COLLISIONS WTH HORIZONTAL WALLS ?
  // Not in the else as the ball can touch both
  // vertical and horizontal walls in corners
  if((b.y + b.radius) > h) {
    // the ball hit the right wall
    // change horizontal direction
    b.speedY = -b.speedY;
    
    // put the ball at the collision point
    b.y = h - b.radius;
  } else if((b.y -b.radius) < 0) {
    // the ball hit the left wall
    // change horizontal direction
    b.speedY = -b.speedY;
    
    // put the ball at the collision point
    b.Y = b.radius;
  }  
}

function drawFilledRectangle(r) {
    // GOOD practice: save the context, use 2D trasnformations
    ctx.save();
  
    // translate the coordinate system, draw relative to it
    ctx.translate(r.x, r.y);
  
    ctx.fillStyle = r.color;
    // (0, 0) is the top left corner of the monster.
    ctx.fillRect(0, 0, r.width, r.height);
  
    // GOOD practice: restore the context
    ctx.restore();
}

function drawFilledCircle(c) {
    // GOOD practice: save the context, use 2D trasnformations
    ctx.save();
  
    // translate the coordinate system, draw relative to it
    ctx.translate(c.x, c.y);
  
    ctx.fillStyle = c.color;
    // (0, 0) is the top left corner of the monster.
    ctx.beginPath();
    ctx.arc(0, 0, c.radius, 0, 2*Math.PI);
    ctx.fill();
 
    // GOOD practice: restore the context
    ctx.restore();
}
```

#### How do we detect collisions?

First, if you're into game programming, we have a full section about collision detection in week 2 of the W3Cx HTML5 Apps and Games advanced course.

We have a player that is a rectangle and other objects that are circles. This is cool, as it allows us to find a short function that tests if a circle collides with a rectangle whose sides are aligned to the X-axis and Y-axis. (we implemented this after reading this Thread at StackOverflow):
https://stackoverflow.com/questions/401847/circle-rectangle-collision-detection-intersection


```javascript
// Collisions between rectangle and circle
function circRectsOverlap(x0, y0, w0, h0, cx, cy, r) {
   var testX=cx;
   var testY=cy;
   if (testX < x0) testX=x0;
   if (testX > (x0+w0)) testX=(x0+w0);
   if (testY < y0) testY=y0;
   if (testY > (y0+h0)) testY=(y0+h0);
   return (((cx-testX)*(cx-testX)+(cy-testY)*(cy-testY))< r*r);
}   
```


```javascript
function moveAllBalls(ballArray) {
    // iterate on all balls in array
    ballArray.forEach(function(b, index) {
        // b is the current ball in the array
        b.x += b.speedX;
        b.y += b.speedY;
        testCollisionBallWithWalls(b);
        testCollisionWithPlayer(b, index);
    });
}
 
function testCollisionWithPlayer(b, index) {
    if(circRectsOverlap(player.x, player.y,
                        player.width, player.height,
                        b.x, b.y, b.radius)) {
     // we remove the element located at index
     // from the balls array
     // splice: first parameter = starting index
     // second parameter = number of elements to remove
    balls.splice(index, 1);
    }
}
```
Line 3: Look at the iterator;  this time instead of just one parameter (the current element), we've added a second optional parameter that will be the index of the current element, starting from zero.

Line 10: for each ball in the array, we will call `testCollisionWithPlayer(b, index);` that will check if there is a collision between the ball b and the player. We also pass the index of the ball. If a collision occurs, we will have to remove the ball from the array, and for that, we will need its index in the array.

Line 15 is the collision test, and if it is true (collision with the player), then the ball dies and we remove it from the array using the splice method you can use on arrays.

Line 22: here it is, we remove the current ball in the array using `balls.splice(position, numberOfElementsToRemove)`. The positon is given by index, and the number of balls to remove is one.

We've also added a function for displaying the number of balls in the array while we are playing. When this number reaches zero, we display "You Win!":


```javascript
function drawNumberOfBallsAlive(balls) {
    ctx.save();
    ctx.font="30px Arial";
    if(balls.length === 0) {
        ctx.fillText("YOU WIN!", 20, 30);
    } else {
        ctx.fillText(balls.length, 20, 30);
    }
    ctx.restore();
}
```
This function is called by the mainLoop:

```javascript
function mainLoop() {
    // 1 - clear the canvas
    ctx.clearRect(0, 0, w, h);
    ...
    drawNumberOfBallsAlive(balls);
    ...
    // ask for a new animation frame
    requestAnimationFrame(mainLoop);
}
```

---

#### Module 2: Adding interactivity to HTML documents   2.6 Let's write a small game   Adding input fields to parameterize the game

# Adding input fields to parameterize the game

#### We want some game setup options

Let's use some other techniques that we've learnt in this module: some input fields: sliders, color chooser, number chooser, and use the DOM API to handle them.

We will use these input fields to indicate the number of balls we want, the max speed we would like, the color and size of the player, etc.

New version:


```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>Draw a monster in a canvas</title>
</head>
<body>
  <div id="controls">
    <label for="nbBalls">Number of balls: </label>
    <input type="number" min=1 max=30 
           value=10 id="nbBalls"
           oninput="changeNbBalls(this.value);">
    <p></p>
   <label for="colorChooser">Player color: </label>
    <input type="color" value='#FF0000'
           oninput="changePlayerColor(this.value);" id="colorChooser">
    <p></p>
      <label for="selectColorOfBallToEat">Color of ball to eat: </label>
      <select onchange="changeColorToEat(this.value);" id="selectColorOfBallToEat">
        <option value='red'>red</option>
        <option value='blue'>blue</option>
        <option value='green'>green</option>
    </select>
    <p></p>

   <label for="ballSpeed">Change ball speed: </label>
    - <input type="range" value='1'
             min=0.1 max=3 step=0.1
           oninput="changeBallSpeed(this.value);"
             id="ballSpeed"> + 
    <p></p>
    
  </div>
  <canvas id="myCanvas"  width="400" height="400"></canvas>
</body>
</html>
```


```css
#myCanvas {
  border: 1px solid black;
  float:left;
}

#controls {
  float:left;
}
```



```javascript
// useful to have them as global variables
var canvas, ctx, w, h; 
var mousePos;

// an empty array!
var balls = []; 
var initialNumberOfBalls;
var globalSpeedMutiplier = 1;
var colorToEat = 'red';
var wrongBallsEaten = goodBallsEaten = 0;
var numberOfGoodBalls;

var player = {
  x:10,
  y:10,
  width:20,
  height:20,
  color:'red'
}

window.onload = function init() {
    // called AFTER the page has been loaded
    canvas = document.querySelector("#myCanvas");
  
    // often useful
    w = canvas.width; 
    h = canvas.height;  
  
    // important, we will draw with this object
    ctx = canvas.getContext('2d');
  
    // start game with 10 balls, balls to eat = red balls
    startGame(10);
  
    // add a mousemove event listener to the canvas
    canvas.addEventListener('mousemove', mouseMoved);

    // ready to go !
    mainLoop();
};

function startGame(nb) {
  do {
    balls = createBalls(nb);
    initialNumberOfBalls = nb;
    numberOfGoodBalls = countNumberOfGoodBalls(balls, colorToEat);
  } while(numberOfGoodBalls === 0);
  
  wrongBallsEaten = goodBallsEaten = 0;
}

function countNumberOfGoodBalls(balls, colorToEat) {
  var nb = 0;
  
  balls.forEach(function(b) {
    if(b.color === colorToEat)
      nb++;
  });
  
  return nb;
}

function changeNbBalls(nb) {
  startGame(nb);
}

function changeColorToEat(color) {
  colorToEat = color;
}

function changePlayerColor(color) {
  player.color = color;
}

function changeBallSpeed(coef) {
    globalSpeedMutiplier = coef;
}

function mouseMoved(evt) {
    mousePos = getMousePos(canvas, evt);
}

function getMousePos(canvas, evt) {
    // necessary work in the canvas coordinate system
    var rect = canvas.getBoundingClientRect();
    return {
        x: evt.clientX - rect.left,
        y: evt.clientY - rect.top
    };
}

function movePlayerWithMouse() {
  if(mousePos !== undefined) {
    player.x = mousePos.x;
    player.y = mousePos.y;
  }
}

function mainLoop() {
  // 1 - clear the canvas
  ctx.clearRect(0, 0, w, h);
  
  // draw the ball and the player
  drawFilledRectangle(player);
  drawAllBalls(balls);
  drawBallNumbers(balls);

  // animate the ball that is bouncing all over the walls
  moveAllBalls(balls);
  
  movePlayerWithMouse();
  
  // ask for a new animation frame
  requestAnimationFrame(mainLoop);
}

// Collisions between rectangle and circle
function circRectsOverlap(x0, y0, w0, h0, cx, cy, r) {
   var testX=cx;
   var testY=cy;
   if (testX < x0) testX=x0;
   if (testX > (x0+w0)) testX=(x0+w0);
   if (testY < y0) testY=y0;
   if (testY > (y0+h0)) testY=(y0+h0);
   return (((cx-testX)*(cx-testX)+(cy-testY)*(cy-testY))< r*r);
}

function createBalls(n) {
  // empty array
  var ballArray = [];
  
  // create n balls
  for(var i=0; i < n; i++) {
     var b = {
        x:w/2,
        y:h/2,
        radius: 5 + 30 * Math.random(), // between 5 and 35
        speedX: -5 + 10 * Math.random(), // between -5 and + 5
        speedY: -5 + 10 * Math.random(), // between -5 and + 5
        color:getARandomColor(),
      }
     // add ball b to the array
     ballArray.push(b);
    }
  // returns the array full of randomly created balls
  return ballArray;
}

function getARandomColor() {
  var colors = ['red', 'blue', 'cyan', 'purple', 'pink', 'green', 'yellow'];
  // a value between 0 and color.length-1
  // Math.round = rounded value
  // Math.random() a value between 0 and 1
  var colorIndex = Math.round((colors.length-1)*Math.random()); 
  var c = colors[colorIndex];
  
  // return the random color
  return c;
}

function drawBallNumbers(balls) {
  ctx.save();
  ctx.font="20px Arial";
  
  if(balls.length === 0) {
    ctx.fillText("Game Over!", 20, 30);
  } else if(goodBallsEaten === numberOfGoodBalls) {
    ctx.fillText("You Win! Final score : " + (initialNumberOfBalls - wrongBallsEaten), 
                 20, 30);
  } else {
    ctx.fillText("Balls still alive: " + balls.length, 210, 30);
    ctx.fillText("Good Balls eaten: " + goodBallsEaten, 210, 50);
     ctx.fillText("Wrong Balls eaten: " + wrongBallsEaten, 210, 70);
  }
  ctx.restore();
}

function drawAllBalls(ballArray) {
    ballArray.forEach(function(b) {
      drawFilledCircle(b);
    });
}

function moveAllBalls(ballArray) {
  // iterate on all balls in array
  balls.forEach(function(b, index) {
      // b is the current ball in the array
      b.x += (b.speedX * globalSpeedMutiplier);
      b.y += (b.speedY * globalSpeedMutiplier);
  
      testCollisionBallWithWalls(b); 
    
      testCollisionWithPlayer(b, index);
  });
}

function testCollisionWithPlayer(b, index) {
  if(circRectsOverlap(player.x, player.y,
                     player.width, player.height,
                     b.x, b.y, b.radius)) {
    // we remove the element located at index
    // from the balls array
    // splice: first parameter = starting index
    //         second parameter = number of elements to remove
    if(b.color === colorToEat) {
      // Yes, we remove it and increment the score
      goodBallsEaten += 1;
    } else {
      wrongBallsEaten += 1;
    }
    
    balls.splice(index, 1);

  }
}

function testCollisionBallWithWalls(b) {
    // COLLISION WITH VERTICAL WALLS ?
    if((b.x + b.radius) > w) {
    // the ball hit the right wall
    // change horizontal direction
    b.speedX = -b.speedX;
    
    // put the ball at the collision point
    b.x = w - b.radius;
  } else if((b.x -b.radius) < 0) {
    // the ball hit the left wall
    // change horizontal direction
    b.speedX = -b.speedX;
    
    // put the ball at the collision point
    b.x = b.radius;
  }
  
  // COLLISIONS WTH HORIZONTAL WALLS ?
  // Not in the else as the ball can touch both
  // vertical and horizontal walls in corners
  if((b.y + b.radius) > h) {
    // the ball hit the right wall
    // change horizontal direction
    b.speedY = -b.speedY;
    
    // put the ball at the collision point
    b.y = h - b.radius;
  } else if((b.y -b.radius) < 0) {
    // the ball hit the left wall
    // change horizontal direction
    b.speedY = -b.speedY;
    
    // put the ball at the collision point
    b.Y = b.radius;
  }  
}

function drawFilledRectangle(r) {
    // GOOD practice: save the context, use 2D trasnformations
    ctx.save();
  
    // translate the coordinate system, draw relative to it
    ctx.translate(r.x, r.y);
  
    ctx.fillStyle = r.color;
    // (0, 0) is the top left corner of the monster.
    ctx.fillRect(0, 0, r.width, r.height);
  
    // GOOD practice: restore the context
    ctx.restore();
}

function drawFilledCircle(c) {
    // GOOD practice: save the context, use 2D trasnformations
    ctx.save();
  
    // translate the coordinate system, draw relative to it
    ctx.translate(c.x, c.y);
  
    ctx.fillStyle = c.color;
    // (0, 0) is the top left corner of the monster.
    ctx.beginPath();
    ctx.arc(0, 0, c.radius, 0, 2*Math.PI);
    ctx.fill();
 
    // GOOD practice: restore the context
    ctx.restore();
}
```

#### Explanations

HTML code: this time we've used an oninput in each input field, and an onchange attribute on the <select> HTML drop down menu:


```javascript
<div id="controls">
   <label for="nbBalls">Number of balls: </label>
   <input type="number" min=1 max=30
         value=10 id="nbBalls"
         oninput="changeNbBalls(this.value);">
   <p></p>
   <label for="nbBalls">Player color: </label>
   <input type="color" value='#FF0000'
          oninput="changePlayerColor(this.value);">
   <p></p>
   <label for="nbBalls">Color of ball to eat: </label>
   <select onchange="changeColorToEat(this.value);">
      <option value='red'>red</option>
      <option value='blue'>blue</option>
      <option value='green'>green</option>
   </select>
   <p></p>
 
   <label for="nbBalls">Change ball speed: </label>
   - <input type="range" value='1'
            min=0.1 max=3 step=0.1
            oninput="changeBallSpeed(this.value);"> +
   <p></p>
</div>
```
JavaScript code: we've added some new variables in order to get closer to a real game with a goal, levels, game over menu and so on.


```javascript
var initialNumberOfBalls;       // number of balls at the beginning
var globalSpeedMutiplier = 1;   // will change when we move the speed 
                                // slider
var colorToEat = 'red';         // color of the "good" balls to eat
var wrongBallsEaten = goodBallsEaten = 0;   //number of good/bad balls
                                            // eaten
var numberOfGoodBalls;          // number of good balls in the set
```

And here are the callback functions called when you use the input fields:


```javascript
function changeNbBalls(nb) {
  startGame(nb);
}
 
function changeColorToEat(color) {
  colorToEat = color;
  startGame(initialNumberOfBalls);
}
 
function changePlayerColor(color) {
  player.color = color;
}
 
function changeBallSpeed(coef) {
  globalSpeedMutiplier = coef;
}
```
Each time we change the number of balls in the game, or the color of the balls you need to eat, we need to restart the game. 

Here is the `startGame(nb_balls)` function:


```javascript
function startGame(nb) {
  do {
     balls = createBalls(nb);
     initialNumberOfBalls = nb;
     numberOfGoodBalls = countNumberOfGoodBalls(balls, colorToEat);
  } while(numberOfGoodBalls === 0); // in case no good ball in the set
  wrongBallsEaten = goodBallsEaten = 0;
}
```

... and here is the function that counts the number of good balls in the newly created set of balls:


```javascript
function countNumberOfGoodBalls(balls, colorToEat) {
  var nb = 0;
  balls.forEach(function(b) {
    if(b.color === colorToEat) // we count the number of balls
    nb++;                      // of this color in the balls array
  });
  return nb;                   // return this number to the caller
}
```
#### Module 2: Adding interactivity to HTML documents   2.6 Let's write a small game   Discussion topics and project

# Discussion topics and project

Here is the discussion forum for this part of the course. Please either post your comments/observations/questions or share your creations.

See below for suggested topics of discussion and an optional project.

Suggested topics

* First, do not forget to share your creations in the forum!
* Do you know about jQuery or equivalent libraries that were developed to try to make the DOM easier to manipulate? Some people do not recommend using them now - why is this?
* Some of things seen during this week, such as the document.querySelector method, do not work on old versions of Internet Explorer, for example. How can we make them work on these old browsers?

Optional project

The game is not completely finished, as you may have noticed :-) So, try to make "levels": when all good balls have been eaten, let's restart automatically, but this time with one more ball in the initial set!






















