# Closures Lab

Fork and clone this repo. On your fork, answer and commit the follow questions. When you are finished, submit the link to your repo on Canvas.

## Question 1

Write a function named `applyKTimes` that takes an integer `K` and a closure and calls the closure K times. The closure will not take any parameters and will not have a return value.

Function Definition:
func applyKTimes(_ K: Int, _ closure: () -> ())

Example:
Input:

```swift
applyKTimes(3) {
    print("Hello Closures!")
}
```
Output:

```swift
Hello Closures!
Hello Closures!
Hello Closures!
```

```swift
func applyKTimes(_ K: Int, _ closure: () -> ()) {
    for _ in 1...K {
        closure()
    }
}

applyKTimes(2) {
    print("Closures are lit!")
}
```

## Question 2

Use `filter` to create an array called `multiples` that contains all the multiples of 3 from `numbers` and then print it.

`let numbers = [1, 2, 3, 4, 6, 8, 9, 3, 12, 11]`

Example:
Input: `let numbers = [1, 2, 3, 4, 6, 8, 9, 3, 12, 11]`

Expected values: `multiples = [3, 6, 9, 3, 12]`

```swift
let numbers = [1, 2, 3, 4, 6, 8, 9, 3, 12, 11]

let multiples = numbers.filter({ $0 % 3 == 0})

print(multiples)
```

## Question 3

Find the largest number from `numbers` and then print it. Use `reduce` to solve this exercise.

Example:
Input: `let numbers = [4, 7, 1, 9, 6, 5, 6, 9]`

Output: `9`

```swift
let numbers = [4, 7, 1, 9, 6, 5, 6, 9]

let largestNumber = numbers.reduce(0, {
    $0 > $1 ? $0 : $1
})
print(largestNumber)
```

## Question 4

Join all the strings from `strings` into one using `reduce`. Add spaces in between strings. Print your result.

Example:
Input: `let strings = ["We", "Heart", "Swift"]`

Output: `"We Heart Swift"`

```swift
let strings = ["We", "Heart", "Swift"]

let singleString = strings.reduce(into:"", {
    $0 += "\($1) "
}).dropLast()

print(singleString,".", separator: "")
```

## Question 5

`let cities = ["Shanghai", "Beijing", "Delhi", "Lagos", "Tianjin", "Karachi", "Karachi", "Tokyo", "Guangzhou", "Mumbai", "Moscow", "São Paulo"]`

a. Use `sortedBy` to sort `cities` in alphabetical order.

b. Use `sortedBy` to sort `cities` alphabetical order of the second character of the city name.

c. Use `sortedBy` to sort `cities` in order of the length of the city name.

```swift
let cities = ["Shanghai", "Beijing", "Delhi", "Lagos", "Tianjin", "Karachi", "Karachi", "Tokyo", "Guangzhou", "Mumbai", "Moscow", "São Paulo"]

// Use `sortedBy` to sort `cities` in alphabetical order.
let alphabeticalOrder = cities.sorted(by: <)
print("Sorted by alphabetical order of the city name:",alphabeticalOrder, separator: "\n",terminator: "\n\n")

// Use `sortedBy` to sort `cities` alphabetical order of the second character of the city name.
let secondLetterAlphabeticalOrder = cities.sorted(by: { x, y in
    Array(x)[1] < Array(y)[1]
})
print("Sorted by alphabetical order of the second character in city name:",secondLetterAlphabeticalOrder, separator: "\n",terminator: "\n\n")

// Use `sortedBy` to sort `cities` in order of the length of the city name.
let lengthOfCityName = cities.sorted(by: { x, y in
    x.count > y.count
})
print("Sorted by the length of the city name:",lengthOfCityName, separator: "\n",terminator: "\n\n")
```

## Question 6

`let citiesWithPopulation: [(String, Int)] = [("Shanghai", 24256800), ("Beijing", 21516000), ("Delhi", 16787941), ("Lagos", 16060303), ("Tianjin", 15200000), ("Karachi", 14910352), ("Karachi", 14160467), ("Tokyo", 13513734), ("Guangzhou", 13080500), ("Mumbai", 12442373), ("Moscow", 12380664), ("São Paulo", 12038175)]`

