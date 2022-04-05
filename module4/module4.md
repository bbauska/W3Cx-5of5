#### Module 4: Structuring data   4.1 Introduction - Module 4   Module 4 outline

# Module 4 outline

### What you will learn in Module 4

We continue exploring JavaScript Object Oriented Programming:

You will learn new things about JavaScript object properties and methods
You will see how to build many instances of objects using ES5 constructor functions and the new ES6 classes
You will learn how to use the "new" keyword for building objects, and about the mysterious "this" keyword you already met in some examples
You will learn about "class properties and methods" (vs. "instance properties and methods")
Finally, you will use these new concepts for improving the small game we started to develop in Module 2!

---

#### Module 4: Structuring data   4.2 Objects (part 2): properties and methods   Introduction

# Introduction

You're already familiar with the concept of objects, but so far we've only seen one simple form, called **"objects literals"** or 
**"singleton objects"**. I think we've referred to them as **"simple objects"** in the course. Here is an example:

```javascript
var js1 = {
    courseName: 'JavaScript intro',
    weeks: 5,
    madeBy: 'W3Cx',
    author: 'Michel Buffa' // no "," after the last property!, even if ES5/6 accept it
}
```

And we access properties values using the "." operator, like this:

```javascript
> js1.author
"Michel Buffa"
 
> js1.weeks
5
```

However, we haven't explained 90% of what is going on, and what we can do with **"objects"**. Our objective in this module, is to 
explain the most important features of objects, while keeping it simple (more advanced topics will be taught in a future 
**"JavaScript Advanced"** course, such as prototypes, context binding, etc.).

#### Features you will learn:

* The relationship between JavaScript objects and arrays,
* What a "reference" is in a programming language,
* How to embed methods in your objects (functions inside an object),
* The `this` object that you very often encounter in Object Oriented JavaScript code,
* How to add methods and properties to your objects,
* How to make multiple objects of the same class using ES6 classes,
* The built-in JavaScript objects and classes: `Array`, `String`, `RegExp`, `Date`, `Math`, `Error`, etc. And, we will remind you about objects such as `navigator`, `document`, `window`, `screen`, etc.

#### Features you will learn in an upcoming course:

* JavaScript prototypes,
* Inheritance,
* Advanced manipulations of properties and methods,
* Methods such as bind, call, etc., that can be useful for changing the value of "this",
* And more!

#### Knowledge check 4.2.1 (not graded)
```javascript
var myBoss = {
    positon: 'The Boss!',
    givenName: 'John, John the Boss!',
    office: 31
};
```
How do we call an object defined like the one shown above?
A JavaScript object literal

#### Explanation
A JavaScript **object literal** is a comma-separated list of name-value pairs wrapped in curly braces. Object literals encapsulate 
data, enclosing it in a tidy package. This minimizes the use of global variables which can cause problems when combining code.

---

#### Module 4: Structuring data   4.2 Objects (part 2): properties and methods   From objects to arrays

# From objects to arrays

Source code of the example in the above video
https://codepen.io/w3devcampus/pen/XgNdLK?editors=0012



### From objects to arrays

In Javascript, an object = a table whose keys/indexes are defined!

Important note: Darth Vader is called "Dark Vador" in the French versions of SW, and, as a French tutor, I think it's cool to give to one of the heroes an international name. :-)

Look at this array:

```javascript
> var darkVador = ['villain', 'half human half machine'];
undefined
 
> darkVador[0]
"villain"
 
> darkVador[1]
"half human half machine"
```

And now, look at this object:

```javascript
var darkVador = {
    job: 'villain',
    race: 'half human half machine'
};
```
They look a bit similar, don't they?

* Same name of the variable that contains the object `= darkVador`
* Instead of `[` and `]` that we used for defining an array, we use `{` and `}` for defining an object
* The elements of the object (its properties) are separated by a comma `,`
* The pairs of keys/values are separated by `:` as in `race: 'half human, half machine'`
* The last pair of keys/values has no `,` at the end.
* It is possible to access the object's properties with `.` or with brackets

We saw that we can use the `.` operator, followed by the property name. It's also possible to use the bracket notation, and manipulate 
the object as an array whose indexes, instead of being 0, 1, 2 etc., are the property names!

```javascript
> var book = {
title: 'Le Petit Prince',
author: 'Saint-Exupery'
};
undefined
 
> var title = book.title;
undefined
 
> title;
"Le Petit Prince"
 
> var title = book['title'];
undefined
 
> title
"Le Petit Prince";
 
> var author = book['author'];
undefined
 
> author;
"Saint-Exupery"
```
As you can see, if you look at lines 7-10 and 13-16, writing book.title or book['title'] is equivalent!

### In JavaScript, objects are arrays whose indexes are property names: please remember this!

Knowledge check 4.2.2 (not graded)
```javascript
let michel = {
    job:'Your Teacher'
}
```
Check the correct proposal:

michel.job and michel['job'] are equivalent correcto
Explication
We saw that we can use the `.` operator, followed by the property name, like michel.job. It's also possible to use the bracket 
notation, and manipulate the object as an array whose indexes, instead of being 0, 1, 2, etc., are the property names! So `michel.job` 
and michel followed by brackets with `'job'` or `"job"` as an index are equivalent.

---

#### Module 4: Structuring data   4.2 Objects (part 2): properties and methods   Property declaration syntax

# Property declaration syntax

Property names: different possibilities

We can put single or double quotes around the name of the property, or nothing at all:

```javascript
var louis = {age: 40}; // WE DO THIS MOST OF THE TIME!
var louis = {"age": 40};
var louis = {'age': 40};
```

In some cases we have to put quotes around the property name:

* When it is a reserved word from JavaScript,
* Or it contains spaces or special characters,
* Or it begins with a number.

Examples:

```javascript
book.1stPublication = '6 avril 1943'; // begins with a number
                                      // Throws a SyntaxError
book['1stPublication'] = '6 avril 1943'; // OK
book.date of publication = '6 avril 1943'; // spaces not allowed!
book['date of publication'] = '6 avril 1943'; // allowed, but avoid!
```

Another classic case where the name of a property is in a variable

In this case it is necessary  to use the syntax with '[' and ']' ...

Example:

```javascript
> var key = 'title';
undefined
 
> book[key];
"Le Petit Prince"
```

---

#### Module 4: Structuring data   4.2 Objects (part 2): properties and methods   An object can contain another object

# An object can contain another object

```javascript
> var book = {
    name: 'Catch-22',
    published: 1961,
    author: {                 // embedded object!
        givenName: 'Joseph',
        familyName: 'Heller'
    }
};
undefined
 
> book.author.givenName;
"Joseph"
 
> book.author.familyName;
"Heller"
```

Accessing the embedded object author is done by chaining property accesses using the "." operator, like in book.author.givenName (here we access the givenName property of the object author, which is also a property of the book object).

---

#### Module 4: Structuring data   4.2 Objects (part 2): properties and methods   Elements, properties and methods

# Elements, properties and methods

### Live coding video: object methods

>! Missing video/transcript

