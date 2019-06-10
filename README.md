# Closures lab 2

Fork and clone this repo. On your fork, answer and commit the follow questions. When you are finished, submit the link to your repo on Canvas.


## Question 1

Use `filter` to create an array called `multiples` that contains all the multiples of 3 from `numbers` and then print it.

`let numbers = [1, 2, 3, 4, 6, 8, 9, 3, 12, 11]`

Example:
Input: `let numbers = [1, 2, 3, 4, 6, 8, 9, 3, 12, 11]`

Expected values: `multiples = [3, 6, 9, 3, 12]`


## Question 2

Implement a function `combineArrays` that takes 2 arrays and a closure that combines 2 Ints into a single Int. The function combines the two arrays into a single array using the provided closure. Assume that the 2 arrays have equal length.

Example:
Input:

```swift
var array1 = [1,2,3,4]
var array2 = [5,5,5,3]
combineArrays(array1,array2) {
    $0 * $1
}
```

Output: `[5,10,15,12]`


## Question 3

a) Write a function called `intsToStrings` that takes an array of Ints and a closure as parameters and returns an array of Strings. The closure should take an Int and return a String. The function should apply the closure to the ints in the array.

`let theInts = [1, 2, 3, 44, 555, 6600, 10763]`

b) Define a closure assigned to a constant called `asString` that just turns an Int to a String and pass it to `intsToStrings`.

c) Define a closure assigned to a constant called `evenOdd` that returns "odd" or "even" if the Int is odd or even and pass it to `intsToStrings`.

d) Define a closure assigned to a constant called `englishWords` that returns the written english word of each digit in an Int, 234 -> "two three four", and pass it to `intsToStrings`.

e) Use the built in `map` method on `theInts` to recreate the answers for b, c and d.

Example:
Input:

```swift
let a = intsToStrings(arr: theInts, toString: asString)
let b = intsToStrings(arr: theInts, toString: evenOdd)
let c = intsToStrings(arr: theInts, toString: englishWords)
```

Output:

```swift
a) ["1", "2", "3", "44", "555", "6600", "10763"]
b) ["odd", "even", "odd", "even", "odd", "even", "odd"]
c) ["one ", "two ", "three ", "four four ", "five five five ", "six six zero zero ", "one zero seven six three "]
```


## Question 4

let myArray = [34,42,42,1,3,4,3,2,49]

a) Sort `myArray` in ascending order by defining the constant `ascendingOrder` below.

```swift
let mySortedArray = myArray.sort(ascendingOrder)
let ascendingOrder =
```

b) Sort `myArray` in descending order by defining the constant `descendingOrder` below.

```swift
let mySecondSortedArray = myArray.sort(descendingOrder)
let descendingOrder =
```


## Question 5

`let arrayOfArrays = [[3,65,2,4],[25,3,1,6],[245,2,3,5,74]]`

a) Sort `arrayOfArrays` in ascending order by the **3rd element** in each array. You can assume each array will have at least 3 elements.

b) Sort `arrayOfArrays` in ascending order by the 3rd element in each array. Don't assume each array will have at least 3 elements. Put all arrays that have less than 3 elements at the end in any order.


## Question 6

```swift
let letterValues = [
"a" : 54,
"b" : 24,
"c" : 42,
"d" : 31,
"e" : 35,
"f" : 14,
"g" : 15,
"h" : 311,
"i" : 312,
"j" : 32,
"k" : 93,
"l" : 203,
"m" : 212,
"n" : 41,
"o" : 102,
"p" : 999,
"q" : 1044,
"r" : 404,
"s" : 649,
"t" : 414,
"u" : 121,
"v" : 838,
"w" : 555,
"x" : 1001,
"y" : 123,
"z" : 432
]
```

a) Sort the string below in descending order according the dictionary `letterValues`:

`var codeString = "aldfjaekwjnfaekjnf"`

b) Sort the string below in ascending order according the dictionary `letterValues`

`var codeStringTwo = "znwemnrfewpiqn"`

## Question 7

```swift
let firstAndLastTuples = [("Johann S.", "Bach"),
("Claudio", "Monteverdi"),
("Duke", "Ellington"),
("W. A.", "Mozart"),
("Nicolai","Rimsky-Korsakov"),
("Scott","Joplin"),
("Josquin","Des Prez")]
```

Sort the array of tuples by last name. Print the sorted array using string interpolation so that the output looks like:

```swift
Bach, Johann S.
Des Prez, Josquin
...etc
```


## Question 8

Create a closure that takes an two arrays of strings as input. Output a new string with the contents of the arrays in alternating order and separated by a space. If one array's length is longer than the other's length, append the rest of its contents to the new string.

Example:
Input:
```swift
array1: ["Hello", "My", "Friend"]
array2: ["Darkness", "Old"]
```
Output:  `"Hello Darkness My Old Friend"`


## Question 9

a) Write a function called `myFilter` that takes an array of Double and a closure as parameters and returns an array of Double. The closure should take a Double and return a Bool. The function should apply the closure to the doubles in the array.

`let theDoubles = [11.45, 3.2, 4.0, 5.67, 58.65, 66.0, 5.2, 5.0]`

b) Define a closure assigned to a constant called `biggerThanTen` that takes a double and returns true if it is greater or equal to 10.0 and pass it to `myFilter`.

c) Define a closure assigned to a constant called `wholeNumber` that takes a double and returns true if it is a whole number and pass it to `myFilter`.

d) Define a closure assigned to a constant called `justEven` that takes a double and returns true if the number to the left of the point is even and pass it to `myFilter`.

e. Use the built in filter method on `theDoubles` to recreate the answers for b, c and d.

Example
Input:

```swift
let a = myFilter(arr: theDoubles, filter: biggerThanTen)
let b = myFilter(arr: theDoubles, filter: wholeNumber)
let c = myFilter(arr: theDoubles, filter: justEven)
```

output:

```swift
a. [11.45, 58.65, 66]
b. [4, 66, 5]
c. [4, 58.65, 66]
```


## Question 10

a) Write a closure that takes two arrays of Ints and returns an array of Ints. The array it returns should be the two arrays combined and sorted in ascending order.

b) Write a closure that takes two arrays of Ints and returns an array of Ints. The array it returns should be the two arrays combined but contain only the positive even numbers.

c) Write a closure that takes two arrays of ints and returns an array of ints. The array it returns should be the two arrays combined, with each element doubled minus 5.