a. Use `sortedBy` to sort `citiesWithPopulation` in ascending order of population.

b. Use `sortedBy` to sort `citiesWithPopulation` in reverse alphabetical order of the last character in the city name.

```swift
let citiesWithPopulation: [(String, Int)] = [("Shanghai", 24256800), ("Beijing", 21516000), ("Delhi", 16787941), ("Lagos", 16060303), ("Tianjin", 15200000), ("Karachi", 14910352), ("Karachi", 14160467), ("Tokyo", 13513734), ("Guangzhou", 13080500), ("Mumbai", 12442373), ("Moscow", 12380664), ("São Paulo", 12038175)]

// Use `sortedBy` to sort `citiesWithPopulation` in ascending order of population.
let orderOfPopulation = citiesWithPopulation.sorted(by: { x, y in
    x.1 < y.1
})
print("Sorted by order of population:",orderOfPopulation, separator: "\n",terminator: "\n\n")

// Use `sortedBy` to sort `citiesWithPopulation` in reverse alphabetical order of the last character in the city name.
let reverseAlphabeticalOrderOfTheLastChar = citiesWithPopulation.sorted(by: {x, y in
    Array(x.0)[x.0.count - 1] > Array(y.0)[y.0.count - 1]
})
print("Sorted by alphabetical order of the last character in the city name:",reverseAlphabeticalOrderOfTheLastChar, separator: "\n",terminator: "\n\n")
```

## Question 7

Sort `numbers` in ascending order by the number of divisors. If two numbers have the same number of divisors the order in which they appear in the sorted array does not matter.

`var numbers = [1, 2, 3, 4, 5, 6]`

Example:
Input: `var numbers = [1, 2, 3, 4, 5, 6]`

Output:

```swift
numbers = [1, 2, 3, 5, 4, 6]
// 1 has one divisor
// 2, 3 and 5 have 2
// 4 has 3 divisors
// 6 has 4 divisors

// [1, 5, 2, 3, 4, 6] would also have been a valid solution
```

```swift
var numbers = [1, 2, 3, 4, 5, 6,7]

let sortByNumberOfDivisors = { (arr: [Int] ) -> [Int] in
    var outputArray = [Int]()
    var divisorCountTuple = [(number: Int , count: Int)]()

    for number in arr {
        var numberOfDivisors = 0
        for x in 1...number where number % x == 0{
            numberOfDivisors += 1
        }
        divisorCountTuple.append((number: number, count: numberOfDivisors))
    }
    divisorCountTuple.sort(by: {(x,y) in
        x.count < y.count
    })

    for (number, _) in divisorCountTuple {
        outputArray.append(number)
    }
    return outputArray
}

print(sortByNumberOfDivisors(numbers))
```

## Question 8

Find the sum of the squares of all the odd numbers from `numbers` and then print it.

`var numbers = [1, 2, 3, 4, 5, 6]`

a. Write code that removes all the odd numbers from the array.

b. Write code that squares all the numbers in the array.

c. Write code that finds the sum of the array.

d. Now use `map`, `filter` and `reduce` to solve this problem.

Example:
Input: `var numbers = [1, 2, 3, 4, 5, 6]`

Output: `35 // 1 + 9 + 25 -> 35`

