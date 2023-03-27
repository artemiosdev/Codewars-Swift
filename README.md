<!--
<h1><a href="https://www.codewars.com/users/artemiosdev">Codewars</a><img src="images/codewars.gif" height="44" align="right"></h1>
-->

<h1><a href="https://www.codewars.com/users/artemiosdev">Codewars</a><a href="https://gph.is/st/mqqDGdx"><img src="https://git.io/JMd4a" height="44" align="right"></a></h1>

<div>
<a href="https://codewars.com/users/artemiosdev"><img src="https://www.codewars.com/users/artemiosdev/badges/large" align="left"></img></a>
</div>
<br>
<hr>
<br>

### 8 kyu

### [Sum The Strings](https://www.codewars.com/kata/5966e33c4e686b508700002d/swift)

Create a function that takes 2 integers in form of a string as an input, and outputs the sum (also as a string):

Example: `(Input1, Input2 -->Output)`

Notes:

- If either input is an empty string, consider it as zero.

- Inputs and the expected output will never exceed the signed 32-bit integer limit (2^31 - 1)

My solution:
```swift
func sum_str(_ a:String, _ b:String) -> String {
    let a = Int(a) ?? 0
    let b = Int(b) ?? 0
    let result = a + b
    return String(result)
}

print(sum_str(".","-9")) // -9
print(sum_str("8","-8")) // 0
print(sum_str("2","-")) // 2
print(sum_str(",","+")) // 0
```

Other solutions:
```swift
func sum_str(_ a:String, _ b:String) -> String {
    return String((Int(a) ?? 0) + (Int(b) ?? 0))
}
```

```swift
func sum_str(_ a:String, _ b:String) -> String {
    return String(convertStringToInt(a) + convertStringToInt(b))
}

func convertStringToInt(_ str: String) -> Int {
  return (str as NSString).integerValue
}
```

---

### [Multiplication table for number](https://www.codewars.com/kata/5a2fd38b55519ed98f0000ce/swift)

Your goal is to return multiplication table for number that is always an integer from 1 to 10.

