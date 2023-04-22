## 24th November 2022

#### `Array.prototype.fill()`
Change elements in the array to a same value according to specified start and end position <br>
`return a modified array with filled values (it will change the original array)`

Usage
```js
let myArray = [1,2,4,5,6]
let secondArray = myArray.fill(6)  // will return [6,6,6,6,6]
console.log(myArray) // will return [6,6,6,6,6] as well as the fill method updates the original
```
#### `Throw away variables`
Throw away variables are variables that are deliberatery indicated that they are not used anywhere or have any effect to the codebase. for example when you are filtering into an array based on the index of elements in that case you may not need the elements themselves but their indexes insted

let's say we want to filter only numbers on even index
```js
let numbers = [1,2,3,4,5,6,7]
let evenIndexedNumbers = numbers.filter((_, index)=> index % 2 === 0) // we don't care about the first parameter therefore is a throw away
```
The `_` (underscore) is not a special character here it is just as any variable name we could use the underscore is used for convention.
`Note That`: Using underscore in this way may results into unexpected behaviours when using packages like lodash it is better to avoid them and some common names like `foo`, `dummy`, `garbage`...


## 06 March 2023

### Updating an element in an array of objects using the spread (...) operator

## 07 March 2023

### Object Computed properties in ES6
