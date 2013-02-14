front-end-interview-questions
=============================



Implement a function that calculates square roots
Sort and concat arrays in a optimal way
Guess the two missing numbers in a array with n - 2 length containing 1..n unsorted numbers
Calculate the number of digits for a given number
Implement a function to detect palindromes
What is a closure and which disadvantages has
What is hoisting
How does this work
How float works and which issues have
How does the event loop work on the browser and how to delay a function to the next tick
How to optimize CSS, and how does specificity work


How do you waste time in JavaScript?
--------
Redraw parts of the DOM, e.g. increase font-size in a loop.
See http://www.bennadel.com/blog/2370-Overcoming-Asynchronous-Anxiety-By-Testing-JavaScript-s-Event-Loop.htm

What is the difference between var x = 1 and x = 1?
--------
Novice JS programmers might have a basic answer about locals vs globals

Intermediate JS guys should definitely have that answer, and should probably mention function-level scope

"advanced" JS programmer should be prepared to talk about locals, implied globals (defined without var, assumed belongs to window DOM, problem if third-party script uses same var name and uses var, they can conflict), the window object, function-scope, declaration hoisting (if statements do not create new scope, only functions do), and . Furthermore, I'd love to hear about [[DontDelete]], hoisting precedence (parameters vs var vs function), and undefined.

See
http://sharkysoft.com/tutorials/jsa/content/031.html
http://schalk-neethling.com/2011/07/quick-tip-the-problem-with-implied-globals-in-javascript/
http://www.adequatelygood.com/2010/2/JavaScript-Scoping-and-Hoisting
http://stackoverflow.com/questions/1484143/scope-chain-in-javascript


What is a closure?
--------
A closure is formed when you nest functions, inner functions can refer to the variables present in their outer enclosing functions even after their parent functions have already executed.

What language is JavaScript based on?
--------
ECMAScript = core language that JS is based on.

What's the difference between a variable and a property?
--------
var a = 'hello'; // variable
You cant access variables with a . from the owner, you just need to know that they're there.

Properties are the building blocks of objects.
foo.bar 

They only appear interchangeable if the parent objects are the same


Write a function to add arguments together
---------
function sum() {
  var i, l, result = 0;
  for (i = 0, l = arguments.length; i < l; i++) {
    result += parseInt(arguments[i]);
  }
  return result;
}

sum(1,2,3); // 6

And they should invoke it on your array like this (context for apply can be whatever, I usually use null in that case):

var data = [1,2,3];
sum.apply(null, data); // 6


Why use frameworks?
---------
Good coders code, great coders reuse. Thousands of man hours have been poured into these libraries to abstract DOM capabilities away from browser specific implementations. There's no reason to go through all of the different browser DOM headaches yourself just to reinvent the fixes.

Public, private and privaledged members in JavaScript
---------

Private

// Constructor
function Kid (name) {
	// Private
	var idol = "Paris Hilton";
}


You can delete or replace a privileged method, but you cannot alter its contents.
// Constructor
function Kid (name) {
	// Private
	var idol = "Paris Hilton";
	
	// Privileged
	this.getIdol = function () {
		return idol;
	};
}


A static member is shared by all instances of the class as well as the class itself (i.e. the Kid object), but it is only stored in one place. This means that its value is not inherited down to the object’s instances

// Constructor
function Kid (name) {
	// Constructor code
}

// Static property
Kid.town = "South Park";


Public
// Constructor
function Kid (name) {
	// Public
	this.name = name;
}
Kid.prototype.getName = function () {
	return this.name;
};

// ---------------------- all examples

// Constructor
function Kid (name) {
	// Private
	var idol = "Paris Hilton";
	
	// Privileged
	this.getIdol = function () {
		return idol;
	};
	
	// Public
	this.name = name;
}

// Public
Kid.prototype.getName = function () {
	return this.name;
};

// Static property
Kid.town = "South Park";

// ---------------- usage

 // Create a new instance

var cartman = new Kid("Cartman");

// Access private property
cartman.idol; // undefined

// Access privileged method
cartman.getIdol(); // "Paris Hilton"

// Access public property
cartman.name; // "Cartman"

// Access public method
cartman.getName(); // "Cartman"

// Access static property on an instance
cartman.town; // undefined