```swift
var numbers = [1, 2, 3, 4, 5, 6]
print("Numbers array:", numbers, separator: "\n", terminator: "\n\n")

// Write code that removes all the odd numbers from the array.
var allEvenNumbers = [Int]()
for number in numbers where number % 2 != 1 {
    allEvenNumbers.append(number)
}
print("Removed all odd numbers from the numbers array using for loops:", allEvenNumbers, separator: "\n", terminator: "\n\n")

// Write code that squares all the numbers in the array.
var squareOfAllNumbers = [Int]()
for number in numbers {
    squareOfAllNumbers.append(number * number)
}
print("Squared all the numbers in the numbers array using for loops:", squareOfAllNumbers, separator: "\n", terminator: "\n\n")

// Write code that finds the sum of the array.
var sumOfAllNumbersInTheArray = 0
for number in numbers {
    sumOfAllNumbersInTheArray += number
}
print("Sum of all the numbers in the numbers array using for loops:", sumOfAllNumbersInTheArray, separator: "\n", terminator: "\n\n")

// Write code that removes all the odd numbers from the array.
let noOddNumbers = numbers.filter({ $0 % 2 != 01 })
print("Removed all the odd numbers using filter:",noOddNumbers, separator: "\n", terminator: "\n\n")

// Write code that squares all the numbers in the array.
let numbersSquared = numbers.map({$0 * $0})
print("Squared all the numbers using map:",numbersSquared, separator: "\n", terminator: "\n\n")

// Write code that finds the sum of the array.
let sumNumbers = numbers.reduce(0, {$0 + $1})
print("Sum of numbers in the array using reduce:",sumNumbers, separator: "\n", terminator: "\n\n")
```

## Question 9

Implement a function `forEach(array: [Int], _ closure: Int -> ())` that takes an array of integers and a closure and runs the closure for each element of the array.

Example:
Function with Input:

```swift
forEach([1, 2, 3, 4]) {
    print($0 * $0)
}
```

Output:

```swift
1
4
9
16
```

```swift
func forEach(_ array: [Int], _ closure: (Int) -> ()) {
    for number in array {
        closure(number)
    }
}

forEach([1, 2, 3, 4]) {
    print($0 * $0)
}
```

## Question 10

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

```swift
func combineArrays(_ arr1: [Int], _ arr2: [Int], _ closure: (Int, Int) -> Int) -> [Int] {
    var outputArray = [Int]()
    for index in 0...arr1.count - 1 {
        outputArray.append(closure(arr1[index], arr2[index]))
    }
    return outputArray
}

var array1 = [1,2,3,4]
var array2 = [5,5,5,3]
print(combineArrays(array1,array2) {
    $0 * $1
})
```

## Question 11

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

```swift
let theInts = [1, 2, 3, 44, 555, 6600, 10763]

// a) Write a function called `intsToStrings` that takes an array of Ints and a closure as parameters and returns an array of Strings. The closure should take an Int and return a String. The function should apply the closure to the ints in the array.

func intsToStrings(_ arr: [Int], toString closure: (Int) -> String ) -> [String] {
    var outputString = [String]()
    for number in arr {
       outputString.append(closure(number))
    }
    return outputString
}

//  b) Define a closure assigned to a constant called `asString` that just turns an Int to a String and pass it to `intsToStrings`.
let asString = { (a: Int) -> String in
    return String(a)
}

// c) Define a closure assigned to a constant called `evenOdd` that returns "odd" or "even" if the Int is odd or even and pass it to `intsToStrings`.
let evenOdd = { (a: Int) -> String in
    return a % 2 == 0 ? "even" : "odd"
}

// d) Define a closure assigned to a constant called `englishWords` that returns the written english word of each digit in an Int, 234 -> "two three four", and pass it to `intsToStrings`.

let digitToWord = [
    1: "one",
    2: "two",
    3: "three",
    4: "four",
    5: "five",
    6: "six",
    7: "seven",
    8: "eight",
    9: "nine",
    0: "zero"
]

let englishWords = { (a: Int) -> String in
    var outputString = ""
    var numberToModify = a
    repeat {
        if let stringNum = digitToWord[numberToModify % 10] {
            outputString = "\(stringNum) " + outputString
        }
        numberToModify /= 10
    } while (numberToModify / 10) + (numberToModify % 10)  != 0
    outputString.removeLast()
    return outputString
}

let a = intsToStrings(theInts, toString: asString)
let b = intsToStrings(theInts, toString: evenOdd)
let c = intsToStrings(theInts, toString: englishWords)

print("Making the array of integers an array of strings:",a, separator: "\n", terminator: "\n\n")
print("Making the array of integers an array even or odd values:",b, separator: "\n", terminator: "\n\n")
print("Making the array of integers an array of english spellings of the integers:",c, separator: "\n", terminator: "\n\n")


// e) Use the built in `map` method on `theInts` to recreate the answers for b, c and d.
    // Define a closure assigned to a constant called `asString` that just turns an Int to a String and pass it to `intsToStrings`.
let mapToString = theInts.map({ String($0) })
print("Making the array of integers an array of strings using map:",mapToString, separator: "\n", terminator: "\n\n")

    // Define a closure assigned to a constant called `evenOdd` that returns "odd" or "even" if the Int is odd or even and pass it to `intsToStrings`.
let mapToEvenOdd = theInts.map({ $0 % 2 == 0 ? "even" : "odd" })
print("Making the array of integers an array even or odd values using map:",mapToEvenOdd, separator: "\n", terminator: "\n\n")

    // Define a closure assigned to a constant called `englishWords` that returns the written english word of each digit in an Int, 234 -> "two three four", and pass it to `intsToStrings`.
let mapToEnglishWords = theInts.map({ x -> String in
    var outputString = ""
    var numberToModify = x
    repeat {
        if let stringNum = digitToWord[numberToModify % 10] {
            outputString = "\(stringNum) " + outputString
        }
        numberToModify /= 10
    } while (numberToModify / 10) + (numberToModify % 10)  != 0
    outputString.removeLast()
    return outputString
})
print("Making the array of integers an array of english spellings of the integers using map:",mapToEnglishWords, separator: "\n", terminator: "\n\n")
```

