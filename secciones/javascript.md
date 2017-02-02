# JavaScript & jQuery

## 1. JavaScript

JavaScript ("JS" for short) is a high-level, dynamic, untyped, and interpreted programming language. JS is a programming language that adds interactivity to your website (for example: games, responses when buttons are pressed or data entered in forms, dynamic styling, animation).

JS itself is fairly compact yet very flexible. Developers have written a large variety of tools complementing the core JavaScript language, unlocking a vast amount of extra functionality with minimum effort. These include:

* Application Programming Interfaces (APIs) built into web browsers, providing functionality like dynamically creating HTML and setting CSS styles, collecting and manipulating a video stream from the user's webcam, or generating 3D graphics and audio samples.

* Third-party APIs to allow developers to incorporate functionality in their sites from other content providers, such as Twitter or Facebook.

* Third-party frameworks and libraries you can apply to your HTML to allow you to rapidly build up sites and applications.

### 1.1. Variables

**Variables** are containers that you can store values in. You start by declaring a variable with the var keyword, followed by any name you want to call it:

```javascript
var myVariable;
```

After declaring a variable, you can give it a value:

```javascript
myVariable = 'Bob';
```

You can do both these operations on the same line if you wish:

```javascript
var myVariable = 'Bob';
```

You can retrieve the value by just calling the variable by name:

```javascript
myVariable;
```

After giving a variable a value, you can later choose to change it:

```javascript
var myVariable = 'Bob';
myVariable = 'Steve';
```

Note that variables have different **data types**:

```javascript
var myString = 'Bob';
var myNumber = 10;
var myBoolean = true;
var myArray = [1,'Bob','Steve',10];
var myObject = document.querySelector('h1');
```

### 1.2. Comments

You can put **comments** into JS code, just as you can in CSS:

```javascript
/*
Everything in between is a comment.
*/
```

If your comment contains no line breaks, it's often easier to put it behind two slashes like this:

```javascript
// This is a comment
```

### 1.3. Operators

An **operator** is a mathematical symbol which produces a result based on two values (or variables). In the following table you can see some of the simplest operators, along with some examples to try out in the JavaScript console.

```javascript
// add/concatenation
6 + 9;
"Hello " + "world!";

// subtract, multiply, divide
9 - 3;
8 * 2; // multiply in JS is an asterisk
9 / 3;

// assignment operator
var myVariable = 'Bob';

// Identity operator
var myVariable = 3;
myVariable === 4;

// Negation, not equal
var myVariable = 3;
!(myVariable === 3);
```

### 1.4. Functions

**Functions** are a way of packaging functionality that you wish to reuse. When you need the procedure you can call a function, with the function name, instead of rewriting the entire code each time.

You can define your own functions — in this next example we write a simple function which takes two numbers as arguments and multiplies them:

```javascript
function multiply(num1,num2) {
  var result = num1 * num2;
  return result;
}
```

Try running the above function in the console, then test with several arguments. For example:

```javascript
multiply(4,7);
multiply(20,20);
multiply(0.5,3);
```

### 1.5. Objects

As with many things in JS, creating an **object** often begins with defining and initializing a variable. Try entering the following below the JavaScript code that's already in your file, then saving and refreshing:

```javascript
var person = {};
```

If you enter person into your text input and press the button, you should get the following result:

```javascript
[object Object]
```

Congratulations, you've just created your first object. Job done! But this an empty object, so we can't really do much with it. Let's update our object to look like this:

```javascript
var person = {
  name: ['Bob', 'Smith'],
  age: 32,
  gender: 'male',
  interests: ['music', 'skiing'],
  bio: function() {
    alert(this.name[0] + ' ' + this.name[1] + ' is ' + this.age + ' years old. He likes ' + this.interests[0] + ' and ' + this.interests[1] + '.');
  },
  greeting: function() {
    alert('Hi! I\'m ' + this.name[0] + '.');
  }
};
```

After saving and refreshing, try entering some of the following into your text input:

```javascript
person.name[0]
person.age
person.interests[1]
person.bio()
person.greeting()
```

## 2. jQuery

jQuery is a fast, small, and feature-rich JS library. It makes things like HTML document traversal and manipulation, event handling, animation, and Ajax much simpler with an easy-to-use API that works across a multitude of browsers. With a combination of versatility and extensibility, jQuery has changed the way that millions of people write JS.

### 2.1. How to add jQuery library to a HTML document

You can download the last jQuery version from their website, or you can add it from Google, Microsoft or other CDNs like this:

```html
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.1.1/jquery.min.js"></script>
```

### 2.2. Standard jQuery Syntax

A jQuery statement typically starts with the dollar sign (`$`) and ends with a semicolon (`;`). In jQuery, the dollar sign (`$`) is just an alias for jQuery. Let's consider the following example code which demonstrates the most basic statement of the jQuery.

```javascript
<html>
<head>
    <meta charset="utf-8">
    <title>My First jQuery Application</title>
    <link rel="stylesheet" type="text/css" href="css/style.css">
    <script src="js/jquery-1.11.3.min.js"></script>
    <script type="text/javascript">
        $(document).ready(function(){
            $("h1").css("color", "#0088ff");
        });
    </script>
</head>
<body>
    <h1>Hello, World!</h1>
</body>
</html>
```

In the above example we've performed a simple jQuery operation by changing the color of the heading i.e. the `<h1>` element using the jQuery element selector and `css()` method when the document is ready which is known as document ready event. We'll learn about jQuery selectors, events and methods in upcoming chapters.

## 3. References

* [Mozilla Developer Network](https://developer.mozilla.org/)
* [Learn jQuery](https://learn.jquery.com/)
* [Tutorial Republic](http://www.tutorialrepublic.com/jquery-tutorial/)





