// Access static property on the constructor object
Kid.town; // "South Park"

See http://robertnyman.com/2008/10/14/javascript-how-to-get-private-privileged-public-and-static-members-properties-and-methods/

What is Progressive Enhancement?
----------
Progressive Enhancement consists of the following core principles:

basic content should be accessible to all browsers
basic functionality should be accessible to all browsers
sparse, semantic markup contains all content
enhanced layout is provided by externally linked CSS
enhanced behavior is provided by [[Unobtrusive JavaScript|unobtrusive]], externally linked JavaScript
end user browser preferences are respected

Can you describe the difference between progressive enhancement and graceful degradation?
----------


What is FOUC? How do you avoid FOUC?
----------
http://www.learningjquery.com/2008/10/1-way-to-avoid-the-flash-of-unstyled-content
http://paulirish.com/2009/avoiding-the-fouc-v3/


What's a doctype do, and how many can you name?
----------
When you use a DOCTYPE declarations in your web pages, you are telling the web browser what version of (X)HTML your web page should be displayed in. The doctype gives the browser a list of supported tags and does not include any deprecated or proprietary tags in the list. You can get away with writing invalid or incorrect HTML code because most web browsers are amazingly forgiving.


To define the language of a section of the document, add the lang attribute to the appropriate element, such as a div element:


How do you serve a page with content in multiple languages?
----------
<div lang="fr-CA" xml:lang="fr-CA">
 Canadian French content...
 </div>
 <div lang="en-CA" xml:lang="en-CA">
 Canadian English content...
 </div>

 What's the difference between Java and JavaScript?
 ---------
 Here are some differences between the two languages:

Java is an OOP programming language while Java Script is an OOP scripting language.
Java creates applications that run in a virtual machine or browser while JavaScript code is run on a browser only.
Java code needs to be compiled while JavaScript code are all in text.

Java is a statically typed language; JavaScript is dynamic.
Java is class-based; JavaScript is prototype-based.
Java constructors are special functions that can only be called at object creation; JavaScript "constructors" are just standard functions.
Java requires all non-block statements to end with a semicolon; JavaScript inserts semicolons at the ends of certain lines.
Java uses block-based scoping; JavaScript uses function-based scoping.
Java has an implicit this scope for non-static methods, and implicit class scope; 
JavaScript has implicit global scope.

Here are some features that I think are particular strengths of JavaScript:

JavaScript supports closures; Java can simulate sort-of "closures" using anonymous classes. (Real closures may be supported in a future version of Java.)
All JavaScript functions are variadic; Java functions are only variadic if explicitly marked.
JavaScript prototypes can be redefined at runtime, and has immediate effect for all referring objects. Java classes cannot be redefined in a way that affects any existing object instances.
JavaScript allows methods in an object to be redefined independently of its prototype (think eigenclasses in Ruby, but on steroids); methods in a Java object are tied to its class, and cannot be redefined at runtime.


How would you optimize a websites assets/resources?
---------
File concatenation
File minification
CDN Hosted
Caching
etc.

Why is it better to serve site assets from multiple domains?
---------
Browsers restrict simultaneous downloads per domain, so you can just add different A records to point to the same location if you like, or create different buckets on a blob storage account.




Advantages of LESS	http://tympanus.net/codrops/2012/01/27/modular-front-end-development-with-less/
---------
Variables. Define any variable like so: @color1: #df0290;and use it later in your code:
Mixins.Define useful functions with or without parameters
Nested rules.Pretty self-explanatory, as I’m sure this is something you’ve been wishing for in CSS since you started using it

What does & stand for in LESS?
-----------
An ampersand (&) refers to the parent rule. So &.category would translate to article h2.category once the LESS code had been compiled.

How would you organize a LESS library for a large project?
-----------
/project/css/
- reset.css — resets default browser styling
- grid.less — supplies mixins for a grid system, such as the .col(@width) mixin above
- type.less — supplies mixins for font styling as well as @font-face rules
- colorscheme.less — LESS variables for the design’s various colors
- interface.less — mixins for interface features like buttons, forms, and dialogs
- layout.less — design-specific layout of the site
- style.less — the main stylesheet, including all of the above and adding in whatever site-specific styles are otherwise necessary