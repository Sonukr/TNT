## Tips for Javascript Shorthand and Debugging with Console.

#### Tips for Javascript Debugging with Console - 

### console.table();
 - I found console.table this is a true gem in my opinion! You can actually print a very nice table with the objects you log using the console.table()
 
 ```javascript
 console.table(
    [   {name:"Sonu", Role: "Front-end develoepr"},
        {name:"John", Role: "UI develoepr"}
     ]
 )
 ```

 ### Adding CSS to console.log statements.
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

### console.trace()

If you want to know where the log is being prompted from use console.trace() to get the stack trace with the logged data.

### console.time() && console.timeEnd()

If you are trying to find a sneaky performance issue, start counting time with **console.time()**  and print with **console.timeEnd()**.

``` Javascript
console.time()
undefined
console.timeEnd()
default: 3327.244873046875ms
undefined
```

### console.memory
If your performance issue is even trickier, and you are looking for a sneaky memory leak, you might like to try and utilize **console.memory** (property, not a function) to check out your heap size status.

```Javascript
 console.memory
 MemoryInfo {totalJSHeapSize: 44700000, usedJSHeapSize: 39600000,jsHeapSizeLimit: 2190000000}
   jsHeapSizeLimit:2190000000
   totalJSHeapSize:44700000
   usedJSHeapSize:39600000
   __proto__:MemoryInfo
```
### console.count()
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

### console.assert(false, “Log me!”);
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

### console.group(‘group’) & console.groupEnd(‘group’)
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

### String substitutions
When logging, you can incorporate variables using string substitutions. These references should be types (%s = string, %i = integer, %o = object, %f = float).

```Javascript
console.log("Hello, %s. You have Won $ %i", "Sonu", 100000);
Hello, Sonu. You have Won $ 100000
```


### console.clear()
Well, having written so many logs, it’s now time to clear your console a little.

```javascript
console.clear();
Console was cleared
undefined
```