## Question 12

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

```swift
var myArray = [34,42,42,1,3,4,3,2,49]

// Sort `myArray` in ascending order by defining the constant `ascendingOrder` below.
let ascendingOrder = { (x: Int, y: Int) in
    x < y
}
let mySortedArray = myArray.sorted(by: ascendingOrder)
print("myArray sorted in ascending order:", mySortedArray, separator: "\n", terminator: "\n\n")

// Sort `myArray` in descending order by defining the constant `descendingOrder` below.
let descendingOrder = { (x: Int, y: Int) in
    x > y
}
let mySecondSortedArray = myArray.sorted(by: descendingOrder)
print("myArray sorted in descending order:", mySecondSortedArray, separator: "\n", terminator: "\n\n")
```

## Question 13

`let arrayOfArrays = [[3,65,2,4],[25,3,1,6],[245,2,3,5,74]]`

a) Sort `arrayOfArrays` in ascending order by the **3rd element** in each array. You can assume each array will have at least 3 elements.

b) Sort `arrayOfArrays` in ascending order by the 3rd element in each array. Don't assume each array will have at least 3 elements. Put all arrays that have less than 3 elements at the end in any order.

```swift
let arrayOfArrays = [[3,65,2,4],[25,3,1,6],[245,2,3,5,74]]

// Sort `arrayOfArrays` in ascending order by the **3rd element** in each array. You can assume each array will have at least 3 elements.
let sortedByThirdElement = arrayOfArrays.sorted(by: { (arr1: [Int], arr2: [Int]) in
    arr1[2] < arr2[2]
})
print("Sorted arrayOfArrays in ascending order by the third element in the array:", sortedByThirdElement, separator: "\n", terminator: "\n\n")

// Sort `arrayOfArrays` in ascending order by the 3rd element in each array. Don't assume each array will have at least 3 elements. Put all arrays that have less than 3 elements at the end in any order.
let arrayOfArraysPlus = [[1,2],[3,65,2,4],[25,3,1,6],[245,2,3,5,74],[1]]
let sortedByThirdWithoutAssumtion = arrayOfArraysPlus.sorted(by: { (arr1: [Int], arr2:[Int]) in
    if arr1.count >= 3 && arr2.count >= 3 {
        return arr1[2] < arr2[2]
    } else {
        return arr1.count > arr2.count
    }
})
print("Sorted with no assumtions to the length of the array:", sortedByThirdWithoutAssumtion, separator: "\n", terminator: "\n\n")
```

## Question 14

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

// a) Sort the string below in descending order according the dictionary `letterValues`:

var codeString = "aldfjaekwjnfaekjnf"
let sortInDescendingOrder = codeString.sorted(by: { (char1, char2) in
    if let num1 = letterValues[String(char1)], let num2 = letterValues[String(char2)] {
        return num1 > num2
    }
    return char1 > char2
})
print("String sorted in descending order by the values in the dictionary:",sortInDescendingOrder, separator: "\n", terminator: "\n\n")

// b) Sort the string below in ascending order according the dictionary `letterValues`

var codeStringTwo = "znwemnrfewpiqn"
let sortInAscendingOrder = codeStringTwo.sorted(by: { (char1, char2) in
    if let num1 = letterValues[String(char1)], let num2 = letterValues[String(char2)] {
        return num1 < num2
    }
    return char1 < char2
})
print("String sorted in ascending order by the values in the dictionary:",sortInAscendingOrder, separator: "\n", terminator: "\n\n")
```

## Question 15

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

```swift
let firstAndLastTuples = [("Johann S.", "Bach"),
                          ("Claudio", "Monteverdi"),
                          ("Duke", "Ellington"),
                          ("W. A.", "Mozart"),
                          ("Nicolai","Rimsky-Korsakov"),
                          ("Scott","Joplin"),
                          ("Josquin","Des Prez")]

let tuplesSortedByLastName = firstAndLastTuples.sorted(by: { (tuple1, tuple2) in
    tuple1.1 < tuple2.1
})

for tuple in tuplesSortedByLastName {
    print(tuple.1,tuple.0,separator: ", ")
}
```

## Question 16

a) Write a function called `myFilter` that takes an array of Doubles and a closure as parameters and returns an array of Doubles. The closure should take a Double and return a Bool. The function should apply the closure to the doubles in the array.

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

```swift
// Write a function called `myFilter` that takes an array of Double and a closure as parameters and returns an array of Double. The closure should take a Double and return a Bool. The function should apply the closure to the doubles in the array.
func myFilter(arr: [Double], filter closure: (Double) -> Bool) -> [Double] {
    var filteredArr = [Double]()

    for double in arr where closure(double){
        filteredArr.append(double)
    }
    return filteredArr
}

let theDoubles = [11.45, 3.2, 4.0, 5.67, 58.65, 66.0, 5.2, 5.0]

// b) Define a closure assigned to a constant called `biggerThanTen` that takes a double and returns true if it is greater or equal to 10.0 and pass it to `myFilter`.
let biggerThanTen = { (a: Double) -> Bool in
    return a >= 10
}

let a = myFilter(arr: theDoubles, filter: biggerThanTen)
print("theDoubles array filtered by numbers bigger than ten:",a, separator: "\n", terminator: "\n\n")

// c) Define a closure assigned to a constant called `wholeNumber` that takes a double and returns true if it is a whole number and pass it to `myFilter`.
let wholeNumber = { (a: Double) -> Bool in
    return a == Double(Int(a))
}
let b = myFilter(arr: theDoubles, filter: wholeNumber)
print("theDoubles array filtered by whole numbers:",b, separator: "\n", terminator: "\n\n")

// d) Define a closure assigned to a constant called `justEven` that takes a double and returns true if the number to the left of the point is even and pass it to `myFilter`.
let justEven = { (a: Double) -> Bool in
    return Int(a) % 2 == 0
}
let c = myFilter(arr: theDoubles, filter: justEven)
print("theDoubles array filtered by even whole numbers:",c, separator: "\n", terminator: "\n\n")

// e. Use the built in filter method on `theDoubles` to recreate the answers for b, c and d.
let biggerThanTenUsingFilter = theDoubles.filter({ $0 >= 10 })
print("theDoubles array filtered by numbers bigger than ten using filter:",biggerThanTenUsingFilter, separator: "\n", terminator: "\n\n")

let wholeNumberUsingFilter = theDoubles.filter({ $0 == Double(Int($0)) })
print("theDoubles array filtered by whole numbers using filter:",wholeNumberUsingFilter, separator: "\n", terminator: "\n\n")

let justEvenUsingFilter = theDoubles.filter({ Int($0) % 2 == 0 })
print("theDoubles array filtered by even whole numbers using filter:",justEvenUsingFilter, separator: "\n", terminator: "\n\n")
```