Use [joined](https://developer.apple.com/documentation/swift/array/joined()) - Returns the elements of this sequence of sequences, concatenated.

My solution:
```swift
func multi_table(_ number: Int) -> String {
        var arrayResults: [String] = []
    for i in 1...10 {
        arrayResults.append("\(i) * \(number) = \(i * number)")
    }
    let result = arrayResults.joined(separator:"\n")
    return result
}
print(multi_table(5))
```

Other solutions:
```swift
func multi_table(_ number: Int) -> String {
    (1...10).map {"\($0) * \(number) = \($0 * number)"}.joined(separator: "\n")
}
print(multi_table(5))
```

```bash
1 * 5 = 5
2 * 5 = 10
3 * 5 = 15
4 * 5 = 20
5 * 5 = 25
6 * 5 = 30
7 * 5 = 35
8 * 5 = 40
9 * 5 = 45
10 * 5 = 50
```

---

### [Gravity Flip](https://www.codewars.com/kata/5f70c883e10f9e0001c89673/swift)

Examples (input -> output):

`'R', [3, 2, 1, 2]      ->  [1, 2, 2, 3]`

`'L', [1, 4, 5, 3, 5 ]  ->  [5, 5, 4, 3, 1]`

My solution:
```swift
func flip(_ direction: String, _ a: [Int]) -> [Int] {
    guard a.count > 1 else { return a }
    var newArray: [Int] = []
    if direction == "R" {
        newArray = a.sorted { $0 < $1 }
    } else if direction == "L" {
        newArray = a.sorted { $0 > $1 }
    }
    return newArray
}

print(flip("R", [3, 2, 1, 2]))    // [1, 2, 2, 3]
print(flip("L", [1, 4, 5, 3, 5])) // [5, 5, 4, 3, 1])
```

Mетод `.sort` сортирует оригинальный массив, а метод `sorted()` возвращает новый отсортированный массив, никак не изменяя старый.

---

### [Stringy Strings](https://www.codewars.com/kata/563b74ddd19a3ad462000054)

Write me a function stringy that takes a size and returns a string of alternating '1s' and '0s'.

The string should start with a 1.

A string with size 6 should return : `'101010'.

With size 4 should return : `'1010'`.

With size 12 should return : `'101010101010'`.

The size will always be positive and will only use whole numbers.

My solution:
```swift
func stringy(_ size: Int) -> String {
    var result = [String]()
    var i = 0
    while i < size {
        i += 1
        result.append("\(i % 2)")
    }
    return result.joined()
}

print(stringy(1)) // "1"
print(stringy(2)) // "10"
print(stringy(3)) // "101"
```

Other solutions:
```swift
func stringy(_ size: Int) -> String {
    if size % 2 == 0 {
        return String(repeating: "10", count: size / 2)
    } else {
        return "1" + String(repeating: "01", count: size / 2)
    }
}
```

```swift
func stringy(_ size: Int) -> String {
    var newString = ""
    for i in 1...size {
        newString += "\(i % 2)"
    }
    return newString
}
```


---

### [Is he gonna survive?](https://www.codewars.com/kata/59ca8246d751df55cc00014c)

A hero is on his way to the castle to complete his mission. However, he's been told that the castle is surrounded with a couple of powerful dragons! each dragon takes 2 bullets to be defeated, our hero has no idea how many bullets he should carry.. Assuming he's gonna grab a specific given number of bullets and move forward to fight another specific given number of dragons, will he survive?

Return True if yes, False otherwise 

My solution:
```swift
func hero(bullets: Int, dragons: Int) -> Bool {
    return bullets >= dragons * 2
}

print(hero(bullets: 4, dragons: 2)) // true
print(hero(bullets: 1, dragons: 3)) // false
print(hero(bullets: 11, dragons: 5)) // true
```

---

### [Get Planet Name By ID](https://www.codewars.com/kata/515e188a311df01cba000003)

The function is not returning the correct values. Can you figure out why?

Example (Input --> Output ):

`3 --> "Earth"`

My solution:
```swift
func getPlanetName(_ id: Int) -> String {
  var name:String
  switch id {
    case 1: 
      name = "Mercury"
    case 2: 
      name = "Venus"
    case 3: 
      name = "Earth"
    case 4: 
      name = "Mars"
    case 5: 
      name = "Jupiter"
    case 6: 
      name = "Saturn"
    case 7: 
      name = "Uranus"
    case 8: 
      name = "Neptune"
    default:
      name = ""
  } 
  return name
}
```

----

### [Quarter of the year](https://www.codewars.com/kata/5ce9c1000bab0b001134f5af)

Given a month as an integer from 1 to 12, return to which quarter of the year it belongs as an integer number.

For example: month 2 (February), is part of the first quarter; month 6 (June), is part of the second quarter; and month 11 (November), is part of the fourth quarter.

Constraint:

`1 <= month <= 12`

My solution:
```swift
func quarter(of month: Int) -> Int {
     switch month {
    case 1...3: return 1
    case 4...6: return 2
    case 7...9: return 3
    case 10...12: return 4
    default: print("error")
    }
  return month
}

print(quarter(of: 8)) // 3
print(quarter(of: 3)) // 1
print(quarter(of: 11)) // 4
```

Other solutions:
```swift
func quarter(of month: Int) -> Int {
    let months = [
        1: [1, 2, 3],
        2: [4, 5, 6],
        3: [7, 8, 9],
        4: [10, 11, 12]
    ]
    for (key, values) in months where values.contains(month) {
        return key
    }
    return 0
}
```

---

### [A wolf in sheep's clothing](https://www.codewars.com/kata/5c8bfa44b9d1192e1ebd3d15)

Warn the sheep in front of the wolf that it is about to be eaten. Remember that you are standing at the front of the queue which is at the end of the array:

`[sheep, sheep, sheep, sheep, sheep, wolf, sheep, sheep]      (YOU ARE HERE AT THE FRONT OF THE QUEUE)`

   `7      6      5      4      3            2      1`

If the wolf is the closest animal to you, return "Pls go away and stop eating my sheep". Otherwise, return "Oi! Sheep number N! You are about to be eaten by a wolf!" where N is the sheep's position in the queue.

Note: there will always be exactly one wolf in the array.

Examples:

`Input: ["sheep", "sheep", "sheep", "wolf", "sheep"]`

`Output: "Oi! Sheep number 1! You are about to be eaten by a wolf!"`

`Input: ["sheep", "sheep", "wolf"]`

`Output: "Pls go away and stop eating my sheep"`

My solution:
```swift
func warnTheSheep(_ queue: [String]) -> String {
    var alertString = ""
    let numberWolf = Array(queue.reversed()).firstIndex(where: { $0 == "wolf" })!
    if numberWolf > 0 {
        alertString = "Oi! Sheep number \(numberWolf)! You are about to be eaten by a wolf!"
    } else {
        alertString = "Pls go away and stop eating my sheep"
    }
    return alertString
}
```

Other solutions:
```swift
func warnTheSheep(_ queue: [String]) -> String {
    let num = queue.count - queue.firstIndex(of: "wolf")! - 1
    return num == 0
    ? "Pls go away and stop eating my sheep"
    : "Oi! Sheep number \(num)! You are about to be eaten by a wolf!"
}
```

```swift
func warnTheSheep(_ queue: [String]) -> String {
    let wolfIndex = queue.firstIndex(of: "wolf") ?? 0
    return queue.last == "wolf"
    ? "Pls go away and stop eating my sheep"
    : "Oi! Sheep number \(queue.count - wolfIndex - 1)! You are about to be eaten by a wolf!"
}

warnTheSheep(["sheep", "sheep", "sheep", "sheep", "sheep", "wolf", "sheep", "sheep"])
// "Oi! Sheep number 2! You are about to be eaten by a wolf!"

warnTheSheep(["sheep", "wolf", "sheep", "sheep", "sheep", "sheep", "sheep"])
// "Oi! Sheep number 5! You are about to be eaten by a wolf!"

warnTheSheep(["sheep", "sheep", "wolf"]) // "Pls go away and stop eating my sheep"

warnTheSheep(["wolf"]) // "Pls go away and stop eating my sheep"
```

---

### [Expressions Matter](https://www.codewars.com/kata/5ae62fcf252e66d44d00008e)

Given three integers `a ,b ,c`, return the largest number obtained after inserting the following operators and brackets: `+, *, ()`

In other words , try every combination of `a,b,c` with `[*+()]` , and return the Maximum Obtained

Example:

With the numbers are 1, 2 and 3 , here are some ways of placing signs and brackets:

```bash
1 * (2 + 3) = 5
1 * 2 * 3 = 6
1 + 2 * 3 = 7
(1 + 2) * 3 = 9
```

So the maximum value that you can obtain is 9.

Notes:

- The numbers are always positive.
- The numbers are in the range (1  ≤  a, b, c  ≤  10).
- You can use the same operation more than once.
- It's not necessary to place all the signs and brackets.
- Repetition in numbers may occur .
- You cannot swap the operands. For instance, in the given example you cannot get expression `(1 + 3) * 2 = 8`

**Input >> Output Examples:**

`expressionsMatter(1,2,3)  ==>  return 9`

Explanation:
After placing signs and brackets, the Maximum value obtained from the expression `(1+2) * 3 = 9`.

or 

`expressionsMatter(1,1,1)  ==>  return 3`
Explanation:
After placing signs, the Maximum value obtained from the expression is `1 + 1 + 1 = 3`.

or 

`expressionsMatter(9,1,1)  ==>  return 18`

`9 * (1+1) = 18`

My solution:
```swift
func expressionMatter(_ a: Int, _ b: Int, _ c: Int) -> Int {
    var results: [Int] = []
    results.append(a * (b + c))
    results.append(a * b * c)
    results.append(a + b * c)
    results.append((a + b) * c)
    results.append(a + b + c)
    return results.max()!
}

print(expressionMatter(2, 1, 2)) // 6
print(expressionMatter(2, 1, 1)) // 4
print(expressionMatter(1, 1, 1)) // 3
print(expressionMatter(1, 2, 3)) // 9
print(expressionMatter(1, 3, 1)) // 5
print(expressionMatter(2, 2, 2)) // 8
```

Other solutions:
```swift
func expressionMatter(_ a: Int, _ b: Int, _ c: Int) -> Int {
  return max(a + b + c, (a + b) * c, a * (b + c),  a * b * c)
}
```

```swift
func expressionMatter(_ a: Int, _ b: Int, _ c: Int) -> Int {
    let possibleValues = [
      a * (b + c),
      a * b * c,
      a + b * c,
      a * b + c,
      (a + b) * c,
      a + b + c
    ]
    return possibleValues.max() ?? 3
}
```

---

### [Century From Year](https://www.codewars.com/kata/5a3fe3dde1ce0e8ed6000097)

The first century spans from the year 1 up to and including the year 100, the second century - from the year 101 up to and including the year 200, etc.

Task:
Given a year, return the century it is in.

Examples:

```bash
1705 --> 18
1900 --> 19
1601 --> 17
2000 --> 20
```

My solution:
```swift
func century(_ year: Int) -> Int {
    if year < 100 {
        return 1
    } else if year % 100 == 0 {
        return year / 100
    }
    return (year / 100) + 1
}
```

Other solutions:
```swift
func century(_ year: Int) -> Int {
    let century = year % 100 == 0 ? (year / 100) : (year / 100) + 1
    return century
}
```

---

### [Reversed sequence](https://www.codewars.com/kata/5a00e05cc374cb34d100000d)

Build a function that returns an array of integers from n to 1 where n>0.

Example : `n=5 --> [5,4,3,2,1]`

My solution:
```swift
func reverseSeq(n: Int) -> [Int] {
    var result: [Int] = []
    for i in 1...n {
        result.append(i)
    }
    return result.reversed()
}
print(reverseSeq(n: 5)) //  [5,4,3,2,1]
```

Other solutions:
```swift
func reverseSeq(n: Int) -> [Int] {
  return (1...n).reversed()
}
// or
// подробнее func reversed() -> [Self.Element]
// 0(n)

func reverseSeq(n: Int) -> [Int] {
  let r = 1...n
  return r.reversed()
}
```

---

### [Get Nth Even Number](https://www.codewars.com/kata/5933a1f8552bc2750a0000ed)

Return the Nth Even Number

Example(Input --> Output)

```bash
1 --> 0 (the first even number is 0)
3 --> 4 (the 3rd even number is 4 (0, 2, 4))
100 --> 198
1298734 --> 2597466
```

The input will not be 0.

My solution:
```swift
func nthEven(_ n: Int) -> Int {
    return 2 * n - 2
}

print(nthEven(1))  // 0
print(nthEven(2))  // 2
print(nthEven(3))  // 4
print(nthEven(100))  // 198
print(nthEven(1298734))  // 2597466
```

---

### [Find the first non-consecutive number](https://www.codewars.com/kata/58f8a3a27a5c28d92e000144)

Your task is to find the first element of an array that is not consecutive.

By not consecutive we mean not exactly 1 larger than the previous element of the array.

E.g. If we have an array `[1,2,3,4,6,7,8]` then 1 then 2 then 3 then 4 are all consecutive but 6 is not, so that's the first non-consecutive number.

If the whole array is consecutive then `return null^2`.

The array will always have at least 2 elements^1 and all elements will be numbers. The numbers will also all be unique and in ascending order. The numbers could be positive or negative and the first non-consecutive could be either to

My solution:

```swift
func firstNonConsecutive (_ arr: [Int]) -> Int? {
    let sortedArray = arr.sorted()
    var result = sortedArray.first ?? 0
    for i in sortedArray {
        if i - result > 1 {
            result = i
            return result
        }
        result = i
    }
    if result == sortedArray.last {
        return nil
    } else {
        return result
    }
}
```

Other solutions:
```swift
func firstNonConsecutive (_ arr: [Int]) -> Int? {
    for i in 1..<arr.count where arr[i] - arr[i-1] > 1 {
        return arr[i]
    }
    return nil
}

print(firstNonConsecutive([1,2,3,4,6,7,8]))  // 6
```

---

### [Difference of Volumes of Cuboids](https://www.codewars.com/kata/58cb43f4256836ed95000f97)

In this simple exercise, you will create a program that will take two lists of integers, a and b. Each list will consist of 3 positive integers above 0, representing the dimensions of cuboids a and b. You must find the difference of the cuboids' volumes regardless of which is bigger.

For example, if the parameters passed are `([2, 2, 3], [5, 4, 1])`, the volume of a is 12 and the volume of b is 20. Therefore, the function should return 8.


My solution:
```swift
func findDifference(_ a: [Int], _ b: [Int]) -> Int {
    var sum1 = 1
    var sum2 = 1
    
    for i in a {
        sum1 *= i
    }
    for i in b {
        sum2 *= i
    }
    
    if sum1 >= sum2{
        return sum1 - sum2
    } else {
        return sum2 - sum1
    }
}
findDifference([3, 2, 5], [1, 4, 4]) // 14
findDifference([9, 7, 2], [5, 2, 2]) // 106
```

Use [reduce(_:_:)](https://developer.apple.com/documentation/swift/array/reduce(_:_:)) - Returns the result of combining the elements of the sequence using the given closure.

Other solutions:
```swift
func findDifference(_ a: [Int], _ b: [Int]) -> Int {
    return a.reduce(1,*) - b.reduce(1,*)
}
```

---

### [Simple multiplication](https://www.codewars.com/kata/583710ccaa6717322c000105)

This kata is about multiplying a given number by 8 if it is an even number and by 9 otherwise.

My solution:
```swift
func simpleMultiplication(_ num: Int) -> Int {
  return num % 2 == 0 ? num * 8 : num * 9
}
```

Other solutions:
```swift
func simpleMultiplication(_ num: Int) -> Int{
        return num * (num % 2 + 8)
}

// or

func simpleMultiplication(_ num: Int) -> Int {
  num.isMultiple(of: 2) ? num * 8 : num * 9 
}
```

---

### [Switch it Up!](https://www.codewars.com/kata/5808dcb8f0ed42ae34000031)

When provided with a number between 0-9, return it in words.

My solution:
```swift
func switchItUp(_ number: Int) -> String {
    switch number {
    case 0:
        return "Zero"
    case 1:
        return "One"
    case 2:
        return "Two"
    case 3:
        return "Three"
    case 4:
        return "Four"
    case 5:
        return "Five"
    case 6:
        return "Six"
    case 7:
        return "Seven"
    case 8:
        return "Eight"
    case 9:
        return "Nine"
    default:
        return "Wrong input"
    }
}

print(switchItUp(8)) // Eight
```

Other solutions:
```swift
func switchItUp(_ number: Int) -> String {
    let array = ["Zero", "One", "Two", "Three", "Four", "Five", "Six", "Seven", "Eight", "Nine"]
    return array[number]
}
```

```swift
import Foundation 

func switchItUp(_ number: Int) -> String {
  let formatter = NumberFormatter()
  formatter.numberStyle = NumberFormatter.Style.spellOut
  return formatter.string(from: NSNumber(value: number))!.capitalized
}
```

```swift
import Foundation

func switchItUp(_ number: Int) -> String {
  return NumberFormatter.localizedString(from: number as NSNumber, number: .spellOut).capitalized
}
```

---

### [Beginner - Lost Without a Map](https://www.codewars.com/kata/57f781872e3d8ca2a000007e)

Given an array of integers, return a new array with each value doubled.

For example:

`[1, 2, 3] --> [2, 4, 6]`

My solution:
```swift
func maps(a : Array<Int>) -> Array<Int> {
    var array: [Int] = []
    for index in a {
        let newNumber = index + index
        array.append(newNumber)
    }
    return array
}
```

Other solutions:
```swift
func maps(a : Array<Int>) -> Array<Int> {
    return a.map { $0 * 2}
}
```

```swift
func maps(a : Array<Int>) -> Array<Int> {
  var result: [Int] = []
  for n in a {
     result.append(n*2)
  }
  return result
}
```

```swift
func maps(a : Array<Int>) -> Array<Int> {
  var b = a;
  for i in 0 ..< a.count {
    b[i] = a[i] * 2
  }
  return b;
}
```

---

### [Beginner - Reduce but Grow](https://www.codewars.com/kata/57f780909f7e8e3183000078)

Given a non-empty array of integers, return the result of multiplying the values together in order. Example:

`[1, 2, 3, 4] => 1 * 2 * 3 * 4 = 24`

My solution:
```swift
func grow(_ arr: [Int]) -> Int {
    var b = 1
    arr.forEach { index in
        b *= index
    }
    return b;
}
```

Other solutions:
```swift
func grow(_ arr: [Int]) -> Int {
  return arr.reduce(1,*)
}
```

```swift
func grow(_ arr: [Int]) -> Int {
    var product = 1
    for num in arr {
        product *= num
    }
    return product
}
```

---

### [To square(root) or not to square(root)](https://www.codewars.com/kata/57f6ad55cca6e045d2000627)

Write a method, that will get an integer array as parameter and will process every number from this array.

Return a new array with processing every number of the input-array like this:

If the number has an integer square root, take this, otherwise square the number.

Example

`[4,3,9,7,2,1] -> [2,9,3,49,4,1]`

Notes
The input array will always contain only positive numbers, and will never be empty or null.

My solution:
```swift
import Foundation

func squareOrSquareRoot(_ input: [Int]) -> [Int] {
      return input.map {
        let n = sqrt(Double($0))
        return n == Double(Int(n)) ? Int(n) : $0 * $0
    }
}

print(squareOrSquareRoot([4, 3, 9, 7, 2, 1])) // [2, 9, 3, 49, 4, 1]
```

Use [truncatingRemainder(dividingBy:)](https://developer.apple.com/documentation/swift/double/truncatingremainder(dividingby:)) - Returns the remainder of this value divided by the given value using truncating division.

Other solutions:
```swift
import Foundation

func squareOrSquareRoot(_ input: [Int]) -> [Int] {
    return input.map { i in
        let r = sqrt(Double(i))
        return r.truncatingRemainder(dividingBy: 1).isZero ? Int(r) : i * i
    }
}
```

Use [floor()](https://www.educative.io/answers/what-is-the-floor-function-in-swift)

```swift
func squareOrSquareRoot(_ input: [Int]) -> [Int] {
    var result = [Int]()
    for item in input {
        let square = Double(item).squareRoot()
        if floor(square) == square {
            result.append(Int(square))
        } else {
            result.append(item * item)
        }
    }
    return result
}
```

---

### [Sum Mixed Array](https://www.codewars.com/kata/57eaeb9578748ff92a000009)

Given an array of integers as strings and numbers, return the sum of the array values as if all were numbers.

Return your answer as a number.

My solution:
```swift
func sumMix(_ arr: [Any]) -> Int {
  var sum = 0
  for item in arr {
    if let test = item as? String {
      sum += Int(test)!
    } else {
        sum += item as! Int
    }
  }
  return sum
}

print(sumMix([9, 3, "7", "3"])) // 22
```

Other solutions:
```swift
func sumMix(_ arr: [Any]) -> Int {
    return arr.reduce(0) { $0 + (Int("\($1)") ?? 0) }
}
```

[compactMap(_:)](https://developer.apple.com/documentation/swift/sequence/compactmap(_:)) - Returns an array containing the non-nil results of calling the given transformation with each element of this sequence.

```swift
func sumMix(_ arr: [Any]) -> Int {
  return arr
          .compactMap { Int("\($0)") }
          .reduce(0,+)
}
```

```swift
func sumMix(_ arr: [Any]) -> Int {
  return arr.map{ $0 as? Int ?? Int($0 as? String ?? "0")! }.reduce(0, +)
}
```

---

### [Fake Binary](https://www.codewars.com/kata/57eae65a4321032ce000002d)

Given a string of digits, you should replace any digit below 5 with '0' and any digit 5 and above with '1'. Return the resulting string.

Note: input will never be an empty string

My solution:
```swift
func fakeBin(digits: String) -> String {
  var newString: String = ""
  for char in digits {
    if let number = Int(String(char)) {
      if(number < 5) {
        newString += "0"
      } else {
        newString += "1"
      }
    }
  }
  return newString
}
fakeBin(digits: "45385593107843568") // 01011110001100111
```

Other solutions:
```swift
func fakeBin(digits: String) -> String {
  return digits.map({$0 < "5" ? "0" : "1"}).joined()
}
```

```swift
func fakeBin(digits: String) -> String {
    digits.reduce("") { $0 + ("01234".contains($1) ? "0" : "1") }
    
// or
// digits.reduce("") { $0 + ($1 < "5" ? "0" : "1") }
}
```

---

### [You only need one - Beginner](https://www.codewars.com/kata/57cc975ed542d3148f00015b)

You will be given an array `a` and a value `x`. All you need to do is check whether the provided array contains the value.

The type of `a` and `x` can be `String` or `Int`.

Return true if the array contains the value, false if not.

My solution:
```swift
func check<T: Equatable>(_ a: [T], _ x: T) -> Bool {
    if a.contains(x) {
        return true
    } else {
        return false
    }
}
print(check(["t", "e", "s", "t"], "e")) //true
```

Other solutions:
```swift
func check<T: Equatable>(_ a: [T], _ x: T) -> Bool {
    return a.contains(x)
}

// or
func check<T: Equatable>(_ a: [T], _ x: T) -> Bool {
    return a.contains(where: { $0 == x})
}
```

---

### [Calculate BMI](https://www.codewars.com/kata/57a429e253ba3381850000fb)

Write function bmi that calculates body mass index (`bmi = weight / (height * height)`).

```bash
if bmi <= 18.5 return "Underweight"
if bmi <= 25.0 return "Normal"
if bmi <= 30.0 return "Overweight"
if bmi > 30 return "Obese"
```

My solution:
```swift
func bmi(_ weight: Int, _ height: Double) -> String {
    let bmiValue = Double(weight) / (height * height)
    var stringResult = ""
    if bmiValue <= 18.5 { stringResult = "Underweight" }
    else if bmiValue <= 25.0 { stringResult = "Normal" }
    else if bmiValue <= 30.0 { stringResult = "Overweight" }
    else if bmiValue > 30 { stringResult = "Obese"}
    return stringResult
}
```

Other solutions:
```swift
enum BMIKind: CustomStringConvertible {
    case underweight
    case normal
    case overweight
    case obese
    
    var description: String {
        switch self {
        case .underweight:
            return "Underweight"
        case .normal:
            return "Normal"
        case .overweight:
            return "Overweight"
        case .obese:
            return "Obese"
        }
    }

    init(bmiIndex: Double) {
        if bmiIndex <= 18.5 {
            self = .underweight
        } else if bmiIndex <= 25.0 {
            self = .normal
        } else if bmiIndex <= 30.0 {
            self = .overweight
        } else {
            self = .obese
        }
    }
}

struct BMIIndex {
    var rawValue: Double
    init(weight: Int, height: Double) {
        rawValue = Double(weight) / (height * height)
    }
}

func bmi(_ weight: Int, _ height: Double) -> String {
    let bmiIndex = BMIIndex(weight: weight, height: height)
    let bmiKind = BMIKind(bmiIndex: bmiIndex.rawValue)
    return bmiKind.description
}
```

---

### [String repeat](https://www.codewars.com/kata/57a0e5c372292dd76d000d7e)

Write a function that accepts an integer `n` and a string `s` as parameters, and returns a string of s repeated exactly `n` times.

Examples (input -> output)

```bash
6, "I"     -> "IIIIII"
5, "Hello" -> "HelloHelloHelloHelloHello"
```

My solution:
```swift
func repeatStr(_ n: Int, _ string: String) -> String {
    var repeatString = ""
    if n > 0 {
        for _ in 1...n {
            repeatString += string
        }
    }
    return repeatString
}

print(repeatStr(3, "Hello")) // HelloHelloHello
```

Other solutions:
```swift

func repeatStr(_ n: Int, _ string: String) -> String {
  return String(repeating: string, count: n)
}
```

---

### [Grasshopper - Personalized Message](https://www.codewars.com/kata/5772da22b89313a4d50012f7)

Create a function that gives a personalized greeting. This function takes two parameters: name and owner.

Use conditionals to return the proper message:

case	return

`name equals owner	-> 'Hello boss'`
`otherwise	-> 'Hello guest'`

My solution:
```swift
func great(_ name: String, _ owner: String) -> String {
    if name == owner {
        return "Hello boss"
    } else {
        return "Hello guest"
    }
}

print(great("Daniel", "Daniel")) // Hello boss
print(great("Greg", "Daniel")) // Hello guest
```

Other solutions:
```swift
func great(_ name: String, _ owner: String) -> String {
  return "Hello \(name == owner ? "boss" : "guest")"
}
```

```swift
func great(_ name: String, _ owner: String) -> String {
  return name == owner ? "Hello boss" : "Hello guest"
}
```

---

### [Sum of positive](https://www.codewars.com/kata/5715eaedb436cf5606000381)

You get an array of numbers, return the sum of all of the positives ones.

Example `[1,-4,7,12] => 1 + 7 + 12 = 20`

Note: if there is nothing to sum, the sum is default to 0.

My solution:
```swift
func sumOfPositives (_ numbers: [Int] ) -> Int {
    var result: Int = 0
  for index in numbers {
    if index > 0 {
      result += index
    } else {
      continue
    }
  }
    return result
}
sumOfPositives([1,2,3,4,5]) // 15
sumOfPositives([1,-2,3,4,5]) // 13
```

Other solutions:
```swift
func sumOfPositives (_ numbers: [Int] ) -> Int {
    var x = 0
    numbers.forEach {
        if $0 > 0 {
            x += $0
        }
    }
    return x
}
```

```swift
func sumOfPositives (_ numbers: [Int] ) -> Int {
    return numbers.filter{ $0 > 0 }.reduce(0, +)
}
```

```swift
func sumOfPositives (_ numbers: [Int] ) -> Int {
    return numbers.reduce (0) {$0 + max($1, 0)}
}
```

---

### [Count the Monkeys!](https://www.codewars.com/kata/56f69d9f9400f508fb000ba7)

Given the number `n`, populate an array with all numbers up to and including that number, but excluding zero.

For example(Input --> Output):

`10 --> [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]`

` 1 --> [1]`

My solution:
```swift
func monkeyCount(_ n: Int) -> [Int] {
    var results: [Int] = []
    for i in 1...n {
        results.append(i)
    }
    return results
}

monkeyCount(5) // [1, 2, 3, 4, 5]
```

Other solutions:
```swift
func monkeyCount(_ n: Int) -> [Int] {
  guard n > 0 else {return []}
    return Array(1...n)
}
```

```swift
func monkeyCount(_ n: Int) -> [Int] {
    return n > 0 ? [Int](1...n) : []
}
```

```swift
func monkeyCount(_ n: Int) -> [Int] {
  let monkeys = 1...n
  return [Int](monkeys)
}
```

---

### [Opposite number](https://www.codewars.com/kata/56dec885c54a926dcd001095)

Very simple, given an integer or a floating-point number, find its opposite.

Examples:

```bash
1: -1
14: -14
-34: 34
```

Use [abs(_:)](https://developer.apple.com/documentation/swift/abs(_:))

My solution:
```swift
func opposite(number: Double) -> Double {
  var result: Double = 0.0
  if number > 0 {
    result = -number
  } else {
    result = abs(number)
  }
  return result
}
```

Other solutions:
```swift
func opposite(number: Double) -> Double {
  return -number
}
```

---

### [Subtract the Sum](https://www.codewars.com/kata/56c5847f27be2c3db20009c3)

Complete the function which get an input number `n` such that `n >= 10` and `n < 10000`, then:

1. Sum all the digits of `n`.
2. Subtract the sum from `n`, and it is your new `n`.
3. If the new `n` is in the list below return the associated fruit, otherwise return back to task 1.

Example
```bash
n = 325
sum = 3+2+5 = 10
n = 325-10 = 315 (not in the list)
sum = 3+1+5 = 9
n = 315-9 = 306 (not in the list)
sum = 3+0+6 = 9
n =306-9 = 297 (not in the list)
.
.
.
```

...until you find the first n in the list below.

Use [compactMap(_:)](https://developer.apple.com/documentation/swift/sequence/compactmap(_:)) - Returns an array containing the non-nil results of calling the given transformation with each element of this sequence.

[.wholeNumberValue](https://developer.apple.com/documentation/swift/character/wholenumbervalue) - The numeric value this character represents, if it represents a whole number.

My solution:
```swift
func subtractSum(_ n: Int) -> String {
      let number = n - "\(n)".compactMap { Int(String($0)) }.reduce(0, +)
    switch number {
    case 9, 18, 27, 36, 45, 54, 63, 72, 81, 90, 99:
        return "apple"
    case 4, 6, 25, 29, 48, 50, 71, 73, 92, 94, 96:
        return "banana"
    case 20, 22, 41, 43, 62, 64, 66, 85, 87, 89:
        return "cherry"
    case 11, 13, 34, 55, 57, 59, 78, 80:
        return "cucumber"
    case 15, 17, 19, 38, 40, 61, 82, 84, 86:
        return "grape"
    case 1, 3, 24, 26, 47, 49, 68, 70, 91, 93:
        return "kiwi"
    case 5, 7, 28, 30, 32, 51, 53, 74, 76, 95, 97:
        return "melon"
    case 14, 16, 35, 37, 39, 58, 60, 83:
        return "orange"
    case 2, 21, 23, 42, 44, 46, 65, 67, 69, 88:
        return "pear"
    case 8, 10, 12, 31, 33, 52, 56, 75, 77, 79, 98, 100:
        return "pineapple"
    default:
        return subtractSum(number)
    }
}
```


Other solutions:
```swift
func subtractSum1(_ n: Int) -> String {
    let strN = String(n)
    let sum = strN.compactMap{$0.wholeNumberValue}.reduce(0, +)
    var subSum = n - sum
    
    while subSum >= 100 {
        var strN2 = String(subSum)
        var sum2 = strN2.compactMap{$0.wholeNumberValue}.reduce(0, +)
        
        subSum -= sum2
        
    }
    
    switch subSum {
    case 1,3,24,26,47,49,68,70,91,93: return "kiwi"
    case 2,21,23,42,44,46,65,67,69,88: return "pear"
    case 4,6,25,29,48,50,71,73,92,94,96: return "banana"
    case 5,7,28,30,32,51,53,74,76,95,97: return "melon"
    case 8,10,12,31,33,52,56,75,77,79,98,100: return "pineapple"
    case 9,18,27,36,45,54,63,72,81,90,99: return "apple"
    case 11,13,34,55,57,59,78,80: return "cucumber"
    case 14,16,35,37,39,58,60,83: return "orange"
    case 15,17,19,38,40,61,82,84,86: return "grape"
    case 20,22,41,43,62,64,66,85,87,89: return "cheryy"
    default: return ""
    }
}
```

```swift
func subtractSum(_ n: Int) -> String {
    let id: Int = n - "\(n)".compactMap { Int("\($0)") }.reduce(0, { $0 + $1 })
    return fruits[id] != nil ? fruits[id]! : subtractSum(id)
}

let fruits: [Int:String] = [
    1: "kiwi",
    2: "pear",
    3: "kiwi",
    4: "banana",
    5: "melon",
    6: "banana",
    7: "melon",
    8: "pineapple",
    9: "apple",
    10: "pineapple",
    11: "cucumber",
    12: "pineapple",
    13: "cucumber",
    14: "orange",
    15: "grape",
    16: "orange",
    17: "grape",
    18: "apple",
    19: "grape",
    20: "cherry",
    21: "pear",
    22: "cherry",
    23: "pear",
    24: "kiwi",
    25: "banana",
    26: "kiwi",
    27: "apple",
    28: "melon",
    29: "banana",
    30: "melon",
    31: "pineapple",
    32: "melon",
    33: "pineapple",
    34: "cucumber",
    35: "orange",
    36: "apple",
    37: "orange",
    38: "grape",
    39: "orange",
    40: "grape",
    41: "cherry",
    42: "pear",
    43: "cherry",
    44: "pear",
    45: "apple",
    46: "pear",
    47: "kiwi",
    48: "banana",
    49: "kiwi",
    50: "banana",
    51: "melon",
    52: "pineapple",
    53: "melon",
    54: "apple",
    55: "cucumber",
    56: "pineapple",
    57: "cucumber",
    58: "orange",
    59: "cucumber",
    60: "orange",
    61: "grape",
    62: "cherry",
    63: "apple",
    64: "cherry",
    65: "pear",
    66: "cherry",
    67: "pear",
    68: "kiwi",
    69: "pear",
    70: "kiwi",
    71: "banana",
    72: "apple",
    73: "banana",
    74: "melon",
    75: "pineapple",
    76: "melon",
    77: "pineapple",
    78: "cucumber",
    79: "pineapple",
    80: "cucumber",
    81: "apple",
    82: "grape",
    83: "orange",
    84: "grape",
    85: "cherry",
    86: "grape",
    87: "cherry",
    88: "pear",
    89: "cherry",
    90: "apple",
    91: "kiwi",
    92: "banana",
    93: "kiwi",
    94: "banana",
    95: "melon",
    96: "banana",
    97: "melon",
    98: "pineapple",
    99: "apple",
    100: "pineapple"
]
```

```swift
func subtractSum(_ n: Int) -> String {
    var count = n
    var sum = 0
    var newN = n
    var str = ""
    while newN > 0 {
        sum = String(count).compactMap( { $0.wholeNumberValue }).reduce(0, +)
        newN = newN - sum
        count = newN
        if newN > 0 && newN <= 100 {
            switch newN {
            case 1, 3, 24, 26, 47, 49, 68, 70, 91, 93: str = "kiwi"
            case 2, 21, 23, 42, 44, 46, 65, 67, 69, 88: str = "pear"
            case 4, 6, 25, 29, 48, 50, 71, 73, 92, 94, 96: str = "banana"
            case 5, 7, 28, 30, 32, 51, 53, 74, 76, 95, 97: str = "melon"
            case 8, 10, 12, 31, 33, 52, 56, 75, 77, 79, 98, 100: str = "pineapple"
            case 9, 18, 27, 36, 45, 54, 63, 72, 81, 90, 99: str = "apple"
            case 11, 13, 34, 55, 57, 59, 78, 80: str = "cucumber"
            case 14, 16, 35, 37, 39, 58, 60, 83: str = "orange"
            case 15, 17, 19, 38, 40, 61, 82, 84, 86: str = "grape"
            case 20, 22, 41, 43, 62, 64, 66, 85, 87, 89: str = "cherry"
            default: str = ""
            }
        }
    }
    return str
}
```

---

### [Transportation on vacation](https://www.codewars.com/kata/568d0dd208ee69389d000016)

Every day you rent the car costs $40. If you rent the car for 7 or more days, you get $50 off your total. Alternatively, if you rent the car for 3 or more days, you get $20 off your total.

Write a code that gives out the total amount for different days(d).

My solution:
```swift
func RentalCarCost(_ days: Int) -> Int {
    var result: Int = 0
    if days < 3 {
        result = days * 40
   }
    if days >= 3 && days < 7 {
         result = days * 40 - 20
    }
    if days >= 7 {
        result = days * 40 - 50
    }
    return result
}

RentalCarCost(1) // 40
RentalCarCost(2) // 80
RentalCarCost(3) // 100
RentalCarCost(4) // 140
RentalCarCost(5) // 180
RentalCarCost(7) // 230
```

Other solutions:
```swift
func RentalCarCost(_ days: Int) -> Int {
        let rentCostPerDay = 40
        var total = days * rentCostPerDay
        
        if days >= 7 {
            total -= 50
        } else if days >= 3 {
            total -= 20
        }
        return total
}
```

---

### [Get the mean of an array](https://www.codewars.com/kata/563e320cee5dddcf77000158)

Return the average of the given array rounded down to its nearest integer.

The array will never be empty.

My solution:
```swift
func getAverage(_ marks: [Int]) -> Int { 
  return marks.reduce(.zero, +) / marks.count
  // or
  // return marks.reduce(0) {($0 + $1)} / marks.count
}
getAverage([1,2,3,4,5,]) // 3
```

Other solutions:
```swift
func getAverage(_ marks: [Int]) -> Int {
    var sum = 0
    var count = 0
    for i in marks {
        sum += i
        count += 1
    }
    var average = sum / count
    return average //TODO : calculate the downwar rounded average of the marks array
}
```

---

### [Grasshopper - Terminal game move function](https://www.codewars.com/kata/563a631f7cbbc236cf0000c2)

Create a function for the terminal game that takes the current position of the hero and the roll (1-6) and return the new position.

Example:
`move(3, 6) should equal 15`

My solution:
```swift
func move(_ p: Int, _ r: Int) -> Int {
    return p + (r * 2)
}
```

---

### [Beginner Series #2 Clock](https://www.codewars.com/kata/55f9bca8ecaa9eac7100004a)

Clock shows `h` hours, `m` minutes and `s` seconds after midnight.

Your task is to write a function which returns the time since midnight in milliseconds.

Example:

```bash
h = 0
m = 1
s = 1
result = 61000
```

Input constraints:

```bash
0 <= h <= 23
0 <= m <= 59
0 <= s <= 59
```

My solution:
```swift
func past(_ h: Int, _ m: Int, _ s: Int) -> Int {
    return (h * 60 * 60 + m * 60 + s) * 1000
}
past(0, 1, 1) // 61000
past(1, 1, 1) // 3661000
```

---

### [Grasshopper - Summation](https://www.codewars.com/kata/55d24f55d7dd296eb9000030)

Write a program that finds the summation of every number from 1 to num. The number will always be a positive integer greater than 0.

For example (Input -> Output):

```bash
2 -> 3 (1 + 2)
8 -> 36 (1 + 2 + 3 + 4 + 5 + 6 + 7 + 8)
```

My solution:
```swift
func summation(_ n: Int) -> Int {
    return n * ( n + 1 ) / 2
    // or
    // return (1...n).reduce(0){ $0 + $1 }
}

summation(1) // 1
summation(8) // 36
summation(22) // 253
```

```swift
func summation(_ n: Int) -> Int {
         var answer = 0
         for number in 1...n { answer = answer + number }
         return answer
}
```

---

### []()



My solution:
```swift

```

Other solutions:
```swift

```

```swift

```