Source code of the live video example
https://codepen.io/w3devcampus/pen/EXNrjB?editors=0011

### Elements, properties and methods

Some vocabulary:

* For **arrays**, we speak of elements
* For **objects**, we talk about properties
* But a **property can also be a function**, in which case it is called a **method**

Yes, it is possible for an object's property to be a function!

A very simple example:


```javascript
var medor = {
    name: 'Benji',
    bark: function(){
        alert('Ouarf, Ouarf!');
    }
};
```
In this example, the `bark` property's value is a function, so we call bark **"a method"**.

A method is a special property that corresponds to the object's behavior

> Properties correspond to an object's DNA (its characteristics), and are nouns (`age`, `name`, etc.)

> Methods correspond to an object's behavior and are verbs (`bark`, `move`, `changeSpeed`, etc.)

Calling a method

Since a method is a property we can use the `.` operator (or brackets with the method's name as a string index).

Let's see some examples:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>JavaScript OOP: methods</title>
  </head>
  <body>
    <button onclick='dvSpeak();'>Make Dark Vador speak!</button>
    </body>
</html>
```

```javascript
var darkVador = {
  race: 'human',
  job: 'villain',
  talk: function() {
    return 'come to the dark side, Luke!';
  },
  describeYourself: function() {
    return "I'm a " + this.race + " and I'm a " + this.job + " in a series of movies!";
  }
}

function dvSpeak() {
 document.body.innerHTML += '<p>Dark Vador describes himself: ' + darkVador.describeYourself(); + '</p>';  
 document.body.innerHTML += '<p>Dark Vador says ' + darkVador.talk(); + '</p>';
}
```


```javascript
var darkVador = {
    race: 'human',
    job: 'villain',
    talk: function() {
        return 'come to the dark side, Luke!';
    }
}
 
function dvSpeak() {
    document.body.innerHTML += '<p>Dark Vador says ' + darkVador.talk(); + '</p>';
}
```
* In line 1, we created a simple object named `darkVador`, that has two properties (`race` and `job`) and a method (`talk`).

In the `dvSpeak` function, at line 10, we call `darkVador`'s `talk` method. The syntax is a mix between the one for accessing a property (with the `.` operator), and 
the one for calling a function (with parentheses and `;` at the end).

When we write `darkVador.talk()`, we are executing the `talk` method of the object `darkVador`, but in plain English, we're just asking Dark Vador to talk. We invoke 
its behavior!

#### Another example with the player we saw briefly in Module 2

Here is the last version of the player object we saw in our small game:
https://codepen.io/w3devcampus/pen/xqNoJX

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


```css
canvas {
  border: 1px solid black;
}
```


```javascript
// useful to have them as global variables
var canvas, ctx, w, h; 
var mousePos;

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
  
  // draw the player
  drawFilledRectangle(player);
  
  // make the player follow the mouse
  movePlayerWithMouse();
  
  // ask for a new animation frame
  requestAnimationFrame(mainLoop);
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
```
JavaScript source code:

```javascript
var player = {
    x:10,
    y:10,
    width:20,
    height:20,
    color:'red'
}
 
// and we also used two other functions for moving the player with the mouse
// and for drawing it as a filled rectangle
 
function movePlayerWithMouse() {
    if(mousePos !== undefined) {
        player.x = mousePos.x;
        player.y = mousePos.y;
    }
}
 
function drawFilledRectangle(r) {
    // BEST practice: save the context, use 2D transformations
    ctx.save();
    // translate the coordinate system, draw relative to it
    ctx.translate(r.x, r.y);
    ctx.fillStyle = r.color;
    // (0, 0) is the top left corner of the monster
    ctx.fillRect(0, 0, r.width, r.height);
    // BEST practice: restore the context
    ctx.restore();
}
```

Now that we've seen that we can include methods into objects, here is a better, more readable and more encapsulated version of our player object:

```javascript
var player = {
    x:10,
    y:10,
    width:20,
    height:20,
    color:'red',
    move(x, y) {
        // change x and y coordinates of the player
        // TODO!
    },
    draw() {
        // draw the player at its current position
        // with current width, height and color
        // TODO!
    }
}
```
Assuming that the move and draw methods are fully implemented, we will now be able to call:

player.move(mousePos.x, mousePos.y) to change the position of the player,
player.draw() to draw the player at its current position, with its current size and color.
Readability is better, it is like asking the player to move, or asking it to draw itself. And we do not need to pass the x, y, width, height, color to the draw method: it is inside the player object, and it can access all its internal property values!

In the next section we will look at how we can access other object's properties from a method or call other methods.

---

#### Module 4: Structuring data   4.2 Objects (part 2): properties and methods   "this": accessing properties

# "this": accessing properties

Live coding video: add methods to the player object from the game

>! Missing video/transcript

Source code of examples shown in the above video

* Game without methods in the player object (example included in the previous course page), here on [CodePen](https://codepen.io/w3devcampus/pen/xqNoJX)
* Game with methods (example also included in this course page), here on [CodePen](https://codepen.io/w3devcampus/pen/oZRrQd/)

### The this keyword: Accessing properties from a method

#### The this keyword!

When one wants to access an object property or wants to call another method from an object method, we must use the `this` keyword. In the code of the 
player object, `this` means "from this object".

Let's look at our game again, with a new version of the player object - this time fully functional:

Let's look at our game again, with a new version of the player object - this time fully functional:


```javascript
// useful to have them as global variables
var canvas, ctx, w, h; 
var mousePos;

var player = {
  x:10,
  y:10,
  width:20,
  height:20,
  color:'red',
  
  move: function(x, y) {
    this.x = x;
    this.y = y;
  },
  
  draw: function(ctx) {
    // draw the player at its current position
    // with current width, height and color
    // GOOD practice: save the context, use 2D trasnformations
    ctx.save();
  
    // translate the coordinate system, draw relative to it
    ctx.translate(this.x, this.y);
  
    ctx.fillStyle = this.color;
    // (0, 0) is the top left corner of the monster.
    ctx.fillRect(0, 0, this.width, this.height);
  
    // GOOD practice: restore the context
    ctx.restore();    
  }
}

window.onload = function init() {
    // called AFTER the page has been loaded
    canvas = document.querySelector("#myCanvas");
  
    // often useful
    w = canvas.width; 
    h = canvas.height;  
  
    // important, we will draw with this object
    ctx = canvas.getContext('2d');
  
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

function mainLoop() {
  // 1 - clear the canvas
  ctx.clearRect(0, 0, w, h);
  
  // draw the player
  player.draw(ctx);
  
  // make the player follow the mouse
  // the animations starts as the page is loaded
  // maybe the mouse is not yet over the canvas
  // this is why we test if the mousePos is defined
  if(mousePos !== undefined)
      player.move(mousePos.x, mousePos.y);
  
  // ask for a new animation frame
  requestAnimationFrame(mainLoop);
}

```
JavaScript code extract:

```javascript

var player = {
    x:10,
    y:10,
    width:20,
    height:20,
    color:'red',
    move: function(x, y) {
        this.x = x; // this.x is the property of "this object"
        this.y = y;
    },
    draw: function(ctx) {
        // draw the player at its current position
        // with current width, height and color
        // it's nearly the same code as the old drawFilledRect function
        ctx.save();
        // translate the coordinate system, draw relative to it
        ctx.translate(this.x, this.y);
        ctx.fillStyle = this.color;
        // (0, 0) is the top left corner of the monster
        ctx.fillRect(0, 0, this.width, this.height);
        // BEST practice: restore the context
        ctx.restore();
    }
}
```

Notice that we've used this followed by the `.` operator every time we've had to access the current value of an object's property (lines 9, 10, 20, 22 and 24).

We passed the canvas' graphic context as a parameter to the `draw` method (it's always good not to create dependencies when making objects). Passing the context 
as a parameter avoids using it as a global variable. If in another project we've got a context named "context" instead of "ctx", then we will just change the parameter when we call player.draw, otherwise we would have had to rename all occurrences of ctx in the code).

Same with the mouse coordinates we passed to the move method.

#### Let's see the Dark Vador example with the use of this in a method

```javascript
var darkVador = {
  race: 'human',
  job: 'villain',
  talk: function() {
    return 'come to the dark side, Luke!' + this.breathe();
  },
  describeYourself: function() {
    return "I'm a " + this.race + " and I'm a " + this.job + " in a series of movies!" + this.breathe();
  },
  breathe() {
    return ".....shhhhhhhhh.....";
  }
}

function dvSpeak() {
 document.body.innerHTML += '<p>Dark Vador describes himself: ' + darkVador.describeYourself(); + '</p>';  document.body.innerHTML += '<p>Dark Vador says: ' + darkVador.talk(); + '</p>';
}

```

```javascript
var darkVador = {
    race: 'human',
    job: 'villain',
    talk: function() {
        return 'come to the dark side, Luke!' + this.breathe();
    },
    describeYourself: function() {
        return "I'm a " + this.race + " and I'm a " + this.job +
               " in a series of movies!" + this.breathe();
        },
    breathe() {
        return ".....shhhhhhhhh.....";
    }
}
 
function dvSpeak() {
    document.body.innerHTML += '<p>Dark Vador describes himself: ' +     
                                darkVador.describeYourself(); +
                                '</p>';
    document.body.innerHTML += '<p>Dark Vador says: ' +
                                darkVador.talk(); +
                                '</p>';
}
```
In this example, notice that the describeYourself method from the `darkVador` object uses the two properties `name` and `job` using the `this` keyword. 
We also call the `breathe` method from the two methods `describeYourself` and `talk`, using `this.breathe();`.

---

#### Module 4: Structuring data   4.2 Objects (part 2): properties and methods   Adding/deleting properties and methods

# Adding/deleting properties and methods

### Properties and methods can be added/deleted after an object has been defined

> Unlike other object-oriented languages, it is possible in JavaScript to add or to remove properties after an object has been created

Examples:
https://codepen.io/w3devcampus/pen/WpqeyK

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>JavaScript OOP: methods</title>
  </head>
  <body>
    <p>Look at the JS code. This time we created an empty object and added properties and methods afterwards.</p>
    <button onclick='dvSpeak();'>Make Dark Vador speak!</button>
    </body>
</html>
```

```javascript
// empty object with no properties/methods
var darkVador = {};

// add properties after darkVador has been created
 darkVador.race = 'human';
  darkVador.job = 'villain';
  darkVador.talk = function() {
    return 'come to the dark side, Luke!' + this.breathe();
  };

  darkVador.describeYourself = function() {
    return "I'm a " + this.race + " and I'm a " + this.job + " in a series of movies!" + this.breathe();
  };

  darkVador.breathe = function() {
    return ".....shhhhhhhhh.....";
  };


function dvSpeak() {
 document.body.innerHTML += '<p>Dark Vador describes himself: ' + darkVador.describeYourself(); + '</p>';  document.body.innerHTML += '<p>Dark Vador says: ' + darkVador.talk(); + '</p>';
}
```

```javascript
// empty object with properties/methods
var darkVador = {};
 
// add properties after darkVador has been created
darkVador.race = 'human';
darkVador.job = 'villain';
 
// add some methods
darkVador.talk = function() {
    return 'come to the dark side, Luke!' + this.breathe();
};
```
* Lines 5, 6 and 9: we can add properties and methods after the object has been created empty at line 2.

### Deleting a property or a method

You can use the JavaScript keyword `delete` to delete an object's property (it will become undefined).

Example:
https://codepen.io/w3devcampus/pen/RpzNEP
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>JavaScript OOP: methods</title>
  </head>
  <body>
    <p>Look at the JS code. This time we created an empty object and added properties and methods afterwards.</p>
    <button onclick='dvSpeak();'>Make Dark Vador speak!</button>
    <p>Click the button below (it will delete the "race" property of the darkVador object). Then click again the button above and see the "undefined" value of the darkVador.race property now.</p>
    <button onclick="deleteSomeProperties()">Delete some of Dark Vador's properties</button>
    </body>
</html>
```

```javascript
// empty object with properties/methods
var darkVador = {};

// add properties after darkVador has been created
 darkVador.race = 'human';
 darkVador.job = 'villain';

// add some methods
  darkVador.talk = function() {
    return 'come to the dark side, Luke!' + this.breathe();
  };

  darkVador.describeYourself = function() {
    return "I'm a " + this.race 
      + " and I'm a " + this.job 
      + " in a series of movies!" + this.breathe();
  };

  darkVador.breathe = function() {
    return ".....shhhhhhhhh.....";
  };


function dvSpeak() {
 document.body.innerHTML += '<p>Dark Vador describes himself: ' + darkVador.describeYourself(); + '</p>';  document.body.innerHTML += '<p>Dark Vador says: ' + darkVador.talk(); + '</p>';
}

function deleteSomeProperties() {
  delete darkVador.race;
  delete darkVador.job;
}
```

JavaScript code extract:

```javascript
function deleteSomeProperties() {
  delete darkVador.race;
  delete darkVador.job;
}
```

#### Knowledge check 4.2.4 (not graded)

```javascript
let pacman = {};
pacman.color:'yellow';
pacman.shape: 'pizza';
```
Explanation
No, it's not correct! While adding and removing properties after the object has been declared/created (line 1 of the source code), the syntax for declaring 
properties INSIDE an object (with `:`) is no more valid. You must use the `=` operator for the assignment. The correct code is:

```javascript
let pacman = {};
pacman.color = 'yellow';
pacman.shape = 'pizza';
```
---

#### Module 4: Structuring data   4.2 Objects (part 2): properties and methods   Discussion topic

# Discussion topic

Here is the discussion forum for this part of the course. Please either post your comments/observations/questions or share your creations.

Suggested topic of discussion:

We simplified the explanations for `this` in this introductory course. Normally, `this` is the current object when you use it inside an "object literal" 
(like in this [CodePen example from the course](https://codepen.io/w3devcampus/pen/JWqgGZ)). 

But... we also met `this` in event listeners (see in this [example from the course](https://codepen.io/w3devcampus/pen/gmygzV?editors=1000). Look at the 
`onchange = "changePageBackgroundColor(this.value);")` ... 

In fact, the `this` keyword can be confusing in JavaScript. The key thing to remember is that it is bound to the calling object when the function is called, not when the function is created.

And in the case of event listeners, the callbacks are called by the browser... You can conclude that it's a good habit not to have event listeners in your 
objects: just use methods in which there is no confusion about `this`.

Let's discuss that (or `this`?) in the forum :-)

---

#### Module 4: Structuring data   4.3 Objects (part 3): creating multiple objects   Classes: definition

# Classes: definition
#### Introduction: the concept of "class" in object oriented programming languages

So far in this course, we've only used **singleton objects**: objects that only occur once: `player`, `darkVador`, etc.

Ok, this is not quite true, I'd forgotten that we created many balls in the module 2 game. We'll come back to this example 
further down the page!

But even with the balls from module 2, we did not use a template to tell us how to easily create multiple objects that share 
the same properties and the same methods, but whose properties' values may differ.

For example, imagine `Luke Skywalker`, `Ian Solo` and `Dark Vador`. What do they have in common? They all are Star Wars heroes, 
they all have a name, they all belong to one side (the good/bad people, or rebels vs empire), etc. Imagine that we have a way 
of programming that describes not the objects themselves, but a **model**, a **template** for these objects. We could call it 
`StarWarsHero` and use it for creating our heroes' objects.

Imagine the balls from module 2: they all had the same shape (`circle`), the same `x`, `y`, `radius` and `color` properties, 
but they were all different. They all belonged to the same class of object (`ball`), but they were all different in terms 
of their properties' values.

In many programming languages, these templates are called `classes`.

* **In JavaScript 5** (also called **ES5**), we did not have such a concept, instead we had `constructor functions`.
* **In JavaScript 6 (ES6)**, we have the concept of `classes`, and the syntax is rather similar to what we find in other 
object oriented programming languages.

Let's introduce these two ways of defining **pseudo classes** with ES5's function constructors, and with ES6 classes!


---

#### Module 4: Structuring data   4.3 Objects (part 3): creating multiple objects   ES5's constructor functions, the "new" keyword

# ES5's constructor functions, the "new" keyword

### Live coding video: ES5 constructor functions, the "new" keyword

>! Missing video/transcript

Source code shown in the video
https://codepen.io/w3devcampus/pen/eRBoyr?editors=0011

### ES5's constructor functions, the new keyword

With JavaScript version 5 (and previous versions), you can define a pseudo-class template called **"a constructor function"**. 
The syntax is the same as for creating a function, except that:

* **By convention, its name is Capitalized**. The first letter of the function name is in uppercase, this is a good way to know, when you read someone else's code, that this is not a regular function, but a constructor function. **Its name is a noun, the name of the class of objects you are going to build**. Example: `Person`, `Vehicle`, `Enemy`, `Product`, `Circle`, `Ball`, `Player`, `Hero`, etc.
* **You build new objects using the `new` keyword**: 

    * Examples (`Car`, `Hero`, `Ball`, `Product` are constructor function names):

```javascript	
var car = new Car('Ferrari', 'red');
var luke = new Hero('Luke Skywalker', 'rebels");
var ball1 = new Ball(10, 10, 20, 'blue'); // x=10, y=10, radius = 20, color = 'blue'
var p1 = new Product('Epson printer P1232', '183', 'Mr Buffa'); // ref, price, customer
//etc.
```

* **The parameters of the function are the "constructor parameters": the new object that you are building will take these as its initial properties' values**. You can build a Hero, but you must give him/her a name, a side, etc.
* **You define the property names and method names using the `this` keyword**. But beware: the syntax is not the same as the syntax we used for singleton/simple objects. No more `:` and `,` between properties. Here we use `=` and `;` like in regular functions.

Example

```javascript
function Hero(name, side) {
    this.name = name;
    this.side = side;
    this.speak = function() {
        console.log("My name is " + this.name + " and I'm with the " + this.side);
    }
}
```

In a constructor function named `Hero`, you will find properties declared like this: `this.name` `this.side;` and methods declared like this: `this.speak = function() {...}`

* Very often some properties are initialized using the constructor function parameters, so that the newly constructed objects will get an initial value for their properties. In this case, we use the this keyword to distinguish the property from the constructor function parameter:

Example: 

```javascript
function Hero(name) {
    this.name = name;
    ...
}
```

#### Full interactive example that uses a constructor function
https://codepen.io/w3devcampus/pen/KWjMRw

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>JavaScript OOP: create objects</title>
  </head>
  <body>
    <p>Look at the JS code. This time we created multiple objects using a "constructor function.</p>
 <p>   
   <button onclick='makeHeroesSpeak();'>Make Star Wars heroes speak!</button>
    </p>
  
    </body>
</html>
```


```javascript
function Hero(name, side) {
  this.name = name;
  this.side = side;
  
  this.speak = function() {
    return "<p>My name is " + this.name +
      ", I'm with the " + this.side + ".</p>";
  }
}

var darkVador = new Hero("Dark Vador", "empire");
var luke = new Hero("Luke Skywalker", "rebels");
var ianSolo = new Hero("Ian Solo", "rebels");

function makeHeroesSpeak() {
  document.body.innerHTML += darkVador.speak();
   document.body.innerHTML += luke.speak();
   document.body.innerHTML += ianSolo.speak();
}
```

JavaScript source code:

```javascript
function Hero(name, side) {
    this.name = name; // code outside of methods is usually for initializing
    this.side = side; // the properties. Very often, they match the parameters
    this.speak = function() {
        return "<p>My name is " + this.name +
               ", I'm with the " + this.side + ".</p>";
    }
}
 
var darkVador = new Hero("Dark Vador", "empire");
var luke = new Hero("Luke Skywalker", "rebels");
var ianSolo = new Hero("Ian Solo", "rebels");
 
function makeHeroesSpeak() {
    document.body.innerHTML += darkVador.speak();
    document.body.innerHTML += luke.speak();
    document.body.innerHTML += ianSolo.speak();
}
```

* Lines 1-9: see how the constructor function is declared: the function name starts with an uppercase letter `Hero`. The parameters have the same name as the properties they correspond to (`name`, `side`). And in the first source code lines after the function declaration, we initialize some properties using these parameters (lines 2 and 3). We use the `this` keyword to distinguish the property and the parameter. You will often see things like: `this.name = name;` `this.age = age;` etc.

* Lines 11-13: creation of three heroes. We use the same constructor function (`Hero`) along with the `new` keyword. `Luke`, `darkVador` and `ianSolo` ARE each a `Hero`, and share the same properties (`name`, `side`, lines 2 and 3) and the same behavior (they can speak, they all have a `speak` method, declared at line 5).


---

#### Module 4: Structuring data   4.3 Objects (part 3): creating multiple objects   Creating objects using the new ES6 classes

# Creating objects using the new ES6 classes
Source code from above video examples

https://codepen.io/w3devcampus/pen/mwOYWm

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>JavaScript OOP: create objects</title>
  </head>
  <body>
    <p>Look at the JS code. This time we created multiple objects using a "constructor function.</p>
 <p>   
   <button onclick='makeHeroesSpeak();'>Make Star Wars heroes speak!</button>
    </p>
  
    </body>
</html>
```


```javascript
/* ES5's constructor function syntax is not easy to read. If someone does not respect the "conventions" that we've just discussed (start the class with an uppercase, etc.), then the code may work, but it will be difficult to guess that we are not in front of a regular function.

ES5 construction function
*/
function HeroES5(name, side) {
  this.name = name;
  this.side = side;
  
  this.describeYourself = function() {
    console.log("I'm " + this.name + " and I'm from the " + this.side);
  }
}

let ianSoloES5 = new HeroES5('Ian Solo', 'Rebels');








/* ES6 created a class keyword and a constructor keyword, along with advanced concepts that will be the subject of an "advanced JavaScript" course. 

Using ES6 classes
*/
class Hero {
  // must be UNIQUE!, called when "new" is used
  constructor(name, side) { 
    this.name = name;
    this.side = side;   
  }
  
  // no "function" keyword here!
  speak() {
    return "<p>My name is " + this.name +
      ", I'm with the " + this.side + ".</p>";
  }
}

var darkVador = new Hero("Dark Vador", "empire");
var luke = new Hero("Luke Skywalker", "rebels");
var ianSolo = new Hero("Ian Solo", "rebels");

function makeHeroesSpeak() {
  document.body.innerHTML += darkVador.speak();
   document.body.innerHTML += luke.speak();
   document.body.innerHTML += ianSolo.speak();
}

```

### Creating objects using the new ES6 classes

ES5's constructor function syntax is not easy to read. If someone does not respect the **"conventions"** that we've 
just discussed (start the class with an uppercase, etc.), then the code may work, but it will be difficult to guess 
that we are not in front of a regular function. 

ES6 created a `class` keyword and a `constructor` keyword, along with advanced concepts that will be the subject of 
an "advanced JavaScript" course. 

Main changes:

* A class is simply defined using the keyword `class` followed by the name of the class
* The unique constructor is defined using the `constructor` keyword followed by the parameters
* The constructor is executed when an object is created using the keyword `new`
  * Example: `let h1 = new Hero('Ian Solo', 'rebels');`
  * This will call `constructor(name, side)` in the example below.

* A method is simply defined by its name followed by its parameters (we no more use the keyword "function"). Example: `speak() {...}` in the source code below.
Here is the new version of the Hero "template", this time with the ES6 class syntax:


Here is the new version of the Hero "template", this time with the ES6 class syntax:

```javascript
class Hero {
    constructor(name, side) {
        this.name = name; // property
        this.side = side; // property
    }
    speak() { // method, no more "function"
        return "<p>My name is " + this.name +
               ", I'm with the " + this.side + ".</p>";
    }
}
 
var darkVador = new Hero("Dark Vador", "empire");
```

* Line 1: a class is simply defined using the keyword `class` followed by the name of the class. Like for constructor functions, the convention is to use a noun, capitalized.
* Line 2: the constructor is defined using the `constructor` keyword. THERE CAN BE ONLY ONE CONSTRUCTOR in the class.  A `SyntaxError` will be thrown if the class contains more than one occurrence of a constructor method. No more use of the `function` keyword. Simply use the `constructor` keyword followed by the parameters.

> The instructions in the body of the constructor are executed when an object is created using the keyword `new` followed by the name of the class, with arguments between parentheses. These arguments will be passed to the constructor.

Line 7: a method is simply defined by its name followed by its parameters. Again, no more use of the function keyword.

#### Interactive example that uses an ES6 class to create Star Wars heroes

Example on CodePen:
https://codepen.io/w3devcampus/pen/PpMpBo

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>JavaScript OOP: create objects with an ES6 class</title>
  </head>
  <body>
    <p>Look at the JS code. This time we created multiple objects using an ES6 class named Hero.</p>
 <p>   
   <button onclick='makeHeroesSpeak();'>Make Star Wars heroes speak!</button>
    </p>
  
    </body>
</html>
```


```javascript
class Hero {
  constructor(name, side) {
    this.name = name;
    this.side = side;   
  }
  
  speak() {
    return "<p>My name is " + this.name +
      ", I'm with the " + this.side + ".</p>";
  }
}

var darkVador = new Hero("Dark Vador", "empire");
var luke = new Hero("Luke Skywalker", "rebels");
var ianSolo = new Hero("Ian Solo", "rebels");

function makeHeroesSpeak() {
  document.body.innerHTML += darkVador.speak();
   document.body.innerHTML += luke.speak();
   document.body.innerHTML += ianSolo.speak();
}

```

---

#### Module 4: Structuring data   4.3 Objects (part 3): creating multiple objects   You must declare a class before using it!

# You must declare a class before using it!

Unlike functions, classes must be declared BEFORE using them.

An important difference between function declarations and class declarations is that function declarations are "hoisted" and class declarations are not. This means that you can call a function BEFORE it has been declared in your source code. This is not the case with ES6 classes!

You first need to declare your class and then access it, otherwise code like the following will throw a ReferenceError:

#### Incorrect version => you try to create an instance of a class before it has been declared:
```javascript
var p = new Rectangle(); // ReferenceError
 
class Rectangle {...}
```
#### Correct version =>
```javascript
class Rectangle {...}
 
var p = new Rectangle(); // WORKS !
```
Note: 
* A great article on [hoisting](http://www.adequatelygood.com/JavaScript-Scoping-and-Hoisting.html)
* A question on StackOverflow on [hoisting](https://stackoverflow.com/questions/7506844/javascript-function-scoping-and-hoisting)

---

#### Module 4: Structuring data   4.3 Objects (part 3): creating multiple objects   Creating objects with functions (factories)

# Creating objects with functions (factories)

We have already seen three different ways to create objects (literals, constructor functions and ES6 classes)

Objects can be created as **literals** : 

```javascript
var darkVador = { firstName:’Dark’, lastName:’Vador’};
```
Objects can be created with the keyword `new` and a **constructor function** or an ES6 class:

```javascript
var darkVador = new Hero(’Dark Vador’, ’empire’);
```

Here is a new one: objects can also be created by functions that return objects (**factories**)

```javascript
function getMousePos(event, canvas) {
    var rect = canvas.getBoundingClientRect();
    var mxx = event.clientX - rect.left;
    var my = event.clientY - rect.top;
 
    return { // the getMousePos function returns an object. It’s a factory
        x: mx,
        y: my
    }
}

//And here is how you can use this:

var mousePos = getMousePos(evt, canvas);
 
console.log("Mouse position x = " + mousePos.x + " y = " + mousePos.y);
```

The call to `getMousePos` returns an object that has an `x` and a `y` property.

---

#### Module 4: Structuring data   4.3 Objects (part 3): creating multiple objects   Static properties and methods

# Static properties and methods

### Live coding video: static properties and methods

>! Missing video/transcript

Source code from the examples in the above video

* The first example is available at [CodePen](https://codepen.io/w3devcampus/pen/NgbVQo?editors=0012)
* The second example is further in this page, or at [CodePen](https://codepen.io/w3devcampus/pen/rmOjrv?editors=0011)


### Static properties and methods

#### Class properties and methods vs. instances' properties and methods

Sometimes, there are methods **attached* to a class, not to an instance of a class.

For example, imagine the Hero class we've already seen, and we would like to know how many Star Wars's heroes have been created. If zero hero has been created, it's 
obvious that we could not use this property with an instance of the class such as Dark Vador: `darkVador.getNbHeroes();` this would make no sense.

Instead, object oriented programming languages have the concept of **class properties** and **class methods** that complete the **instance properties** and **instance 
methods** that we've seen up to this point. `Hero.getNbHeroes()` means "Hey, class Hero, can you tell me how many heroes have been created using your class?". 
Class methods define the "class behavior", and instance methods define the instances' behavior. `darVador.speak();` means "Hey, Dark Vador, please, tell us 
something!". I speak to Dark Vador and I'm expecting something creative from him, such as "I'm your father, Luke!".

It's the same for properties. If there is a property named `nbHerosCreated` in the class Hero, it represents the DNA of the class, not of the instances. You can 
say "the Hero class has the number of heroes it created", and you can say "Dark Vador has a name and belongs to the empire side", but not "Dark Vador has a number 
of heroes he created". We have class properties and instance properties.

#### The static keyword is used for defining class methods

#### Class methods

> How do we distinguish them? By using the `static` keyword. When you see a method preceded by the `static` keyword, it means that you see a class property or a 
> class method.

> The **static** keyword defines a static method for a class. 

> Static methods are called without instantiating their class 
> and can not be called through a class instance. 

> Consequence: do not use instance properties in their body!

> Static methods are often used to create utility functions for an application (source: MDN).

#### Class properties

Class properties should be defined ***after*** the class definition, and declared using the name of the class followed by the `.` operator and the name of the property. 
Example: `Point.nbPointsCreated` in the example below. A best practice is to ALWAYS use them this way.

There is another way to declare Class properties (using static getters and setters -- see next section, for advanced users), but we recommend using this one for beginners.

#### Example of creation and use of class methods and properties using an ES6 class

Source code:
https://codepen.io/w3devcampus/pen/rmOjrv

```javascript
class Point {
   constructor(x, y) {
      this.x = x;
      this.y = y;
      // static property
      Point.nbPointsCreated++;
   }
 
   // static method
   static distance(a, b) {
      const dx = a.x - b.x;
      const dy = a.y - b.y;
 
      return Math.sqrt(dx*dx + dy*dy);
   }
}
// static property definition is necessarily outside of the class with ES6
Point.nbPointsCreated=0;
 
// We create 3 points
const p1 = new Point(5, 5);
const p2 = new Point(10, 10);
const p3 = new Point(12, 27);
 
document.body.innerHTML += "<p>Distance between points (5, 5) and (10, 10) is " +
                           Point.distance(p1, p2) + "</p>";
document.body.innerHTML += "Number of Points created is " + Point.nbPointsCreated;
```

---

#### Module 4: Structuring data   4.3 Objects (part 3): creating multiple objects   [Advanced] ES6 getters and setters

# [Advanced] ES6 getters and setters

#### Definition

It is possible to use special methods that are called **getters** and **setters**. They allow to make some checks when one is trying to set a value to a property, or to 
do some processing when accessing it (for example for displaying it in uppercase, even if its value is in lowercase).

These special functions are called **getters** and **setters**, and are declared using the keywords `get` and `set` followed by the name of the property they define.

Typical use (lines 7 and 11):


```javascript
class Person {
    constructor(givenName, familyName) {
        this.givenName = givenName; // "normal name"
        this._familyName = familyName; // starts with "_"
    }
    get familyName() {
        return this._familyName.toUpperCase();
    }
    set familyName(newName) {
        // validation could be checked here such as
        // only allowing non numerical values
        this._familyName = newName;
    }
    walk() {
        return (this.givenName + ' ' + this._familyName + ' is walking.');
    }
}
let p1 = new Person('Michel', 'Buffa');
console.log(p1.familyName); // will display BUFFA in the devtool console
                            // this will call implicitly get familyName();
p1.familyName = 'Smith';    // this will call implicitly set familyName('Smith');
```

Notice that when you declare `get familyName() {...}` for example, you define implicitly a property whose name is "familyName" and that will be accessible using 
`object.familyName`, where object is an instance of the class. See lines 22-25 in the example above. Displaying the value of `p1.familyName` will call implicitly 
`get familyName()`, while `p1.familyName = 'Smith';` will call `set Name('Smith');`

As `get familyName()` defines an implicit property named `familyName`, the convention is to use `this._familyName` for storing its value (the same name preceded 
by an underscore).

Example at CodePen:
https://codepen.io/w3devcampus/pen/WOoQgw



```javascript
// ES6 get and set
class Person {
    constructor(givenName, familyName) {
        this.givenName = givenName;    // "normal name"
			  this._familyName = familyName; // starts with "_"
    }
  
		// getters and setters are useful for processing
	  // properties, doing checks, changing them before
	  // returning their value, etc.
	  // having "get familyName" is equivalent to declaring a property
	  // named "familyName", but in this case we have to use ANOTHER
	  // name for the variable that will be used to store the property
	  // value. A convention is to keep the same name but add an 
	  // underscore at the beginning. 
    // Ex: get name(n) { this._name = n;}
	  
    get familyName() {
        return this._familyName.toUpperCase();
    }
  
    set familyName(newName) {
			  // validation could be checked here such as 
			  // only allowing non numerical values
        this._familyName = newName;   
    }
  
    walk() {
        return (this.givenName + ' ' + this._familyName + ' is walking.');
    }
}
         
let michel = new Person('Michel', 'Buffa');

document.body.innerHTML += "<p>" 
												+ michel.walk() 
												+ "</p>";

// Notice that we use here the "normal" names givenName and familyName
document.body.innerHTML += "<p>Our teacher is " 
												+ michel.givenName 
												+ ' ' + michel.familyName 
												+ "</p>";
```

---

#### Module 4: Structuring data   4.3 Objects (part 3): creating multiple objects   Discussion topics and project

# Discussion topics and a project

Here is the discussion forum for this part of the course. Please either post your comments/observations/questions or share your creations.

See below for suggested topics of discussion and an optional project.

#### Suggested topics

* Did you now that ES6 classes are just "a syntactic sugar"? In fact they are equivalent to constructor functions from ES5...
* There are two sorts of object-oriented languages: class-based languages and prototype-based languages. 
* JavaScript is a prototype-based language. In this introductory course, we managed to avoid this term! Without getting into too much details, you might be curious about prototypes and maybe read some Web pages related to those.
* And yes, ES6 classes are not "real classes"... They are meant to make developers' lives easier, i.e., for the developers who already know a class-based language such as Java, C#, etc.
* [Advanced] There is a powerful way to define "pseudo classes" using constructor functions: it's called [The Black Box Model](https://hacks.mozilla.org/2014/08/black-box-driven-development-in-javascript/). I recommend it to those of you who are rather comfortable with Object Oriented Programming concepts. Give it a try!

#### Optional project

Try to write one of the example from the previous modules without using any single time the keyword "function", use only ES6 classes and instances. In case of problems -> go the the forum and share your experience, this will be very useful for all students to see what sort of problems can occur when moving from a functional approach to an object-oriented approach

---

#### Module 4: Structuring data   4.4 Improving the game with classes   ES6 class and constructor

# ES6 class and constructor

#### Building balls in our ES6 game: ES6 class and constructor

First, let's look how we were handling balls previously in our game!

Building balls in order to fill the array of balls

OLD VERSION: here is how we built the array of balls

```javascript
function createBalls(n) {
    // empty array
    let ballArray = [];
    // create n balls
    for(let i=0; i < n; i++) { // let's build multiple times a singleton object
        let b = { 
            x:w/2,
            y:h/2,
            radius: 5 + 30 * Math.random(), // between 5 and 35
            speedX: -5 + 10 * Math.random(), // between -5 and + 5
            speedY: -5 + 10 * Math.random(), // between -5 and + 5
            color:getARandomColor(),
        }
        // add ball b to the array
        ballArray.push(b);
    } // end of for loop
    // returns the array full of randomly created balls
    return ballArray;
}
```

In the code above, in order to build n balls, we created **a singleton ball object multiple times**. This worked, but if we have misspelled a property name within the code, or forgot one of the properties that had to be initialized, we would have received no warnings. We will replace these lines with something like let b = new Ball(...);

NEW VERSION: using the new keyword and an ES6 class

```javascript
function createBalls2(n) {
    // empty array
    let ballArray = [];
    // create n balls
    for(let i=0; i < n; i++) {
        // Create some random values...
        let x = w/2;
        let y = h/2;
        let radius = 5 + 30 * Math.random(); // between 5 and 35
        let speedX = -5 + 10 * Math.random(); // between -5 and + 5
        let speedY = -5 + 10 * Math.random(); // between -5 and + 5
        let color = getARandomColor();
 
        // Create the new ball b
        let b = new Ball(x, y, radius, color, speedX, speedY);
        // add ball b to the array
        ballArray.push(b);
    }
    // returns the array full of randomly created balls
    return ballArray;
}
```

Ok, not a very big change here, except that we are no longer manipulating the property names one by one, and we use the `new`keyword. 

And here is the (so far, incomplete) ES6 class for Ball (continued in the next page of this course)

```javascript
class Ball {
    constructor(x, y, radius, color, speedX, speedY) {
        this.x = x;            // properties
        this.y = y;
        this.radius = radius;
        this.color = color;
        this.speedX = speedX;
        this.speedY = speedY;
    }
... // code to come for methods
}
```

---

#### Module 4: Structuring data   4.4 Improving the game with classes   Adding methods to the ES6 class

# Adding methods to the ES6 class

Adding methods to the ES6 class for balls

Ok, we've seen how to define the Ball class: properties and constructor. Properties are the DNA for balls: they all have an x and y position, a radius, a color, a horizontal and a vertical speed.

It is time to add some behaviors: a draw and a move method. Indeed, all balls will be able to draw and move themselves.

Here's how we were drawing a ball in the previous version of the game:


```javascript
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
And this how we were drawing and moving all the balls:


```javascript
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
```
### Adding a draw and a move method to the ES6 ball class

Instead of having these behaviors as separate functions that take a ball reference as a parameter, it is always better to put this as a method inside the class. Indeed, each ball can move, can draw itself, and the content of these methods does not bring any external dependencies.

For example, if we decide to put a method named `testCollisionWithWalls` inside the `Ball` class, it would be bad, in terms of reusability, for its content to rely on external, global variables, such as the canvas size. You could have passed the canvas as a parameter, but then you create more specialization: you have a Ball class for balls that can move inside a rectangular area that is a canvas. It's better to just pass the width and the height of the zone.

Anyway, if you plan to use your balls in another game, it is recommended that you keep the class as simple as possible. It will be more reusable in other projects.

New version of the ES6 Ball class with draw and move methods:

```javascript
class Ball {
    constructor(x, y, radius, color, speedX, speedY) {
        // see previous section for the code
    }
    draw(ctx) { // Nearly the same as the old drawFilledCircle function
        // BEST practice: save the context, use 2D transformations
        ctx.save();
        // translate the coordinate system, draw relative to it
        ctx.translate(this.x, this.y);
        ctx.fillStyle = this.color;
        // (0, 0) is the top left corner of the monster.
        ctx.beginPath();
        ctx.arc(0, 0, this.radius, 0, 2*Math.PI);
        ctx.fill();
        // BEST practice: restore the context
        ctx.restore();
    }
    move() {
        this.x += this.speedX;
        this.y += this.speedY;
    }
}
```
Explanations:

* Line 6: the `draw` function's content is nearly the same as the `drawFilledCircle` function we previously used. We replaced all `c.x`, `c.y` etc. by `this.x`, `this.y`, to use the properties of the current object. This means that when we create a ball with `var b = new Ball(...);` and when we draw it using `b.draw(ctx)`, then `this.x` will be the value of the `x` property of the ball `b`, etc.
* Line 23: the `move` function takes no parameter as it will add the value of the `speedX/speedY `properties to the current `x` and `y` value of the current ball.

> Notice that we did not take into account the `globalSpeedMultiplier` we had in the old `moveAllBalls` function, as this is not something that is individually relevant to each ball: it is more something that affect ALL balls. This should raise an alert into your mind: use an ES6 class property for that, try to do it!

In other words, even if zero ball has been created, this globalSpeedMultiplier is set and can be modified using a slider in the graphic user interface. Consequently, it is not a ball property, more **a property of the Ball class itself**.

This setting could be created using a class property, as seen in a previous section of this course.

And here is how we can now move and draw ALL balls

```javascript
function drawAllBalls2(ballArray) {
    ballArray.forEach(function(b) {
        b.draw(ctx);
    });
}
 
function moveAllBalls2(ballArray) {
    // iterate on all balls in array
    balls.forEach(function(b, index) {
        // b is the current ball in the array
        b.move();
        testCollisionBallWithWalls(b);
        testCollisionWithPlayer(b, index);
});
}
```

And here is the CodePen version of the game that includes these improvements:
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>Small game with sound</title>
    	<script src="https://cdnjs.cloudflare.com/ajax/libs/howler/1.1.28/howler.min.js"></script>
</head>
<body>
  <audio src = "http://mainline.i3s.unice.fr/mooc/SkywardBound/assets/sounds/humbug.mp3" 
        id="audioPlayer">
</audio>
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
let canvas, ctx, w, h; 
let mousePos;

// an empty array!
let balls = []; 
let initialNumberOfBalls;
let globalSpeedMutiplier = 1;
let colorToEat = 'red';
let wrongBallsEaten = goodBallsEaten = 0;
let numberOfGoodBalls;

// SOUNDS
let ballEatenSound;

// Player as a singleton/simple object
let player = {
  x:10,
  y:10,
  width:20,
  height:20,
  color:'red',
  
  move(x, y) {
    this.x = x;
    this.y = y;
  },
  
  draw(ctx) {
    // draw the player at its current position
    // with current width, height and color
    // GOOD practice: save the context, use 2D trasnformations
    ctx.save();
  
    // translate the coordinate system, draw relative to it
    ctx.translate(this.x, this.y);
  
    ctx.fillStyle = this.color;
    // (0, 0) is the top left corner of the monster.
    ctx.fillRect(0, 0, this.width, this.height);
  
    // GOOD practice: restore the context
    ctx.restore();    
  }
}

window.onload = function init() {
    // called AFTER the page has been loaded
  
    // Start playing the background music as soon as the page has loaded
    playBackgroundMusic();
  
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

    // Load the sound and start the game only when the sound has been loaded
    ballEatenSound = new Howl({
                urls: ['http://mainline.i3s.unice.fr/mooc/SkywardBound/assets/sounds/plop.mp3'],
                onload: function () {
                  // start the animation
                    mainLoop();
                }
            });
  
};

function playBackgroundMusic() {
   let audioPlayer = document.querySelector("#audioPlayer");
   audioPlayer.play();
}

function pausebackgroundMusic() {
   let audioPlayer = document.querySelector("#audioPlayer");
   audioPlayer.pause();  
}

function startGame(nb) {
  do {
    balls = createBalls(nb);
    initialNumberOfBalls = nb;
    numberOfGoodBalls = countNumberOfGoodBalls(balls, colorToEat);
  } while(numberOfGoodBalls === 0);
  
  wrongBallsEaten = goodBallsEaten = 0;
}

function countNumberOfGoodBalls(balls, colorToEat) {
  let nb = 0;
  
  balls.forEach(function(b) {
    if(b.color === colorToEat)
      nb++;
  });
  
  return nb;
}

//===== CALLED BY GUI WHEN THE USER USES INPUT FIELDS
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

//==== CALLED WHEN A USER USES ITS MOUSE
function mouseMoved(evt) {
    mousePos = getMousePos(canvas, evt);
}

function getMousePos(canvas, evt) {
    // necessary work in the canvas coordinate system
    let rect = canvas.getBoundingClientRect();
    return {
        x: evt.clientX - rect.left,
        y: evt.clientY - rect.top
    };
}

//==== MAIN ANIMATION GAME LOOP
function mainLoop() {
  // 1 - clear the canvas
  ctx.clearRect(0, 0, w, h);
  
  // draw the player
  player.draw(ctx);
  // draw all balls
  drawAllBalls(balls);
  
  // animate the ball that is bouncing all over the walls
  moveAllBalls(balls);
  
 // make the player follow the mouse
  // the animations starts as the page is loaded
  // maybe the mouse is not yet over the canvas
  // this is why we test if the mousePos is defined
  if(mousePos !== undefined)
      player.move(mousePos.x, mousePos.y);
  
  // draw the game score
  drawScore(balls);

  // ask for a new animation frame
  requestAnimationFrame(mainLoop);
}

//==== UTILITY FUNCTION
// Collisions between rectangle and circle
function circRectsOverlap(x0, y0, w0, h0, cx, cy, r) {
   let testX=cx;
   let testY=cy;
   if (testX < x0) testX=x0;
   if (testX > (x0+w0)) testX=(x0+w0);
   if (testY < y0) testY=y0;
   if (testY > (y0+h0)) testY=(y0+h0);
   return (((cx-testX)*(cx-testX)+(cy-testY)*(cy-testY))< r*r);
}

//=== FUNCTIONS RELATED TO BALLS

class Ball {
  constructor(x, y, radius, color, speedX, speedY) {
    this.x = x;
    this.y = y;
    this.radius = radius;
    this.color = color;
    this.speedX = speedX;
    this.speedY = speedY;
  }
  
  draw(ctx) {
    // GOOD practice: save the context, use 2D trasnformations
    ctx.save();
  
    // translate the coordinate system, draw relative to it
    ctx.translate(this.x, this.y);
  
    ctx.fillStyle = this.color;
    // (0, 0) is the top left corner of the monster.
    ctx.beginPath();
    ctx.arc(0, 0, this.radius, 0, 2*Math.PI);
    ctx.fill();
 
    // GOOD practice: restore the context
    ctx.restore();    
  }
  
  move() {
      this.x += this.speedX;
      this.y += this.speedY;    
  }
}

function createBalls(n) {
  // empty array
  let ballArray = [];
  
  // create n balls
  for(let i=0; i < n; i++) {
     
    // Create some random values...
    let x = w/2;
    let y = h/2;
    let radius =  5 + 30 * Math.random(); // between 5 and 35
    let speedX =  -5 + 10 * Math.random(); // between -5 and + 5
    let speedY =  -5 + 10 * Math.random(); // between -5 and + 5
    let color = getARandomColor();

    // Create the new ball b
    let b = new Ball(x, y, radius, color, speedX, speedY);
    
    // add ball b to the array
    ballArray.push(b);
  }
  // returns the array full of randomly created balls
  return ballArray;
}

function getARandomColor() {
  let colors = ['red', 'blue', 'cyan', 'purple', 'pink', 'green', 'yellow'];
  // a value between 0 and color.length-1
  // Math.round = rounded value
  // Math.random() a value between 0 and 1
  let colorIndex = Math.round((colors.length-1)*Math.random()); 
  let c = colors[colorIndex];
  
  // return the random color
  return c;
}

function drawScore(balls) {
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
      b.draw(ctx);
    });
}


function moveAllBalls(ballArray) {
  // iterate on all balls in array
  balls.forEach(function(b, index) {
      // b is the current ball in the array
      b.move();
  
      testCollisionBallWithWalls(b); 
    
      testCollisionWithPlayer(b, index);
  });
}

function testCollisionWithPlayer(b, index) {
  if(circRectsOverlap(player.x, player.y,
                     player.width, player.height,
                     b.x, b.y, b.radius)) {
    // PLAY A PLOP SOUND!
    ballEatenSound.play();
    
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
```

---

#### Module 4: Structuring data   4.4 Improving the game with classes   Discussion topics and project

# Discussion topics and project

Here is the discussion forum for this part of the course. Please either post your comments/observations/questions or share your creations.

See below for a suggested topics of discussion and an optional project.

#### Suggested topic

* Did you register to HTML5 Apps and Games MOOC? There is module about video game programming, and with the knowledge acquired from this JS intro MOOC, you should have no problem following it. 
* It uses JavaScript object oriented programming and shows many examples that share the concepts seen during the first 4 modules of this course.

#### Optional project

* Try to use ES6 classes as much as you can!

### Hello CR
