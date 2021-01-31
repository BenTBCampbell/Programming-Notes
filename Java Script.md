## Java Script

[Arrow Functions](#arrow-functions)  
[Date](#date)

### Arrow Functions
Arrow functions are a shorthand for funcions.

```js
// Traditional Function
function (a) {
  return a + 100;
}

// Arrow Function
a => a + 100;
```

Some other versions:
* multiple parameters: `(a, b) => a + b + 100;`
* no parameters: `() => a + b + 100;`
* multi-line body: 
  ```js
  (a, b) => {
    let c = 42;
    return a + b + c;
  }
  ```
  
### Date
A way to use times and dates in Java Script.

Some ways to make dates:
* `var date = new Date() // now`
* `var date = new Date('January 27, 2000, 12:18:00')`
* `var date = new Date(2000, 0, 27) // year, month, day. the month is zero-indexed`
* `var date = new Date(2000, 0, 27, 12, 18, 0) // year, month, day, minute, seconds, milliseconds`
* `var date = new Date(949000680000) // from milliseconds sinc the Unix Epoch (January 1, 1970, 00:00:00 UTC)`

Useful functions:

* `date.toDateString() // returns a string like 'Thu Apr 12 2018'`
* `date.toString() // returns a string like 'Wed Dec 31 1969 17:00:00 GMT-0700 (mountain time standard)'`
* `date.getTime() // time in milliseconds since Unix Epoch`
* Get info about specific parts of the date:
  * `date.getFullYear()`
  * `date.getMonth() // month of the year`
  * `date.getDate() // day of the month`
  * `date.getDay() // day of the week`
  * `date.getHours()`
  * `date.getMinutes()`
  * `date.getSeconds()`
  * `date.getMilliseconds()`
  * `date.getMilliseconds()`

  There are also setters for all of these. The setter for `getFullYear()` is `setFullYear()`, for example.