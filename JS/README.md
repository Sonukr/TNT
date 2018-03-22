## Tips for Javascript Shorthand and Debugging with Console.

 - [Javascript](https://github.com/Sonukr/TNT/tree/master/JS)
      - [Javascript Debugging with Console](https://github.com/Sonukr/TNT/tree/master/JS#tips-for-javascript-debugging-with-console--)
      - [JS shorthand tricks](https://github.com/Sonukr/TNT/tree/master/JS#useful-javascript-shorthand-properties--)
      - [ES6 Tips and Tricks]()

## Tips for Javascript Debugging with Console - 

#### 1 - console.table();
- I found console.table this is a true gem in my opinion! You can actually print a very nice table with the objects you log using the console.table()

```javascript
console.table(
    [   {name:"Sonu", Role: "Front-end develoepr"},
        {name:"John", Role: "UI develoepr"}
    ]
)
```

 #### 2 - Adding CSS to console.log statements.
 - This is an another fun with console. To add styles to logs, the method expects **`%c`** within the first argument of console.log() and it picks up the very next argument as CSS style for the **%c** pattern argument text. Try the following basic example now in this tab’s console window.

```Javascript
console.log(
    '%c Hey.!, This is a styled Console',
    'color:red; font-size:18px'
    );
```
 - This will print the text in red color with 18px of font-size.

 - If you want to add multiple style, then simply add multiple %c text and add style arguments respectively.

``` javascript
console.log(
    '%c Hey.!, This is a styled Console. %c This is another text.',
    'color:white; font-size:18px; background:green; margin-right:10px',
    'color:white;font-size14px;background:#333'
    );
```

- Please note, there are two %c pattern text and hence two CSS style arguments. And the CSS arguments are picked up respectively from left to right.

- You can add any style which is supported by browsers like shadow, padding, margin etc.

#### 3 - console.trace()

If you want to know where the log is being prompted from use console.trace() to get the stack trace with the logged data.

#### 4 - console.time() && console.timeEnd()

If you are trying to find a sneaky performance issue, start counting time with **console.time()**  and print with **console.timeEnd()**.

``` Javascript
console.time()
undefined
console.timeEnd()
default: 3327.244873046875ms
undefined
```

#### 5 - console.memory
If your performance issue is even trickier, and you are looking for a sneaky memory leak, you might like to try and utilize **console.memory** (property, not a function) to check out your heap size status.

```Javascript
 console.memory
 MemoryInfo {totalJSHeapSize: 44700000, usedJSHeapSize: 39600000,jsHeapSizeLimit: 2190000000}
   jsHeapSizeLimit:2190000000
   totalJSHeapSize:44700000
   usedJSHeapSize:39600000
   __proto__:MemoryInfo
```
#### 6 - console.count()
In a case of recurring function or code, you can use console.count(‘?’) to keep count of how many times your code is read.

```Javascript
console.count("Function Read Count");
Function Read Count: 1
undefined
console.count("Function Read Count");
Function Read Count: 2
undefined
console.count("Function Read Count");
Function Read Count: 3
undefined
console.count("Function Read Count");
Function Read Count: 4
undefined
```

#### 7 - console.assert(false, “Log me!”);
Yes, conditional logging without wrapping your logs with if-else :) 
You can use console.assert(condition, msg) to log something when the condition is falsy. \
*disclaimer — in Node.js this will throw Assertion Error!

```Javascript
console.assert(true, "Log me!");
undefined
console.assert(false, "Log me!");
Assertion failed: Log me!
undefined
```

#### 8 - console.group(‘group’) & console.groupEnd(‘group’)
After writing so many logs, you might want to organize them. A small and useful tool for that is the console.group() & console.groupEnd(). Using console group, your console logs are grouped together, while each grouping creates another level in the hierarchy. Calling groupEnd reduces one.

```Javascript
Try something like this in console and see the grouping

console.log("Outter one");
console.group();
console.log("Level 1");
console.group();
console.groupEnd();
console.log("GOing Back");
```
#### 9 - Copying the data/obj/array to clipboard from console.
Somtimes, all of us want to copy the data/obj/array from console to clipboard. generally we select entire content then use ctrl+c or cmd+c. using this method we never get pefetct(entire) object/array. we can use `copy` for get this done perfectly.

```javascript
let arr = [{id:1, name:'Sonu'},{id:2, name:'John'}]
    
```
we can easily copy above array by selecting. but, what if an opertaion is performed on this array and stored in another variable and we want to copy exact data in clipboard ?
 
Ex: I performed some opertions over a variable data;
```Javascript   
<!-- Converting the array item to a bing object -->
let obj = {};
for(i=0;i<arr.length; i++){
	obj[arr[i].id]=arr[i]
}
<!-- converting the above object's key value to an object and push into an array -->
const newArr = [];
for(let key in obj){
	let newObj= {};
	if(obj.hasOwnProperty(key)){
		newObj[key]=obj[key];
	}
	newArr.push(newObj)
}
```

now, if i will check the obj and newArr output in console We will get something like this.

```jvascript
{1: {…}, 2: {…}} //a bing object from array
(2) [{…}, {…}]   //an array from above object
```
We can **expand this object**, but we can't **copy** entire object as a single object in **clipboard**. To solve these kind of issue we can use `copy()`.

so, we have data in obj variable. let's use that.
```
copy(obj);
copy(newArr)
```
The content of `obj` and `newArray` are copied respectively  in your `clipboard`. you can paste it anywhere.  you will find something like this.
```javascript
<!-- A big object from array-->
{
  "1": {
    "id": 1,
    "name": "Sonu"
  },
  "2": {
    "id": 2,
    "name": "John"
  }
}
<!-- An array from the above object -->
[
  {
    "1": {
      "id": 1,
      "name": "Sonu"
    }
  },
  {
    "2": {
      "id": 2,
      "name": "Monu"
    }
  }
]
```



#### 10 - String substitutions
When logging, you can incorporate variables using string substitutions. These references should be types (%s = string, %i = integer, %o = object, %f = float).

```Javascript
console.log("Hello, %s. You have Won $ %i", "Sonu", 100000);
Hello, Sonu. You have Won $ 100000
```


#### 11 - console.clear()
Well, having written so many logs, it’s now time to clear your console a little.

```javascript
console.clear();
Console was cleared
undefined
```


## Useful Javascript Shorthand properties - 

#### 1 - The Ternary Operator
This is a great code saver when you want to write an if..else statement in just one line.

Longhand:

```javascript
const x = 10;
let answer;
if (x>10) {
    answer = 'You are in true loop';
} else {
    answer = 'You are in false loop';
}
```
Shorthand:

```javascript
const answer = x > 10 ? 'You are in true loop' : 'You are in false loop';
```

#### 2 - Short-circuit Evaluation Shorthand
When assigning a variable value to another variable, you may want to ensure that the source variable is not null, undefined or empty. You can either write a long if statement with multiple conditionals, or use a short-circuit evaluation.

Longhand:
```Javascript
if (variable1 !== null || variable1 !== undefined || variable1 !== '') {
     let variable2 = variable1;
}
```
Shorthnd:
```Javascript
const variable2 = variable1  || 'new';
```

#### 3 - Declaring Variables Shorthand
It is good practice to declare your variable assignments at the beginning of your functions. This shorthand method can save you lots of time and space when declaring multiple variables at the same time.

Longhand:
```javascript
let x;
let y;
let z = 3;
```
Shorthand:
```javascript
let x, y, z=3;
```

#### 4 - If Presence Shorthand
This might be trivial, but worth a mention. When doing “if checks”, assignment operators can sometimes be omitted.

Longhand:
```javascript
if (condition === true)
```
Shorthand:
```javascript
if (condition)
```
Here is another example. If “condition” is NOT equal to true, then do something.

Longhand:
```javascript
let condition;
if ( condition !== true ) {
// do something...
}
```
Shorthand:
```javascript
let condition;
if (!condition) {
// do something...
}
```

#### 5 - JavaScript for Loop Shorthand
This little tip is really useful if you want plain JavaScript and not rely on external libraries such as jQuery or lodash.

Longhand:
```javascript
for (let i = 0; i < Users.length; i++)
```
Shorthand:
```javascript
for (let index of Users)
```
Shorthand for Array.forEach:

```Javascript
function logArrayElements(element, index, array) {
  console.log("a[" + index + "] = " + element);
}
[2, 5, 9].forEach(logArrayElements);
// logs:
// a[0] = 2
// a[1] = 5
// a[2] = 9
```

#### 6 -  Short-circuit Evaluation
Instead of writing six lines of code to assign a default value if the intended parameter is null or undefined, we can simply use a short-circuit logical operator and accomplish the same thing with just one line of code.

 Longhand:
```javascript
let SERVER;
if (process.env.SERVER) {
  SERVER = process.env.SERVER;
} else {
  SERVER = 'localhost';
}
```
Shorthand:
```javascript
const SERVER = process.env.SERVER || 'localhost';
```

#### 7 - Decimal base exponents
You may have seen this one around. It’s essentially a fancy way to write numbers without the trailing zeros. For example, `1e3` essentially means `1 followed by 3 zeros`. It represents a decimal base (which JavaScript interprets as a float type) equal to `1,000`.

Longhand:
```Javascript
for (let i = 0; i < 10000; i++) {}
```

Shorthand: 
```javascript
for (let i = 0; i < 1e3; i++) {}
// All the below will evaluate to true
1e0 === 1;
1e1 === 10;
1e2 === 100;
.
.
.
you can continue so on.
```

#### 8 - Object Property Shorthand
Defining object literals in JavaScript makes life much easier. ES6 provides an even easier way of assigning properties to objects. If the property name is the same as the key name, you can take advantage of the shorthand notation.

Longhand:
```Javascript
const obj = { x:x, y:y };
```

Shorthand: 
```javascript
const obj = { x, y };
```

#### 9 -  Arrow Functions Shorthand
Classical functions are easy to read and write in their plain form, but they do tend to become a bit verbose and confusing once you start nesting them in other function calls.

Longhand:
```Javascript
function sayHello(name) {
  console.log('Hello', name);
}

setTimeout(function() {
  console.log('Loaded')
}, 2000);

list.forEach(function(item) {
  console.log(item);
});
```

Shorthand: 
```javascript
sayHello = name => console.log('Hello', name);

setTimeout(() => console.log('Loaded'), 2000);

list.forEach(item => console.log(item));
```
It’s important to note that the value of this inside an arrow function is determined differently than for longhand functions, so the two examples are not strictly equivalent. 

#### 10 - Implicit Return Shorthand
Return is a keyword we use often to return the final result of a function. An arrow functions with a single statement will implicitly return the result its evaluation (the function must omit the braces ({}) in order to omit the return keyword).

To return a multi-line statement (such as an object literal), it’s necessary to use () instead of {} to wrap your function body. This ensures the code is evaluated as a single statement.

Longhand:
```Javascript
function calcCircumference(diameter) {
  return Math.PI * diameter
}
```

Shorthand: 
```javascript
calcCircumference = diameter => (
  Math.PI * diameter;
)
```

#### 11 - Default Parameter Values
You can use the if statement to define default values for function parameters. In ES6, you can define the default values in the function declaration itself.

Longhand:
```Javascript
function volume(l, w, h) {
  if (w === undefined)
    w = 2;
  if (h === undefined)
    h = 5;
  return l * w * h;
}
```

Shorthand: 
```javascript
volume = (l, w = 2, h = 5 ) => (l * w * h);
volume(2) //output: 20
```

#### 12 - Template Literals
Aren’t you tired of using ' + ' to concatenate multiple variables into a string? Isn’t there a much easier way of doing this? If you are able to use ES6, then you are in luck. All you need to do is use is the backtick(`), and ${} to enclose your variables.

Longhand:
```Javascript
const welcome = 'You have logged in as ' + first + ' ' + last + '.'

const db = 'http://' + host + ':' + port + '/' + database;
```

Shorthand: 
```javascript
const welcome = `You have logged in as ${first} ${last}`;
const db = `http://${host}:${port}/${database}`;
```
