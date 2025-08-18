**ECMAScript** - official name, but JavaScript is trademarked by Oracle
- used to refer to version of language (ECMAScript 5, 6)
(has problems since originally didn't have exception handling)
(In other languages, you learn language features, in JS, you often learn patterns instead.)

**Numbers**: All numbers are floating-point:
- > 1 === 1.0
- **true**
- > Number('xyz') // 'xyz' can't be converted to a number
- **NaN** // not a number
- > 3/0
- Infinity // mostly an error value
- Math.pow(2, 1024) // number too large
- **Infinity** // useful as **default values** for a minimum or maximum

**Basic Operators**:
- Remainder: num1 % num2
- Increment: ++var, var++
- Decrement: --var, var--
- Negate: -val
- Convert to number: ++val
- ***Bitwise operators***

**Strings**: single or double quotes, escape character (\\)
'Did she say "Hello"?'
"Did she say \\"Hello\\"?"
'Line1 \nLine2'

**Access string properties**: (IMMUTABLE)
- *chars:* var str = 'abc';  str[1]  // 'b'
- *length:* 'abc'.length // 3
- ***concatenation***
**String Methods:**
slice -
- 'abc'.slice(1) // copy substring
- 'bc'
- 'abc'.slice(1,2) // inclusive, exclusive
- 'b'
trim -
- '\t xyz '.trim() // trim whitespace
- 'xyz'
*toUpperCase()*
*indexOf(string/char)* // Success: index, Failure: -1

Special Variable: **Arguments**
- function f() ( return **arguments** }
- var args = f('a', 'b', 'c');
- args[0] // 'a'
	- arguments - looks like an array, but w/o the array methods
- return toArray(**arguments**)
- [ 'a', 'b', 'c' ]

---

Setting **Default Vals** to **Params**:
- function pair(x, y) {
	- x = x || 0; // returns x if it is truthy (not null, undef, etc)
	- y = y || 0;
	- return [ x, y ];
  }

**Nullish Coalescing operator**: *??*
- ternary op that checks value is "defined" (nonnull and not undef)
EX:
```javascript
  result = a ?? b
  ```
Same thing as:
```javascript
result = (a !== null && a !== undefined) ? a : b;
```

```javascript
let firstName = null;
let lastName = null;
let nickName = "Supercoder";

// shows the first defined value:
alert(firstName ?? lastName ?? nickName ?? "Anonymous"); // Supercoder
```

- **Can be replaced with ||**
- `||` returns the first _truthy_ value.
	- falsy includes: `false`, `0`, an empty string `""` and `null/undefined`
- `??` returns the first _defined_ value.

```javascript
let height = 0;

alert(height || 100); // 100
alert(height ?? 100); // 0
```
- **DIFFERENCE**:
- || = if truthy, return this
- ?? if defined, don't return this
---

**Arrow Functions:**
*simple and concise syntax for creating functions


---

**Asynchronous Programming:**
***Asynchronous Operations*:** occur at any time, usually stuff that takes time to complete:
- fetching data from API, reading file, interacting w database
***Promises:*** an object representing the eventual completion (or failure) of an async operation
- async and await build on Promises to make them easier to work w

***async*** and ***await***
coroutines - a coroutine is a function which can pause its execution and return control to main loop until some event occurs

**async**: marks a function as asynchronous
- automatically wraps return val of func in a *Promise*
```javascript
async function myAsyncFunction() { 
	return "Hello, Async!"; 
	}
/* old method to handle result of a Promise */
myAsyncFunction().then((result) => console.log(result));     
// Logs: Hello, Async!
```
- .then() - method available on Promises
- it takes a callback func that runs when Promise is resolved (success)
- returns a new Promise, allowing chaining of further .then() calls
- ESSENTIALLY:
	- just says what to do after async func resolves/returns Promise

**await:** pauses execution of async func until a Promise is resolved/rejected
- makes asynchronous code look synchronous and easier to read
- avoids use of .then()
``` javascript
async function fetchData() {
	const response = await fetch("https://jsonplaceholder.typicode.com/posts");
	const data = await response.json();
	console.log(data);
}
```
